---
title: Element "ReDim" może zmienić tylko najwyższy wymiar
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 8e42e0df7b97fb96f468ce37dd4cfc52fad8c596
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358299"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>Element "ReDim" może zmienić tylko najwyższy wymiar
`ReDim`Instrukcja próbowała użyć `Preserve` słowa kluczowego, aby zmienić wymiar tablicy, która nie jest ostatnim wymiarem. W przypadku używania `Preserve` , można zmienić rozmiar tylko ostatniego wymiaru tablicy. Dla wszystkich innych wymiarów należy określić ten sam rozmiar jak dla istniejącej tablicy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń `Preserve` słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz też

- [Tablice w Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Wymiary tablicy w Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim, instrukcja](../language-reference/statements/redim-statement.md)
- [Dim, instrukcja](../language-reference/statements/dim-statement.md)
