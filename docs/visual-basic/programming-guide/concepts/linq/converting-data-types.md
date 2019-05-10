---
title: Konwertowanie typów danych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 866b30d3d65add8714f2088169b0769c340f264e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641980"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="7e3b6-102">Konwertowanie typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e3b6-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="7e3b6-103">Metody konwersji zmienić typ danych wejściowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="7e3b6-104">Operacje konwersji w zapytaniach LINQ są przydatne w wielu różnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="7e3b6-105">Poniżej przedstawiono kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="7e3b6-105">Following are some examples:</span></span>  
  
- <span data-ttu-id="7e3b6-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metoda może służyć do ukrywanie niestandardowych implementacji standardowego operatora zapytania typu.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="7e3b6-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metoda może służyć do włączenia kolekcji zdefiniowanych na potrzeby zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="7e3b6-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, I <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody może służyć do wymuszenia wykonanie zapytania bezpośredniego zamiast odracza ją do czasu wyliczenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e3b6-109">Metody</span><span class="sxs-lookup"><span data-stu-id="7e3b6-109">Methods</span></span>  
 <span data-ttu-id="7e3b6-110">Poniższa tabela zawiera listę metod standardowych operatorów zapytań, które wykonują konwersje typów danych.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="7e3b6-111">Metody konwersji w tej tabeli, których nazwy rozpoczynają się od "Jako" Zmiana typu statycznego kolekcji źródłowej, ale nie wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="7e3b6-112">Typ metody, których nazwy rozpoczynają się od "Do wyliczania kolekcji źródłowej i umieść elementy w odpowiedniej kolekcji".</span><span class="sxs-lookup"><span data-stu-id="7e3b6-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="7e3b6-113">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="7e3b6-113">Method Name</span></span>|<span data-ttu-id="7e3b6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7e3b6-114">Description</span></span>|<span data-ttu-id="7e3b6-115">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7e3b6-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="7e3b6-116">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="7e3b6-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="7e3b6-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="7e3b6-117">AsEnumerable</span></span>|<span data-ttu-id="7e3b6-118">Zwraca dane wejściowe wpisanych w formie <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="7e3b6-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7e3b6-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="7e3b6-120">AsQueryable</span></span>|<span data-ttu-id="7e3b6-121">Konwertuje (ogólny) <xref:System.Collections.IEnumerable> do (ogólny) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="7e3b6-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7e3b6-123">Rzutowanie</span><span class="sxs-lookup"><span data-stu-id="7e3b6-123">Cast</span></span>|<span data-ttu-id="7e3b6-124">Rzutuje elementy kolekcji do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7e3b6-125">OfType</span><span class="sxs-lookup"><span data-stu-id="7e3b6-125">OfType</span></span>|<span data-ttu-id="7e3b6-126">Służy do przefiltrowania wartości, w zależności od ich możliwości, można rzutować do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="7e3b6-127">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7e3b6-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="7e3b6-128">ToArray</span></span>|<span data-ttu-id="7e3b6-129">Konwertuje kolekcję na tablicę.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-129">Converts a collection to an array.</span></span> <span data-ttu-id="7e3b6-130">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-130">This method forces query execution.</span></span>|<span data-ttu-id="7e3b6-131">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7e3b6-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="7e3b6-132">ToDictionary</span></span>|<span data-ttu-id="7e3b6-133">Umieszcza elementy do <xref:System.Collections.Generic.Dictionary%602> oparte na funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="7e3b6-134">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-134">This method forces query execution.</span></span>|<span data-ttu-id="7e3b6-135">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7e3b6-136">Tolist —</span><span class="sxs-lookup"><span data-stu-id="7e3b6-136">ToList</span></span>|<span data-ttu-id="7e3b6-137">Konwertuje kolekcję do <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="7e3b6-138">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-138">This method forces query execution.</span></span>|<span data-ttu-id="7e3b6-139">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7e3b6-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="7e3b6-140">ToLookup</span></span>|<span data-ttu-id="7e3b6-141">Umieszcza elementy do <xref:System.Linq.Lookup%602> (Słownik jeden do wielu) na podstawie selektora kluczy funkcji.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="7e3b6-142">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-142">This method forces query execution.</span></span>|<span data-ttu-id="7e3b6-143">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="7e3b6-144">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="7e3b6-144">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="7e3b6-145">Poniższy przykład kodu wykorzystuje `From As` klauzuli rzutowanie typu podtypem przed uzyskaniem dostępu do składowej, która jest dostępna tylko na podtypu.</span><span class="sxs-lookup"><span data-stu-id="7e3b6-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e3b6-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e3b6-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="7e3b6-147">Omówienie operatorów standardowej kwerendy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e3b6-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7e3b6-148">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="7e3b6-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="7e3b6-149">Instrukcje: Zapytanie w ArrayList za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e3b6-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
