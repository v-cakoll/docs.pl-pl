---
title: Element "reDim" można zmienić tylko wymiar najdalej z prawej strony
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 86d639e70e85b19a91f89fa4e0cab330af07dccf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943367"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="cff2c-102">Element "reDim" można zmienić tylko wymiar najdalej z prawej strony</span><span class="sxs-lookup"><span data-stu-id="cff2c-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="cff2c-103">A `ReDim` instrukcji podjęto próbę użycia `Preserve` — słowo kluczowe, aby zmienić wymiaru tablicy, która nie jest ostatniego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="cff2c-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="cff2c-104">Korzystając z `Preserve`, zmiany rozmiaru tylko ostatniego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="cff2c-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="cff2c-105">Dla innych wymiarach należy określić ten sam rozmiar jak w przypadku istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="cff2c-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cff2c-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cff2c-106">To correct this error</span></span>  
  
- <span data-ttu-id="cff2c-107">Usuń `Preserve` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="cff2c-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff2c-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cff2c-108">See also</span></span>

- [<span data-ttu-id="cff2c-109">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cff2c-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="cff2c-110">Wymiary tablic w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cff2c-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="cff2c-111">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cff2c-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="cff2c-112">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cff2c-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
