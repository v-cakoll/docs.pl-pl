---
title: Przykład wykonania odroczonego
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 6ab8f6434bb24b7a66ca4afd1d082911481671f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354227"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="5ead1-102">Deferred Execution Example (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ead1-102">Deferred Execution Example (Visual Basic)</span></span>

<span data-ttu-id="5ead1-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span><span class="sxs-lookup"><span data-stu-id="5ead1-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example"></a><span data-ttu-id="5ead1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ead1-104">Example</span></span>

<span data-ttu-id="5ead1-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span><span class="sxs-lookup"><span data-stu-id="5ead1-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="5ead1-106">The example declares an array of three strings.</span><span class="sxs-lookup"><span data-stu-id="5ead1-106">The example declares an array of three strings.</span></span> <span data-ttu-id="5ead1-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="5ead1-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

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

<span data-ttu-id="5ead1-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5ead1-108">This example produces the following output:</span></span>

```console
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="5ead1-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span><span class="sxs-lookup"><span data-stu-id="5ead1-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="5ead1-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span><span class="sxs-lookup"><span data-stu-id="5ead1-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ead1-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ead1-111">See also</span></span>

- [<span data-ttu-id="5ead1-112">Tutorial: Deferred Execution (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ead1-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
