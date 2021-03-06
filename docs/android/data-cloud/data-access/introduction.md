---
title: Introducción al almacenamiento de datos en Android
ms.prod: xamarin
ms.assetid: FDAC0771-4749-4758-865A-F1BD190CA54B
ms.technology: xamarin-android
author: conceptdev
ms.author: crdun
ms.date: 03/28/2017
ms.openlocfilehash: 69d5222bb6c50870d0c42bea6ff71236e3d1580c
ms.sourcegitcommit: 699de58432b7da300ddc2c85842e5d9e129b0dc5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "70754562"
---
# <a name="introduction"></a>Introducción

## <a name="when-to-use-a-database"></a>Cuándo usar una base de datos

Aunque las capacidades de almacenamiento y procesamiento de los dispositivos móviles están aumentando, los teléfonos y las tabletas siguen retrasando sus homólogos de escritorio y portátiles. Por esta razón, merece la pena dedicar algún tiempo a planear la arquitectura de almacenamiento de datos de la aplicación en lugar de asumir simplemente que una base de datos es la respuesta correcta en todo momento. Hay varias opciones diferentes que se adaptan a diferentes requisitos, como:

- **Preferencias** : Android ofrece un mecanismo integrado para almacenar pares de datos de clave-valor simples. Si va a almacenar una configuración de usuario simple o pequeñas partes de datos (como información de personalización), use las características nativas de la plataforma para almacenar este tipo de información.
- **Archivos de texto** : datos proporcionados por el usuario o memorias caché del contenido descargado (por ejemplo, HTML) se puede almacenar directamente en el sistema de archivos. Use una Convención de nomenclatura de archivos adecuada para ayudarle a organizar los archivos y a encontrar los datos.
- **Archivos de datos serializados: los** objetos se pueden almacenar como XML o JSON en el sistema de archivos. .NET Framework incluye bibliotecas que facilitan la serialización y la deserialización de objetos. Use los nombres adecuados para organizar los archivos de datos.
- **Base** de datos: el motor de base de datos SQLite está disponible en la plataforma Android y es útil para almacenar datos estructurados que necesita consultar, ordenar o manipular de otra manera. El almacenamiento de base de datos es adecuado para listas de datos con muchas propiedades.
- **Archivos de imagen** : aunque es posible almacenar datos binarios en la base de datos en un dispositivo móvil, se recomienda almacenarlos directamente en el sistema de archivos. Si es necesario, puede almacenar los nombres de archivo en una base de datos para asociar la imagen a otros datos. Cuando se trabaja con imágenes de gran tamaño, o muchas imágenes, es recomendable planear una estrategia de almacenamiento en caché que elimine los archivos que ya no necesita para evitar consumir todo el espacio de almacenamiento del usuario.

Si una base de datos es el mecanismo de almacenamiento adecuado para su aplicación, en el resto de este documento se explica cómo usar SQLite en la plataforma de Xamarin.

## <a name="advantages-of-using-a-database"></a>Ventajas del uso de una base de datos

Hay varias ventajas en el uso de una base de datos SQL en la aplicación móvil:

- Las bases de datos SQL permiten un almacenamiento eficaz de datos estructurados.
- Los datos específicos se pueden extraer con consultas complejas.
- Los resultados de la consulta se pueden ordenar.
- Los resultados de la consulta se pueden agregar.
- Los desarrolladores con conocimientos de bases de datos existentes pueden aprovechar sus conocimientos para diseñar la base de datos y el código de acceso a datos.
- El modelo de datos del componente de servidor de una aplicación conectada se puede volver a usar (en su totalidad o en parte) en la aplicación móvil.

## <a name="sqlite-database-engine"></a>Motor de base de datos SQLite

SQLite es un motor de base de datos de código abierto adoptado por Google para su plataforma móvil. El motor de base de datos de SQLite está integrado en ambos sistemas operativos, por lo que no hay trabajo adicional para que los desarrolladores puedan aprovecharlo. SQLite es idóneo para el desarrollo móvil multiplataforma porque:

- El motor de base de datos es pequeño, rápido y fácil de transportar.
- Una base de datos se almacena en un único archivo, que es fácil de administrar en dispositivos móviles.
- El formato de archivo es fácil de usar entre plataformas: si se trata de sistemas de 32 o 64 bits y de Big-Endian.
- Implementa la mayor parte del estándar SQL92.

Dado que SQLite está diseñado para ser pequeño y rápido, hay algunas advertencias sobre su uso:

- No se admiten algunas sintaxis de combinación externa.
- Solo se admiten Rename de tabla y ADDCOLUMN. No se pueden realizar otras modificaciones en el esquema.
- Las vistas son de solo lectura.

Puede obtener más información acerca de SQLite en el sitio Web- [SQLite.org](http://SQLite.org) ; sin embargo, toda la información que necesita para usar SQLite con Xamarin se incluye en este documento y en los ejemplos asociados. El motor de base de datos SQLite se admitía en Android desde Android 2.
Aunque no se trata en este capítulo, SQLite también está disponible para su uso en Windows Phone y aplicaciones Windows.

## <a name="windows-and-windows-phone"></a>Windows y Windows Phone

SQLite también puede usarse en plataformas Windows, aunque dichas plataformas no se describen en este documento.
Lea más en la [tarea](~/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky.md) y en los casos prácticos de [Pro](~/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky.md) con tareas y revise el [blog de Tim Heuer](http://timheuer.com/blog/archive/2012/06/28/seeding-your-metro-style-app-with-sqlite-database.aspx).

## <a name="related-links"></a>Vínculos relacionados

- [Acceso a datos básico (ejemplo)](https://github.com/xamarin/mobile-samples/tree/master/DataAccess/Basic)
- [Acceso a la configuración avanzada (ejemplo)](https://github.com/xamarin/mobile-samples/tree/master/DataAccess/Advanced)
- [Recetas de datos de Android](https://github.com/xamarin/recipes/tree/master/Recipes/android/data)
- [Acceso a datos de Xamarin. Forms](~/xamarin-forms/data-cloud/data/databases.md)
