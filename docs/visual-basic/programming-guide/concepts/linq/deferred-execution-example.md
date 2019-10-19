---
title: Przykład wykonania odroczonego (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: e0bb7f3d125cc48607a534e2c24cbf7083353945
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583330"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="d6a1b-102">Przykład wykonania odroczonego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6a1b-102">Deferred Execution Example (Visual Basic)</span></span>

<span data-ttu-id="d6a1b-103">W tym temacie pokazano, w jaki sposób odroczone wykonywanie i Ocena z opóźnieniem wpływają na wykonywanie zapytań LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="d6a1b-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example"></a><span data-ttu-id="d6a1b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6a1b-104">Example</span></span>

<span data-ttu-id="d6a1b-105">Poniższy przykład pokazuje kolejność wykonywania przy użyciu metody rozszerzenia, która korzysta z odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="d6a1b-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="d6a1b-106">Przykład deklaruje tablicę trzech ciągów.</span><span class="sxs-lookup"><span data-stu-id="d6a1b-106">The example declares an array of three strings.</span></span> <span data-ttu-id="d6a1b-107">Następnie wykonuje iterację w kolekcji zwróconej przez `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="d6a1b-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

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

<span data-ttu-id="d6a1b-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="d6a1b-108">This example produces the following output:</span></span>

```console
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="d6a1b-109">Należy zauważyć, że podczas iteracji kolekcji zwróconej przez `ConvertCollectionToUpperCase` każdy element zostanie pobrany z tablicy ciągów źródłowych i przekonwertowany na wielkie litery przed pobraniem następnego elementu z tablicy ciągów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="d6a1b-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="d6a1b-110">Można zobaczyć, że cała tablica ciągów nie jest konwertowana na wielkie przed każdym elementem w zwróconej kolekcji, w pętli `foreach` w `Main`.</span><span class="sxs-lookup"><span data-stu-id="d6a1b-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6a1b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6a1b-111">See also</span></span>

- [<span data-ttu-id="d6a1b-112">Samouczek: wykonywanie odroczone (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6a1b-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
