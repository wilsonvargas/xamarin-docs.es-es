---
title: Trabajar con botones de tvOS en Xamarin
description: En este documento se describe cómo trabajar con botones en una aplicación tvOS compilada con Xamarin. En él se describe cómo trabajar con botones en el código y en guiones gráficos, y se examina cómo aplicar un estilo a un botón.
ms.prod: xamarin
ms.assetid: DA6EF400-A4E3-4245-A0D4-F2398CAE2C9B
ms.technology: xamarin-ios
author: conceptdev
ms.author: crdun
ms.date: 03/07/2017
ms.openlocfilehash: 869e2e5c3b074c928f3c49ca87c1c1801154df91
ms.sourcegitcommit: 57f815bf0024b1afe9754c0e28054fc0a53ce302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70769976"
---
# <a name="working-with-tvos-buttons-in-xamarin"></a>Trabajar con botones de tvOS en Xamarin

Use una instancia de la `UIButton` clase para crear un botón seleccionable y seleccionable en una ventana de tvOS. Cuando el usuario selecciona un botón, envía un mensaje de acción al objeto de destino, lo que permite que la aplicación de Xamarin. tvOS responda a la entrada del usuario.

[![](buttons-images/buttons01.png "Botones de ejemplo")](buttons-images/buttons01.png#lightbox)

Para obtener más información sobre cómo trabajar con el foco y navegar por el Siri remoto, consulte la documentación sobre [Cómo trabajar con la navegación y el foco](~/ios/tvos/app-fundamentals/navigation-focus.md) y [Siri remoto y los controladores Bluetooth](~/ios/tvos/platform/remote-bluetooth.md) .

<a name="About-Buttons" />

## <a name="about-buttons"></a>Acerca de los botones

En tvOS, los botones se usan para las acciones específicas de la aplicación y pueden contener un título, un icono o ambos. A medida que el usuario navega por la interfaz de usuario de la aplicación mediante el [Remote Siri](~/ios/tvos/platform/remote-bluetooth.md#The-Siri-Remote), el foco se desplaza hasta el botón especificado, por lo que cambia el texto y los colores de fondo. También se aplica una sombra al botón agregando un efecto 3D que parece subir por encima del resto de la interfaz de usuario.

[![](buttons-images/buttons01.png "Botones de ejemplo")](buttons-images/buttons01.png#lightbox)

Apple tiene las siguientes sugerencias para trabajar con botones:

- **Usar un título o un icono** : mientras tanto un icono como un título pueden incluirse en un botón, el espacio está limitado, por lo que intente no combinar ambos.
- **Marque claramente los botones destructivos** : Si el botón realiza una acción destructiva (como eliminar un archivo), márquelo claramente como tal usando texto o icono. Las acciones destructivas siempre deben presentar una [alerta](~/ios/tvos/user-interface/alerts.md) que pida al usuario que limite la acción.
- **No usar botones atrás** : el botón de menú del control remoto Siri se usa para volver a la pantalla anterior. La única excepción a esta regla es para las compras desde la aplicación o las acciones destructivas en las que se debe mostrar un botón **Cancelar** .

Para obtener más información sobre cómo trabajar con el foco y la navegación, consulte nuestra documentación sobre [Cómo trabajar con navegación y foco](~/ios/tvos/app-fundamentals/navigation-focus.md) .

<a name="Button-Icons" />

### <a name="button-icons"></a>Iconos de botón

Apple sugiere que se usan imágenes simples y muy reconocibles para los iconos de botón. Los iconos demasiado complejos son difíciles de reconocer en una pantalla de TV en la habitación de un sofá, por lo que debe intentar usar la representación más sencilla posible para obtener la idea. Siempre que sea posible, use imágenes estándar y bien conocidas para los iconos (como una lupa para la búsqueda).

<a name="Button-Titles" />

### <a name="button-titles"></a>Títulos de botón

Apple tiene las siguientes sugerencias al crear los títulos de los botones:

- **Mostrar el texto descriptivo debajo de los iconos botones** : siempre que sea posible, coloque solo los botones borrar, texto descriptivo debajo del icono para obtener el propósito del botón.
- **Usar verbos o frases verbales para el título** : indica claramente la acción que tendrá lugar cuando el usuario haga clic en el botón.
- **Usar mayúsculas y minúsculas** en el estilo de título: con la excepción de los artículos, las conjunciones o las preposiciones (cuatro letras o menos), cada palabra del título del botón debe escribirse en mayúsculas.
- **Usar un título corto al punto** : Use el palabras más corto posible para describir la acción del botón.

<a name="Buttons-and-Storyboards" />

## <a name="buttons-and-storyboards"></a>Botones y guiones gráficos

La manera más sencilla de trabajar con botones en una aplicación Xamarin. tvOS es agregarlos a la interfaz de usuario de la aplicación mediante el Xamarin Designer para iOS.

# <a name="visual-studio-for-mactabmacos"></a>[Visual Studio para Mac](#tab/macos)

1. En el **Explorador de soluciones**, haga doble clic en `Main.storyboard` el archivo y ábralo para su edición.
1. Arrastre un **botón** desde la **biblioteca** y colóquelo en la vista: 

    [![](buttons-images/storyboard01.png "Un botón")](buttons-images/storyboard01.png#lightbox)
1. En el **Explorador de propiedades**, puede ajustar varias propiedades del botón, como su **título** y **color del texto**: 

    [![](buttons-images/storyboard02.png "Propiedades del botón")](buttons-images/storyboard02.png#lightbox)
1. A continuación, cambie a la **pestaña eventos** y conecte un **evento** desde el `ButtonPressed` **botón** y llámelo: 

    [![](buttons-images/storyboard03.png "Pestaña eventos")](buttons-images/storyboard03.png#lightbox)
1. Se cambiará automáticamente a la `ViewController.cs` vista en la que puede colocar la nueva acción en el código mediante las teclas de dirección **arriba** y **abajo** : 

    [![](buttons-images/storyboard04.png "Colocar una nueva acción en el código")](buttons-images/storyboard04.png#lightbox)
1. Presione la tecla **entrar** para seleccionar la ubicación: 

    [![](buttons-images/storyboard05.png "El editor de código")](buttons-images/storyboard05.png#lightbox)
1. Guarde los cambios en todos los archivos.

# <a name="visual-studiotabwindows"></a>[Visual Studio](#tab/windows)

1. En el **Explorador de soluciones**, haga doble clic en `Main.storyboard` el archivo y ábralo para su edición.
1. Arrastre un **botón** desde la **biblioteca** y colóquelo en la vista: 

    [![](buttons-images/storyboard01vs.png "Un botón")](buttons-images/storyboard01vs.png#lightbox)
1. En el **Explorador de propiedades**, puede ajustar varias propiedades del botón, como su **título** y **color del texto**: 

    [![](buttons-images/storyboard02vs.png "Explorador de propiedades")](buttons-images/storyboard02vs.png#lightbox)
1. A continuación, cambie a la **pestaña eventos** y conecte un **evento** desde el `ButtonPressed` **botón** y llámelo: 

    [![](buttons-images/storyboard03vs.png "Pestaña eventos")](buttons-images/storyboard03vs.png#lightbox)
1. Guarde los cambios en todos los archivos.

Edite el archivo del controlador `ViewController.cs`de vista (ejemplo) y agregue el código siguiente para controlar el botón que se selecciona:

```

using System;
using UIKit;

namespace tvRemote
{
    public partial class ViewController : UIViewController
    {
        ...

        partial void ButtonPressed (UIButton sender) {
            // Handle click here
            ...
        }
    }
}

```

-----

Siempre y cuando la propiedad de `Enabled` un botón `true` sea y no esté incluida en otro control o vista, se puede convertir en el elemento enfocado mediante Siri remoto. Si el usuario selecciona el botón y hace clic en la superficie de toque `ButtonPressed` , se ejecutará la acción definida anteriormente.

> [!IMPORTANT]
> Aunque es posible asignar acciones como `TouchUpInside` a un `UIButton` en el diseñador de iOS al crear un controlador de **eventos**, nunca se llamará porque Apple TV no tiene una pantalla táctil ni eventos táctiles de soporte técnico. Siempre debe usar el tipo de **acción** predeterminada al crear **acciones** para los elementos de la interfaz de usuario de tvOS.

Para obtener más información sobre cómo trabajar con guiones gráficos, vea nuestra [Guía de inicio rápido Hola, tvOS](~/ios/tvos/get-started/hello-tvos.md).

<a name="Buttons-and-Code" />

## <a name="buttons-and-code"></a>Botones y código

Opcionalmente, se `UIButton` puede crear un en C# el código y agregarlo a la vista de la aplicación tvOS. Por ejemplo:

```csharp
var button = new UIButton(UIButtonType.System);
button.Frame = new CGRect (25, 25, 300, 150);
button.SetTitle ("Hello", UIControlState.Normal);
button.AllEvents += (sender, e) => {
    // Do something when the button is clicked
    ...
};
View.AddSubview (button);
```

Cuando se crea un nuevo `UIButton` en el código, se `UIButtonType` especifica como uno de los siguientes elementos:

- **Sistema** : es el tipo de botón estándar presentado por tvOS y es el tipo que usará con mayor frecuencia.
- **DetailDisclosure** : presenta un tipo de botón "desactivar" que se usa para ocultar o Mostrar información detallada.
- **InfoDark** : botón de información detallada oscura que muestra una "i" en un círculo.
- **InfoLight** : botón de información detallada claro que muestra una "i" en un círculo.
- **AddContact** : muestra el botón como botón Agregar contacto.
- **Personalizado** : permite personalizar varios rasgos del botón.

A continuación, defina el tamaño y la ubicación en pantalla del botón. Ejemplo:

```csharp
button.Frame = new CGRect (25, 25, 300, 150);
```

A continuación, establezca el título para el botón. `UIButtons`son diferentes de la `UIKit` mayoría de los controles en que tienen un estado, por lo que no puede simplemente cambiar el título, sino que debe cambiarlo para un determinado. `UIControlState` Por ejemplo:

```csharp
button.SetTitle ("Hello", UIControlState.Normal);
```

A continuación, use `AllEvents` el evento para ver cuándo el usuario hizo clic en el botón. Ejemplo:

```csharp
button.AllEvents += (sender, e) => {
    // Do something when the button is clicked
    ...
};
```

Por último, agregue el botón a la vista para mostrarlo:

```csharp
View.AddSubview (button);
```

> [!IMPORTANT]
> Aunque es posible asignar acciones como `TouchUpInside` `UIButton`a, nunca se llamará porque Apple TV no tiene una pantalla táctil ni eventos táctiles de soporte técnico. Siempre debe utilizar eventos como **AllEvents** o **PrimaryActionTriggered**.

<a name="Styling-a-Button" />

## <a name="styling-a-button"></a>Aplicar estilo a un botón

tvOS proporciona varias propiedades de `UIButton` que se pueden usar para proporcionar su título y estilo con elementos como el color de fondo y las imágenes.

<a name="Button-Titles" />

### <a name="button-titles"></a>Títulos de botón

Como vimos anteriormente, `UIButtons` son diferentes de la mayoría `UIKit` de los controles en que tienen un estado, por lo que no basta con cambiar el título, sino que debe cambiarlo para un determinado. `UIControlState` Por ejemplo:

```csharp
button.SetTitle ("Hello", UIControlState.Normal);
```

Puede establecer el color del título para el botón mediante el `SetTitleColor` método. Por ejemplo:

```csharp
button.SetTitleColor (UIColor.White, UIControlState.Normal);
```

Además, puede ajustar la sombra del título mediante el `SetTitleShadowColor`. Por ejemplo:

```csharp
button.SetTitleShadowColor(UIColor.Black, UIControlState.Normal);
```

Puede establecer la sombra del título para cambiar de *grabado* a en *relieve* cuando el botón se resalte con el código siguiente:

```csharp
button.ReverseTitleShadowWhenHighlighted = true;
```

Además, puede usar texto con atributos como título del botón. Por ejemplo:

```csharp
var normalAttributedTitle = new NSAttributedString (buttonTitle, foregroundColor: UIColor.Blue, strikethroughStyle: NSUnderlineStyle.Single);
myButton.SetAttributedTitle (normalAttributedTitle, UIControlState.Normal);

var highlightedAttributedTitle = new NSAttributedString (buttonTitle, foregroundColor: UIColor.Green, strikethroughStyle: NSUnderlineStyle.Thick);
myButton.SetAttributedTitle (highlightedAttributedTitle, UIControlState.Highlighted);
```

### <a name="button-images"></a>Imágenes de botón

Un `UIButton` puede tener una imagen adjunta y puede utilizar una imagen como fondo.

Para establecer la imagen de fondo de un botón para un `UIControlState`determinado, use el código siguiente:

```csharp
button.SetBackgroundImage(UIImage.FromFile("my image.png"), UIControlState.Normal);
```

Establezca la `AdjustsImageWhenHiglighted` propiedad en `true` para dibujar la imagen más clara cuando el botón esté resaltado (este es el valor predeterminado). Establezca la `AdjustsImageWhenDisabled` propiedad en `true` para dibujar la imagen más oscura cuando el botón está deshabilitado (de nuevo, es el valor predeterminado).

Para establecer la imagen que se muestra en el botón, utilice el siguiente código:

```csharp
button.SetImage(UIImage.FromFile("my image.png"), UIControlState.Normal);
```

Utilice la `TintColor` propiedad para establecer un tinte de color que se aplique al título y a la imagen del botón. En el caso de `Custom` los botones del tipo, esta propiedad no tiene ningún efecto, `TintColor` debe implementar el comportamiento usted mismo.

<a name="Summary" />

## <a name="summary"></a>Resumen

En este artículo se ha tratado el diseño y el uso de botones dentro de una aplicación Xamarin. tvOS. Se ha mostrado cómo trabajar con botones en el diseñador de iOS y cómo crear botones en C# el código. Por último, ha mostrado cómo modificar el título de un botón y cambiar su estilo y apariencia.

## <a name="related-links"></a>Vínculos relacionados

- [Ejemplos de tvOS](https://docs.microsoft.com/samples/browse/?products=xamarin&term=Xamarin.iOS+tvOS)
- [tvOS](https://developer.apple.com/tvos/)
- [Guías de la interfaz humana de tvOS](https://developer.apple.com/tvos/human-interface-guidelines/)
- [Guía de programación de aplicaciones para tvOS](https://developer.apple.com/library/prerelease/tvos/documentation/General/Conceptual/AppleTV_PG/)
