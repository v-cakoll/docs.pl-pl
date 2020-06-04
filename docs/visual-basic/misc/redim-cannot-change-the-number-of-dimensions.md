---
title: Element "ReDim" nie może zmienić liczby wymiarów
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: b2404927c2faf30d1d058d2163fd5d67e1a52e1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358170"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a>Element "ReDim" nie może zmienić liczby wymiarów
Operacja próbuje użyć instrukcji, `ReDim` Aby zmienić rangę (liczbę wymiarów) tablicy. `ReDim`można zmienić rozmiar co najmniej jednego wymiaru tablicy, która została już formalnie zadeklarowana, ale nie może zmienić rangi tablicy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że zamierzasz zmienić rangę tablicy, a nie rozmiary jej wymiarów, a jeśli to możliwe, użyj, `Dim` Aby zadeklarować nową tablicę z odpowiednią rangą.  
  
## <a name="see-also"></a>Zobacz też

- [Tablice w Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Wymiary tablicy w Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim, instrukcja](../language-reference/statements/redim-statement.md)
- [Dim, instrukcja](../language-reference/statements/dim-statement.md)
