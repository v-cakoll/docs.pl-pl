---
title: Przykład wykonania odroczonego (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 6d1f66cbe246b609f634989625688965dd4e5c93
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351803"
---
# <a name="deferred-execution-example-visual-basic"></a>Przykład wykonania odroczonego (Visual Basic)
W tym temacie pokazano, w jaki sposób odroczone wykonywanie i Ocena z opóźnieniem wpływają na wykonywanie zapytań LINQ to XML.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kolejność wykonywania przy użyciu metody rozszerzenia, która korzysta z odroczonego wykonania. Przykład deklaruje tablicę trzech ciągów. Następnie wykonuje iterację w kolekcji zwróconej przez `ConvertCollectionToUpperCase`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module Module1  
  
    <Extension()>  
    Private Iterator Function ConvertCollectionToUpperCase(  
    ByVal source As IEnumerable(Of String)) _  
    As IEnumerable(Of String)   
        For Each str As String In source  
            Console.WriteLine("ToUpper: source {0}", str)   
            Yield str.ToUpper()  
        Next  
    End Function  
  
    Sub Main()  
        Dim stringArray = New String() {"abc", "def", "ghi"}  
  
        Dim q = From str In stringArray.ConvertCollectionToUpperCase()  
                Select str  
  
        For Each Str As String In q  
            Console.WriteLine("Main: str {0}", Str)   
        Next  
    End Sub  
  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```console  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Należy zauważyć, że podczas iteracji kolekcji zwróconej przez `ConvertCollectionToUpperCase` każdy element jest pobierany z tablicy ciągów źródłowych i konwertowany na wielkie przed pobraniem następnego elementu z tablicy ciągów źródłowych.  
  
 Można zobaczyć, że cała tablica ciągów nie jest konwertowana na wielkie przed każdym elementem w zwróconej kolekcji, w pętli `foreach` w `Main`.  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Wykonanie odroczone (Visual Basic) ](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
