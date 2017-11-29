---
title: Filtrowanie danych (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 31e3a4729a98e1f4b588cd415a15fff270587234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="fabf6-102">Filtrowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fabf6-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="fabf6-103">Filtrowanie odnosi się do operacji ograniczyć zestaw wyników do zawierać tylko elementy, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="fabf6-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="fabf6-104">Jest nazywana zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="fabf6-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="fabf6-105">Na poniższej ilustracji przedstawiono wyniki filtrowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="fabf6-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="fabf6-106">Predykat dla filtrowania operacji określa, czy znak musi być "A".</span><span class="sxs-lookup"><span data-stu-id="fabf6-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="fabf6-107">![LINQ filtrowania operacji](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="fabf6-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="fabf6-108">Metody — operator zapytań standardowe, wykonujących wyboru są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="fabf6-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fabf6-109">Metody</span><span class="sxs-lookup"><span data-stu-id="fabf6-109">Methods</span></span>  
  
|<span data-ttu-id="fabf6-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="fabf6-110">Method Name</span></span>|<span data-ttu-id="fabf6-111">Opis</span><span class="sxs-lookup"><span data-stu-id="fabf6-111">Description</span></span>|<span data-ttu-id="fabf6-112">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fabf6-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="fabf6-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="fabf6-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="fabf6-114">OfType</span><span class="sxs-lookup"><span data-stu-id="fabf6-114">OfType</span></span>|<span data-ttu-id="fabf6-115">Wybiera wartości, w zależności od ich możliwości można rzutować na określony typ.</span><span class="sxs-lookup"><span data-stu-id="fabf6-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="fabf6-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="fabf6-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fabf6-117">Gdzie</span><span class="sxs-lookup"><span data-stu-id="fabf6-117">Where</span></span>|<span data-ttu-id="fabf6-118">Wybiera wartości, które są oparte na funkcji predykatu.</span><span class="sxs-lookup"><span data-stu-id="fabf6-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="fabf6-119">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="fabf6-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="fabf6-120">W poniższym przykładzie użyto `Where` do filtrowania z tablicy te ciągi, które mają określoną długość.</span><span class="sxs-lookup"><span data-stu-id="fabf6-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
```vb  
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim query = From word In words   
            Where word.Length = 3   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
```  
  
## <a name="see-also"></a><span data-ttu-id="fabf6-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fabf6-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="fabf6-122">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fabf6-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="fabf6-123">Gdy klauzula</span><span class="sxs-lookup"><span data-stu-id="fabf6-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="fabf6-124">Porady: filtrowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="fabf6-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)  
 [<span data-ttu-id="fabf6-125">Porady: zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fabf6-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [<span data-ttu-id="fabf6-126">Porady: zapytanie o pliki o określonym atrybucie lub nazwie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fabf6-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [<span data-ttu-id="fabf6-127">Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fabf6-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
