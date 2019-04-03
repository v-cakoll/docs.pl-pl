---
title: 'Instrukcje: Usuwanie zasobu systemu (Visual Basic)'
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
ms.openlocfilehash: 2a399b92c66c8a88d10d661ff41aef58a82bbc2a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829918"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Instrukcje: Usuwanie zasobu systemu (Visual Basic)
Możesz użyć `Using` bloku, aby zagwarantować, że system Usuwa zasób po kodzie zamyka blok. Jest to przydatne, jeśli używasz zasób systemowy, który używa dużej ilości pamięci, lub też używać innych składników.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Aby usunąć połączenie z bazą danych po zakończeniu swój kod z nim  
  
1.  Upewnij się, możesz dołączyć odpowiednie [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla połączenia z bazą danych na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlClient>).  
  
2.  Tworzenie `Using` blokowania z `Using` i `End Using` instrukcji. Wewnątrz bloku umieść kod, który zajmuje się połączenie z bazą danych.  
  
3.  Deklarowanie połączenie i utworzyć jej wystąpienie w ramach `Using` instrukcji.  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     Usuwa system zasobów, niezależnie od tego, jak zamknąć blok, w tym przypadku Wystąpił nieobsługiwany wyjątek.  
  
     Należy zauważyć, że nie masz dostępu do `sqc` z poza `Using` zablokować, ponieważ jej zakres jest ograniczony do bloku.  
  
     Można użyć tej samej techniki, w zasobach systemu, takie jak dojście do pliku lub otoka COM. Możesz użyć `Using` zablokować, jeśli chcesz mieć pewność, że opuścić zasób jest dostępny dla innych składników po zostały zakończone `Using` bloku.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.SqlClient.SqlConnection>
- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury decyzji](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Inne struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Zagnieżdżone struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using, instrukcja](../../../../visual-basic/language-reference/statements/using-statement.md)
