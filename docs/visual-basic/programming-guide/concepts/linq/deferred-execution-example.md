---
title: Wykonanie odroczone — przykład (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: a9827b73ebc0df589a14032d99b32d1e1bc891ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642132"
---
# <a name="deferred-execution-example-visual-basic"></a>Wykonanie odroczone — przykład (Visual Basic)
W tym temacie przedstawiono sposób odroczonego wykonania i obliczanie leniwe wpływa na wykonanie programu LINQ do XML zapytania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono kolejność wykonywania, korzystając z metody rozszerzenia, który używa odroczonego wykonania. Przykład deklaruje tablicę trzy ciągi. Go następnie iteruje po kolekcji zwróconej przez `ConvertCollectionToUpperCase`.  
  
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
  
 Zwróć uwagę, że podczas iteracji w kolekcji zwróconej przez `ConvertCollectionToUpperCase`każdego elementu jest pobierana z tablicy ciągów źródła i przekonwertowane na wielkie litery przed następnego elementu jest pobierana z tablicy ciągów źródła.  
  
 Widać, że cała tablica ciągów nie jest przekonwertowany na wielkie litery, przed przetworzeniem każdego elementu w zwracanej kolekcji w `foreach` pętli w `Main`.  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Odroczonego wykonania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
