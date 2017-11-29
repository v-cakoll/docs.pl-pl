---
title: "Modyfikowanie elementy, atrybuty i węzłów w Tree1 XML"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c769885d958abeaa92e19ef0b20d695fbcc4b96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>Modyfikowanie elementy, atrybuty i węzłów w drzewie XML
W poniższej tabeli przedstawiono metody i właściwości, które można zmodyfikować elementu, jego elementy podrzędne lub jego atrybuty.  
  
 Zmodyfikuj następujące metody <xref:System.Xml.Linq.XElement>.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Zamienia element XML przeanalizowany.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Usuwa wszystkie zawartości elementu (węzły podrzędne i atrybuty).|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Usuwa atrybuty elementu.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Zamienia wszystkie zawartości elementu (węzły podrzędne i atrybuty).|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Zamienia atrybuty elementu.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu. Tworzy atrybut, jeśli nie istnieje. Jeśli wartość jest równa `null`, usuwa atrybut.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Ustawia wartość elementu podrzędnego. Tworzy element, jeśli nie istnieje. Jeśli wartość jest równa `null`, usuwa element.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Zamienia określony tekst zawartości elementu (węzłów podrzędnych).|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Ustawia wartość elementu.|  
  
 Zmodyfikuj następujące metody <xref:System.Xml.Linq.XAttribute>.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu.|  
  
 Modyfikowanie następujących metod <xref:System.Xml.Linq.XNode> (łącznie z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>).  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Zamienia węzła nową zawartość.|  
  
 Modyfikowanie następujących metod <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>).  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Węzły podrzędne są zastępowane nową zawartość.|  
  
## <a name="see-also"></a>Zobacz też  
 [Modyfikowanie drzew XML (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
