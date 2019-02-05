---
title: Element "reDim" można zmienić tylko wymiar najdalej z prawej strony
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: d20d0374cd5183b6216d1c6e5b138256cf0a4f17
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738958"
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
