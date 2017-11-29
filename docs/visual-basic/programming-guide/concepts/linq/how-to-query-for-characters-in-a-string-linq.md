---
title: "Porady: zapytanie o znaki w ciągu (LINQ) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ebc832763e271cc53e9c95827c301f82e9a7578a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="5f556-102">Porady: zapytanie o znaki w ciągu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f556-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="5f556-103">Ponieważ <xref:System.String> klasa implementuje ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejsu, dowolny ciąg może być badana sekwencję znaków.</span><span class="sxs-lookup"><span data-stu-id="5f556-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="5f556-104">Jednak nie jest typowym zastosowaniem zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="5f556-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="5f556-105">Złożone wzorzec dopasowany operacje, można użyć <xref:System.Text.RegularExpressions.Regex> klasy.</span><span class="sxs-lookup"><span data-stu-id="5f556-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f556-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f556-106">Example</span></span>  
 <span data-ttu-id="5f556-107">Poniższy przykład kwerendę ciąg, aby określić liczbę cyfr, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="5f556-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="5f556-108">Należy pamiętać, że zapytanie jest "ponownie" po wykonaniu po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="5f556-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="5f556-109">Jest to możliwe, ponieważ zapytanie sam nie przechowuje wszystkie rzeczywiste wyniki.</span><span class="sxs-lookup"><span data-stu-id="5f556-109">This is possible because the query itself does not store any actual results.</span></span>  
  
```vb  
Class QueryAString  
  
    Shared Sub Main()  
  
        ' A string is an IEnumerable data source.  
        Dim aString As String = "ABCDE99F-J74-12-89A"  
  
        ' Select only those characters that are numbers  
        Dim stringQuery = From ch In aString   
                          Where Char.IsDigit(ch)   
                          Select ch  
        ' Execute the query  
        For Each c As Char In stringQuery  
            Console.Write(c & " ")  
        Next  
  
        ' Call the Count method on the existing query.  
        Dim count As Integer = stringQuery.Count()  
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)  
  
        ' Select all characters before the first '-'  
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")  
  
        ' Execute the second query  
        For Each ch In stringQuery2  
            Console.Write(ch)  
        Next  
  
        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 9 9 7 4 1 2 8 9   
' Count = 8  
' ABCDE99F  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f556-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5f556-110">Compiling the Code</span></span>  
 <span data-ttu-id="5f556-111">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5f556-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f556-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f556-112">See Also</span></span>  
 [<span data-ttu-id="5f556-113">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f556-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="5f556-114">Porady: łączenie kwerend LINQ z wyrażeniami regularnymi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f556-114">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
