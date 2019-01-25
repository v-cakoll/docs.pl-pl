---
title: Element "reDim" można zmienić tylko wymiar najdalej z prawej strony
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 97eedabd550be397f9cdffc5fd864d7a88c30c31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714207"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>Element "reDim" można zmienić tylko wymiar najdalej z prawej strony
A `ReDim` instrukcji podjęto próbę użycia `Preserve` — słowo kluczowe, aby zmienić wymiaru tablicy, która nie jest ostatniego wymiaru. Korzystając z `Preserve`, zmiany rozmiaru tylko ostatniego wymiaru tablicy. Dla innych wymiarach należy określić ten sam rozmiar jak w przypadku istniejącej tablicy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń `Preserve` — słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz także
- [Tablice w Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [Wymiary tablic w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim, instrukcja](../../visual-basic/language-reference/statements/redim-statement.md)
- [Dim, instrukcja](../../visual-basic/language-reference/statements/dim-statement.md)
- [Zachowaj — usuwanie](https://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
