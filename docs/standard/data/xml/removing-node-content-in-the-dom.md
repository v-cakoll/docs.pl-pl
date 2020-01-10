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
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="793d4-102">Usuwanie zawartości węzła z modelu DOM</span><span class="sxs-lookup"><span data-stu-id="793d4-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="793d4-103">W przypadku typów węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData>, które są typami węzłów <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>i <xref:System.Xml.XmlSignificantWhitespace>, można usunąć znaki przy użyciu metody <xref:System.Xml.XmlCharacterData.DeleteData%2A>, która usuwa zakres znaków z węzła.</span><span class="sxs-lookup"><span data-stu-id="793d4-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="793d4-104">Jeśli chcesz całkowicie usunąć zawartość, Usuń węzeł, który zawiera zawartość.</span><span class="sxs-lookup"><span data-stu-id="793d4-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="793d4-105">Jeśli chcesz zachować węzeł, ale zawartość jest niepoprawna, zmodyfikuj zawartość.</span><span class="sxs-lookup"><span data-stu-id="793d4-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="793d4-106">Aby uzyskać informacje na temat modyfikowania zawartości węzła, zobacz [Modyfikowanie węzłów, zawartości i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="793d4-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793d4-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="793d4-107">See also</span></span>

- [<span data-ttu-id="793d4-108">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="793d4-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
