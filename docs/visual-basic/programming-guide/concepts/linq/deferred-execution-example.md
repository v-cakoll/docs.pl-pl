---
title: Przykład wykonania odroczonego
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 863b018b6047d61f6fb4a5c1ac68151ed69d24a1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410802"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="b8b6d-102">Przykład wykonania odroczonego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8b6d-102">Deferred Execution Example (Visual Basic)</span></span>

<span data-ttu-id="b8b6d-103">W tym temacie pokazano, w jaki sposób odroczone wykonywanie i Ocena z opóźnieniem wpływają na wykonywanie zapytań LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="b8b6d-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example"></a><span data-ttu-id="b8b6d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8b6d-104">Example</span></span>

<span data-ttu-id="b8b6d-105">Poniższy przykład pokazuje kolejność wykonywania przy użyciu metody rozszerzenia, która korzysta z odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="b8b6d-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="b8b6d-106">Przykład deklaruje tablicę trzech ciągów.</span><span class="sxs-lookup"><span data-stu-id="b8b6d-106">The example declares an array of three strings.</span></span> <span data-ttu-id="b8b6d-107">Następnie wykonuje iterację w kolekcji zwróconej przez `ConvertCollectionToUpperCase` .</span><span class="sxs-lookup"><span data-stu-id="b8b6d-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

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

<span data-ttu-id="b8b6d-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b8b6d-108">This example produces the following output:</span></span>

```console
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="b8b6d-109">Należy zauważyć, że podczas iteracji kolekcji zwróconej przez `ConvertCollectionToUpperCase` , każdy element jest pobierany z tablicy ciągów źródłowych i konwertowany na wielkie przed pobraniem następnego elementu z tablicy ciągów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="b8b6d-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="b8b6d-110">Można zobaczyć, że cała tablica ciągów nie jest konwertowana na wielkie przed każdym elementem w zwróconej kolekcji w `foreach` pętli w `Main` .</span><span class="sxs-lookup"><span data-stu-id="b8b6d-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8b6d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8b6d-111">See also</span></span>

- [<span data-ttu-id="b8b6d-112">Samouczek: wykonywanie odroczone (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8b6d-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](tutorial-deferred-execution.md)
