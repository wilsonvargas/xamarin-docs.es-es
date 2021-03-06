---
title: Autenticación de usuarios con Azure Active Directory B2C
description: Azure Active Directory B2C proporciona administración de identidades en la nube para aplicaciones web y móviles orientadas al consumidor. En este artículo se muestra cómo usar Azure Active Directory B2C para integrar la administración de identidades en una aplicación móvil con la biblioteca de autenticación de Microsoft.
ms.prod: xamarin
ms.assetid: B0A5DB65-0585-4A00-B908-22CCC286E6B6
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 04/17/2019
ms.openlocfilehash: a13501218b6d3039f189693512d185a9d546d23f
ms.sourcegitcommit: 3434624a36a369986b6aeed7959dae60f7112a14
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69629645"
---
# <a name="authenticate-users-with-azure-active-directory-b2c"></a>Autenticación de usuarios con Azure Active Directory B2C

[![Descargar ejemplo](~/media/shared/download.png) Descargar el ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/webservices-azureadb2cauth)

_Azure Active Directory B2C proporciona administración de identidades en la nube para aplicaciones web y móviles orientadas al consumidor. En este artículo se muestra cómo usar Azure Active Directory B2C para integrar la administración de identidades en una aplicación móvil con la biblioteca de autenticación de Microsoft._

## <a name="overview"></a>Información general

Azure Active Directory B2C (ADB2C) es un servicio de administración de identidades para aplicaciones orientadas al consumidor. Permite a los usuarios iniciar sesión en su aplicación mediante sus cuentas de redes sociales existentes o credenciales personalizadas, como el correo electrónico o el nombre de usuario, y la contraseña. Las cuentas de credenciales personalizadas se conocen como cuentas _locales_ .

El proceso para integrar el servicio de administración de identidades de Azure Active Directory B2C en una aplicación móvil es como sigue:

1. Creación de un inquilino de Azure Active Directory B2C
1. Registro de la aplicación móvil con el inquilino de Azure Active Directory B2C
1. Crear directivas para registro e inicio de sesión y olvidar los flujos de usuario de contraseñas
1. Use la biblioteca de autenticación de Microsoft (MSAL) para iniciar un flujo de trabajo de autenticación con su inquilino de Azure Active Directory B2C.

> [!NOTE]
> Azure Active Directory B2C admite varios proveedores de identidades, como Microsoft, GitHub, Facebook, Twitter, etc. Para obtener más información sobre las funcionalidades de Azure Active Directory B2C, consulte la [documentación de Azure Active Directory B2C](/azure/active-directory-b2c/).
>
> La biblioteca de autenticación de Microsoft admite varias arquitecturas de aplicaciones y plataformas. Para obtener información sobre las funcionalidades de MSAL, consulte [biblioteca de autenticación de Microsoft](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki) en github.

## <a name="configure-an-azure-active-directory-b2c-tenant"></a>Configuración de un inquilino de Azure Active Directory B2C

Para ejecutar el proyecto de ejemplo, debe crear un inquilino de Azure Active Directory B2C. Para obtener más información, consulte [crear un inquilino de Azure Active Directory B2C en Azure portal](/azure/active-directory-b2c/active-directory-b2c-get-started/).

Una vez que cree un inquilino, necesitará el **nombre de inquilino** y el **identificador de inquilino** para configurar la aplicación móvil. El identificador de inquilino y el nombre se definen mediante el dominio que se genera cuando se crea la dirección URL del inquilino. Si la dirección URL del inquilino `https://contoso20190410tenant.onmicrosoft.com/` generada es el `contoso20190410tenant.onmicrosoft.com` **identificador** del inquilino es y `contoso20190410tenant`el nombre del **inquilino** es. Busque el dominio del inquilino en el Azure Portal; para ello, haga clic en el **filtro directorio y suscripción** en el menú superior. En la captura de pantalla siguiente se muestra el botón de filtro de suscripción y el directorio de Azure y el dominio del inquilino:

[![Nombre del inquilino en la vista de filtro de suscripciones y directorios de Azure](azure-ad-b2c-images/azure-tenant-name-cropped.png)](azure-ad-b2c-images/azure-tenant-name.png#lightbox)

En el proyecto de ejemplo, edite el archivo **constants.CS** para `tenantName` establecer `tenantId` los campos y. En el código siguiente se muestra cómo se deben establecer estos valores si el dominio `https://contoso20190410tenant.onmicrosoft.com/`del inquilino es, reemplace estos valores con los valores de su portal:

```csharp
public static class Constants
{
    static readonly string tenantName = "contoso20190410tenant";
    static readonly string tenantId = "contoso20190410tenant.onmicrosoft.com";
    ...
}
```

## <a name="register-your-mobile-application-with-azure-active-directory-b2c"></a>Registre su aplicación móvil con Azure Active Directory B2C

Una aplicación móvil debe estar registrada con el inquilino para poder conectarse y autenticar a los usuarios. El proceso de registro asigna un identificador de **aplicación** único a la aplicación y una **dirección URL** de redireccionamiento que dirige las respuestas de vuelta a la aplicación después de la autenticación. Para más información, consulte [Azure Active Directory B2C: Registre la aplicación](/azure/active-directory-b2c/active-directory-b2c-app-registration/). Deberá conocer el ID. de **aplicación** asignado a la aplicación, que aparece después del nombre de la aplicación en la vista Propiedades. En la captura de pantalla siguiente se muestra dónde encontrar el identificador de la aplicación:

[![IDENTIFICADOR de la aplicación en la vista de propiedades de la aplicación de Azure](azure-ad-b2c-images/azure-application-id-cropped.png)](azure-ad-b2c-images/azure-application-id.png#lightbox)

La biblioteca de autenticación de Microsoft espera que la **dirección URL** de redireccionamiento de la aplicación sea el identificador de la **aplicación** con el prefijo "msal" de texto y seguido por un punto de conexión denominado "auth". Si el identificador de la aplicación es "1234abcd", la dirección URL `msal1234abcd://auth`completa debe ser. Asegúrese de que la aplicación ha habilitado la configuración de **Native Client** y cree un URI de redireccionamiento **personalizado** mediante el identificador de la aplicación, tal como se muestra en la siguiente captura de pantalla:

![URI de redireccionamiento personalizado en la vista de propiedades de la aplicación de Azure](azure-ad-b2c-images/azure-redirect-uri.png)

La dirección URL se usará más adelante en Android **ApplicationManifest. XML** y en iOS **info. plist**.

En el proyecto de ejemplo, edite el archivo **constants.CS** para `clientId` establecer el campo en el identificador de la **aplicación**. En el código siguiente se muestra cómo se debe establecer este valor si el identificador `1234abcd`de la aplicación es:

```csharp
public static class Constants
{
    static readonly string tenantName = "contoso20190410tenant";
    static readonly string tenantId = "contoso20190410tenant.onmicrosoft.com";
    static readonly string clientId = "1234abcd";
    ...
}
```

## <a name="create-sign-up-and-sign-in-policies-and-forgot-password-policies"></a>Crear directivas de registro e inicio de sesión y olvidar las directivas de contraseñas

Una directiva es una experiencia que recorren los usuarios para completar una tarea, como crear una cuenta o restablecer una contraseña. Una directiva también especifica el contenido de los tokens que recibe la aplicación cuando el usuario vuelve de la experiencia. Debe configurar las directivas para el registro y el inicio de sesión de la cuenta y para restablecer la contraseña. Azure tiene directivas integradas que simplifican la creación de directivas comunes. Para más información, consulte [Azure Active Directory B2C: Directivas](/azure/active-directory-b2c/active-directory-b2c-reference-policies/)integradas.

Cuando haya completado la configuración de la Directiva, debe tener dos directivas en la vista **flujos de usuario (directivas)** en el Azure portal. En la captura de pantalla siguiente se muestran dos directivas configuradas en el Azure Portal:

![Dos directivas configuradas en la vista flujos de usuario (directivas) de Azure](azure-ad-b2c-images/azure-application-policies.png)

En el proyecto de ejemplo, edite el archivo **constants.CS** para `policySignin` establecer `policyPassword` los campos y para que reflejen los nombres elegidos durante la configuración de la Directiva:

```csharp
public static class Constants
{
    static readonly string tenantName = "contoso20190410tenant";
    static readonly string tenantId = "contoso20190410tenant.onmicrosoft.com";
    static readonly string clientId = "1234abcd";
    static readonly string policySignin = "B2C_1_signupsignin1";
    static readonly string policyPassword = "B2C_1_passwordreset";
    ...
}
```

## <a name="use-the-microsoft-authentication-library-msal-for-authentication"></a>Usar la biblioteca de autenticación de Microsoft (MSAL) para la autenticación

El paquete NuGet de la biblioteca de autenticación de Microsoft (MSAL) debe agregarse al proyecto compartido, .NET Standard y los proyectos de plataforma en una solución de Xamarin. Forms. MSAL incluye una `PublicClientApplicationBuilder` clase que construye un objeto que se adhiere `IPublicClientApplication` a la interfaz. MSAL emplea `With` cláusulas para proporcionar parámetros adicionales al constructor y a los métodos de autenticación.

En el proyecto de ejemplo, el código subyacente de **app. Xaml** define las propiedades `AuthenticationClient` estáticas denominadas y `UIParent`, `AuthenticationClient` y crea instancias del objeto en el constructor. La `WithIosKeychainSecurityGroup` cláusula proporciona un nombre de grupo de seguridad para las aplicaciones de iOS. La `WithB2CAuthority` cláusula proporciona la **autoridad**o directiva predeterminada que se utilizará para autenticar a los usuarios. En el ejemplo siguiente se muestra cómo crear una `PublicClientApplication`instancia de:

```csharp
public partial class App : Application
{
    public static IPublicClientApplication AuthenticationClient { get; private set; }

    public static object UIParent { get; set; } = null;

    public App()
    {
        InitializeComponent();

        AuthenticationClient = PublicClientApplicationBuilder.Create(Constants.ClientId)
            .WithIosKeychainSecurityGroup(Constants.IosKeychainSecurityGroups)
            .WithB2CAuthority(Constants.AuthoritySignin)
            .Build();

        MainPage = new NavigationPage(new LoginPage());
    }

    ...
```

El `OnAppearing` controlador de eventos en el código de LoginPage.Xaml.CS `AcquireTokenSilentAsync` subyacente llama a para actualizar el token de autenticación para los usuarios que iniciaron sesión antes. El proceso de autenticación redirige a `LogoutPage` si es correcto y no realiza ninguna acción en caso de error. En el ejemplo siguiente se muestra el proceso de reautenticación `OnAppearing`silenciosa en:

```csharp
public partial class LoginPage : ContentPage
{
    ...

    protected override async void OnAppearing()
    {
        try
        {
            // Look for existing account
            IEnumerable<IAccount> accounts = await App.AuthenticationClient.GetAccountsAsync();

            AuthenticationResult result = await App.AuthenticationClient
                .AcquireTokenSilent(Constants.Scopes, accounts.FirstOrDefault())
                .ExecuteAsync();

            await Navigation.PushAsync(new LogoutPage(result));
        }
        catch
        {
            // Do nothing - the user isn't logged in
        }
        base.OnAppearing();
    }

    ...
}
```

El `OnLoginButtonClicked` controlador de eventos (que se desencadena cuando se hace clic en el `AcquireTokenAsync`botón de inicio de sesión) llama a. La biblioteca MSAL abre automáticamente el explorador de dispositivos móviles y navega a la página de inicio de sesión. La dirección URL de inicio de sesión, denominada **entidad de certificación**, es una combinación del nombre de inquilino y las directivas definidas en el archivo **constants.CS** . Si el usuario elige la opción Olvidó la contraseña, se devuelve a la aplicación con una excepción, lo que inicia la experiencia de olvido de contraseña. En el ejemplo siguiente se muestra el proceso de autenticación:

```csharp
public partial class LoginPage : ContentPage
{
    ...

    async void OnLoginButtonClicked(object sender, EventArgs e)
    {
        AuthenticationResult result;
        try
        {
            result = await App.AuthenticationClient
                .AcquireTokenInteractive(Constants.Scopes)
                .WithPrompt(Prompt.SelectAccount)
                .WithParentActivityOrWindow(App.UIParent)
                .ExecuteAsync();
    
            await Navigation.PushAsync(new LogoutPage(result));
        }
        catch (MsalException ex)
        {
            if (ex.Message != null && ex.Message.Contains("AADB2C90118"))
            {
                result = await OnForgotPassword();
                await Navigation.PushAsync(new LogoutPage(result));
            }
            else if (ex.ErrorCode != "authentication_canceled")
            {
                await DisplayAlert("An error has occurred", "Exception message: " + ex.Message, "Dismiss");
            }
        }
    }

    ...
}
```

El `OnForgotPassword` método es similar al proceso de inicio de sesión, pero implementa una directiva personalizada. `OnForgotPassword`utiliza una sobrecarga diferente de `AcquireTokenAsync`, que permite proporcionar una **autoridad**específica. En el ejemplo siguiente se muestra cómo proporcionar una **entidad de certificación** personalizada al adquirir un token:

```csharp
public partial class LoginPage : ContentPage
{
    ...
    async Task<AuthenticationResult> OnForgotPassword()
    {
        try
        {
            return await App.AuthenticationClient
                .AcquireTokenInteractive(Constants.Scopes)
                .WithPrompt(Prompt.SelectAccount)
                .WithParentActivityOrWindow(App.UIParent)
                .WithB2CAuthority(Constants.AuthorityPasswordReset)
                .ExecuteAsync();
        }
        catch (MsalException)
        {
            // Do nothing - ErrorCode will be displayed in OnLoginButtonClicked
            return null;
        }
    }
}
```

La parte final de la autenticación es el proceso de cierre de sesión. Se llama al método cuando el usuario presiona el botón Cerrar sesión. `OnLogoutButtonClicked` Recorre en bucle todas las cuentas y garantiza que sus tokens se han invalidado. En el ejemplo siguiente se muestra la implementación de cierre de sesión:

```csharp
public partial class LogoutPage : ContentPage
{
    ...
    async void OnLogoutButtonClicked(object sender, EventArgs e)
    {
        IEnumerable<IAccount> accounts = await App.AuthenticationClient.GetAccountsAsync();

        while (accounts.Any())
        {
            await App.AuthenticationClient.RemoveAsync(accounts.First());
            accounts = await App.AuthenticationClient.GetAccountsAsync();
        }

        await Navigation.PopAsync();
    }
}
```

### <a name="ios"></a>iOS

En iOS, el esquema de la dirección URL personalizada que se registró con Azure Active Directory B2C debe estar registrado en **info. plist**. MSAL espera que el esquema de la dirección URL se adhiere a un patrón específico, descrito anteriormente en [registrar la aplicación móvil con Azure Active Directory B2C](~/xamarin-forms/data-cloud/authentication/azure-ad-b2c.md#register-your-mobile-application-with-azure-active-directory-b2c). En la captura de pantalla siguiente se muestra el esquema de la dirección URL personalizada en **info. plist**.

!["Registrar un esquema de dirección URL personalizado en iOS"](azure-ad-b2c-images/customurl-ios.png)

MSAL también requiere derechos de cadena de claves en iOS, registrados en **Entitilements. plist**, tal como se muestra en la siguiente captura de pantalla:

!["Configuración de los derechos de aplicación en iOS"](azure-ad-b2c-images/entitlements-ios.png)

Cuando Azure Active Directory B2C se completa la solicitud de autorización, redirige a la URL de redireccionamiento registrados. El esquema de la dirección URL personalizada hace que Ios inicie la aplicación móvil y pase la dirección URL como un parámetro de inicio, donde se `OpenUrl` procesa mediante la invalidación `AppDelegate` de la clase de la aplicación, y devuelve el control de la experiencia a MSAL. La `OpenUrl` implementación se muestra en el ejemplo de código siguiente:

```csharp
using Microsoft.Identity.Client;

namespace TodoAzure.iOS
{
    [Register("AppDelegate")]
    public partial class AppDelegate : global::Xamarin.Forms.Platform.iOS.FormsApplicationDelegate
    {
        ...
        public override bool OpenUrl(UIApplication app, NSUrl url, NSDictionary options)
        {
            AuthenticationContinuationHelper.SetAuthenticationContinuationEventArgs(url);
            return base.OpenUrl(app, url, options);
        }
    }
}
```

### <a name="android"></a>Android

En Android, el esquema de la dirección URL personalizada que se registró con Azure Active Directory B2C debe estar registrado en **archivo AndroidManifest. XML**. MSAL espera que el esquema de la dirección URL se adhiere a un patrón específico, descrito anteriormente en [registrar la aplicación móvil con Azure Active Directory B2C](~/xamarin-forms/data-cloud/authentication/azure-ad-b2c.md#register-your-mobile-application-with-azure-active-directory-b2c). En el ejemplo siguiente se muestra el esquema de la dirección URL personalizada en **archivo AndroidManifest. XML**.

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android" android:versionCode="1" android:versionName="1.0" package="com.xamarin.adb2cauthorization">
  <uses-sdk android:minSdkVersion="15" />
  <application android:label="ADB2CAuthorization">
    <activity android:name="microsoft.identity.client.BrowserTabActivity">
      <intent-filter>
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
        <!-- example -->
        <!-- <data android:scheme="msalaaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee" android:host="auth" /> -->
        <data android:scheme="INSERT_URI_SCHEME_HERE" android:host="auth" />
      </intent-filter>
    </activity>"
  </application>
</manifest>
```

La `MainActivity` clase debe modificarse para proporcionar el `UIParent` objeto a la aplicación durante la `OnCreate` llamada. Cuando Azure Active Directory B2C completa la solicitud de autorización, redirige al esquema de URL registrado desde **archivo AndroidManifest. XML**. El esquema de URI registrado hace que Android llame `OnActivityResult` al método con la dirección URL como parámetro de inicio, donde lo procesa el `SetAuthenticationContinuationEventArgs` método.

```csharp
public class MainActivity : FormsAppCompatActivity
{
    protected override void OnCreate(Bundle bundle)
    {
        TabLayoutResource = Resource.Layout.Tabbar;
        ToolbarResource = Resource.Layout.Toolbar;

        base.OnCreate(bundle);

        Forms.Init(this, bundle);
        LoadApplication(new App());
        App.UIParent = this;
    }

    protected override void OnActivityResult(int requestCode, Result resultCode, Intent data)
    {
        base.OnActivityResult(requestCode, resultCode, data);
        AuthenticationContinuationHelper.SetAuthenticationContinuationEventArgs(requestCode, resultCode, data);
    }
}
```

### <a name="universal-windows-platform"></a>Plataforma universal de Windows

No es necesario realizar ninguna configuración adicional para usar MSAL en el Plataforma universal de Windows

## <a name="run-the-project"></a>Ejecución del proyecto

Ejecute la aplicación en un dispositivo físico o virtual. Al pulsar el botón **Inicio de sesión** , debe abrir el explorador y navegar a una página donde puede iniciar sesión o crear una cuenta. Después de completar el proceso de inicio de sesión, debe volver a la página de cierre de sesión de la aplicación. En la captura de pantalla siguiente se muestra la pantalla de inicio de sesión de usuario que se ejecuta en Android e iOS:

!["Pantalla de inicio de sesión de Azure ADB2C en Android e iOS"](azure-ad-b2c-images/login.png)

## <a name="related-links"></a>Vínculos relacionados

- [AzureADB2CAuth (ejemplo)](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/webservices-azureadb2cauth)
- [Azure Active Directory B2C](/azure/active-directory-b2c/)
- [Biblioteca de autenticación de Microsoft](https://www.nuget.org/packages/Microsoft.Identity.Client)
- [Documentación de la biblioteca de autenticación de Microsoft](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki)
