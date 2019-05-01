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
# <a name="redim-cannot-change-the-number-of-dimensions"></a>Element "reDim" nie można zmienić liczbę wymiarów
Operacja podejmują próbę użycia `ReDim` instrukcję, aby zmienić randze (liczba wymiarów) w tablicy. `ReDim` można zmienić rozmiar co najmniej jeden wymiar tablicy, która została już formalnie zadeklarowana, ale nie można zmienić, rangę tablicy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że zamierzasz zmienić rangi tablicy i nie rozmiary jej wymiarów, a jeśli to możliwe, używaj `Dim` do deklarowania nową tablicę z odpowiednią pozycję.  
  
## <a name="see-also"></a>Zobacz także

- [Tablice w Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [Wymiary tablic w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim, instrukcja](../../visual-basic/language-reference/statements/redim-statement.md)
- [Dim, instrukcja](../../visual-basic/language-reference/statements/dim-statement.md)
