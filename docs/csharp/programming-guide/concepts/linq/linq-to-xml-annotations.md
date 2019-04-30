---
title: LINQ to XML Annotations3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 753fc656d78f2cefde98a8cbfb48713c7a107f77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701804"
---
# <a name="linq-to-xml-annotations"></a>Adnotacje LINQ to XML
Adnotacje w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwiają skojarzenie z dowolnych obiektów dowolnego typu za pomocą dowolnego składnika XML w drzewie XML.  
  
 Dodawanie adnotacji do elementu XML, takie jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, należy wywołać <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metody. Możesz pobrać adnotacje według typu.  
  
 Należy pamiętać, że adnotacji nie są częścią zestaw informacji XML; nie jest serializowany lub deserializowany.  
  
## <a name="methods"></a>Metody  
 Podczas pracy z adnotacjami, można użyć następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Dodaje obiekt do listy adnotacji <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Pobiera pierwszy obiekt adnotacji określonego typu z <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Pobiera kolekcję adnotacje określonego typu <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Usuwa adnotacje określonego typu z <xref:System.Xml.Linq.XObject>.|  
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowane LINQ to XML programowania (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
