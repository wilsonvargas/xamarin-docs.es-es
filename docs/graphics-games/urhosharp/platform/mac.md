---
title: Compatibilidad con UrhoSharp Mac
description: Este documento explica la compatibilidad con macOS UrhoSharp. Describe cómo crear un proyecto y proporciona un vínculo al código de ejemplo.
ms.prod: xamarin
ms.assetid: 95FFBD36-14E9-4C17-B1E8-9A04E81E824D
author: conceptdev
ms.author: crdun
ms.date: 03/29/2017
ms.openlocfilehash: ee0a03d168b6e628893b18a27d73b46d3fa2fbc2
ms.sourcegitcommit: 654df48758cea602946644d2175fbdfba59a64f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67832655"
---
# <a name="urhosharp-mac-support"></a>Compatibilidad con UrhoSharp Mac

_Características y configuración específica de Mac_

Aunque Urho es una biblioteca de clases portable, y permite la misma API que se usará en toda la plataforma distintos para la lógica de juego, deberá inicializar Urho en su controlador específico de plataforma y en algunos casos, deseará aprovechar las ventajas de las características específicas de plataforma .

En las páginas siguientes, se supone que `MyGame` es una subclase de la `Application` clase.

## <a name="macos"></a>macOS

**Arquitecturas compatibles:** x86/x86-64 para 32 bits y 64 bits.

## <a name="creating-a-project"></a>Creación de un proyecto

Crear un proyecto de consola, hacen referencia a Urho NuGet y, a continuación, asegúrese de que puede encontrar los recursos (es decir, los directorios que contiene el directorio de datos).

```csharp
DesktopUrhoInitializer.AssetsDirectory = "../Assets";
new MyGame().Run();
```

## <a name="example"></a>Ejemplo

[Ejemplo completo](https://github.com/xamarin/urho-samples/tree/master/FeatureSamples/Cocoa)
