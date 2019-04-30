---
title: Usuwanie zawartości węzła z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 737766586ee920a87c25dd42896bdfb14ae69d98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698710"
---
# <a name="removing-node-content-in-the-dom"></a>Usuwanie zawartości węzła z modelu DOM
Dla typów węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData>, które są <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, i <xref:System.Xml.XmlSignificantWhitespace> typy węzłów można usunąć znaki przy użyciu <xref:System.Xml.XmlCharacterData.DeleteData%2A> metody, która usuwa zakres znaki z węzła. Jeśli chcesz całkowicie usunąć zawartości, należy usunąć węzeł, który zawiera zawartość. Jeśli chcesz zachować węzeł, ale zawartość jest niepoprawny, następnie zmodyfikować zawartość. Aby uzyskać informacji na temat modyfikowania zawartości węzła, zobacz [modyfikowanie węzłów, zawartości i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
