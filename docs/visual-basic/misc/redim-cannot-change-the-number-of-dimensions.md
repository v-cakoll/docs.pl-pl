---
title: Element "reDim" nie można zmienić liczbę wymiarów
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 80546b427afdafaf6e9fcea493d58cf1019e79e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638460"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a>Element "reDim" nie można zmienić liczbę wymiarów
Operacja podejmują próbę użycia `ReDim` instrukcję, aby zmienić randze (liczba wymiarów) w tablicy. `ReDim` można zmienić rozmiar co najmniej jeden wymiar tablicy, która została już formalnie zadeklarowana, ale nie można zmienić, rangę tablicy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że zamierzasz zmienić rangi tablicy i nie rozmiary jej wymiarów, a jeśli to możliwe, używaj `Dim` do deklarowania nową tablicę z odpowiednią pozycję.  
  
## <a name="see-also"></a>Zobacz także
- [Tablice w Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [Wymiary tablic w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim, instrukcja](../../visual-basic/language-reference/statements/redim-statement.md)
- [Dim, instrukcja](../../visual-basic/language-reference/statements/dim-statement.md)
