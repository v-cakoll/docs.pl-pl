---
title: 'Porady: usuwanie zasobu systemu'
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
ms.openlocfilehash: dd15c6746628f45b072d46eea40051ed9afb7921
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403501"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Porady: usuwanie zasobu systemu (Visual Basic)
Można użyć `Using` bloku, aby zagwarantować, że system usuwa zasób, gdy kod opuszcza blok. Jest to przydatne, jeśli używasz zasobu systemowego, który zużywa dużą ilość pamięci, lub że chcesz również użyć innych składników.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Aby usunąć połączenie z bazą danych, gdy kod jest gotowy  
  
1. Upewnij się, że dołączysz odpowiednią [instrukcję Imports (przestrzeń nazw i typ platformy .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) dla połączenia z bazą danych na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlClient> ).  
  
2. Utwórz `Using` blok z `Using` `End Using` instrukcjami i. W bloku należy umieścić kod, który zajmuje się połączeniem z bazą danych.  
  
3. Zadeklaruj połączenie i Utwórz wystąpienie go jako część `Using` instrukcji.  
  
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
  
     Należy zauważyć, że nie można uzyskać dostępu `sqc` spoza `Using` bloku, ponieważ jego zakres jest ograniczony do bloku.  
  
     Tej samej metody można użyć w odniesieniu do zasobu systemowego, takiego jak dojście do pliku lub otoka COM. Możesz użyć `Using` bloku, gdy chcesz, aby pozostawić zasób dostępny dla innych składników po zakończeniu `Using` bloku.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.SqlClient.SqlConnection>
- [Przepływ sterowania](index.md)
- [Struktury decyzji](decision-structures.md)
- [Struktury pętli](loop-structures.md)
- [Inne struktury sterujące](other-control-structures.md)
- [Zagnieżdżone struktury sterujące](nested-control-structures.md)
- [Using, instrukcja](../../../language-reference/statements/using-statement.md)
