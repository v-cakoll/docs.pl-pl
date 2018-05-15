---
title: Konwertowanie typów danych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 9821b2d6caad8feeac856185b92518c25de88da3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="15a72-102">Konwertowanie typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15a72-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="15a72-103">Metody konwersji Zmień typ wejściowy obiektów.</span><span class="sxs-lookup"><span data-stu-id="15a72-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="15a72-104">Konwersja operacje kwerend LINQ są przydatne w wielu aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="15a72-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="15a72-105">Poniżej przedstawiono kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="15a72-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="15a72-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metody można użyć do ukrywania typ implementacji niestandardowego operatora standardowej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="15a72-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="15a72-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> — Metoda można włączyć kolekcji bez parametrów na potrzeby zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="15a72-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="15a72-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, I <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metod można użyć, aby wymusić wykonanie zapytania bezpośredniego zamiast odkładanie go, dopóki wyliczeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="15a72-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15a72-109">Metody</span><span class="sxs-lookup"><span data-stu-id="15a72-109">Methods</span></span>  
 <span data-ttu-id="15a72-110">W poniższej tabeli wymieniono metody — operator zapytań standardowe, wykonujących konwersji typu danych.</span><span class="sxs-lookup"><span data-stu-id="15a72-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="15a72-111">Zmień typ statyczny kolekcji źródłowej metody konwersji w tej tabeli, których nazwy rozpoczynają się od "Jako", ale nie wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="15a72-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="15a72-112">Typ metody, których nazwy rozpoczynają się od "Do wyliczyć kolekcji źródłowej i elementy do odpowiedniej kolekcji".</span><span class="sxs-lookup"><span data-stu-id="15a72-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="15a72-113">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="15a72-113">Method Name</span></span>|<span data-ttu-id="15a72-114">Opis</span><span class="sxs-lookup"><span data-stu-id="15a72-114">Description</span></span>|<span data-ttu-id="15a72-115">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15a72-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="15a72-116">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="15a72-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="15a72-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="15a72-117">AsEnumerable</span></span>|<span data-ttu-id="15a72-118">Zwraca dane wejściowe typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="15a72-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="15a72-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="15a72-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="15a72-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="15a72-120">AsQueryable</span></span>|<span data-ttu-id="15a72-121">Konwertuje (ogólny) <xref:System.Collections.IEnumerable> do (ogólny) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="15a72-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="15a72-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="15a72-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="15a72-123">Rzutowanie</span><span class="sxs-lookup"><span data-stu-id="15a72-123">Cast</span></span>|<span data-ttu-id="15a72-124">Rzutuje elementy kolekcji do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="15a72-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="15a72-125">OfType</span><span class="sxs-lookup"><span data-stu-id="15a72-125">OfType</span></span>|<span data-ttu-id="15a72-126">Filtruje wartości, w zależności od ich możliwości można rzutować na określony typ.</span><span class="sxs-lookup"><span data-stu-id="15a72-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="15a72-127">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="15a72-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="15a72-128">toArray</span><span class="sxs-lookup"><span data-stu-id="15a72-128">ToArray</span></span>|<span data-ttu-id="15a72-129">Konwertuje kolekcję na tablicę.</span><span class="sxs-lookup"><span data-stu-id="15a72-129">Converts a collection to an array.</span></span> <span data-ttu-id="15a72-130">Ta metoda powoduje wykonanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="15a72-130">This method forces query execution.</span></span>|<span data-ttu-id="15a72-131">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="15a72-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="15a72-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="15a72-132">ToDictionary</span></span>|<span data-ttu-id="15a72-133">Umieszcza elementy do <xref:System.Collections.Generic.Dictionary%602> oparte na funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="15a72-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="15a72-134">Ta metoda powoduje wykonanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="15a72-134">This method forces query execution.</span></span>|<span data-ttu-id="15a72-135">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="15a72-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="15a72-136">tolist —</span><span class="sxs-lookup"><span data-stu-id="15a72-136">ToList</span></span>|<span data-ttu-id="15a72-137">Konwertuje kolekcję do <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="15a72-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="15a72-138">Ta metoda powoduje wykonanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="15a72-138">This method forces query execution.</span></span>|<span data-ttu-id="15a72-139">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="15a72-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="15a72-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="15a72-140">ToLookup</span></span>|<span data-ttu-id="15a72-141">Umieszcza elementy do <xref:System.Linq.Lookup%602> (Słownik jeden do wielu) oparte na funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="15a72-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="15a72-142">Ta metoda powoduje wykonanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="15a72-142">This method forces query execution.</span></span>|<span data-ttu-id="15a72-143">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="15a72-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="15a72-144">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="15a72-144">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="15a72-145">Poniższy przykład kodu wykorzystuje `From As` klauzuli do rzutowania typu z podtypem przed uzyskaniem dostępu do elementu członkowskiego, który jest dostępny tylko na podtyp.</span><span class="sxs-lookup"><span data-stu-id="15a72-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15a72-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15a72-146">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="15a72-147">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15a72-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="15a72-148">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="15a72-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="15a72-149">Porady: zapytanie w ArrayList za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15a72-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
