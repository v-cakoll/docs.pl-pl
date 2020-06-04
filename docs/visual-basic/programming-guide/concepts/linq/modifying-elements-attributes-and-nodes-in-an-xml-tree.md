---
title: Modyfikowanie elementów, atrybutów i węzłów w Tree1 XML
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: 002e87d58ad1a3730889225bf4b3e50448431f2d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360933"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>Modyfikowanie elementów, atrybutów i węzłów w drzewie XML
Poniższa tabela zawiera podsumowanie metod i właściwości, których można użyć do modyfikacji elementu, jego elementów podrzędnych lub jego atrybutów.  
  
 Poniższe metody modyfikują <xref:System.Xml.Linq.XElement> .  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Zastępuje element przeanalizowanym kodem XML.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Usuwa całą zawartość (węzły podrzędne i atrybuty) elementu.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Usuwa atrybuty elementu.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Zamienia całą zawartość (węzły podrzędne i atrybuty) elementu.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Zastępuje atrybuty elementu.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu. Tworzy atrybut, jeśli nie istnieje. Jeśli wartość jest ustawiona na `null` , program usuwa atrybut.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Ustawia wartość elementu podrzędnego. Tworzy element, jeśli nie istnieje. Jeśli wartość jest ustawiona na `null` , powoduje usunięcie elementu.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Zamienia zawartość (węzły podrzędne) elementu na określony tekst.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Ustawia wartość elementu.|  
  
 Poniższe metody modyfikują <xref:System.Xml.Linq.XAttribute> .  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu.|  
  
 Następujące metody modyfikują <xref:System.Xml.Linq.XNode> (łącznie z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> ).  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Zamienia węzeł na nową zawartość.|  
  
 Następujące metody modyfikują <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> a lub <xref:System.Xml.Linq.XDocument> ).  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Zamienia węzły podrzędne na nową zawartość.|  
  
## <a name="see-also"></a>Zobacz też

- [Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)
