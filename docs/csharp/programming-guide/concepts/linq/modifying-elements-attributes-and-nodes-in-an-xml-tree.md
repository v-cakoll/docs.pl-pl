---
title: Modyfikowanie elementów, atrybutów i węzłów w Tree3 XML
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484233"
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
