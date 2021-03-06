---
title: Técnicas de procesamiento en segundo plano de iOS
description: 'En este documento se proporcionan vínculos a guías en las que se describen varias técnicas de fondo en iOS: tareas en segundo plano, servicio de transferencia en segundo plano, captura en segundo plano y notificaciones remotas.'
ms.prod: xamarin
ms.assetid: 011A8D48-1CDC-486A-A2B0-C4946118E7A9
ms.technology: xamarin-ios
author: conceptdev
ms.author: crdun
ms.date: 03/18/2017
ms.openlocfilehash: a21ce124e20a421be40d41af5f066e611152317b
ms.sourcegitcommit: 933de144d1fbe7d412e49b743839cae4bfcac439
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70281121"
---
# <a name="ios-backgrounding-techniques"></a>Técnicas de procesamiento en segundo plano de iOS

En las secciones siguientes, se explorarán las siguientes características de iOS junto con las opciones de fondo existentes:

- [Tareas en segundo plano oportunista](~/ios/app-fundamentals/backgrounding/ios-backgrounding-techniques/ios-backgrounding-with-tasks.md#background_tasks_in_iOS_7) : conservar la duración de la batería mediante la ejecución de tareas en segundo plano en fragmentos oportunistas cuando el dispositivo está activo para otro procesamiento.
- [Servicio de transferencia en segundo plano](~/ios/app-fundamentals/backgrounding/ios-backgrounding-techniques/ios-backgrounding-with-tasks.md#background-transfers) : cargue y descargue archivos de forma confiable independientemente del estado de la red o del tamaño de archivo.
- [Captura en segundo plano](~/ios/app-fundamentals/backgrounding/ios-backgrounding-techniques/updating-an-application-in-the-background.md#background_fetch) : actualice una aplicación desde el fondo a intervalos determinados por el sistema.
- [Notificaciones remotas](~/ios/app-fundamentals/backgrounding/ios-backgrounding-techniques/updating-an-application-in-the-background.md#remote_notifications) : Use las notificaciones de envío para desencadenar actualizaciones de contenido en segundo plano antes de que el usuario abra la aplicación, con una opción para notificar al usuario o actualizar de forma silenciosa.
- Actualizaciones de la interfaz de usuario **en segundo plano** : Prepare la interfaz de usuario de la aplicación para el usuario y actualice la instantánea de la aplicación, todo desde el fondo.
