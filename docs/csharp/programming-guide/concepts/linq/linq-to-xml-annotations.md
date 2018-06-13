---
title: LINQ do XML Annotations3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 8b8e03b0174ad2bf044c21eb9a9d3391da37fb7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320121"
---
# <a name="linq-to-xml-annotations"></a>LINQ do XML adnotacji
Adnotacje w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można skojarzyć dowolnych obiektów dowolnego typu dowolnego z dowolnym składnikiem XML w drzewie XML.  
  
 Dodawanie adnotacji do elementu XML, takich jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, należy wywołać <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metody. Możesz pobrać adnotacje według typu.  
  
 Należy pamiętać, że adnotacje nie są częścią XML typu infoset sprawdzonych; nie jest serializowany lub deserializowany.  
  
## <a name="methods"></a>Metody  
 Podczas pracy z adnotacjami, można użyć następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Dodaje obiekt do listy adnotacji <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Pobiera pierwszy obiekt adnotacji określonego typu z <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Pobiera kolekcję adnotacje dla określonego typu <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Usuwa adnotacje określonego typu z <xref:System.Xml.Linq.XObject>.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane LINQ do XML programowania (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
