---
title: Kopiowanie istniejących węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eda5c9b4851b29c0a76e45414d7c47ba52252455
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252873"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="2de11-102">Kopiowanie istniejących węzłów</span><span class="sxs-lookup"><span data-stu-id="2de11-102">Copy Existing Nodes</span></span>
<span data-ttu-id="2de11-103">Istnieje wiele metod i właściwości w XML modelu DOM (Document Object) można użyć, wybierz węzeł, takich jak **SelectSingleNode**, **ChildNodes [int i]**, **atrybutów [int i]**.</span><span class="sxs-lookup"><span data-stu-id="2de11-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="2de11-104">Po wybraniu węzła można wstawić jej do drzewa za pomocą jednej z metod wstawiania, współpracujących dla tego typu określonego węzła.</span><span class="sxs-lookup"><span data-stu-id="2de11-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="2de11-105">Jedynym ograniczeniem do wstawiania węzeł w drzewie jest, że dokument musi być poprawnie sformułowany po wstawieniu węzła.</span><span class="sxs-lookup"><span data-stu-id="2de11-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="2de11-106">Gdy istniejący węzeł jest wstawiany do drzewa DOM, jest usuwane z jego pierwotnej pozycji i dodane do miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="2de11-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de11-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2de11-107">See also</span></span>

- [<span data-ttu-id="2de11-108">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="2de11-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
