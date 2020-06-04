---
title: Element "ReDim" może zmienić tylko najwyższy wymiar
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 8e42e0df7b97fb96f468ce37dd4cfc52fad8c596
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358299"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="6b84e-102">Element "ReDim" może zmienić tylko najwyższy wymiar</span><span class="sxs-lookup"><span data-stu-id="6b84e-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="6b84e-103">`ReDim`Instrukcja próbowała użyć `Preserve` słowa kluczowego, aby zmienić wymiar tablicy, która nie jest ostatnim wymiarem.</span><span class="sxs-lookup"><span data-stu-id="6b84e-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="6b84e-104">W przypadku używania `Preserve` , można zmienić rozmiar tylko ostatniego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b84e-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="6b84e-105">Dla wszystkich innych wymiarów należy określić ten sam rozmiar jak dla istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b84e-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b84e-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6b84e-106">To correct this error</span></span>  
  
- <span data-ttu-id="6b84e-107">Usuń `Preserve` słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6b84e-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b84e-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b84e-108">See also</span></span>

- [<span data-ttu-id="6b84e-109">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b84e-109">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="6b84e-110">Wymiary tablicy w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b84e-110">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="6b84e-111">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b84e-111">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="6b84e-112">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b84e-112">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
