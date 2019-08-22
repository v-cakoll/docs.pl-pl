---
title: Element "ReDim" może zmienić tylko najwyższy wymiar
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: f38bcb99b682ace497859b67fe3bb829bbc80c4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664404"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>Element "ReDim" może zmienić tylko najwyższy wymiar
Instrukcja próbowała użyć słowa kluczowego, aby zmienić wymiar tablicy, która nie jest ostatnim wymiarem. `Preserve` `ReDim` W przypadku `Preserve`używania, można zmienić rozmiar tylko ostatniego wymiaru tablicy. Dla wszystkich innych wymiarów należy określić ten sam rozmiar jak dla istniejącej tablicy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- `Preserve` Usuń słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz także

- [Tablice w Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Wymiary tablicy w Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim, instrukcja](../../visual-basic/language-reference/statements/redim-statement.md)
- [Dim, instrukcja](../../visual-basic/language-reference/statements/dim-statement.md)
