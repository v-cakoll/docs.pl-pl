---
title: Element "reDim" nie można zmienić liczbę wymiarów
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: b6bb78c3f1d7224e6e4b432fd3aef4589f2f1cd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964895"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="498d1-102">Element "reDim" nie można zmienić liczbę wymiarów</span><span class="sxs-lookup"><span data-stu-id="498d1-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="498d1-103">Operacja podejmują próbę użycia `ReDim` instrukcję, aby zmienić randze (liczba wymiarów) w tablicy.</span><span class="sxs-lookup"><span data-stu-id="498d1-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="498d1-104">`ReDim` można zmienić rozmiar co najmniej jeden wymiar tablicy, która została już formalnie zadeklarowana, ale nie można zmienić, rangę tablicy.</span><span class="sxs-lookup"><span data-stu-id="498d1-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="498d1-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="498d1-105">To correct this error</span></span>  
  
- <span data-ttu-id="498d1-106">Upewnij się, że zamierzasz zmienić rangi tablicy i nie rozmiary jej wymiarów, a jeśli to możliwe, używaj `Dim` do deklarowania nową tablicę z odpowiednią pozycję.</span><span class="sxs-lookup"><span data-stu-id="498d1-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="498d1-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="498d1-107">See also</span></span>

- [<span data-ttu-id="498d1-108">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="498d1-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="498d1-109">Wymiary tablic w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="498d1-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="498d1-110">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="498d1-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="498d1-111">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="498d1-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
