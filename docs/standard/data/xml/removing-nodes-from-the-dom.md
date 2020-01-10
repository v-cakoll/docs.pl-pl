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
Aby usunąć węzeł z Document Object Model XML (DOM), użyj metody <xref:System.Xml.XmlNode.RemoveChild%2A> do usunięcia określonego węzła. Po usunięciu węzła Metoda usuwa poddrzewo należące do usuwanego węzła; oznacza to, że jeśli nie jest to węzeł liścia.  
  
 Aby usunąć wiele węzłów z modelu DOM, użyj metody <xref:System.Xml.XmlNode.RemoveAll%2A>, aby usunąć wszystkie elementy podrzędne i atrybuty, jeśli ma zastosowanie, bieżącego węzła.  
  
 W przypadku pracy z <xref:System.Xml.XmlNamedNodeMap>można usunąć węzeł przy użyciu metody <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A>.  
  
 Aby usunąć atrybuty, zobacz [usuwanie atrybutów z węzła elementu w modelu dom](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
