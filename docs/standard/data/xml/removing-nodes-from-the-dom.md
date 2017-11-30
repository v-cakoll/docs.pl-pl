---
title: "Usuwanie węzłów z modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0885d53e737153448fabfd394d49bfdc793e0599
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="removing-nodes-from-the-dom"></a>Usuwanie węzłów z modelu DOM
Aby usunąć węzeł z XML modelu DOM (Document Object), należy użyć <xref:System.Xml.XmlNode.RemoveChild%2A> sposób usunięcia określonego węzła. Po usunięciu węzła metoda usuwa poddrzewo należących do tego węzła zostaną usunięte; oznacza to jeśli nie jest węzłem liścia.  
  
 Aby usunąć wiele węzłów w modelu DOM, użyj <xref:System.Xml.XmlNode.RemoveAll%2A> metodę, aby usunąć wszystkie elementy podrzędne i atrybuty, jeśli ma to zastosowanie, z bieżącego węzła.  
  
 Jeśli pracujesz z <xref:System.Xml.XmlNamedNodeMap>, można usunąć węzła przy użyciu <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metody.  
  
 Aby usunąć atrybuty, zobacz [usuwanie atrybutów z węzłem elementu w modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
