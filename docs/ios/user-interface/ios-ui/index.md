---
title: Interfaces de usuario en iOS
description: En este documento se proporcionan vínculos a guías que describen cómo compilar interfaces de usuario en la aplicación Xamarin. iOS. Las guías vinculadas cubren la API de apariencia, la creación de objetos de interfaz de usuario, las opciones de diseño y mucho más.
ms.prod: xamarin
ms.assetid: 1BB46561-F503-491E-A27C-7878E7EBE00B
ms.technology: xamarin-ios
author: conceptdev
ms.author: crdun
ms.date: 06/14/2017
ms.openlocfilehash: 954e3b8f612fd710dd178cfc296889c9da372183
ms.sourcegitcommit: 57f815bf0024b1afe9754c0e28054fc0a53ce302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70768307"
---
# <a name="user-interfaces-in-ios"></a>Interfaces de usuario en iOS

## <a name="appearance-apiintroduction-to-the-appearance-apimd"></a>[Appearance API](introduction-to-the-appearance-api.md)

iOS permite que muchos atributos visuales de los controles de interfaz de usuario se utilicen con las API de UIAppearance.

## <a name="creating-user-interface-objectsiosuser-interfaceios-uicreating-ui-objectsmd"></a>[Creación de objetos de la interfaz de usuario](~/ios/user-interface/ios-ui/creating-ui-objects.md)

Apple agrupa los elementos de funcionalidad relacionados en "Marcos", que equivalen a los espacios de nombres de Xamarin. iOS. `UIKit`es el espacio de nombres que contiene todos los controles de interfaz de usuario para iOS.

## <a name="layout-optionsiosuser-interfaceios-uilayout-optionsmd"></a>[Opciones de diseño](~/ios/user-interface/ios-ui/layout-options.md)

Hay dos mecanismos diferentes para controlar el diseño cuando se cambia el tamaño o se gira una vista: Ajuste automático de tamaño y diseño automático.

## <a name="providing-haptic-feedbackiosuser-interfaceios-uihaptic-feedbackmd"></a>[Provisión de comentarios hápticos](~/ios/user-interface/ios-ui/haptic-feedback.md)

En este artículo se describen los nuevos tipos de comentarios hápticos disponibles en iOS 10 y cómo implementarlos en Xamarin. iOS.

## <a name="working-with-the-ui-threadiosuser-interfaceios-uiui-threadmd"></a>[Trabajo con el subproceso de la interfaz de usuario](~/ios/user-interface/ios-ui/ui-thread.md)

El código solo debe realizar cambios en los controles de interfaz de usuario del subproceso principal (o UI). Es posible que las actualizaciones de la interfaz de usuario que se producen en un subproceso diferente (como una devolución de llamada o un subproceso en segundo plano) no se representen en la pantalla, o incluso podrían provocar un bloqueo.
