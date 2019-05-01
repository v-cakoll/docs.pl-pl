---
title: Przykład wykonania odroczonego (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 29f118b3e6d49840b94277f17858f1339f2fb08c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977632"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="c346c-102">Przykład wykonania odroczonego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c346c-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="c346c-103">W tym temacie przedstawiono sposób odroczonego wykonania i obliczanie z opóźnieniem wpływa na wykonywanie Twojego zapytaniach składnika LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="c346c-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c346c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c346c-104">Example</span></span>  
 <span data-ttu-id="c346c-105">Poniższy przykład pokazuje kolejność wykonywania, korzystając z metody rozszerzenia, która używa odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="c346c-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="c346c-106">Przykład deklaruje tablicę trzy ciągi.</span><span class="sxs-lookup"><span data-stu-id="c346c-106">The example declares an array of three strings.</span></span> <span data-ttu-id="c346c-107">Następnie wykonuje iterację przez zbiorze zwróconym przez `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="c346c-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="c346c-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c346c-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="c346c-109">Należy zauważyć, że podczas iteracji w kolekcji zwróconej przez `ConvertCollectionToUpperCase`, każdy element jest pobierana z tablicy ciągów źródłowych i przekonwertowane na wielkie litery przed następnego elementu jest pobierana z tablicy ciągów źródła.</span><span class="sxs-lookup"><span data-stu-id="c346c-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="c346c-110">Widać, że całej tablicy ciągów nie jest konwertowana na wielkie litery, przetworzenia każdego elementu w kolekcji zwrócone `foreach` pętli w `Main`.</span><span class="sxs-lookup"><span data-stu-id="c346c-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c346c-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c346c-111">See also</span></span>

- [<span data-ttu-id="c346c-112">Samouczek: Wykonanie odroczone (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c346c-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
