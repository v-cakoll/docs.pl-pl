---
title: Kopiowanie istniejących węzłów
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: fb9ccd7b16d00355ba87bb32f5447906feeecd94
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711067"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="5d07d-102">Kopiowanie istniejących węzłów</span><span class="sxs-lookup"><span data-stu-id="5d07d-102">Copy Existing Nodes</span></span>
<span data-ttu-id="5d07d-103">Istnieje wiele metod i właściwości w Document Object Model XML (DOM), których można użyć do wybrania węzła, takiego jak **SelectSingleNode**, **ChildNodes [int i]** , **Attributes [int i]** .</span><span class="sxs-lookup"><span data-stu-id="5d07d-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="5d07d-104">Po wybraniu węzła można wstawić go do drzewa przy użyciu jednej z metod INSERT, które działają dla danego typu węzła.</span><span class="sxs-lookup"><span data-stu-id="5d07d-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="5d07d-105">Jedynym ograniczeniem do wstawiania węzła do drzewa jest to, że dokument nadal musi być poprawnie sformułowany po wstawieniu węzła.</span><span class="sxs-lookup"><span data-stu-id="5d07d-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="5d07d-106">Gdy istniejący węzeł zostanie wstawiony do drzewa DOM, zostaje usunięty z jego pierwotnej pozycji i dodany do jego pozycji docelowej.</span><span class="sxs-lookup"><span data-stu-id="5d07d-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d07d-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d07d-107">See also</span></span>

- [<span data-ttu-id="5d07d-108">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="5d07d-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
