---
title: Element "reDim" nie można zmienić liczbę wymiarów
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: ba3e389e3732d39f16e2c8ae884fae4e935e6ac9
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2018
ms.locfileid: "53778726"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="6dab3-102">Element "reDim" nie można zmienić liczbę wymiarów</span><span class="sxs-lookup"><span data-stu-id="6dab3-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="6dab3-103">Operacja podejmują próbę użycia `ReDim` instrukcję, aby zmienić randze (liczba wymiarów) w tablicy.</span><span class="sxs-lookup"><span data-stu-id="6dab3-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="6dab3-104">`ReDim` można zmienić rozmiar co najmniej jeden wymiar tablicy, która została już formalnie zadeklarowana, ale nie można zmienić, rangę tablicy.</span><span class="sxs-lookup"><span data-stu-id="6dab3-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6dab3-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6dab3-105">To correct this error</span></span>  
  
-   <span data-ttu-id="6dab3-106">Upewnij się, że zamierzasz zmienić rangi tablicy i nie rozmiary jej wymiarów, a jeśli to możliwe, używaj `Dim` do deklarowania nową tablicę z odpowiednią pozycję.</span><span class="sxs-lookup"><span data-stu-id="6dab3-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dab3-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6dab3-107">See Also</span></span>  
 [<span data-ttu-id="6dab3-108">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6dab3-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="6dab3-109">Wymiary tablic w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6dab3-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="6dab3-110">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6dab3-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="6dab3-111">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6dab3-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
