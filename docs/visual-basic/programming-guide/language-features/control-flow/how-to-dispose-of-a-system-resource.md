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
ms.openlocfilehash: c780ee1a174ad044593960bc30a3ee2e1f929390
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583145"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Porady: usuwanie zasobu systemu (Visual Basic)
Można użyć bloku `Using`, aby zagwarantować, że system usuwa zasób, gdy kod opuszcza blok. Jest to przydatne, jeśli używasz zasobu systemowego, który zużywa dużą ilość pamięci, lub że chcesz również użyć innych składników.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Aby usunąć połączenie z bazą danych, gdy kod jest gotowy  
  
1. Upewnij się, że dołączysz odpowiednią [instrukcję Imports (przestrzeń nazw i typ platformy .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla połączenia z bazą danych na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlClient>).  
  
2. Utwórz blok `Using` przy użyciu instrukcji `Using` i `End Using`. W bloku należy umieścić kod, który zajmuje się połączeniem z bazą danych.  
  
3. Zadeklaruj połączenie i Utwórz wystąpienie go jako część instrukcji `Using`.  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     System usuwa zasób niezależnie od tego, jak zamknięto blok, w tym przypadek nieobsłużonego wyjątku.  
  
     Należy zauważyć, że nie można uzyskać dostępu `sqc` spoza bloku `Using`, ponieważ jego zakres jest ograniczony do bloku.  
  
     Tej samej metody można użyć w odniesieniu do zasobu systemowego, takiego jak dojście do pliku lub otoka COM. Blok `Using` jest używany, gdy chcesz, aby pozostawić zasób dostępny dla innych składników po zakończeniu bloku `Using`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.SqlClient.SqlConnection>
- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury decyzji](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Inne struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Zagnieżdżone struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using, instrukcja](../../../../visual-basic/language-reference/statements/using-statement.md)
