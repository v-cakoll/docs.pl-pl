---
title: Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 5d58b531b670715716e849cd37227bc899195df6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935372"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym
Tablica w strukturze jest zadeklarowana z rozmiarem początkowym. Nie można zainicjować dowolnego elementu struktury i deklarowanie rozmiar tablicy jest jeden formularz inicjowania.  
  
 **Identyfikator błędu:** BC31043  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zdefiniować tablicę w strukturze jako dynamiczna (nie rozmiar początkowy).  
  
2. Jeśli potrzebujesz rozmiar tablicy, możesz redimension tablic dynamicznych z [instrukcji ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) gdy kod jest uruchomiony. Ilustruje to poniższy przykład.  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Instrukcje: deklarowanie struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
