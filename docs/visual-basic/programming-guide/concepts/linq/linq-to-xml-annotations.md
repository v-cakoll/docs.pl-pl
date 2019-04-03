---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: edf8e0126c632deae6b6d4c235c4880d7b8687e8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831753"
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

- [Zaawansowane LINQ to XML programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
