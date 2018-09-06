---
title: Usuwanie węzłów za pomocą modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be592466627e6ee7b23c608e0defe786548907ad
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878362"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="1068c-102">Usuwanie węzłów za pomocą modelu DOM</span><span class="sxs-lookup"><span data-stu-id="1068c-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="1068c-103">Aby usunąć węzeł z XML Document Object Model (DOM), należy użyć <xref:System.Xml.XmlNode.RemoveChild%2A> metodę, aby usunąć określonego węzła.</span><span class="sxs-lookup"><span data-stu-id="1068c-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="1068c-104">Po usunięciu węzła metoda usuwa poddrzewo należących do węzła usunięte; oznacza to jeśli nie jest węzłem liścia.</span><span class="sxs-lookup"><span data-stu-id="1068c-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="1068c-105">Aby usunąć wiele węzłów z modelu DOM, należy użyć <xref:System.Xml.XmlNode.RemoveAll%2A> metodę, aby usunąć wszystkie elementy podrzędne i atrybuty, jeśli ma to zastosowanie, bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="1068c-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="1068c-106">Jeśli pracujesz z <xref:System.Xml.XmlNamedNodeMap>, możesz usunąć za pomocą węzła <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1068c-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="1068c-107">Aby usunąć atrybuty, zobacz [usuwanie atrybutów z węzła elementu w modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="1068c-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1068c-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1068c-108">See also</span></span>

- [<span data-ttu-id="1068c-109">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="1068c-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
