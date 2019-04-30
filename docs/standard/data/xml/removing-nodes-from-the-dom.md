---
title: Usuwanie węzłów z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be592466627e6ee7b23c608e0defe786548907ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698671"
---
# <a name="removing-nodes-from-the-dom"></a>Usuwanie węzłów z modelu DOM
Aby usunąć węzeł z XML Document Object Model (DOM), należy użyć <xref:System.Xml.XmlNode.RemoveChild%2A> metodę, aby usunąć określonego węzła. Po usunięciu węzła metoda usuwa poddrzewo należących do węzła usunięte; oznacza to jeśli nie jest węzłem liścia.  
  
 Aby usunąć wiele węzłów z modelu DOM, należy użyć <xref:System.Xml.XmlNode.RemoveAll%2A> metodę, aby usunąć wszystkie elementy podrzędne i atrybuty, jeśli ma to zastosowanie, bieżącego węzła.  
  
 Jeśli pracujesz z <xref:System.Xml.XmlNamedNodeMap>, możesz usunąć za pomocą węzła <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metody.  
  
 Aby usunąć atrybuty, zobacz [usuwanie atrybutów z węzła elementu w modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
