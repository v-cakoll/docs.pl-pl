---
title: 'Porady: usuwanie zasobu systemu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: cbb66934833da2bd6f0b797944dbb9c4df267cfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Porady: usuwanie zasobu systemu (Visual Basic)
Można użyć `Using` bloku, aby zagwarantować, że system usuwa zasobu, gdy kod jest kończona bloku. Jest to przydatne, jeśli używasz zasób systemowy, który zużywa duże ilości pamięci lub innych składników również chcesz użyć.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Po zakończeniu kodu z nim zlikwidować połączenia z bazą danych  
  
1.  Upewnij się, że możesz dołączyć odpowiednie [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla połączenia z bazą danych na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlClient>).  
  
2.  Utwórz `Using` zablokować z `Using` i `End Using` instrukcje. Wewnątrz bloku umieść kod, który zajmuje się połączenie z bazą danych.  
  
3.  Deklarowanie połączenia i Utwórz wystąpienie go jako część `Using` instrukcji.  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     Usuwa systemu zasobów, niezależnie od tego, jak zakończyć blok, w tym przypadku nieobsługiwany wyjątek.  
  
     Należy pamiętać, że nie masz dostępu do `sqc` z poza `Using` zablokować, ponieważ jej zakres ogranicza się do bloku.  
  
     Ten sam sposób można użyć w zasobach systemu, np. dojście do pliku lub otoki COM. Możesz użyć `Using` zablokować, jeśli chcesz mieć pewność opuścić zasobów dostępne dla innych składników po zostały zakończone `Using` bloku.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.SqlClient.SqlConnection>  
 [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Struktury decyzji](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Inne struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [Zagnieżdżone struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Using, instrukcja](../../../../visual-basic/language-reference/statements/using-statement.md)
