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
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="4043d-102">Usuwanie węzłów z modelu DOM</span><span class="sxs-lookup"><span data-stu-id="4043d-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="4043d-103">Aby usunąć węzeł z XML modelu DOM (Document Object), należy użyć <xref:System.Xml.XmlNode.RemoveChild%2A> sposób usunięcia określonego węzła.</span><span class="sxs-lookup"><span data-stu-id="4043d-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="4043d-104">Po usunięciu węzła metoda usuwa poddrzewo należących do tego węzła zostaną usunięte; oznacza to jeśli nie jest węzłem liścia.</span><span class="sxs-lookup"><span data-stu-id="4043d-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="4043d-105">Aby usunąć wiele węzłów w modelu DOM, użyj <xref:System.Xml.XmlNode.RemoveAll%2A> metodę, aby usunąć wszystkie elementy podrzędne i atrybuty, jeśli ma to zastosowanie, z bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="4043d-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="4043d-106">Jeśli pracujesz z <xref:System.Xml.XmlNamedNodeMap>, można usunąć węzła przy użyciu <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4043d-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="4043d-107">Aby usunąć atrybuty, zobacz [usuwanie atrybutów z węzłem elementu w modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="4043d-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4043d-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4043d-108">See Also</span></span>  
 [<span data-ttu-id="4043d-109">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="4043d-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
