---
title: Navegación por Xamarin.Forms
description: En esta guía se explica cómo navegar por las aplicaciones de Xamarin.Forms. Xamarin.Forms proporciona una serie de experiencias de navegación de páginas diferente, en función del tipo de página que se use.
ms.prod: xamarin
ms.assetid: BC5D0C6C-D5A9-4B12-A492-ED1F570CEC87
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 12/01/2017
ms.openlocfilehash: 682e3bd0ac4cdd651203496dd28586db2cef3165
ms.sourcegitcommit: c2bba24233624c2ec0e9ee9827310ca022212a2c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835262"
---
# <a name="xamarinforms-navigation"></a>Navegación por Xamarin.Forms

_Xamarin.Forms proporciona una serie de experiencias de navegación de páginas diferente, en función del tipo de página que se use._

![](images/page-types.png "Tipos de páginas de Xamarin.Forms")

Como alternativa, las aplicaciones de Xamarin.Forms Shell usan una experiencia de navegación basada en URI que no obliga a una jerarquía de navegación del conjunto. Para más información, consulte [Navegación en Xamarin.Forms Shell](~/xamarin-forms/app-fundamentals/shell/navigation.md).

## <a name="hierarchical-navigationhierarchicalmd"></a>[Navegación jerárquica](hierarchical.md)

La clase [`NavigationPage`](xref:Xamarin.Forms.NavigationPage) proporciona una experiencia de navegación jerárquica en la que el usuario puede navegar por las páginas hacia delante y hacia atrás, si quiere. La clase implementa la navegación como una pila de objetos [`Page`](xref:Xamarin.Forms.Page) en la que el último en entrar es el primero en salir (LIFO).

## <a name="tabbedpagetabbed-pagemd"></a>[TabbedPage](tabbed-page.md)

[`TabbedPage`](xref:Xamarin.Forms.TabbedPage) de Xamarin.Forms consta de una lista de pestañas y un área de detalles mayor. Cada pestaña carga contenido en el área de detalles.

## <a name="carouselpagecarousel-pagemd"></a>[CarouselPage](carousel-page.md)

[`CarouselPage`](xref:Xamarin.Forms.CarouselPage) de Xamarin.Forms es una página que los usuarios pueden deslizar de lado a lado para navegar por páginas de contenido, como una galería.

## <a name="masterdetailpagemaster-detail-pagemd"></a>[MasterDetailPage](master-detail-page.md)

[`MasterDetailPage`](xref:Xamarin.Forms.MasterDetailPage) de Xamarin.Forms es una página que administra dos páginas de información relacionada: una página maestra que presenta los elementos y una página de detalles que muestra los detalles sobre los elementos de la página maestra.

## <a name="modal-pagesmodalmd"></a>[Páginas modales](modal.md)

Xamarin.Forms también es compatible con las páginas modales. Una página modal anima a los usuarios a completar una tarea autocontenida que no se puede abandonar mientras no se complete o se cancele la tarea.
