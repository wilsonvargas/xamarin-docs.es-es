---
title: Referencia de controles de páginas de página
description: En este artículo se presentan los controles que están disponibles en el paquete NuGet de Xamarin. Forms.
ms.prod: xamarin
ms.assetid: 891615D0-E8BD-4ACC-A7F0-4C3725FBCC31
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 12/01/2017
ms.openlocfilehash: e92669d9938b9fe48a1a589e0465acd03f129716
ms.sourcegitcommit: 57f815bf0024b1afe9754c0e28054fc0a53ce302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70759892"
---
# <a name="datapages-controls-reference"></a>Referencia de controles de páginas de página

![](~/media/shared/preview.png "Esta API está actualmente en versión preliminar")

> [!IMPORTANT]
> Las páginas de formularios requieren una referencia de tema de Xamarin. Forms para representar. Esto implica la instalación del paquete de Nuget [Xamarin. Forms. theme. base](https://www.nuget.org/packages/Xamarin.Forms.Theme.Base/) en el proyecto, seguido de los paquetes de Nuget [Xamarin. Forms. theme. Light](https://www.nuget.org/packages/Xamarin.Forms.Theme.Light/) o [Xamarin. Forms. theme. Dark](https://www.nuget.org/packages/Xamarin.Forms.Theme.Dark/) .

Las páginas de datos de Xamarin. Forms Nuget incluyen una serie de controles que pueden aprovechar el enlace de origen de datos.

Para usar estos controles en XAML, asegúrese de que se ha incluido el espacio de nombres, `xmlns:pages` por ejemplo, vea la declaración siguiente:

```xaml
<ContentPage
    xmlns="http://xamarin.com/schemas/2014/forms"
    xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
    xmlns:pages="clr-namespace:Xamarin.Forms.Pages;assembly=Xamarin.Forms.Pages"
    x:Class="DataPagesDemo.Detail">
```

En los ejemplos siguientes `DynamicResource` se incluyen referencias que deben existir en el Diccionario de recursos del proyecto para que funcione. También hay un ejemplo de cómo crear un [control personalizado](#custom) .

## <a name="built-in-controls"></a>Controles integrados

* [HeroImage](#heroimage)
* [ListItem](#listitem)

<a name="heroimage" />

### <a name="heroimage"></a>HeroImage

El `HeroImage` control tiene cuatro propiedades:

* Text
* Detalles
* ImageSource
* 4:3

```xaml
<pages:HeroImage
    ImageSource="{ DynamicResource HeroImageImage }"
    Text="Keith Ballinger"
    Detail="Xamarin"
/>
```

**Android**

![](controls-images/heroimage-light-android.png "Control HeroImage en Android") ![](controls-images/heroimage-dark-android.png "Control HeroImage en Android")

**iOS**

![](controls-images/heroimage-light-ios.png "HeroImage Control en iOS") ![](controls-images/heroimage-dark-ios.png "HeroImage Control en iOS")

<a name="listitem" />

### <a name="listitem"></a>ListItem

El `ListItem` diseño del control es similar a las filas nativas de la tabla o la lista de iOS y Android, pero también se puede usar como vista normal. En el código de ejemplo siguiente `StackLayout`, se muestra hospedado en, pero también se puede usar en controles de lista de scolling enlazados a datos.

Hay cinco propiedades:

* Título
* Detalles
* ImageSource
* PlaceholdImageSource
* 4:3

```xaml
<StackLayout Spacing="0">
    <pages:ListItemControl
        Detail="Xamarin"
        ImageSource="{ DynamicResource UserImage }"
        Title="Miguel de Icaza"
        PlaceholdImageSource="{ DynamicResource IconImage }"
    />
```

Estas capturas `ListItem` de pantallas muestran en las plataformas iOS y Android mediante los temas claro y oscuro:

**Android**

![](controls-images/listitem-light-android.png "Control ListItem en Android") ![](controls-images/listitem-dark-android.png "Control ListItem en Android")

**iOS**

![](controls-images/listitem-light-ios.png "ListItem Control en iOS") ![](controls-images/listitem-dark-ios.png "ListItem Control en iOS")

## <a name="custom-control-example"></a>Ejemplo de control personalizado

El objetivo de este control `CardView` personalizado es similar al CardView nativo de Android.

Contendrá tres propiedades:

* Text
* Detalles
* ImageSource

El objetivo es un control personalizado que se parecerá al código siguiente (tenga en cuenta que se `xmlns:local` requiere un personalizado que haga referencia al ensamblado actual):

```xaml
<local:CardView
  ImageSource="{ DynamicResource CardViewImage }"
  Text="CardView Text"
  Detail="CardView Detail"
/>
```

Debe ser similar a las capturas de pantallas siguientes con los colores correspondientes a los temas de luz y oscuridad integrados:

**Android**

![](controls-images/cardview-light-android.png "Control personalizado CardView en Android") ![](controls-images/cardview-dark-android.png "CardView Custom Control en Android")

**iOS**

![](controls-images/cardview-light-ios.png "Control personalizado de CardView en iOS") ![](controls-images/cardview-dark-ios.png "CardView Custom Control en iOS")

<a name="custom" />

### <a name="building-the-custom-cardview"></a>Compilar el CardView personalizado

1. [DataView (subclase)](#1)
2. [Definir fuente, diseño y márgenes](#2)
3. [Crear estilos para los elementos secundarios del control](#3)
4. [Crear la plantilla de diseño de control](#4)
5. [Agregar los recursos específicos del tema](#5)
6. [Establecer ControlTemplate para la clase CardView](#6)
7. [Agregar el control a una página](#7)

<a name="1" />

#### <a name="1-dataview-subclass"></a>1. DataView (subclase)

La C# subclase de `DataView` define las propiedades enlazables del control.

```csharp
public class CardView : DataView
{
    public static readonly BindableProperty TextProperty =
        BindableProperty.Create ("Text", typeof (string), typeof (CardView), null, BindingMode.TwoWay);

    public string Text
    {
        get { return (string)GetValue (TextProperty); }
        set { SetValue (TextProperty, value); }
    }

    public static readonly BindableProperty DetailProperty =
        BindableProperty.Create ("Detail", typeof (string), typeof (CardView), null, BindingMode.TwoWay);

    public string Detail
    {
        get { return (string)GetValue (DetailProperty); }
        set { SetValue (DetailProperty, value); }
    }

    public static readonly BindableProperty ImageSourceProperty =
        BindableProperty.Create ("ImageSource", typeof (ImageSource), typeof (CardView), null, BindingMode.TwoWay);

    public ImageSource ImageSource
    {
        get { return (ImageSource)GetValue (ImageSourceProperty); }
        set { SetValue (ImageSourceProperty, value); }
    }

    public CardView()
    {
    }
}
```

<a name="2" />

#### <a name="2-define-font-layout-and-margins"></a>2. Definir fuente, diseño y márgenes

El diseñador de controles descifraría estos valores como parte del diseño de la interfaz de usuario para el control personalizado. Cuando se requieren especificaciones específicas de la plataforma, `OnPlatform` se usa el elemento.

Tenga en cuenta que algunos valores `StaticResource`hacen referencia a s: se definirán en el [paso 5](#5).

```xml
<!-- CARDVIEW FONT SIZES -->
<OnPlatform x:TypeArguments="x:Double" x:Key="CardViewTextFontSize">
        <On Platform="iOS, Android" Value="15" />
</OnPlatform>

<OnPlatform x:TypeArguments="x:Double" x:Key="CardViewDetailFontSize">
        <On Platform="iOS, Android" Value="13" />
</OnPlatform>

<OnPlatform x:TypeArguments="Color"    x:Key="CardViewTextTextColor">
        <On Platform="iOS" Value="{StaticResource iOSCardViewTextTextColor}" />
        <On Platform="Android" Value="{StaticResource AndroidCardViewTextTextColor}" />
</OnPlatform>

<OnPlatform x:TypeArguments="Thickness"    x:Key="CardViewTextlMargin">
        <On Platform="iOS" Value="12,10,12,4" />
        <On Platform="Android" Value="20,0,20,5" />
</OnPlatform>

<OnPlatform x:TypeArguments="Color"    x:Key="CardViewDetailTextColor">
        <On Platform="iOS" Value="{StaticResource iOSCardViewDetailTextColor}" />
        <On Platform="Android" Value="{StaticResource AndroidCardViewDetailTextColor}" />
</OnPlatform>

<OnPlatform x:TypeArguments="Thickness"    x:Key="CardViewDetailMargin">
        <On Platform="iOS" Value="12,0,10,12" />
        <On Platform="Android" Value="20,0,20,20" />
</OnPlatform>

<OnPlatform x:TypeArguments="Color"    x:Key="CardViewBackgroundColor">
        <On Platform="iOS" Value="{StaticResource iOSCardViewBackgroundColor}" />
        <On Platform="Android" Value="{StaticResource AndroidCardViewBackgroundColor}" />
</OnPlatform>

<OnPlatform x:TypeArguments="x:Double" x:Key="CardViewShadowSize">
        <On Platform="iOS" Value="2" />
        <On Platform="Android" Value="5" />
</OnPlatform>

<OnPlatform x:TypeArguments="x:Double" x:Key="CardViewCornerRadius">
        <On Platform="iOS" Value="0" />
        <On Platform="Android" Value="4" />
</OnPlatform>

<OnPlatform x:TypeArguments="Color"    x:Key="CardViewShadowColor">
        <On Platform="iOS, Android" Value="#CDCDD1" />
</OnPlatform>
```

<a name="3" />

#### <a name="3-create-styles-for-the-controls-children"></a>3. Crear estilos para los elementos secundarios del control

Haga referencia a todos los elementos definidos sobre para crear los elementos secundarios que se usarán en el control personalizado:

```xml
<!-- EXPLICIT STYLES (will be Classes) -->
<Style TargetType="Label" x:Key="CardViewTextStyle">
    <Setter Property="FontSize" Value="{ StaticResource CardViewTextFontSize }" />
    <Setter Property="TextColor" Value="{ StaticResource CardViewTextTextColor }" />
    <Setter Property="HorizontalOptions" Value="Start" />
    <Setter Property="Margin" Value="{ StaticResource CardViewTextlMargin }" />
    <Setter Property="HorizontalTextAlignment" Value="Start" />
</Style>

<Style TargetType="Label" x:Key="CardViewDetailStyle">
    <Setter Property="HorizontalTextAlignment" Value="Start" />
    <Setter Property="TextColor" Value="{ StaticResource CardViewDetailTextColor }" />
    <Setter Property="FontSize" Value="{ StaticResource CardViewDetailFontSize }" />
    <Setter Property="HorizontalOptions" Value="Start" />
    <Setter Property="Margin" Value="{ StaticResource CardViewDetailMargin }" />
</Style>

<Style TargetType="Image" x:Key="CardViewImageImageStyle">
    <Setter Property="HorizontalOptions" Value="Center" />
    <Setter Property="VerticalOptions" Value="Center" />
    <Setter Property="WidthRequest" Value="220"/>
    <Setter Property="HeightRequest" Value="165"/>
</Style>
```

<a name="4" />

#### <a name="4-create-the-control-layout-template"></a>4. Crear la plantilla de diseño de control

El diseño visual del control personalizado se declara explícitamente en la plantilla de control mediante los recursos definidos anteriormente:

```xml
<!--- CARDVIEW -->
<ControlTemplate x:Key="CardViewControlControlTemplate">
  <StackLayout
    Spacing="0"
    BackgroundColor="{ TemplateBinding BackgroundColor }"
  >

    <!-- CARDVIEW IMAGE -->
    <Image
      Source="{ TemplateBinding ImageSource }"
      HorizontalOptions="FillAndExpand"
      VerticalOptions="StartAndExpand"
      Aspect="AspectFill"
      Style="{ StaticResource CardViewImageImageStyle }"
    />

    <!-- CARDVIEW TEXT -->
    <Label
      Text="{ TemplateBinding Text }"
      LineBreakMode="WordWrap"
      VerticalOptions="End"
      Style="{ StaticResource CardViewTextStyle }"
    />

    <!-- CARDVIEW DETAIL -->
    <Label
      Text="{ TemplateBinding Detail }"
      LineBreakMode="WordWrap"
      VerticalOptions="End"
      Style="{ StaticResource CardViewDetailStyle }" />

  </StackLayout>

</ControlTemplate>
```

<a name="5" />

#### <a name="5-add-the-theme-specific-resources"></a>5. Agregar los recursos específicos del tema

Dado que se trata de un control personalizado, agregue los recursos que coinciden con el tema que usa el Diccionario de recursos:

##### <a name="light-theme-colors"></a>Colores de tema claro

```xaml
<Color x:Key="iOSCardViewBackgroundColor">#FFFFFF</Color>
<Color x:Key="AndroidCardViewBackgroundColor">#FFFFFF</Color>

<Color x:Key="AndroidCardViewTextTextColor">#030303</Color>
<Color x:Key="iOSCardViewTextTextColor">#030303</Color>

<Color x:Key="AndroidCardViewDetailTextColor">#8F8E94</Color>
<Color x:Key="iOSCardViewDetailTextColor">#8F8E94</Color>
```

##### <a name="dark-theme-colors"></a>Colores del tema oscuro

```xaml
<!-- CARD VIEW COLORS -->
            <Color x:Key="iOSCardViewBackgroundColor">#404040</Color>
            <Color x:Key="AndroidCardViewBackgroundColor">#404040</Color>

            <Color x:Key="AndroidCardViewTextTextColor">#FFFFFF</Color>
            <Color x:Key="iOSCardViewTextTextColor">#FFFFFF</Color>

            <Color x:Key="AndroidCardViewDetailTextColor">#B5B4B9</Color>
            <Color x:Key="iOSCardViewDetailTextColor">#B5B4B9</Color>
```

<a name="6" />

#### <a name="6-set-the-controltemplate-for-the-cardview-class"></a>6. Establecer ControlTemplate para la clase CardView

Por último, asegúrese C# de que la clase creada en el [paso 1](#1) usa la plantilla de control definida `Style` en el [paso 4](#4) mediante un `Setter` elemento.

```xml
<Style TargetType="local:CardView">
    <Setter Property="ControlTemplate" Value="{ StaticResource CardViewControlControlTemplate }" />
  ... some custom styling omitted
  <Setter Property="BackgroundColor" Value="{ StaticResource CardViewBackgroundColor }" />
</Style>
```

<a name="7" />

#### <a name="7-add-the-control-to-a-page"></a>7. Agregar el control a una página

Ahora `CardView` se puede Agregar el control a una página. En el ejemplo siguiente se muestra que se `StackLayout`hospeda en un:

```xaml
<StackLayout Spacing="0">
  <local:CardView
    Margin="12,6"
    ImageSource="{ DynamicResource CardViewImage }"
    Text="CardView Text"
    Detail="CardView Detail"
  />
</StackLayout>

```
