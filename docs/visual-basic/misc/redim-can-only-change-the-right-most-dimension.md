---
title: Element "ReDim" może zmienić tylko najwyższy wymiar
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: f38bcb99b682ace497859b67fe3bb829bbc80c4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664404"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="d2f56-102">Element "ReDim" może zmienić tylko najwyższy wymiar</span><span class="sxs-lookup"><span data-stu-id="d2f56-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="d2f56-103">Instrukcja próbowała użyć słowa kluczowego, aby zmienić wymiar tablicy, która nie jest ostatnim wymiarem. `Preserve` `ReDim`</span><span class="sxs-lookup"><span data-stu-id="d2f56-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="d2f56-104">W przypadku `Preserve`używania, można zmienić rozmiar tylko ostatniego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="d2f56-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="d2f56-105">Dla wszystkich innych wymiarów należy określić ten sam rozmiar jak dla istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="d2f56-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d2f56-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d2f56-106">To correct this error</span></span>  
  
- <span data-ttu-id="d2f56-107">`Preserve` Usuń słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d2f56-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f56-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2f56-108">See also</span></span>

- [<span data-ttu-id="d2f56-109">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2f56-109">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="d2f56-110">Wymiary tablicy w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2f56-110">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="d2f56-111">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d2f56-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="d2f56-112">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d2f56-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
