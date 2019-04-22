---
title: Filtrowanie danych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: a673126d928a97bf522783e73fc254debe2a9de8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837450"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="d91ed-102">Filtrowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d91ed-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="d91ed-103">Filtrowanie odnosi się do operacji ograniczyć zestaw wyników, aby zawiera tylko te elementy, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="d91ed-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="d91ed-104">Jest również nazywany zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="d91ed-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="d91ed-105">Poniższa ilustracja przedstawia wyniki filtrowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="d91ed-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="d91ed-106">Predykat dla filtrowania operacji określa, że znak musi być "A".</span><span class="sxs-lookup"><span data-stu-id="d91ed-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagram przedstawiający filtrowanie operację LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="d91ed-108">Metody standardowego operatora zapytań, które wykonują wyboru są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="d91ed-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d91ed-109">Metody</span><span class="sxs-lookup"><span data-stu-id="d91ed-109">Methods</span></span>  
  
|<span data-ttu-id="d91ed-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="d91ed-110">Method Name</span></span>|<span data-ttu-id="d91ed-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d91ed-111">Description</span></span>|<span data-ttu-id="d91ed-112">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d91ed-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="d91ed-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="d91ed-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="d91ed-114">OfType</span><span class="sxs-lookup"><span data-stu-id="d91ed-114">OfType</span></span>|<span data-ttu-id="d91ed-115">Wybiera wartości, w zależności od ich możliwości, można rzutować do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="d91ed-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="d91ed-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="d91ed-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d91ed-117">Gdzie</span><span class="sxs-lookup"><span data-stu-id="d91ed-117">Where</span></span>|<span data-ttu-id="d91ed-118">Wybiera wartości, które są oparte na funkcji predykatu.</span><span class="sxs-lookup"><span data-stu-id="d91ed-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="d91ed-119">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="d91ed-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="d91ed-120">W poniższym przykładzie użyto `Where` filtrującą dane z tablicy tych ciągów, które mają określonej długości.</span><span class="sxs-lookup"><span data-stu-id="d91ed-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d91ed-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d91ed-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="d91ed-122">Omówienie operatorów standardowej kwerendy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d91ed-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d91ed-123">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="d91ed-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="d91ed-124">Instrukcje: Filtrowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="d91ed-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="d91ed-125">Instrukcje: Zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d91ed-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="d91ed-126">Instrukcje: Zapytanie o pliki o określonym atrybucie lub nazwy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d91ed-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="d91ed-127">Instrukcje: Sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d91ed-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
