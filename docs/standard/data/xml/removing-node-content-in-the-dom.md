---
title: Usuwanie zawartości węzła w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 737766586ee920a87c25dd42896bdfb14ae69d98
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44136774"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="f2565-102">Usuwanie zawartości węzła w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="f2565-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="f2565-103">Dla typów węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData>, które są <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, i <xref:System.Xml.XmlSignificantWhitespace> typy węzłów można usunąć znaki przy użyciu <xref:System.Xml.XmlCharacterData.DeleteData%2A> metody, która usuwa zakres znaki z węzła.</span><span class="sxs-lookup"><span data-stu-id="f2565-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="f2565-104">Jeśli chcesz całkowicie usunąć zawartości, należy usunąć węzeł, który zawiera zawartość.</span><span class="sxs-lookup"><span data-stu-id="f2565-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="f2565-105">Jeśli chcesz zachować węzeł, ale zawartość jest niepoprawny, następnie zmodyfikować zawartość.</span><span class="sxs-lookup"><span data-stu-id="f2565-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="f2565-106">Aby uzyskać informacji na temat modyfikowania zawartości węzła, zobacz [modyfikowanie węzłów, zawartości i wartości w dokumencie XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="f2565-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2565-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2565-107">See also</span></span>

- [<span data-ttu-id="f2565-108">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="f2565-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
