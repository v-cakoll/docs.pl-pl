---
title: Konwertowanie typów danych (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347202"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="9fa3e-102">Konwertowanie typów danych (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa3e-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="9fa3e-103">Metody konwersji zmieniają typ obiektów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="9fa3e-104">Operacje konwersji w kwerendach LINQ są przydatne w różnych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="9fa3e-105">Oto kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="9fa3e-105">Following are some examples:</span></span>

- <span data-ttu-id="9fa3e-106">Metoda <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> może służyć do ukrycia implementacji niestandardowej typu standardowego operatora kwerendy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="9fa3e-107">Metoda <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> może służyć do włączania kolekcji niesparametryzowanych dla LINQ zapytań.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="9fa3e-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> i metody mogą służyć do wymuszenia natychmiastowego wykonywania kwerendy zamiast odroczyć go, dopóki kwerenda nie zostanie wyliczona.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="9fa3e-109">Metody</span><span class="sxs-lookup"><span data-stu-id="9fa3e-109">Methods</span></span>
 <span data-ttu-id="9fa3e-110">W poniższej tabeli wymieniono standardowe metody operatora kwerendy, które wykonują konwersje typu danych.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="9fa3e-111">Metody konwersji w tej tabeli, których nazwy zaczynają się od "As", zmieniają statyczny typ kolekcji źródłowej, ale nie wyliczają jej.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="9fa3e-112">Metody, których nazwy zaczynają się od "Do" wyliczyć kolekcji źródłowej i umieścić elementy w odpowiednim typie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="9fa3e-113">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="9fa3e-113">Method Name</span></span>|<span data-ttu-id="9fa3e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9fa3e-114">Description</span></span>|<span data-ttu-id="9fa3e-115">Składnia wyrażenia kwerendy c#</span><span class="sxs-lookup"><span data-stu-id="9fa3e-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="9fa3e-116">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="9fa3e-116">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="9fa3e-117">Asenumerable</span><span class="sxs-lookup"><span data-stu-id="9fa3e-117">AsEnumerable</span></span>|<span data-ttu-id="9fa3e-118">Zwraca dane wejściowe <xref:System.Collections.Generic.IEnumerable%601>wpisane jako .</span><span class="sxs-lookup"><span data-stu-id="9fa3e-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="9fa3e-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="9fa3e-120">Asqueryable</span><span class="sxs-lookup"><span data-stu-id="9fa3e-120">AsQueryable</span></span>|<span data-ttu-id="9fa3e-121">Konwertuje (ogólny) <xref:System.Collections.IEnumerable> na <xref:System.Linq.IQueryable>(ogólny) .</span><span class="sxs-lookup"><span data-stu-id="9fa3e-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="9fa3e-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="9fa3e-123">Rzutowanie</span><span class="sxs-lookup"><span data-stu-id="9fa3e-123">Cast</span></span>|<span data-ttu-id="9fa3e-124">Rzutuje elementy kolekcji do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="9fa3e-125">Użyj jawnie wpisanej zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="9fa3e-126">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9fa3e-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="9fa3e-127">Oftype</span><span class="sxs-lookup"><span data-stu-id="9fa3e-127">OfType</span></span>|<span data-ttu-id="9fa3e-128">Filtruje wartości, w zależności od ich zdolności do rzutowania do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="9fa3e-129">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="9fa3e-130">Toarray</span><span class="sxs-lookup"><span data-stu-id="9fa3e-130">ToArray</span></span>|<span data-ttu-id="9fa3e-131">Konwertuje kolekcję na tablicę.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-131">Converts a collection to an array.</span></span> <span data-ttu-id="9fa3e-132">Ta metoda wymusza wykonanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-132">This method forces query execution.</span></span>|<span data-ttu-id="9fa3e-133">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="9fa3e-134">Todictionary</span><span class="sxs-lookup"><span data-stu-id="9fa3e-134">ToDictionary</span></span>|<span data-ttu-id="9fa3e-135">Umieszcza elementy <xref:System.Collections.Generic.Dictionary%602> w oparciu o funkcję selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="9fa3e-136">Ta metoda wymusza wykonanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-136">This method forces query execution.</span></span>|<span data-ttu-id="9fa3e-137">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="9fa3e-138">Tolist</span><span class="sxs-lookup"><span data-stu-id="9fa3e-138">ToList</span></span>|<span data-ttu-id="9fa3e-139">Konwertuje kolekcję na plik <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="9fa3e-140">Ta metoda wymusza wykonanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-140">This method forces query execution.</span></span>|<span data-ttu-id="9fa3e-141">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="9fa3e-142">Tolookup</span><span class="sxs-lookup"><span data-stu-id="9fa3e-142">ToLookup</span></span>|<span data-ttu-id="9fa3e-143">Umieszcza elementy <xref:System.Linq.Lookup%602> w słowniku (jeden-do-wielu) na podstawie funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="9fa3e-144">Ta metoda wymusza wykonanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-144">This method forces query execution.</span></span>|<span data-ttu-id="9fa3e-145">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="9fa3e-146">Przykład składni wyrażenia kwerendy</span><span class="sxs-lookup"><span data-stu-id="9fa3e-146">Query Expression Syntax Example</span></span>

<span data-ttu-id="9fa3e-147">Poniższy przykład kodu używa jawnie wpisane zmiennej zakresu do rzutowania typu do podtypu przed uzyskując dostęp do elementu członkowskiego, który jest dostępny tylko na podtyp.</span><span class="sxs-lookup"><span data-stu-id="9fa3e-147">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9fa3e-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fa3e-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9fa3e-149">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa3e-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="9fa3e-150">z klauzuli</span><span class="sxs-lookup"><span data-stu-id="9fa3e-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="9fa3e-151">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="9fa3e-151">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="9fa3e-152">Jak zapytanie ArrayList z LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa3e-152">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
