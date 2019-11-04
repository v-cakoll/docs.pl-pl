---
title: Konwertowanie typów danych (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: ddd9407c3b7e25dbfb8fc0bddb5daab7db2e4e53
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418617"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="21c80-102">Konwertowanie typów danych (C#)</span><span class="sxs-lookup"><span data-stu-id="21c80-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="21c80-103">Metody konwersji zmieniają typ obiektów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="21c80-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="21c80-104">Operacje konwersji w zapytaniach LINQ są przydatne w różnych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="21c80-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="21c80-105">Poniżej przedstawiono kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="21c80-105">Following are some examples:</span></span>  
  
- <span data-ttu-id="21c80-106">Metoda <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> może służyć do ukrycia niestandardowej implementacji standardowego operatora zapytań.</span><span class="sxs-lookup"><span data-stu-id="21c80-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="21c80-107">Za pomocą metody <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> można włączyć kolekcje niesparametryzowane dla zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="21c80-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="21c80-108">Metody <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>i <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> mogą być używane do wymuszenia natychmiastowego wykonania zapytania, zamiast odliczenia go do momentu wyliczenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="21c80-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21c80-109">Metody</span><span class="sxs-lookup"><span data-stu-id="21c80-109">Methods</span></span>  
 <span data-ttu-id="21c80-110">W poniższej tabeli wymieniono standardowe metody operatorów zapytań, które wykonują konwersje typów danych.</span><span class="sxs-lookup"><span data-stu-id="21c80-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="21c80-111">Metody konwersji w tej tabeli, których nazwy zaczynają się od "As", zmieniają typ statyczny kolekcji źródłowej, ale nie są wyliczane.</span><span class="sxs-lookup"><span data-stu-id="21c80-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="21c80-112">Metody, których nazwy zaczynają się od "do", wyliczają kolekcję źródłową i umieszczają elementy w odpowiednim typie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="21c80-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="21c80-113">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="21c80-113">Method Name</span></span>|<span data-ttu-id="21c80-114">Opis</span><span class="sxs-lookup"><span data-stu-id="21c80-114">Description</span></span>|<span data-ttu-id="21c80-115">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="21c80-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="21c80-116">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="21c80-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="21c80-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="21c80-117">AsEnumerable</span></span>|<span data-ttu-id="21c80-118">Zwraca dane wejściowe wpisane jako <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="21c80-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="21c80-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="21c80-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="21c80-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="21c80-120">AsQueryable</span></span>|<span data-ttu-id="21c80-121">Konwertuje (ogólne) <xref:System.Collections.IEnumerable> na (ogólne) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="21c80-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="21c80-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="21c80-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="21c80-123">Rzutowanie</span><span class="sxs-lookup"><span data-stu-id="21c80-123">Cast</span></span>|<span data-ttu-id="21c80-124">Rzutuje elementy kolekcji na określony typ.</span><span class="sxs-lookup"><span data-stu-id="21c80-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="21c80-125">Użyj jawnie wpisanej zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="21c80-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="21c80-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="21c80-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="21c80-127">OfType</span><span class="sxs-lookup"><span data-stu-id="21c80-127">OfType</span></span>|<span data-ttu-id="21c80-128">Filtruje wartości w zależności od ich zdolności do rzutowania do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="21c80-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="21c80-129">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="21c80-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="21c80-130">ToArray —</span><span class="sxs-lookup"><span data-stu-id="21c80-130">ToArray</span></span>|<span data-ttu-id="21c80-131">Konwertuje kolekcję na tablicę.</span><span class="sxs-lookup"><span data-stu-id="21c80-131">Converts a collection to an array.</span></span> <span data-ttu-id="21c80-132">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="21c80-132">This method forces query execution.</span></span>|<span data-ttu-id="21c80-133">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="21c80-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="21c80-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="21c80-134">ToDictionary</span></span>|<span data-ttu-id="21c80-135">Umieszcza elementy w <xref:System.Collections.Generic.Dictionary%602> na podstawie funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="21c80-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="21c80-136">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="21c80-136">This method forces query execution.</span></span>|<span data-ttu-id="21c80-137">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="21c80-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="21c80-138">ToList —</span><span class="sxs-lookup"><span data-stu-id="21c80-138">ToList</span></span>|<span data-ttu-id="21c80-139">Konwertuje kolekcję na <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="21c80-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="21c80-140">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="21c80-140">This method forces query execution.</span></span>|<span data-ttu-id="21c80-141">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="21c80-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="21c80-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="21c80-142">ToLookup</span></span>|<span data-ttu-id="21c80-143">Umieszcza elementy w <xref:System.Linq.Lookup%602> (słownik jeden-do-wielu) na podstawie funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="21c80-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="21c80-144">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="21c80-144">This method forces query execution.</span></span>|<span data-ttu-id="21c80-145">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="21c80-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="21c80-146">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="21c80-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="21c80-147">Poniższy przykład kodu używa zmiennej zakresu jawnie wpisanej do rzutowania typu na podtyp przed uzyskaniem dostępu do elementu członkowskiego, który jest dostępny tylko dla podtypu.</span><span class="sxs-lookup"><span data-stu-id="21c80-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
```csharp  
class Plant  
{  
    public string Name { get; set; }  
}  
  
class CarnivorousPlant : Plant  
{  
    public string TrapType { get; set; }  
}  
  
static void Cast()  
{  
    Plant[] plants = new Plant[] {  
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },  
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },  
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },  
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }  
    };  
  
    var query = from CarnivorousPlant cPlant in plants  
                where cPlant.TrapType == "Snap Trap"  
                select cPlant;  
  
    foreach (Plant plant in query)  
        Console.WriteLine(plant.Name);  
  
    /* This code produces the following output:  
  
        Venus Fly Trap  
        Waterwheel Plant  
    */  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="21c80-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21c80-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="21c80-149">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="21c80-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="21c80-150">from, klauzula</span><span class="sxs-lookup"><span data-stu-id="21c80-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="21c80-151">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="21c80-151">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="21c80-152">Instrukcje: zapytanie do ArrayList za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="21c80-152">How to: Query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
