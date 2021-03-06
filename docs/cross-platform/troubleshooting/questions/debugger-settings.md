---
title: ¿Qué configuración del proyecto es necesaria para el depurador?
ms.topic: troubleshooting
ms.prod: xamarin
ms.assetid: 3A024E4E-ACA3-4C7A-ADEF-541665D15779
author: conceptdev
ms.author: crdun
ms.date: 05/08/2018
ms.openlocfilehash: a3677117e30538c4df8c9b797acce0be602c3b59
ms.sourcegitcommit: 6b833f44d5fd8dc7ab7f8546e8b7d383e5a989db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106088"
---
# <a name="what-project-settings-are-required-for-the-debugger"></a>¿Qué configuración del proyecto es necesaria para el depurador?

Para que el depurador funcione según lo esperado (puntos de interrupción, Mostrar registros de depuración, etc.), se debe habilitar la presentación de la información de depuración y la instrumentación del desarrollador.

Siga estos pasos para comprobar la configuración del entorno:

## <a name="visual-studio"></a>Visual Studio

1. Abrir las opciones del proyecto
2. Vaya a **Compilar > avanzadas...** Establecer la información de depuración en **completa**
3. Configuración de cada plataforma:
   - Vaya a **Opciones de Android > opciones de depuración**. Marque el cuadro **Habilitar instrumentación de desarrollador** .
   - Vaya a la **depuración de iOS > la instrumentación de &** . Marque el cuadro **Habilitar depuración** .

## <a name="visual-studio-for-mac"></a>Visual Studio para Mac

1. Abrir las opciones del proyecto
2. Vaya a **compilación > Compilador > opciones generales**. Establecer la información de depuración en **completa**
3. Configuración de cada plataforma:
    - Vaya a **compilación > opciones de depuración de compilación > Android**. Marque el cuadro **Habilitar instrumentación de desarrollador** .
    - Vaya a **compilación > depuración de iOS**. Marque el cuadro **Habilitar depuración** .
