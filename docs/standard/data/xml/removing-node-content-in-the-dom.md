---
title: "Usuwanie zawartości węzła w modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76be90829a414b091d3b311b96bf9bab9a2b56ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="removing-node-content-in-the-dom"></a>Usuwanie zawartości węzła w modelu DOM
Dla typów węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData>, które są <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, i <xref:System.Xml.XmlSignificantWhitespace> typy węzłów, można usunąć znaki przy użyciu <xref:System.Xml.XmlCharacterData.DeleteData%2A> metodę, która usuwa zakres znaki z węzła. Jeśli chcesz całkowicie usunąć zawartości, należy usunąć węzeł z zawartością. Jeśli chcesz zachować węzeł, ale zawartość jest nieprawidłowa, następnie zmodyfikować zawartość. Aby uzyskać informacje na temat modyfikowania zawartości węzła, zobacz [modyfikowanie węzłów, zawartość i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
