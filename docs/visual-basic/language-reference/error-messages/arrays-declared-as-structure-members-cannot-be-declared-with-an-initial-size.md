---
title: "Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords: BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 983154a144a79991c86db5056ad0e0e563a3ba73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Porady: deklarowanie struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
