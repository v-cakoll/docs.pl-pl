---
title: "Skopiuj istniejących węzłów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c026d9f825375d74d53d5cc46969ff0f713bab1c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="741f3-102">Skopiuj istniejących węzłów</span><span class="sxs-lookup"><span data-stu-id="741f3-102">Copy Existing Nodes</span></span>
<span data-ttu-id="741f3-103">Istnieje wiele metod i właściwości w XML modelu DOM (Document Object) można wybrać węzła, takiej jak **SelectSingleNode**, **ChildNodes [int i]**, **atrybutów [int i]**.</span><span class="sxs-lookup"><span data-stu-id="741f3-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="741f3-104">Po wybraniu węzła można wstawić je do drzewa przy użyciu jednej z metod wstawiania, które działają dla tego typu określonego węzła.</span><span class="sxs-lookup"><span data-stu-id="741f3-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="741f3-105">Tylko ograniczenie do wstawiania węzeł w drzewie jest czy dokument nadal należy poprawnie sformułowanym po wstawieniu węzła.</span><span class="sxs-lookup"><span data-stu-id="741f3-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="741f3-106">Po wstawieniu istniejący węzeł w drzewie DOM, jest usunięte z oryginalnej pozycji i dodane do miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="741f3-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="741f3-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="741f3-107">See Also</span></span>  
 [<span data-ttu-id="741f3-108">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="741f3-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
