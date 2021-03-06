---
title: Diseños de Xamarin.Forms
description: Los diseños de Xamarin.Forms se utilizan para crear controles de interfaz de usuario en estructuras visuales. En este artículo se enumera los diseños que se incluye en Xamarin.Forms.
ms.prod: xamarin
ms.assetid: F4180997-BA21-453A-9958-D1E2940DF050
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 05/21/2018
ms.openlocfilehash: 59c6f9e7ec6c40c938fda2665bbae5685e7de830
ms.sourcegitcommit: 4cf434b126eb7df6b2fd9bb1d71613bf2b6aac0e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71997213"
---
# <a name="xamarinforms-layouts"></a>Diseños de Xamarin.Forms

[![Descargar ejemplo](~/media/shared/download.png) descargar el ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/formsgallery)

_Los diseños de Xamarin.Forms se utilizan para crear controles de interfaz de usuario en estructuras visuales._

El [ `Layout` ](xref:Xamarin.Forms.Layout) y [ `Layout<T>` ](xref:Xamarin.Forms.Layout`1) clases de Xamarin.Forms son subtipos especializadas de las vistas que actúan como contenedores para otros diseños y vistas. El `Layout` propia clase se deriva de [ `View` ](views.md). Un `Layout` derivado normalmente contiene lógica para establecer la posición y tamaño de los elementos secundarios en las aplicaciones de Xamarin.Forms.

[Tipos de diseño de Xamarin. ![Forms]tipos de(layouts-images/layouts-sml.png "diseño de Xamarin. Forms")](layouts-images/layouts.png#lightbox "Tipos de diseño de Xamarin. Forms")

Las clases que derivan de `Layout` pueden dividirse en dos categorías:

## <a name="layouts-with-single-content"></a>Diseños con contenido único

Estas clases derivan de [ `Layout` ](xref:Xamarin.Forms.Layout), que define [ `Padding` ](xref:Xamarin.Forms.Layout.Padding) y [ `IsClippedToBounds` ](xref:Xamarin.Forms.Layout.IsClippedToBounds) propiedades.

<a name="contentView" />

### <a name="contentview"></a>ContentView

|     |     |
| --- | --- |
| [`ContentView`](xref:Xamarin.Forms.ContentView) contiene un único elemento secundario que se establece con el [ `Content` ](xref:Xamarin.Forms.ContentView.Content) propiedad. El `Content` propiedad puede establecerse en cualquier `View` derivados, incluidos otros `Layout` derivados. `ContentView` se usa principalmente como un elemento estructural y actúa como clase base para [ `Frame` ](#frame).<br /><br />[Documentación de API](xref:Xamarin.Forms.ContentView) / [guía](~/xamarin-forms/user-interface/layouts/contentview.md) / [ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-cardview/) | [(layouts-images/ContentView.png "Ejemplo de ContentView") de ![ContentView ejemplo]](layouts-images/ContentView-Large.png#lightbox "Ejemplo de ContentView")<br />[Código C# para esta página](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/CodeExamples/ContentViewDemoPage.cs) / [página XAML](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/XamlExamples/ContentViewDemoPage.xaml) |
|     |     |

<a named="frame" />

### <a name="frame"></a>Fotograma

|     |     |
| --- | --- |
| La clase [`Frame`](xref:Xamarin.Forms.Frame) deriva de [`ContentView`](#contentView) y muestra un borde, o marco, alrededor de su elemento secundario. La clase `Frame` tiene un valor predeterminado de [@no__t 2](xref:Xamarin.Forms.Layout.Padding) de 20 y también define las propiedades [@no__t 4](xref:Xamarin.Forms.Frame.BorderColor), [`CornerRadius`](xref:Xamarin.Forms.Frame.CornerRadius)y [`HasShadow`](xref:Xamarin.Forms.Frame.HasShadow) .<br /><br />[Documentación de API](xref:Xamarin.Forms.Frame) / [guía](~/xamarin-forms/user-interface/layouts/frame.md) / [ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-frame/) | [![](layouts-images/Frame.png "Ejemplo de marco") de ejemplo de marco](layouts-images/Frame-Large.png#lightbox "Ejemplo de marco")<br />[Código C# para esta página](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/CodeExamples/FrameDemoPage.cs) / [página XAML](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/XamlExamples/FrameDemoPage.xaml) |
|     |     |

<a name="scrollView" />

### <a name="scrollview"></a>ScrollView

|     |     |
| --- | --- |
| [`ScrollView`](xref:Xamarin.Forms.ScrollView) es capaz de desplazar su contenido. Establecer el [ `Content` ](xref:Xamarin.Forms.ScrollView.Content) propiedad a una vista o diseño demasiado grande para caber en la pantalla. (El contenido de un `ScrollView` es muy a menudo un [ `StackLayout` ](#stackLayout).) Establecer el [ `Orientation` ](xref:Xamarin.Forms.ScrollView.Orientation) propiedad para indicar si el desplazamiento debe ser vertical, horizontal, o ambos.<br /><br />[Documentación de API](xref:Xamarin.Forms.ScrollView) / [guía](~/xamarin-forms/user-interface/layouts/scroll-view.md) / [ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-layout) | [(layouts-images/ScrollView.png "Ejemplo de ScrollView") de ![ScrollView ejemplo]](layouts-images/ScrollView-Large.png#lightbox "Ejemplo de ScrollView")<br />[Código C# para esta página](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/CodeExamples/ScrollViewDemoPage.cs) / [página XAML](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/XamlExamples/ScrollViewDemoPage.xaml) |
|     |     |

### <a name="templatedview"></a>TemplatedView

|     |     |
| --- | --- |
| [`TemplatedView`](xref:Xamarin.Forms.TemplatedView) Muestra el contenido con una plantilla de control, y es la clase base para [ `ContentView` ](#contentView).<br /><br />[Documentación de API](xref:Xamarin.Forms.TemplatedView) / [guía](~/xamarin-forms/app-fundamentals/templates/control-templates/index.md) | [(layouts-images/TemplatedView.png "Ejemplo de TemplatedView") de ![TemplatedView ejemplo]](layouts-images/TemplatedView.png#lightbox "Ejemplo de TemplatedView") |
|     |     |

### <a name="contentpresenter"></a>ContentPresenter

|     |     |
| --- | --- |
| [`ContentPresenter`](xref:Xamarin.Forms.ContentPresenter) es un administrador de diseño para las vistas con plantilla, se utiliza dentro de un [ `ControlTemplate` ](xref:Xamarin.Forms.ControlTemplate) para marcar dónde aparece el contenido que debe presentarse.<br /><br />[Documentación de API](xref:Xamarin.Forms.ContentPresenter) / [guía](~/xamarin-forms/app-fundamentals/templates/control-templates/index.md) | [Ejemplo de(layouts-images/ContentPresenter.png "ContentPresenter") de ![ejemplo ContentPresenter]](layouts-images/ContentPresenter.png#lightbox "Ejemplo de ContentPresenter") |
|     |     |

## <a name="layouts-with-multiple-children"></a>Diseños con varios elementos secundarios

Estas clases derivan de [ `Layout<View>` ](xref:Xamarin.Forms.Layout`1).

<a name="stackLayout" />

### <a name="stacklayout"></a>StackLayout

|     |     |
| --- | --- |
| [`StackLayout`](xref:Xamarin.Forms.StackLayout) coloca los elementos secundarios en una pila horizontal o verticalmente se basa en el [ `Orientation` ](xref:Xamarin.Forms.StackLayout.Orientation) propiedad. El [ `Spacing` ](xref:Xamarin.Forms.StackLayout.Spacing) propiedad controla el espaciado entre los elementos secundarios y tiene un valor predeterminado de 6.<br /><br />[Documentación de API](xref:Xamarin.Forms.StackLayout) / [guía](~/xamarin-forms/user-interface/layouts/stack-layout.md) / [ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-layout)| [(layouts-images/StackLayout.png "Ejemplo de StackLayout") de ![StackLayout ejemplo]](layouts-images/StackLayout-Large.png#lightbox "Ejemplo de StackLayout")<br />[Código C# para esta página](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/CodeExamples/StackLayoutDemoPage.cs) / [página XAML](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/XamlExamples/StackLayoutDemoPage.xaml) |
|     |     |

<a name="grid" />

### <a name="grid"></a>Cuadrícula

|     |     |
| --- | --- |
| [`Grid`](xref:Xamarin.Forms.Grid) coloca sus elementos secundarios en una cuadrícula de filas y columnas. Posición del elemento secundario se indica mediante el [propiedades adjuntas](~/xamarin-forms/xaml/attached-properties.md) [ `Row` ](xref:Xamarin.Forms.Grid.RowProperty), [ `Column` ](xref:Xamarin.Forms.Grid.ColumnProperty), [ `RowSpan` ](xref:Xamarin.Forms.Grid.RowSpanProperty), y [ `ColumnSpan` ](xref:Xamarin.Forms.Grid.ColumnSpanProperty).<br /><br />[Documentación de API](xref:Xamarin.Forms.Grid) / [guía](~/xamarin-forms/user-interface/layouts/grid.md) / [ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-layout) | [![](layouts-images/Grid.png "Ejemplo de cuadrícula") de ejemplo de cuadrícula](layouts-images/Grid-Large.png#lightbox "Ejemplo de cuadrícula")<br />[Código C# para esta página](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/CodeExamples/GridDemoPage.cs) / [página XAML](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/XamlExamples/GridDemoPage.xaml) |
|     |     |

### <a name="absolutelayout"></a>AbsoluteLayout

|     |     |
| --- | --- |
| [`AbsoluteLayout`](xref:Xamarin.Forms.AbsoluteLayout) coloca los elementos secundarios en ubicaciones específicas en relación con su elemento primario. Posición del elemento secundario se indica mediante el [propiedades adjuntas](~/xamarin-forms/xaml/attached-properties.md) [ `LayoutBounds` ](xref:Xamarin.Forms.AbsoluteLayout.LayoutBoundsProperty) y [ `LayoutFlags` ](xref:Xamarin.Forms.AbsoluteLayout.LayoutFlagsProperty). Un `AbsoluteLayout` es útil para animar las posiciones de las vistas.<br /><br />[Documentación de API](xref:Xamarin.Forms.AbsoluteLayout) / [guía](~/xamarin-forms/user-interface/layouts/absolute-layout.md) / [ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-layout) | [(layouts-images/AbsoluteLayout.png "Ejemplo de AbsoluteLayout") de ![AbsoluteLayout ejemplo]](layouts-images/AbsoluteLayout-Large.png#lightbox "Ejemplo de AbsoluteLayout")<br />[Código C# para esta página](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/CodeExamples/AbsoluteLayoutdDemoPage.cs) / [página XAML](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/XamlExamples/AbsoluteLayoutDemoPage.xaml) con [código subyacente](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/XamlExamples/AbsoluteLayoutDemoPage.xaml.cs) |
|     |     |

### <a name="relativelayout"></a>RelativeLayout

|     |     |
| --- | --- |
| [`RelativeLayout`](xref:Xamarin.Forms.RelativeLayout) coloca los elementos secundarios respecto a la `RelativeLayout` propio o a sus elementos relacionados. Posición del elemento secundario se indica mediante el [propiedades adjuntas](~/xamarin-forms/xaml/attached-properties.md) que se establecen en objetos de tipo [ `Constraint` ](xref:Xamarin.Forms.Constraint) y [ `BoundsConstraint` ](xref:Xamarin.Forms.Constraint).<br /><br />[Documentación de API](xref:Xamarin.Forms.RelativeLayout) / [guía](~/xamarin-forms/user-interface/layouts/relative-layout.md) / [ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-layout) | [(layouts-images/RelativeLayout.png "Ejemplo de RelativeLayout") de ![RelativeLayout ejemplo]](layouts-images/RelativeLayout-Large.png#lightbox "Ejemplo de RelativeLayout")<br />[Código C# para esta página](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/CodeExamples/RelativeLayoutDemoPage.cs) / [página XAML](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/XamlExamples/RelativeLayoutDemoPage.xaml) |
|     |     |

### <a name="flexlayout"></a>FlexLayout

|     |     |
| --- | --- |
| [`FlexLayout`](xref:Xamarin.Forms.FlexLayout) se basa en la hoja CSS [Flexible diseño módulo](http://www.w3.org/TR/css-flexbox-1/), normalmente conocido como _flex diseño_ o _flex cuadro_. `FlexLayout` define propiedades enlazables seis y cinco propiedades enlazables adjuntas que permiten a los elementos secundarios se pueden superponer ni ajusta con muchas opciones de alineación y orientación.<br /><br />[Documentación de API](xref:Xamarin.Forms.FlexLayout) / [guía](~/xamarin-forms/user-interface/layouts/flex-layout.md) / [ejemplo](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-flexlayoutdemos) | [(layouts-images/FlexLayout.png "Ejemplo de FlexLayout") de ![FlexLayout ejemplo]](layouts-images/FlexLayout-Large.png#lightbox "Ejemplo de FlexLayout")<br />[Código C# para esta página](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/CodeExamples/FlexLayoutDemoPage.cs) / [página XAML](https://github.com/xamarin/xamarin-forms-samples/blob/master/FormsGallery/FormsGallery/FormsGallery/XamlExamples/FlexLayoutDemoPage.xaml) |
|     |     |

## <a name="related-links"></a>Vínculos relacionados

- [Ejemplo de Xamarin.Forms FormsGallery](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/formsgallery)
- [Xamarin.Forms Samples](https://docs.microsoft.com/samples/browse/?products=xamarin&term=Xamarin.Forms) (Ejemplos de Xamarin.Forms)
- [Documentación de la API de Xamarin.Forms](https://docs.microsoft.com/dotnet/api/xamarin.forms?view=xamarin-forms)
