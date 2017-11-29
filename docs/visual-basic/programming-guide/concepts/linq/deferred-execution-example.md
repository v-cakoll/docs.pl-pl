---
title: "Wykonanie odroczone — przykład (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a4d2146901d9282b0df706b483afef79f714f660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="c29c0-102">Wykonanie odroczone — przykład (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c29c0-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="c29c0-103">W tym temacie przedstawiono sposób odroczonego wykonania i obliczanie leniwe wpływa na wykonanie programu LINQ do XML zapytania.</span><span class="sxs-lookup"><span data-stu-id="c29c0-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c29c0-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c29c0-104">Example</span></span>  
 <span data-ttu-id="c29c0-105">W poniższym przykładzie przedstawiono kolejność wykonywania, korzystając z metody rozszerzenia, który używa odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="c29c0-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="c29c0-106">Przykład deklaruje tablicę trzy ciągi.</span><span class="sxs-lookup"><span data-stu-id="c29c0-106">The example declares an array of three strings.</span></span> <span data-ttu-id="c29c0-107">Go następnie iteruje po kolekcji zwróconej przez `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="c29c0-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="c29c0-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c29c0-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="c29c0-109">Zwróć uwagę, że podczas iteracji w kolekcji zwróconej przez `ConvertCollectionToUpperCase`każdego elementu jest pobierana z tablicy ciągów źródła i przekonwertowane na wielkie litery przed następnego elementu jest pobierana z tablicy ciągów źródła.</span><span class="sxs-lookup"><span data-stu-id="c29c0-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="c29c0-110">Widać, że cała tablica ciągów nie jest przekonwertowany na wielkie litery, przed przetworzeniem każdego elementu w zwracanej kolekcji w `foreach` pętli w `Main`.</span><span class="sxs-lookup"><span data-stu-id="c29c0-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c29c0-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c29c0-111">See Also</span></span>  
 [<span data-ttu-id="c29c0-112">Samouczek: Odroczonego wykonania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c29c0-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
