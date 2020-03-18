---
title: LINQ do Adnotacji XML3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 5f1940be2fc126ff9e9c7a4cb37e5cc7fc95d3c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66689945"
---
# <a name="linq-to-xml-annotations"></a>Adnotacje LINQ to XML

Adnotacje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwiające skojarzenie dowolnego obiektu dowolnego dowolnego typu z dowolnym składnikiem XML w drzewie XML.

Aby dodać adnotację do składnika XML, takiego jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, należy wywołać <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metodę. Adnotacje można pobrać według typu.

Należy zauważyć, że adnotacje nie są częścią zestawu informacji XML; nie są serializowane ani deserializowane.

## <a name="methods"></a>Metody

Podczas pracy z adnotacjami można użyć następujących metod:

|Metoda|Opis|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Dodaje obiekt do listy adnotacji pliku <xref:System.Xml.Linq.XObject>.|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Pobiera pierwszy obiekt adnotacji określonego typu <xref:System.Xml.Linq.XObject>z pliku .|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Pobiera kolekcję adnotacji określonego typu dla <xref:System.Xml.Linq.XObject>.|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Usuwa adnotacje określonego typu z <xref:System.Xml.Linq.XObject>pliku .|
