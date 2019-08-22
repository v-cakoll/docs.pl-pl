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
# <a name="redim-cannot-change-the-number-of-dimensions"></a>Element "ReDim" nie może zmienić liczby wymiarów
Operacja próbuje użyć `ReDim` instrukcji, aby zmienić rangę (liczbę wymiarów) tablicy. `ReDim`można zmienić rozmiar co najmniej jednego wymiaru tablicy, która została już formalnie zadeklarowana, ale nie może zmienić rangi tablicy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że zamierzasz zmienić rangę tablicy, a nie rozmiary jej wymiarów, a jeśli to możliwe, użyj `Dim` , aby zadeklarować nową tablicę z odpowiednią rangą.  
  
## <a name="see-also"></a>Zobacz także

- [Tablice w Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Wymiary tablicy w Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim, instrukcja](../../visual-basic/language-reference/statements/redim-statement.md)
- [Dim, instrukcja](../../visual-basic/language-reference/statements/dim-statement.md)
