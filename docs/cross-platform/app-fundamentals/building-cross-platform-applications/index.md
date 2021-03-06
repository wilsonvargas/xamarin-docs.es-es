---
title: Creación de aplicaciones multiplataforma
description: En esta sección se analiza, en un resumen más de seis partes, cómo crear aplicaciones con la plataforma de desarrollo de Xamarin, desde comprender cómo funciona Xamarin para diseñar aplicaciones móviles y, a continuación, probar e implementar en las distintas tiendas de aplicaciones.
ms.prod: xamarin
ms.assetid: 442FC40A-84DD-A218-0D15-EAD86594B6D7
author: conceptdev
ms.author: crdun
ms.date: 01/28/2016
ms.openlocfilehash: 2c630e58ff5a1221ec9e95099df4781041ecf2b4
ms.sourcegitcommit: 699de58432b7da300ddc2c85842e5d9e129b0dc5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "70288059"
---
# <a name="building-cross-platform-applications"></a>Creación de aplicaciones multiplataforma

Hay dos opciones para compartir código entre aplicaciones móviles multiplataforma: Proyectos de recursos compartidos y bibliotecas de clases portables. Estas opciones se [tratan aquí](~/cross-platform/app-fundamentals/code-sharing.md): también está disponible más información sobre las [bibliotecas de clases portable](~/cross-platform/app-fundamentals/pcl.md) y los [proyectos compartidos](~/cross-platform/app-fundamentals/shared-projects.md) .

<a name="Sections" />

 [Información general](~/cross-platform/app-fundamentals/building-cross-platform-applications/overview.md)

 [Parte 1: Descripción de la plataforma móvil Xamarin](~/cross-platform/app-fundamentals/building-cross-platform-applications/understanding-the-xamarin-mobile-platform.md)

 [Parte 2: arquitectura](~/cross-platform/app-fundamentals/building-cross-platform-applications/architecture.md)

 [Parte 3: configurar una solución multiplataforma de Xamarin](~/cross-platform/app-fundamentals/building-cross-platform-applications/setting-up-a-xamarin-cross-platform-solution.md)

 [Parte 4: trabajar con varias plataformas](~/cross-platform/app-fundamentals/building-cross-platform-applications/platform-divergence-abstraction-divergent-implementation.md)

 [Parte 5: estrategias prácticas de uso compartido de código](~/cross-platform/app-fundamentals/building-cross-platform-applications/practical-code-sharing-strategies.md)

 [Parte 6: Pruebas y aprobaciones de App Store](~/cross-platform/app-fundamentals/building-cross-platform-applications/testing-and-app-store-approvals.md)

 <a name="Cross-Platform_Mobile_Application_Case_Studies" />

## <a name="case-studies"></a>Casos prácticos

Los principios descritos en este documento se ponen en práctica en la *tarea*de aplicación de ejemplo, así como en [las aplicaciones precompiladas](https://xamarin.com/prebuilt) como [Xamarin CRM](https://xamarin.com/prebuilt/#xamarincrm).

 <a name="Tasky" />

### <a name="tasky"></a>Tasky

Tasky es una sencilla aplicación de lista de tareas pendientes para iOS, Android y Windows Phone.
Se muestran los aspectos básicos de la creación de una aplicación multiplataforma con Xamarin y se usa una base de datos SQLite local.

 lista de tareas de lista [ ![de tareas](images/iphone-list-sml.png)](images/iphone-list.png#lightbox) [ ![](images/iphone-list-sml.png)](images/iphone-list.png#lightbox)

Lea el [caso práctico de tarea](~/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky.md).

## <a name="summary"></a>Resumen

En esta sección se presentan las herramientas de desarrollo de aplicaciones de Xamarin y se explica cómo crear aplicaciones destinadas a varias plataformas móviles.

Incluye una arquitectura en capas que estructura el código para reutilizarlo en varias plataformas y describe distintos patrones de software que se pueden usar en esa arquitectura.

Se proporcionan ejemplos de funciones de aplicación comunes (como operaciones de archivos y redes) y cómo se pueden compilar de forma multiplataforma.

Por último, analiza brevemente las pruebas y proporciona referencias a un caso práctico que pone estos principios en acción.

## <a name="related-links"></a>Vínculos relacionados

- [Opciones de código compartido](~/cross-platform/app-fundamentals/code-sharing.md)
- [Caso práctico: Tasky](~/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky.md)
- [Aplicación de ejemplo de tarea (GitHub)](https://docs.microsoft.com/samples/xamarin/mobile-samples/taskyportable/)
- [Desarrollo de aplicaciones móviles de Xamarin: Aspectos básicos de C# Xamarin. Forms y multiplataforma (Amazon)](http://www.amazon.com/Xamarin-Mobile-Application-Development-Cross-Platform/dp/1484202155/)
- [Desarrollo móvil con C# por Greg shackles (O'Reilly)](http://shop.oreilly.com/product/0636920024002.do)
- [Desarrollo Móvil multiplataforma profesional en C# Scott Olson, John Hunter, Ben Horgen, Kenny goers (Wrox)](http://www.wrox.com/WileyCDA/WroxTitle/Professional-Cross-Platform-Mobile-Development-in-C-.productCd-1118157702.html)
