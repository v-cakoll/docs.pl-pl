---
title: Konwertowanie typów danych (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 9e8b7726b94871a17a4be50a9b24d8b73abcf79c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594616"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="ebcc6-102">Konwertowanie typów danych (C#)</span><span class="sxs-lookup"><span data-stu-id="ebcc6-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="ebcc6-103">Metody konwersji zmieniają typ obiektów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="ebcc6-104">Operacje konwersji w zapytaniach LINQ są przydatne w różnych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="ebcc6-105">Poniżej przedstawiono kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="ebcc6-105">Following are some examples:</span></span>  
  
- <span data-ttu-id="ebcc6-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metoda może służyć do ukrycia niestandardowej implementacji standardowego operatora zapytań.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="ebcc6-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metoda może służyć do włączenia kolekcji niesparametryzowanej dla zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="ebcc6-108">Metody <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>i mogąbyćużywanedowymuszenianatychmiastowegowykonaniazapytaniazamiastodliczeniagodomomentuwyliczeniazapytania.<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ebcc6-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebcc6-109">Metody</span><span class="sxs-lookup"><span data-stu-id="ebcc6-109">Methods</span></span>  
 <span data-ttu-id="ebcc6-110">W poniższej tabeli wymieniono standardowe metody operatorów zapytań, które wykonują konwersje typów danych.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="ebcc6-111">Metody konwersji w tej tabeli, których nazwy zaczynają się od "As", zmieniają typ statyczny kolekcji źródłowej, ale nie są wyliczane.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="ebcc6-112">Metody, których nazwy zaczynają się od "do", wyliczają kolekcję źródłową i umieszczają elementy w odpowiednim typie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="ebcc6-113">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="ebcc6-113">Method Name</span></span>|<span data-ttu-id="ebcc6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ebcc6-114">Description</span></span>|<span data-ttu-id="ebcc6-115">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="ebcc6-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="ebcc6-116">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="ebcc6-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="ebcc6-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="ebcc6-117">AsEnumerable</span></span>|<span data-ttu-id="ebcc6-118">Zwraca dane wejściowe wpisane jako <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="ebcc6-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ebcc6-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="ebcc6-120">AsQueryable</span></span>|<span data-ttu-id="ebcc6-121">Konwertuje (ogólne) <xref:System.Collections.IEnumerable> na (rodzajowy). <xref:System.Linq.IQueryable></span><span class="sxs-lookup"><span data-stu-id="ebcc6-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="ebcc6-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ebcc6-123">Rzutowanie</span><span class="sxs-lookup"><span data-stu-id="ebcc6-123">Cast</span></span>|<span data-ttu-id="ebcc6-124">Rzutuje elementy kolekcji na określony typ.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="ebcc6-125">Użyj jawnie wpisanej zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="ebcc6-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ebcc6-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ebcc6-127">OfType</span><span class="sxs-lookup"><span data-stu-id="ebcc6-127">OfType</span></span>|<span data-ttu-id="ebcc6-128">Filtruje wartości w zależności od ich zdolności do rzutowania do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="ebcc6-129">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ebcc6-130">ToArray —</span><span class="sxs-lookup"><span data-stu-id="ebcc6-130">ToArray</span></span>|<span data-ttu-id="ebcc6-131">Konwertuje kolekcję na tablicę.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-131">Converts a collection to an array.</span></span> <span data-ttu-id="ebcc6-132">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-132">This method forces query execution.</span></span>|<span data-ttu-id="ebcc6-133">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ebcc6-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="ebcc6-134">ToDictionary</span></span>|<span data-ttu-id="ebcc6-135">Umieszcza elementy w <xref:System.Collections.Generic.Dictionary%602> oparciu o funkcję selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="ebcc6-136">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-136">This method forces query execution.</span></span>|<span data-ttu-id="ebcc6-137">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ebcc6-138">ToList —</span><span class="sxs-lookup"><span data-stu-id="ebcc6-138">ToList</span></span>|<span data-ttu-id="ebcc6-139">Konwertuje kolekcję na <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="ebcc6-140">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-140">This method forces query execution.</span></span>|<span data-ttu-id="ebcc6-141">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ebcc6-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="ebcc6-142">ToLookup</span></span>|<span data-ttu-id="ebcc6-143">Umieszcza elementy w <xref:System.Linq.Lookup%602> (słownik jeden-do-wielu) w oparciu o funkcję selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="ebcc6-144">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-144">This method forces query execution.</span></span>|<span data-ttu-id="ebcc6-145">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="ebcc6-146">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="ebcc6-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="ebcc6-147">Poniższy przykład kodu używa zmiennej zakresu jawnie wpisanej do rzutowania typu na podtyp przed uzyskaniem dostępu do elementu członkowskiego, który jest dostępny tylko dla podtypu.</span><span class="sxs-lookup"><span data-stu-id="ebcc6-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ebcc6-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebcc6-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ebcc6-149">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="ebcc6-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ebcc6-150">from, klauzula</span><span class="sxs-lookup"><span data-stu-id="ebcc6-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="ebcc6-151">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="ebcc6-151">LINQ Query Expressions</span></span>](../../linq-query-expressions/index.md)
- [<span data-ttu-id="ebcc6-152">Instrukcje: Kwerenda ArrayList za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="ebcc6-152">How to: Query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
