---
title: Konwertowanie typów danych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 744dec0093384a15470186fc09695c17e79468fa
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524231"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="e8930-102">Konwertowanie typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8930-102">Converting Data Types (Visual Basic)</span></span>

<span data-ttu-id="e8930-103">Metody konwersji zmieniają typ obiektów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e8930-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="e8930-104">Operacje konwersji w zapytaniach LINQ są przydatne w różnych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="e8930-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="e8930-105">Poniżej przedstawiono kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="e8930-105">The following are some examples:</span></span>

- <span data-ttu-id="e8930-106">Metoda <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> może służyć do ukrycia niestandardowej implementacji standardowego operatora zapytań.</span><span class="sxs-lookup"><span data-stu-id="e8930-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="e8930-107">Za pomocą metody <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> można włączyć kolekcje niesparametryzowane dla zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="e8930-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="e8930-108">Metody <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> i <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> mogą być używane do wymuszenia natychmiastowego wykonania zapytania, zamiast odliczenia go do momentu wyliczenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="e8930-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="e8930-109">Metody</span><span class="sxs-lookup"><span data-stu-id="e8930-109">Methods</span></span>

<span data-ttu-id="e8930-110">W poniższej tabeli wymieniono standardowe metody operatorów zapytań, które wykonują konwersje typów danych.</span><span class="sxs-lookup"><span data-stu-id="e8930-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

<span data-ttu-id="e8930-111">Metody konwersji w tej tabeli, których nazwy zaczynają się od "As", zmieniają typ statyczny kolekcji źródłowej, ale nie są wyliczane.</span><span class="sxs-lookup"><span data-stu-id="e8930-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="e8930-112">Metody, których nazwy zaczynają się od "do", wyliczają kolekcję źródłową i umieszczają elementy w odpowiednim typie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e8930-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="e8930-113">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="e8930-113">Method Name</span></span>|<span data-ttu-id="e8930-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e8930-114">Description</span></span>|<span data-ttu-id="e8930-115">Składnia wyrażenia zapytania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e8930-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="e8930-116">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="e8930-116">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="e8930-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="e8930-117">AsEnumerable</span></span>|<span data-ttu-id="e8930-118">Zwraca dane wejściowe wpisane jako <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="e8930-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="e8930-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e8930-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="e8930-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="e8930-120">AsQueryable</span></span>|<span data-ttu-id="e8930-121">Konwertuje (ogólne) <xref:System.Collections.IEnumerable> na (ogólne) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="e8930-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="e8930-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e8930-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="e8930-123">Rzutowanie</span><span class="sxs-lookup"><span data-stu-id="e8930-123">Cast</span></span>|<span data-ttu-id="e8930-124">Rzutuje elementy kolekcji na określony typ.</span><span class="sxs-lookup"><span data-stu-id="e8930-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="e8930-125">OfType</span><span class="sxs-lookup"><span data-stu-id="e8930-125">OfType</span></span>|<span data-ttu-id="e8930-126">Filtruje wartości w zależności od ich zdolności do rzutowania do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="e8930-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="e8930-127">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e8930-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="e8930-128">ToArray —</span><span class="sxs-lookup"><span data-stu-id="e8930-128">ToArray</span></span>|<span data-ttu-id="e8930-129">Konwertuje kolekcję na tablicę.</span><span class="sxs-lookup"><span data-stu-id="e8930-129">Converts a collection to an array.</span></span> <span data-ttu-id="e8930-130">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="e8930-130">This method forces query execution.</span></span>|<span data-ttu-id="e8930-131">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e8930-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="e8930-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="e8930-132">ToDictionary</span></span>|<span data-ttu-id="e8930-133">Umieszcza elementy w <xref:System.Collections.Generic.Dictionary%602> na podstawie funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="e8930-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="e8930-134">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="e8930-134">This method forces query execution.</span></span>|<span data-ttu-id="e8930-135">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e8930-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="e8930-136">ToList —</span><span class="sxs-lookup"><span data-stu-id="e8930-136">ToList</span></span>|<span data-ttu-id="e8930-137">Konwertuje kolekcję na <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="e8930-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="e8930-138">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="e8930-138">This method forces query execution.</span></span>|<span data-ttu-id="e8930-139">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e8930-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="e8930-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="e8930-140">ToLookup</span></span>|<span data-ttu-id="e8930-141">Umieszcza elementy w <xref:System.Linq.Lookup%602> (słownik jeden-do-wielu) na podstawie funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="e8930-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="e8930-142">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="e8930-142">This method forces query execution.</span></span>|<span data-ttu-id="e8930-143">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e8930-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="e8930-144">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="e8930-144">Query Expression Syntax Example</span></span>

<span data-ttu-id="e8930-145">Poniższy przykład kodu używa klauzuli `From As` do rzutowania typu na podtyp przed uzyskaniem dostępu do elementu członkowskiego, który jest dostępny tylko dla podtypu.</span><span class="sxs-lookup"><span data-stu-id="e8930-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e8930-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8930-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="e8930-147">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8930-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="e8930-148">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="e8930-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="e8930-149">Instrukcje: wykonywanie zapytań do ArrayList za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8930-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
