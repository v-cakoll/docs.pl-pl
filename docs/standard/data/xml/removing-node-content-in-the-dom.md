---
title: Usuwanie zawartości węzła z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: 02737c5b680321392d93d785b757c58f2b8da9ee
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288657"
---
# <a name="removing-node-content-in-the-dom"></a>Usuwanie zawartości węzła z modelu DOM
W przypadku typów węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData> , które są <xref:System.Xml.XmlComment> <xref:System.Xml.XmlText> typami węzłów,, <xref:System.Xml.XmlCDataSection> , <xref:System.Xml.XmlWhitespace> i, można <xref:System.Xml.XmlSignificantWhitespace> usunąć znaki przy użyciu <xref:System.Xml.XmlCharacterData.DeleteData%2A> metody, która usuwa zakres znaków z węzła. Jeśli chcesz całkowicie usunąć zawartość, Usuń węzeł, który zawiera zawartość. Jeśli chcesz zachować węzeł, ale zawartość jest niepoprawna, zmodyfikuj zawartość. Aby uzyskać informacje na temat modyfikowania zawartości węzła, zobacz [Modyfikowanie węzłów, zawartości i wartości w dokumencie XML](modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
