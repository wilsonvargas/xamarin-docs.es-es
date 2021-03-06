---
title: Azure Active Directory
description: En este documento se describen los pasos que deben seguirse para permitir que una aplicación móvil se autentique con Azure Active Directory.
ms.prod: xamarin
ms.assetid: 70B3C2AB-CB4D-420C-9CFA-20CCFA0E3C78
author: conceptdev
ms.author: crdun
ms.date: 03/23/2017
ms.openlocfilehash: b28fcea37d991879df0231609d09eeb2eca49505
ms.sourcegitcommit: 57f815bf0024b1afe9754c0e28054fc0a53ce302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766350"
---
# <a name="azure-active-directory"></a>Azure Active Directory

_Registro de una aplicación para usar Azure Active Directory_

Azure Active Directory permite a los desarrolladores proteger recursos como archivos, vínculos y API Web con la misma cuenta de la organización que usan los empleados para iniciar sesión en sus sistemas o comprobar sus mensajes de correo electrónico.

El desarrollo de aplicaciones móviles que pueden autenticarse con Azure Active Directory implica tres pasos.
Los dos primeros pasos suelen ser los mismos, independientemente de los servicios que tenga previsto usar. El tercer paso es diferente para cada tipo de servicio:

  1. [Registro con Azure Active Directory](~/cross-platform/data-cloud/active-directory/get-started/register.md) en el portal de *windowsazure.com* ,
  2. [Configurar servicios](~/cross-platform/data-cloud/active-directory/get-started/configure.md).
  3. Desarrolle aplicaciones móviles con los servicios.

Entre los ejemplos de los distintos servicios a los que puede acceder se incluyen:

- [Graph API](~/cross-platform/data-cloud/active-directory/graph.md)
- Web API
- Office365

## <a name="conclusion"></a>Conclusión

Con los pasos anteriores, puede autenticar las aplicaciones móviles en Azure Active Directory. El Biblioteca de autenticación de Active Directory (ADAL) hace que sea mucho más fácil con menos líneas de código, a la vez que mantiene la mayor parte del código de la misma y, por lo tanto, se comparte en todas las plataformas.

## <a name="related-links"></a>Vínculos relacionados

- [Ejemplo de Microsoft NativeClient](https://github.com/AzureADSamples/NativeClient-MultiTarget-DotNet)
