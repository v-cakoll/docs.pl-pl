---
title: Element "reDim" można zmienić tylko wymiar najdalej z prawej strony
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 584370f356180fe8b1710a9e145018be7f2d8a0f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592299"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="9ce93-102">Element "reDim" można zmienić tylko wymiar najdalej z prawej strony</span><span class="sxs-lookup"><span data-stu-id="9ce93-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="9ce93-103">A `ReDim` instrukcji podjęto próbę użycia `Preserve` — słowo kluczowe, aby zmienić wymiaru tablicy, która nie jest ostatniego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="9ce93-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="9ce93-104">Korzystając z `Preserve`, zmiany rozmiaru tylko ostatniego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="9ce93-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="9ce93-105">Dla innych wymiarach należy określić ten sam rozmiar jak w przypadku istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="9ce93-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9ce93-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9ce93-106">To correct this error</span></span>  
  
- <span data-ttu-id="9ce93-107">Usuń `Preserve` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9ce93-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce93-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ce93-108">See also</span></span>

- [<span data-ttu-id="9ce93-109">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ce93-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="9ce93-110">Wymiary tablic w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ce93-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="9ce93-111">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9ce93-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="9ce93-112">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9ce93-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
