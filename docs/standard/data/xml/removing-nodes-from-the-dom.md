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
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="4746f-102">Usuwanie węzłów z modelu DOM</span><span class="sxs-lookup"><span data-stu-id="4746f-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="4746f-103">Aby usunąć węzeł z Document Object Model XML (DOM), użyj metody <xref:System.Xml.XmlNode.RemoveChild%2A> do usunięcia określonego węzła.</span><span class="sxs-lookup"><span data-stu-id="4746f-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="4746f-104">Po usunięciu węzła Metoda usuwa poddrzewo należące do usuwanego węzła; oznacza to, że jeśli nie jest to węzeł liścia.</span><span class="sxs-lookup"><span data-stu-id="4746f-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="4746f-105">Aby usunąć wiele węzłów z modelu DOM, użyj metody <xref:System.Xml.XmlNode.RemoveAll%2A>, aby usunąć wszystkie elementy podrzędne i atrybuty, jeśli ma zastosowanie, bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="4746f-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="4746f-106">W przypadku pracy z <xref:System.Xml.XmlNamedNodeMap>można usunąć węzeł przy użyciu metody <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="4746f-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="4746f-107">Aby usunąć atrybuty, zobacz [usuwanie atrybutów z węzła elementu w modelu dom](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="4746f-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4746f-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4746f-108">See also</span></span>

- [<span data-ttu-id="4746f-109">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="4746f-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
