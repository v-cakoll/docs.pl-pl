---
title: Przykład wykonania odroczonego (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 29f118b3e6d49840b94277f17858f1339f2fb08c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838932"
---
# <a name="deferred-execution-example-visual-basic"></a>Przykład wykonania odroczonego (Visual Basic)
W tym temacie przedstawiono sposób odroczonego wykonania i obliczanie z opóźnieniem wpływa na wykonywanie Twojego zapytaniach składnika LINQ to XML.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kolejność wykonywania, korzystając z metody rozszerzenia, która używa odroczonego wykonania. Przykład deklaruje tablicę trzy ciągi. Następnie wykonuje iterację przez zbiorze zwróconym przez `ConvertCollectionToUpperCase`.  
  
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
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Należy zauważyć, że podczas iteracji w kolekcji zwróconej przez `ConvertCollectionToUpperCase`, każdy element jest pobierana z tablicy ciągów źródłowych i przekonwertowane na wielkie litery przed następnego elementu jest pobierana z tablicy ciągów źródła.  
  
 Widać, że całej tablicy ciągów nie jest konwertowana na wielkie litery, przetworzenia każdego elementu w kolekcji zwrócone `foreach` pętli w `Main`.  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Wykonanie odroczone (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
