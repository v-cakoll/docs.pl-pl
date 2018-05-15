---
title: Filtrowanie danych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: d3f44d0b6478103a10fb731988aeebc005cde82e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="206e3-102">Filtrowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="206e3-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="206e3-103">Filtrowanie odnosi się do operacji ograniczyć zestaw wyników do zawierać tylko elementy, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="206e3-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="206e3-104">Jest nazywana zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="206e3-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="206e3-105">Na poniższej ilustracji przedstawiono wyniki filtrowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="206e3-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="206e3-106">Predykat dla filtrowania operacji określa, czy znak musi być "A".</span><span class="sxs-lookup"><span data-stu-id="206e3-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="206e3-107">![LINQ filtrowania operacji](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="206e3-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="206e3-108">Metody — operator zapytań standardowe, wykonujących wyboru są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="206e3-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="206e3-109">Metody</span><span class="sxs-lookup"><span data-stu-id="206e3-109">Methods</span></span>  
  
|<span data-ttu-id="206e3-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="206e3-110">Method Name</span></span>|<span data-ttu-id="206e3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="206e3-111">Description</span></span>|<span data-ttu-id="206e3-112">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="206e3-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="206e3-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="206e3-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="206e3-114">OfType</span><span class="sxs-lookup"><span data-stu-id="206e3-114">OfType</span></span>|<span data-ttu-id="206e3-115">Wybiera wartości, w zależności od ich możliwości można rzutować na określony typ.</span><span class="sxs-lookup"><span data-stu-id="206e3-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="206e3-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="206e3-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="206e3-117">Gdzie</span><span class="sxs-lookup"><span data-stu-id="206e3-117">Where</span></span>|<span data-ttu-id="206e3-118">Wybiera wartości, które są oparte na funkcji predykatu.</span><span class="sxs-lookup"><span data-stu-id="206e3-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="206e3-119">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="206e3-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="206e3-120">W poniższym przykładzie użyto `Where` do filtrowania z tablicy te ciągi, które mają określoną długość.</span><span class="sxs-lookup"><span data-stu-id="206e3-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="206e3-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="206e3-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="206e3-122">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="206e3-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="206e3-123">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="206e3-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="206e3-124">Porady: filtrowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="206e3-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)  
 [<span data-ttu-id="206e3-125">Porady: zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="206e3-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [<span data-ttu-id="206e3-126">Porady: zapytanie o pliki o określonym atrybucie lub nazwie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="206e3-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [<span data-ttu-id="206e3-127">Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="206e3-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
