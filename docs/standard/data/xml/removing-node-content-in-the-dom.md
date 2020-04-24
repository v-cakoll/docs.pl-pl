---
title: Usuwanie zawartości węzła z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: f5086bdea8ff1f0ee5329f347223ebb4a6bd71da
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710339"
---
# <a name="removing-node-content-in-the-dom"></a>Usuwanie zawartości węzła z modelu DOM
W przypadku typów węzłów, które <xref:System.Xml.XmlCharacterData>dziedziczą z, <xref:System.Xml.XmlComment>które <xref:System.Xml.XmlText>są <xref:System.Xml.XmlCDataSection>typami <xref:System.Xml.XmlWhitespace>węzłów, <xref:System.Xml.XmlSignificantWhitespace> ,, i, można usunąć znaki przy użyciu <xref:System.Xml.XmlCharacterData.DeleteData%2A> metody, która usuwa zakres znaków z węzła. Jeśli chcesz całkowicie usunąć zawartość, Usuń węzeł, który zawiera zawartość. Jeśli chcesz zachować węzeł, ale zawartość jest niepoprawna, zmodyfikuj zawartość. Aby uzyskać informacje na temat modyfikowania zawartości węzła, zobacz [Modyfikowanie węzłów, zawartości i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Zobacz też

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
