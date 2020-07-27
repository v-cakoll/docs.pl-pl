---
title: Adnotacje LINQ to XML
description: Dowiedz się, jak używać adnotacji w LINQ to XML do kojarzenia dowolnego dowolnego dowolnego obiektu dowolnego dowolnego typu z dowolnym składnikiem XML w drzewie XML.
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: e7da666139c10b26de37816693202d96498f52d8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165574"
---
# <a name="linq-to-xml-annotations"></a>Adnotacje LINQ to XML

Adnotacje w programie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwiają kojarzenie dowolnego dowolnego dowolnego obiektu dowolnego dowolnego typu z dowolnym składnikiem XML w drzewie XML.

Aby dodać adnotację do składnika XML, takiego jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> , należy wywołać <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metodę. Pobierasz adnotacje według typu.

Zwróć uwagę, że adnotacje nie są częścią sprawdzonych XML; nie są one serializowane ani deserializowane.

## <a name="methods"></a>Metody

Podczas pracy z adnotacjami można użyć następujących metod:

|Metoda|Opis|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Dodaje obiekt do listy adnotacji elementu <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Pobiera pierwszy obiekt adnotacji określonego typu z <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Pobiera kolekcję adnotacji określonego typu dla <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Usuwa adnotacje określonego typu z <xref:System.Xml.Linq.XObject> .|
