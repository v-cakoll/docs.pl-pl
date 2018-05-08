---
title: Usuwanie zawartości węzła w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4acbdb53b20c10362385b468c2eb13ab9b17eef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="removing-node-content-in-the-dom"></a>Usuwanie zawartości węzła w modelu DOM
Dla typów węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData>, które są <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, i <xref:System.Xml.XmlSignificantWhitespace> typy węzłów, można usunąć znaki przy użyciu <xref:System.Xml.XmlCharacterData.DeleteData%2A> metodę, która usuwa zakres znaki z węzła. Jeśli chcesz całkowicie usunąć zawartości, należy usunąć węzeł z zawartością. Jeśli chcesz zachować węzeł, ale zawartość jest nieprawidłowa, następnie zmodyfikować zawartość. Aby uzyskać informacje na temat modyfikowania zawartości węzła, zobacz [modyfikowanie węzłów, zawartość i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
