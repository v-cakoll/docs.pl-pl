---
title: Modyfikowanie elementów, atrybutów i węzłów w drzewie XML3
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484233"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>Modyfikowanie elementów, atrybutów i węzłów w drzewie XML
W poniższej tabeli podsumowano metody i właściwości, których można użyć do zmodyfikowania elementu, jego elementów podrzędnych lub jego atrybutów.  
  
 Następujące metody modyfikują plik <xref:System.Xml.Linq.XElement>.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Zastępuje element przeanalizowanym kodem XML.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Usuwa całą zawartość (węzły podrzędne i atrybuty) elementu.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Usuwa atrybuty elementu.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Zastępuje całą zawartość (węzły podrzędne i atrybuty) elementu.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Zastępuje atrybuty elementu.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu. Tworzy atrybut, jeśli nie istnieje. Jeśli wartość jest `null`ustawiona na , usuwa atrybut.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Ustawia wartość elementu podrzędnego. Tworzy element, jeśli nie istnieje. Jeśli wartość jest `null`ustawiona na , usuwa element.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Zastępuje zawartość (węzły podrzędne) elementu określonym tekstem.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Ustawia wartość elementu.|  
  
 Następujące metody modyfikują plik <xref:System.Xml.Linq.XAttribute>.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Ustawia wartość atrybutu.|  
  
 Następujące metody modyfikują <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XElement> (w tym lub <xref:System.Xml.Linq.XDocument>).  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Zastępuje węzeł nową zawartością.|  
  
 Następujące metody modyfikują <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>(an <xref:System.Xml.Linq.XContainer> lub ).  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Zastępuje węzły podrzędne nową zawartością.|  
