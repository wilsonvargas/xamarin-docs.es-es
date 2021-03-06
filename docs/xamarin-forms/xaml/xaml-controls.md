---
title: Controles de XAML
description: A todas las vistas que se definen en Xamarin. Forms se puede hacer referencia desde archivos XAML.
ms.topic: article
ms.prod: xamarin
ms.assetid: 639BD392-1496-41BB-BB09-7652273AC9D8
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 07/10/2019
ms.openlocfilehash: f146fc25af5b5c62acece5c736522773e6dc455d
ms.sourcegitcommit: 1341f2950b775a4daa7d0548a51fdef759afd6e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69976529"
---
# <a name="xaml-controls"></a>Controles de XAML

[![Descargar ejemplo](~/media/shared/download.png) Descargar el ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/formsgallery)

Las vistas son objetos de interfaz de usuario, como etiquetas, botones y los controles deslizantes que se conocen normalmente como *controles* o *widgets* en otros entornos de programación de gráficos. Las vistas compatibles con Xamarin.Forms todos se derivan los [ `View` ](xref:Xamarin.Forms.View) clase.

A todas las vistas que se definen en Xamarin. Forms se puede hacer referencia desde archivos XAML.

## <a name="views-for-presentation"></a>Vistas de presentación

|     |     |
| --- | --- |
| <h3>BoxView</h3>Muestra un rectángulo de un color determinado.<p align="center">![Captura de pantalla de un BoxView](xaml-controls-images/BoxView.png "BoxView")</p>[API](xref:Xamarin.Forms.BoxView) / [Guía](~/xamarin-forms/user-interface/boxview.md) | <pre valign="center">&lt;BoxView Color="Accent"<br />         WidthRequest="150"<br />         HeightRequest="150"<br />         HorizontalOptions="Center"&gt;</pre></p> |
| <h3>Image</h3>Muestra un mapa de bits.<p align="center">![Captura de pantalla de una imagen](xaml-controls-images/Image.png "Imagen") de</p>[API](xref:Xamarin.Forms.Image) / [Guía](~/xamarin-forms/user-interface/images.md) | <pre>&lt;Image Source="https://aka.ms/campus.jpg"<br />       Aspect="AspectFit"<br />       HorizontalOptions="Center" /&gt;</pre></p> |
| <h3>Etiqueta</h3>Muestra una o varias líneas de texto.<p align="center">![Captura de pantalla de una etiqueta](xaml-controls-images/Label.png "Etiqueta") de</p>[API](xref:Xamarin.Forms.Label) / [Guía](~/xamarin-forms/user-interface/text/label.md) | <p valign="center"><pre>&lt;Label Text="Hello, Xamarin.Forms!"<br />       FontSize="Large"<br />       FontAttributes="Italic"<br />       HorizontalTextAlignment="Center" /&gt;</pre></p> |
| <h3>Map</h3>Muestra un mapa.<p align="center">![Captura de pantalla de un mapa](xaml-controls-images/Map.png "Asignación") de</p>[API](xref:Xamarin.Forms.Maps.Map) / [Guía](~/xamarin-forms/user-interface/map.md) | <p valign="center"><pre>&lt;maps:Map ItemsSource="{Binding Locations}" /&gt;</pre></p> |
| <h3>WebView</h3>Muestra páginas web o contenido HTML.<p align="center">![Captura de pantalla de un WebView](xaml-controls-images/WebView.png "Vista previa")</p>[API](xref:Xamarin.Forms.WebView) / [Guía](~/xamarin-forms/user-interface/webview.md) | <p valign="center"><pre>&lt;WebView Source="https://docs.microsoft.com/xamarin/"<br/>         VerticalOptions="FillAndExpand" /&gt;</pre></p> |
|     |     |

## <a name="views-that-initiate-commands"></a>Vistas que inician comandos

|     |     |
| --- | --- |
| <h3>Botón</h3>Muestra texto en un objeto rectangular.<p align="center">![Captura de pantalla de un botón](xaml-controls-images/Button.png "Botón") de</p>[API](xref:Xamarin.Forms.Button) / [Guía](~/xamarin-forms/user-interface/button.md) | <p valign="center"><pre>&lt;Button Text="Click Me!"<br />        Font="Large"<br />        BorderWidth="1"<br />        HorizontalOptions="Center"<br />        VerticalOptions="CenterAndExpand"<br />        Clicked="OnButtonClicked" /&gt;</pre></p> |
| <h3>ImageButton</h3>Muestra una imagen en un objeto rectangular.<p align="center">![Captura de pantalla de un ImageButton](xaml-controls-images/ImageButton.png "ImageButton")</p>[API](xref:Xamarin.Forms.ImageButton) / [Guía](~/xamarin-forms/user-interface/imagebutton.md) | <p valign="center"><pre>&lt;ImageButton Source="XamarinLogo.png"<br />             HorizontalOptions="Center"<br />             VerticalOptions="CenterAndExpand"<br />             Clicked="OnImageButtonClicked" /&gt;</pre></p> |
| <h3>Barra de búsqueda</h3>Muestra una barra de búsqueda para realizar una búsqueda.<p align="center">![Captura de pantalla de un barra](xaml-controls-images/SearchBar.png "Barra")</p>[API](xref:Xamarin.Forms.SearchBar) / [Guía](~/xamarin-forms/user-interface/searchbar.md) | <p valign="center"><pre>&lt;SearchBar Placeholder="Xamarin.Forms Property"<br />           SearchButtonPressed="OnSearchBarButtonPressed" /&gt;</pre></p> |
|     |     |

## <a name="views-for-setting-values"></a>Para establecer valores de las vistas

|     |     |
| --- | --- |
| <h3>CheckBox</h3>Permite la selección de un `boolean` valor.<p align="center">![Captura de pantalla de una casilla](xaml-controls-images/CheckBox.png "Casilla de verificación")</p> [Guíe](~/xamarin-forms/user-interface/checkbox.md) | <p valign="center"><pre>&lt;CheckBox IsChecked="true"<br />          HorizontalOptions="Center"<br />          VerticalOptions="CenterAndExpand" /&gt;</pre></p> |
| <h3>Slider</h3>Permite la selección de un `double` valor de un intervalo continuo.<p align="center">![Captura de pantalla de un control deslizante](xaml-controls-images/Slider.png "Control deslizante")</p>[API](xref:Xamarin.Forms.Slider) / [Guía](~/xamarin-forms/user-interface/slider.md) | <p valign="center"><pre>&lt;Slider Minimum="0"<br />        Maximum="100"<br />        VerticalOptions="CenterAndExpand" /&gt;</pre></p> |
| <h3>Control de incremento</h3>Permite la selección de un `double` valor de un intervalo incremental.<p align="center">![Captura de pantalla de un stepper](xaml-controls-images/Stepper.png "Stepper")</p>[API](xref:Xamarin.Forms.Stepper) / [Guía](~/xamarin-forms/user-interface/stepper.md) | <p valign="center"><pre>&lt;Stepper Minimum="0"<br />         Maximum="10"<br />         Increment="0.1"<br />         HorizontalOptions="Center"<br />         VerticalOptions="CenterAndExpand" /&gt;</pre></p> |
| <h3>Modificador</h3>Permite la selección de un `boolean` valor.<p align="center">![Captura de pantalla de un conmutador](xaml-controls-images/Switch.png "Cambiar")</p>[API](xref:Xamarin.Forms.Switch) / [Guía](~/xamarin-forms/user-interface/switch.md)| <p valign="center"><pre>&lt;Switch IsToggled="false"<br />        HorizontalOptions="Center"<br />        VerticalOptions="CenterAndExpand" /&gt;</pre></p> |
| <h3>DatePicker</h3>Permite seleccionar una fecha.<p align="center">![Captura de pantalla de un DatePicker](xaml-controls-images/DatePicker.png "DatePicker")</p>[API](xref:Xamarin.Forms.DatePicker) / [Guía](~/xamarin-forms/user-interface/datepicker.md) | <p valign="center"><pre>&lt;DatePicker Format="D"<br/>            VerticalOptions="CenterAndExpand" /&gt;</pre></p> |
| <h3>TimePicker</h3>Permite la selección de una vez.<p align="center">![Captura de pantalla de un TimePicker](xaml-controls-images/TimePicker.png "TimePicker")</p>[API](xref:Xamarin.Forms.TimePicker) / [Guía](~/xamarin-forms/user-interface/timepicker.md) | <p valign="center"><pre>&lt;TimePicker Format="T"<br />            VerticalOptions="CenterAndExpand" /&gt;</pre></p> |
|     |     |

## <a name="views-for-editing-text"></a>Vistas para editar texto

|     |     |
| --- | --- |
| <h3>Entrada</h3>Permite escribir y editar una sola línea de texto.<p align="center">![Captura de pantalla de una entrada](xaml-controls-images/Entry.png "Entrada") de</p>[API](xref:Xamarin.Forms.Entry) / [Guía](~/xamarin-forms/user-interface/text/entry.md) | <p valign="center"><pre>&lt;Entry Keyboard="Email"<br />       Placeholder="Enter email address"<br />       VerticalOptions="CenterAndExpand" /&gt;</pre></p> |
| <h3>Editor</h3>Permite escribir y editar varias líneas de texto.<p align="center">![Captura de pantalla de un editor](xaml-controls-images/Editor.png "Etiqueta") de</p>[API](xref:Xamarin.Forms.Editor) / [Guía](~/xamarin-forms/user-interface/text/editor.md) | <p valign="center"><pre>&lt;Editor VerticalOptions="FillAndExpand" /&gt;</pre></p> |
|     |     |

## <a name="views-to-indicate-activity"></a>Vistas para indicar actividad

|     |     |
| --- | --- |
| <h3>ActivityIndicator</h3>Muestra una animación para mostrar que la aplicación está ocupada en una actividad prolongada, sin indicar ningún progreso.<p align="center">![Captura de pantalla de un ActivityIndicator](xaml-controls-images/ActivityIndicator.png "ActivityIndicator")</p>[API](xref:Xamarin.Forms.ActivityIndicator) / [Guía](~/xamarin-forms/user-interface/activityindicator.md) | <p valign="center"><pre>&lt;ActivityIndicator IsRunning="True"<br />                   VerticalOptions="CenterAndExpand" /&gt;</pre></p> |
| <h3>ProgressBar</h3>Muestra una animación para mostrar que la aplicación progresa a través de una actividad prolongada.<p align="center">![Captura de pantalla de un ProgressBar](xaml-controls-images/ProgressBar.png "ProgressBar")</p>[API](xref:Xamarin.Forms.ProgressBar) / [Guía](~/xamarin-forms/user-interface/progressbar.md) | <p valign="center"><pre>&lt;ProgressBar Progress=".5"<br />             VerticalOptions="CenterAndExpand" /&gt;</pre></p> |
|     |     |

## <a name="views-that-display-collections"></a>Vistas que muestran colecciones

|     |     |
| --- | --- |
| <h3>CollectionView</h3>Muestra una lista desplazable de elementos de datos seleccionables, con distintas especificaciones de diseño.<p align="center">![Captura de pantalla de una CollectionView](xaml-controls-images/CollectionView.png "CollectionView")</p>[Guíe](~/xamarin-forms/user-interface/collectionview/index.md) | <p valign="center"><pre>&lt;CollectionView ItemsSource="{Binding Monkeys}"&gt;<br/>                ItemTemplate="{StaticResource MonkeyTemplate}"<br />    &lt;CollectionView.ItemsLayout&gt;<br />       &lt;GridItemsLayout Orientation="Vertical"<br />                        Span="2" /&gt;<br />    &lt;/CollectionView.ItemsLayout&gt;<br />&lt;/CollectionView/&gt;</pre></p> |
| <h3>ListView</h3>Muestra una lista desplazable de elementos de datos seleccionables.<p align="center">![Captura de pantalla de un control ListView](xaml-controls-images/ListView.png "Vista") de</p>[API](xref:Xamarin.Forms.ListView) / [Guía](~/xamarin-forms/user-interface/listview/index.md) | <p valign="center"><pre>&lt;ListView ItemsSource="{Binding Monkeys}"&gt;<br />          ItemTemplate="{StaticResource MonkeyTemplate}" /&gt;</pre></p> |
| <h3>Selector</h3>Muestra un elemento seleccionado en una lista de cadenas de texto.<p align="center">![Captura de pantalla de un selector](xaml-controls-images/Picker.png "Selector") de</p>[API](xref:Xamarin.Forms.Picker) / [Guía](~/xamarin-forms/user-interface/picker/index.md) | <p valign="center"><pre>&lt;Picker Title="Select a monkey"<br />        TitleColor="Red"&gt;<br />  &lt;Picker.ItemsSource&lt;<br />    &lt;x:Array Type="{x:Type x:String}"&gt;<br />      &lt;x:String&gt;Baboon&lt;/x:String&gt;<br />      &lt;x:String&gt;Capuchin Monkey&lt;/x:String&gt;<br />      &lt;x:String&gt;Blue Monkey&lt;/x:String&gt;<br />      &lt;x:String&gt;Squirrel Monkey&lt;/x:String&gt;<br />      &lt;x:String&gt;Golden Lion Tamarin&lt;/x:String&gt;<br />      &lt;x:String&gt;Howler Monkey&lt;/x:String&gt;<br />      &lt;x:String&gt;Japanese Macaque&lt;/x:String&gt;<br />    &lt;/x:Array&gt;<br />  &lt;/Picker.ItemsSource&gt;<br />&lt;/Picker&gt;</pre></p> |
| <h3>TableView</h3>Muestra una lista de filas interactivas.<p align="center">![Captura de pantalla de un TableView](xaml-controls-images/TableView.png "TableView")</p>[API](xref:Xamarin.Forms.TableView) / [Guía](~/xamarin-forms/user-interface/tableview.md) | <p valign="center"><pre>&lt;TableView Intent="Settings"&gt;<br />    &lt;TableRoot&gt;<br />        &lt;TableSection Title="Ring"&gt;<br />            &lt;SwitchCell Text="New Voice Mail" /&gt;<br />            &lt;SwitchCell Text="New Mail" On="true" /&gt;<br />        &lt;/TableSection&gt;<br />    &lt;/TableRoot&gt;<br />&lt;/TableView&gt;</pre></p> |
|     |     |

## <a name="related-links"></a>Vínculos relacionados

- [Ejemplo de Xamarin.Forms FormsGallery](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/formsgallery)
- [Xamarin.Forms Samples](https://docs.microsoft.com/samples/browse/?products=xamarin&term=Xamarin.Forms) (Ejemplos de Xamarin.Forms)
- [Documentación de la API de Xamarin.Forms](https://docs.microsoft.com/dotnet/api/xamarin.forms?view=xamarin-forms)
