---
title: '&#39;ReDim&#39; nie można zmienić liczby wymiarów'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: bfd4096141833b85a2126340ef549e1e1d1f8e3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39redim39-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="938a3-102">&#39;ReDim&#39; nie można zmienić liczby wymiarów</span><span class="sxs-lookup"><span data-stu-id="938a3-102">&#39;ReDim&#39; cannot change the number of dimensions</span></span>
<span data-ttu-id="938a3-103">Operacja próbuje użyć `ReDim` instrukcji, aby zmienić rangę tablicy (liczba wymiarów).</span><span class="sxs-lookup"><span data-stu-id="938a3-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="938a3-104">`ReDim` można zmienić rozmiar co najmniej jeden wymiar tablicy, która została już formalnie zadeklarowana, ale nie można zmienić rangę tablicy.</span><span class="sxs-lookup"><span data-stu-id="938a3-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="938a3-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="938a3-105">To correct this error</span></span>  
  
-   <span data-ttu-id="938a3-106">Upewnij się, że chcesz zmienić rangę tablicy i nie rozmiary jej wymiarów i, jeśli to możliwe, użyj `Dim` Aby zadeklarować nowej tablicy z odpowiednią pozycję.</span><span class="sxs-lookup"><span data-stu-id="938a3-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938a3-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="938a3-107">See Also</span></span>  
 [<span data-ttu-id="938a3-108">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="938a3-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="938a3-109">Wymiary tablicy w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="938a3-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="938a3-110">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="938a3-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="938a3-111">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="938a3-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
