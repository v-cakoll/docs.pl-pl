---
title: Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: de9d77aa9ea853b6f044e91878044115588ca77c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701254"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym
Tablica w strukturze jest zadeklarowana z rozmiarem początkowym. Nie można zainicjować żadnego elementu struktury i deklarowania rozmiaru tablicy jest jedną z form inicjalizacji.  
  
 **Identyfikator błędu:** BC31043  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zdefiniuj tablicę w strukturze jako dynamiczną (bez początkowego rozmiaru).  
  
2. Jeśli potrzebujesz pewnego rozmiaru tablicy, możesz zmienić wymiar tablicy dynamicznej z [instrukcją ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) , gdy kod jest uruchomiony. Ilustruje to poniższy przykład.  
  
    ```vb  
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
