---
title: Modyfikowanie elementów, atrybutów i węzłów w Tree1 XML
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: c3863f52976303407cbad3d0bacc9bd0b2ec1d31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547543"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>Modyfikowanie elementów, atrybutów i węzłów w drzewie XML
W poniższej tabeli podsumowano, metody i właściwości, których można zmodyfikować elementu, jego elementów podrzędnych lub jego atrybuty.  
  
 Zmodyfikuj następujące metody <xref:System.Xml.Linq.XElement>.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Zamienia element przeanalizowany plik XML.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Usuwa wszystkie zawartości elementu (węzły podrzędne i atrybuty).|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Usuwa atrybuty elementu.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Zastępuje całą zawartość elementu (węzły podrzędne i atrybuty).|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Zastępuje atrybuty elementu.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu. Tworzy atrybut, jeśli nie istnieje. Jeśli wartość jest równa `null`, usuwa atrybut.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Ustawia wartość elementu podrzędnego. Tworzy element, jeśli nie istnieje. Jeśli wartość jest równa `null`, usuwa element.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Zamienia określony tekst zawartości elementu (węzły podrzędne).|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Ustawia wartość elementu.|  
  
 Zmodyfikuj następujące metody <xref:System.Xml.Linq.XAttribute>.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu.|  
  
 Zmodyfikuj następujące metody <xref:System.Xml.Linq.XNode> (w tym <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>).  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Zamienia węzeł nowej zawartości.|  
  
 Zmodyfikuj następujące metody <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>).  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Zamienia węzłów podrzędnych nowej zawartości.|  
  
## <a name="see-also"></a>Zobacz także
- [Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
