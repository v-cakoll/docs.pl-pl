---
title: Usuwanie węzłów z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: a34b92abc59215c3cb2b94afd88e2e30405b4e9a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710313"
---
# <a name="removing-nodes-from-the-dom"></a>Usuwanie węzłów z modelu DOM
Aby usunąć węzeł z Document Object Model XML (DOM), użyj <xref:System.Xml.XmlNode.RemoveChild%2A> metody w celu usunięcia określonego węzła. Po usunięciu węzła Metoda usuwa poddrzewo należące do usuwanego węzła; oznacza to, że jeśli nie jest to węzeł liścia.  
  
 Aby usunąć wiele węzłów z modelu DOM, użyj <xref:System.Xml.XmlNode.RemoveAll%2A> metody w celu usunięcia wszystkich elementów podrzędnych i atrybutów, jeśli ma zastosowanie, bieżącego węzła.  
  
 Jeśli pracujesz z programem <xref:System.Xml.XmlNamedNodeMap>, możesz usunąć węzeł przy użyciu <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metody.  
  
 Aby usunąć atrybuty, zobacz [usuwanie atrybutów z węzła elementu w modelu dom](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Zobacz też

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
