---
title: Element "ReDim" nie może zmienić liczby wymiarów
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: fb60c93f988ca40305f13cca07f55a70bd779081
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664397"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="aa390-102">Element "ReDim" nie może zmienić liczby wymiarów</span><span class="sxs-lookup"><span data-stu-id="aa390-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="aa390-103">Operacja próbuje użyć `ReDim` instrukcji, aby zmienić rangę (liczbę wymiarów) tablicy.</span><span class="sxs-lookup"><span data-stu-id="aa390-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="aa390-104">`ReDim`można zmienić rozmiar co najmniej jednego wymiaru tablicy, która została już formalnie zadeklarowana, ale nie może zmienić rangi tablicy.</span><span class="sxs-lookup"><span data-stu-id="aa390-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aa390-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="aa390-105">To correct this error</span></span>  
  
- <span data-ttu-id="aa390-106">Upewnij się, że zamierzasz zmienić rangę tablicy, a nie rozmiary jej wymiarów, a jeśli to możliwe, użyj `Dim` , aby zadeklarować nową tablicę z odpowiednią rangą.</span><span class="sxs-lookup"><span data-stu-id="aa390-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa390-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa390-107">See also</span></span>

- [<span data-ttu-id="aa390-108">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa390-108">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="aa390-109">Wymiary tablicy w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa390-109">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="aa390-110">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="aa390-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="aa390-111">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="aa390-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
