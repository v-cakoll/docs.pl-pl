---
title: Usuwanie węzłów z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: 5df95700bb1e84aa5f3adcc752b2314dc964477b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288644"
---
# <a name="removing-nodes-from-the-dom"></a>Usuwanie węzłów z modelu DOM
Aby usunąć węzeł z Document Object Model XML (DOM), użyj <xref:System.Xml.XmlNode.RemoveChild%2A> metody w celu usunięcia określonego węzła. Po usunięciu węzła Metoda usuwa poddrzewo należące do usuwanego węzła; oznacza to, że jeśli nie jest to węzeł liścia.  
  
 Aby usunąć wiele węzłów z modelu DOM, użyj <xref:System.Xml.XmlNode.RemoveAll%2A> metody w celu usunięcia wszystkich elementów podrzędnych i atrybutów, jeśli ma zastosowanie, bieżącego węzła.  
  
 Jeśli pracujesz z programem <xref:System.Xml.XmlNamedNodeMap> , możesz usunąć węzeł przy użyciu <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metody.  
  
 Aby usunąć atrybuty, zobacz [usuwanie atrybutów z węzła elementu w modelu dom](removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
