---
title: Crear una aplicación de Xamarin. Forms
description: Los temas se pueden implementar en aplicaciones de Xamarin. Forms creando un ResourceDictionary para cada tema y, a continuación, cargando los recursos con la extensión de marcado DynamicResource.
ms.prod: xamarin
ms.assetId: B7B17F66-4E37-4B50-9A57-351B62BE4FED
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 08/07/2019
ms.openlocfilehash: 3e0f508a9c980c02681f1be581846f9f2f25e2d0
ms.sourcegitcommit: 699de58432b7da300ddc2c85842e5d9e129b0dc5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "69529276"
---
# <a name="theming-a-xamarinforms-application"></a>Crear una aplicación de Xamarin. Forms

[![Descargar ejemplo](~/media/shared/download.png) Descargar el ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-theming/)

Las aplicaciones de Xamarin. Forms pueden responder de forma dinámica a los cambios de `DynamicResource` estilo en tiempo de ejecución mediante la extensión de marcado. Esta extensión de marcado es similar a `StaticResource` la extensión de marcado, en que ambos usan una clave de diccionario para capturar un [`ResourceDictionary`](xref:Xamarin.Forms.ResourceDictionary)valor de un. Sin embargo, mientras `StaticResource` que la extensión de marcado realiza una búsqueda de `DynamicResource` un solo diccionario, la extensión de marcado mantiene un vínculo a la clave del diccionario. Por consiguiente, si se reemplaza el valor asociado a la clave, el cambio se aplica a [`VisualElement`](xref:Xamarin.Forms.VisualElement). Esto permite que los encargados de tiempo de ejecución se implementen en aplicaciones de Xamarin. Forms.

El proceso de implementación de los procesos en tiempo de ejecución en una aplicación de Xamarin. Forms es el siguiente:

1. Defina los recursos para cada tema en un [`ResourceDictionary`](xref:Xamarin.Forms.ResourceDictionary).
1. Consume recursos de tema en la aplicación mediante `DynamicResource` la extensión de marcado.
1. Establezca un tema predeterminado en el archivo **app. Xaml** de la aplicación.
1. Agregue código para cargar un tema en tiempo de ejecución.

Las siguientes capturas de pantallas muestran páginas con temas, con la aplicación de iOS que usa un tema claro y la aplicación Android con un tema oscuro:

[![Captura de pantalla de la Página principal de una aplicación de la que se ha importado, en iOS y Android] (theming-images/main-page-both-themes.png "Página principal de la aplicación") ](theming-images/main-page-both-themes-large.png#lightbox "Página principal de la aplicación con la que se han importado") con la que se han importado Captura de [ ![pantalla de la página de detalles de una aplicación de la que se ha importado, en la](theming-images/detail-page-both-themes.png "Página de detalles") de iOS y Android de la aplicación.](theming-images/detail-page-both-themes-large.png#lightbox "Página de detalles de la aplicación con el mismo") 


## <a name="define-themes"></a>Definir temas

Un tema se define como una colección de objetos de recursos almacenados en [`ResourceDictionary`](xref:Xamarin.Forms.ResourceDictionary)un.

En el ejemplo siguiente se `LightTheme` muestra el de la aplicación de ejemplo:

```xaml
<ResourceDictionary xmlns="http://xamarin.com/schemas/2014/forms"
                    xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                    x:Class="ThemingDemo.LightTheme">
    <Color x:Key="PageBackgroundColor">White</Color>
    <Color x:Key="NavigationBarColor">WhiteSmoke</Color>
    <Color x:Key="PrimaryColor">WhiteSmoke</Color>
    <Color x:Key="SecondaryColor">Black</Color>
    <Color x:Key="PrimaryTextColor">Black</Color>
    <Color x:Key="SecondaryTextColor">White</Color>
    <Color x:Key="TertiaryTextColor">Gray</Color>
    <Color x:Key="TransparentColor">Transparent</Color>
</ResourceDictionary>
```

En el ejemplo siguiente se `DarkTheme` muestra el de la aplicación de ejemplo:

```xaml
<ResourceDictionary xmlns="http://xamarin.com/schemas/2014/forms"
                    xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                    x:Class="ThemingDemo.DarkTheme">
    <Color x:Key="PageBackgroundColor">Black</Color>
    <Color x:Key="NavigationBarColor">Teal</Color>
    <Color x:Key="PrimaryColor">Teal</Color>
    <Color x:Key="SecondaryColor">White</Color>
    <Color x:Key="PrimaryTextColor">White</Color>
    <Color x:Key="SecondaryTextColor">White</Color>
    <Color x:Key="TertiaryTextColor">WhiteSmoke</Color>
    <Color x:Key="TransparentColor">Transparent</Color>
</ResourceDictionary>
```

Cada [`ResourceDictionary`](xref:Xamarin.Forms.ResourceDictionary) `ResourceDictionary` contiene [`Color`](xref:Xamarin.Forms.Color) recursos que definen sus respectivos temas, cada uno con valores de clave idénticos. Para obtener más información acerca de los diccionarios de recursos, consulte [los diccionarios de recursos](~/xamarin-forms/xaml/resource-dictionaries.md).

> [!IMPORTANT]
> Se requiere un archivo de código subyacente para `ResourceDictionary`cada, que llama `InitializeComponent` al método. Esto es necesario para que un objeto CLR que representa el tema elegido se pueda crear en tiempo de ejecución.

## <a name="set-a-default-theme"></a>Establecer un tema predeterminado

Una aplicación requiere un tema predeterminado, de modo que los controles tengan valores para los recursos que consumen. Se puede establecer un tema predeterminado combinando el tema [`ResourceDictionary`](xref:Xamarin.Forms.ResourceDictionary) en el nivel `ResourceDictionary` de aplicación que se define en **app. Xaml**:

```xaml
<Application xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="ThemingDemo.App">
    <Application.Resources>
        <ResourceDictionary Source="Themes/LightTheme.xaml" />
    </Application.Resources>
</Application>
```

Para obtener más información sobre la combinación de diccionarios de recursos, vea [diccionarios de recursos combinados](~/xamarin-forms/xaml/resource-dictionaries.md#merged-resource-dictionaries).

## <a name="consume-theme-resources"></a>Consumir recursos de tema

Cuando una aplicación desea consumir un recurso almacenado en un [`ResourceDictionary`](xref:Xamarin.Forms.ResourceDictionary) objeto que representa un tema, debe hacerlo con la `DynamicResource` extensión de marcado. Esto garantiza que, si se selecciona un tema diferente en tiempo de ejecución, se aplicarán los valores del nuevo tema.

En el ejemplo siguiente se muestran tres estilos de la aplicación de ejemplo que se [`Label`](xref:Xamarin.Forms.Label) pueden aplicar a los objetos:

```xaml
<Application xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="ThemingDemo.App">
    <Application.Resources>

        <Style x:Key="LargeLabelStyle"
               TargetType="Label">
            <Setter Property="TextColor"
                    Value="{DynamicResource SecondaryTextColor}" />
            <Setter Property="FontSize"
                    Value="30" />
        </Style>

        <Style x:Key="MediumLabelStyle"
               TargetType="Label">
            <Setter Property="TextColor"
                    Value="{DynamicResource PrimaryTextColor}" />
            <Setter Property="FontSize"
                    Value="25" />
        </Style>

        <Style x:Key="SmallLabelStyle"
               TargetType="Label">
            <Setter Property="TextColor"
                    Value="{DynamicResource TertiaryTextColor}" />
            <Setter Property="FontSize"
                    Value="15" />
        </Style>

    </Application.Resources>
</Application>
```

Estos estilos se definen en el Diccionario de recursos de nivel de aplicación, de modo que se puedan usar en varias páginas. Cada estilo consume recursos de tema con `DynamicResource` la extensión de marcado.

Estos estilos los utilizan las páginas:

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:local="clr-namespace:ThemingDemo"
             x:Class="ThemingDemo.UserSummaryPage"
             Title="User Summary"
             BackgroundColor="{DynamicResource PageBackgroundColor}">
    ...
    <ScrollView>
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="200" />
                <RowDefinition Height="120" />
                <RowDefinition Height="70" />
            </Grid.RowDefinitions>
            <Grid BackgroundColor="{DynamicResource PrimaryColor}">
                <Label Text="Face-Palm Monkey"
                       VerticalOptions="Center"
                       Margin="15"
                       Style="{StaticResource MediumLabelStyle}" />
                ...
            </Grid>
            <StackLayout Grid.Row="1"
                         Margin="10">
                <Label Text="This monkey reacts appropriately to ridiculous assertions and actions."
                       Style="{StaticResource SmallLabelStyle}" />
                <Label Text="  &#x2022; Cynical but not unfriendly."
                       Style="{StaticResource SmallLabelStyle}" />
                <Label Text="  &#x2022; Seven varieties of grimaces."
                       Style="{StaticResource SmallLabelStyle}" />
                <Label Text="  &#x2022; Doesn't laugh at your jokes."
                       Style="{StaticResource SmallLabelStyle}" />
            </StackLayout>
            ...
        </Grid>
    </ScrollView>
</ContentPage>
```

Cuando un recurso de tema se utiliza directamente, se debe usar con la `DynamicResource` extensión de marcado. Sin embargo, cuando se consume un `DynamicResource` estilo que utiliza la extensión de marcado, se debe usar `StaticResource` con la extensión de marcado.

Para obtener más información sobre los estilos, consulte aplicar estilos a [aplicaciones de Xamarin. Forms con estilos XAML](~/xamarin-forms/user-interface/styles/xaml/index.md). Para obtener más información sobre `DynamicResource` la extensión de marcado, vea [estilos dinámicos en Xamarin. Forms](~/xamarin-forms/user-interface/styles/xaml/dynamic.md).

## <a name="load-a-theme-at-runtime"></a>Cargar un tema en tiempo de ejecución

Cuando se selecciona un tema en tiempo de ejecución, la aplicación debe:

1. Quitar el tema actual de la aplicación. Esto se logra borrando la [`MergedDictionaries`](xref:Xamarin.Forms.ResourceDictionary.MergedDictionaries) propiedad del nivel [`ResourceDictionary`](xref:Xamarin.Forms.ResourceDictionary)de la aplicación.
2. Cargar el tema seleccionado. Esto se logra agregando una instancia del tema seleccionado a la `MergedDictionaries` propiedad del nivel `ResourceDictionary`de la aplicación.

Cualquier [`VisualElement`](xref:Xamarin.Forms.VisualElement) objeto que establezca propiedades con la `DynamicResource` extensión de marcado aplicará entonces los nuevos valores de tema. Esto se debe a `DynamicResource` que la extensión de marcado mantiene un vínculo a las claves del diccionario. Por lo tanto, cuando se reemplazan los valores asociados a las claves, los cambios `VisualElement` se aplican a los objetos.

En la aplicación de ejemplo, se selecciona un tema a través de una página modal [`Picker`](xref:Xamarin.Forms.Picker)que contiene un. En el código siguiente se `OnPickerSelectionChanged` muestra el método, que se ejecuta cuando cambia el tema seleccionado:

```csharp
void OnPickerSelectionChanged(object sender, EventArgs e)
{
    Picker picker = sender as Picker;
    Theme theme = (Theme)picker.SelectedItem;

    ICollection<ResourceDictionary> mergedDictionaries = Application.Current.Resources.MergedDictionaries;
    if (mergedDictionaries != null)
    {
        mergedDictionaries.Clear();

        switch (theme)
        {
            case Theme.Dark:
                mergedDictionaries.Add(new DarkTheme());
                break;
            case Theme.Light:
            default:
                mergedDictionaries.Add(new LightTheme());
                break;
        }
    }
}
```

## <a name="related-links"></a>Vínculos relacionados

- [Cómo hacerlo (ejemplo)](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-theming/)
- [Diccionarios de recursos](~/xamarin-forms/xaml/resource-dictionaries.md)
- [Estilos dinámicos en Xamarin. Forms](~/xamarin-forms/user-interface/styles/xaml/dynamic.md)
- [Aplicación de estilos para aplicaciones Xamarin.Forms con estilos XAML](~/xamarin-forms/user-interface/styles/xaml/index.md)
