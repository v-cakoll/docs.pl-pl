---
title: Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 0a7424e5dbfadd78c4071ba5b76086b7f6c9b94a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585856"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym
Tablicy w strukturze jest zadeklarowana z rozmiarem początkowym. Nie można zainicjować dowolny element struktury i deklarowanie rozmiaru tablicy jest jeden formularz inicjowania.  
  
 **Identyfikator błędu:** BC31043  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zdefiniuj tablicy w strukturze jako dynamiczny (nie początkowy rozmiar).  
  
2.  Jeśli potrzebujesz rozmiar tablicy można zmiany jego wymiarów tablicy dynamicznej z [instrukcji ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) gdy kod jest uruchomiony. Ilustruje to poniższy przykład.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Instrukcje: deklarowanie struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
