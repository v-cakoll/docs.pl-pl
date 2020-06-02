---
title: Kopiowanie istniejących węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 392490d04ff713529d501e199ac2496ff37de1a0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289216"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="3a3f3-102">Kopiowanie istniejących węzłów</span><span class="sxs-lookup"><span data-stu-id="3a3f3-102">Copy Existing Nodes</span></span>
<span data-ttu-id="3a3f3-103">Istnieje wiele metod i właściwości w Document Object Model XML (DOM), których można użyć do wybrania węzła, takiego jak **SelectSingleNode**, **ChildNodes [int i]**, **Attributes [int i]**.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="3a3f3-104">Po wybraniu węzła można wstawić go do drzewa przy użyciu jednej z metod INSERT, które działają dla danego typu węzła.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="3a3f3-105">Jedynym ograniczeniem do wstawiania węzła do drzewa jest to, że dokument nadal musi być poprawnie sformułowany po wstawieniu węzła.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="3a3f3-106">Gdy istniejący węzeł zostanie wstawiony do drzewa DOM, zostaje usunięty z jego pierwotnej pozycji i dodany do jego pozycji docelowej.</span><span class="sxs-lookup"><span data-stu-id="3a3f3-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a3f3-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a3f3-107">See also</span></span>

- [<span data-ttu-id="3a3f3-108">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="3a3f3-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
