---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: 891c451bc573e41e26833878187224cf54510435
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566856"
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
