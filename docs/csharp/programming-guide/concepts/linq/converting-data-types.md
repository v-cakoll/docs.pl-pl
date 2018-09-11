---
title: Konwertowanie typów danych (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 54ef612ad4e92058d9af4d96b7b3cde9732b2f9c
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271078"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="3f94a-102">Konwertowanie typów danych (C#)</span><span class="sxs-lookup"><span data-stu-id="3f94a-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="3f94a-103">Metody konwersji zmienić typ danych wejściowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="3f94a-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="3f94a-104">Operacje konwersji w zapytaniach LINQ są przydatne w wielu różnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f94a-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="3f94a-105">Poniżej przedstawiono kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="3f94a-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="3f94a-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metoda może służyć do ukrywanie niestandardowych implementacji standardowego operatora zapytania typu.</span><span class="sxs-lookup"><span data-stu-id="3f94a-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="3f94a-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metoda może służyć do włączenia kolekcji zdefiniowanych na potrzeby zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="3f94a-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="3f94a-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, I <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody może służyć do wymuszenia wykonanie zapytania bezpośredniego zamiast odracza ją do czasu wyliczenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="3f94a-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f94a-109">Metody</span><span class="sxs-lookup"><span data-stu-id="3f94a-109">Methods</span></span>  
 <span data-ttu-id="3f94a-110">Poniższa tabela zawiera listę metod standardowych operatorów zapytań, które wykonują konwersje typów danych.</span><span class="sxs-lookup"><span data-stu-id="3f94a-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="3f94a-111">Metody konwersji w tej tabeli, których nazwy rozpoczynają się od "Jako" Zmiana typu statycznego kolekcji źródłowej, ale nie wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="3f94a-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="3f94a-112">Typ metody, których nazwy rozpoczynają się od "Do wyliczania kolekcji źródłowej i umieść elementy w odpowiedniej kolekcji".</span><span class="sxs-lookup"><span data-stu-id="3f94a-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="3f94a-113">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="3f94a-113">Method Name</span></span>|<span data-ttu-id="3f94a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3f94a-114">Description</span></span>|<span data-ttu-id="3f94a-115">Składnia wyrażeń zapytania języka C#</span><span class="sxs-lookup"><span data-stu-id="3f94a-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="3f94a-116">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="3f94a-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="3f94a-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="3f94a-117">AsEnumerable</span></span>|<span data-ttu-id="3f94a-118">Zwraca dane wejściowe wpisanych w formie <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="3f94a-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="3f94a-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3f94a-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3f94a-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="3f94a-120">AsQueryable</span></span>|<span data-ttu-id="3f94a-121">Konwertuje (ogólny) <xref:System.Collections.IEnumerable> do (ogólny) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="3f94a-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="3f94a-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3f94a-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3f94a-123">Rzutowanie</span><span class="sxs-lookup"><span data-stu-id="3f94a-123">Cast</span></span>|<span data-ttu-id="3f94a-124">Rzutuje elementy kolekcji do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="3f94a-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="3f94a-125">Można użyć zmiennej jawnie wpisanych zakresu.</span><span class="sxs-lookup"><span data-stu-id="3f94a-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="3f94a-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3f94a-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3f94a-127">OfType</span><span class="sxs-lookup"><span data-stu-id="3f94a-127">OfType</span></span>|<span data-ttu-id="3f94a-128">Służy do przefiltrowania wartości, w zależności od ich możliwości, można rzutować do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="3f94a-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="3f94a-129">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3f94a-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3f94a-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="3f94a-130">ToArray</span></span>|<span data-ttu-id="3f94a-131">Konwertuje kolekcję na tablicę.</span><span class="sxs-lookup"><span data-stu-id="3f94a-131">Converts a collection to an array.</span></span> <span data-ttu-id="3f94a-132">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="3f94a-132">This method forces query execution.</span></span>|<span data-ttu-id="3f94a-133">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3f94a-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3f94a-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="3f94a-134">ToDictionary</span></span>|<span data-ttu-id="3f94a-135">Umieszcza elementy do <xref:System.Collections.Generic.Dictionary%602> oparte na funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="3f94a-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="3f94a-136">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="3f94a-136">This method forces query execution.</span></span>|<span data-ttu-id="3f94a-137">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3f94a-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3f94a-138">Tolist —</span><span class="sxs-lookup"><span data-stu-id="3f94a-138">ToList</span></span>|<span data-ttu-id="3f94a-139">Konwertuje kolekcję do <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="3f94a-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="3f94a-140">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="3f94a-140">This method forces query execution.</span></span>|<span data-ttu-id="3f94a-141">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3f94a-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3f94a-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="3f94a-142">ToLookup</span></span>|<span data-ttu-id="3f94a-143">Umieszcza elementy do <xref:System.Linq.Lookup%602> (Słownik jeden do wielu) na podstawie selektora kluczy funkcji.</span><span class="sxs-lookup"><span data-stu-id="3f94a-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="3f94a-144">Ta metoda wymusza wykonanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="3f94a-144">This method forces query execution.</span></span>|<span data-ttu-id="3f94a-145">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3f94a-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="3f94a-146">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="3f94a-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="3f94a-147">Poniższy przykład kodu używa zmiennej zakresu jawnie wpisane rzutowanie typu podtypem przed uzyskaniem dostępu do składowej, która jest dostępna tylko na podtypu.</span><span class="sxs-lookup"><span data-stu-id="3f94a-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f94a-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f94a-148">See Also</span></span>

- <xref:System.Linq>  
- [<span data-ttu-id="3f94a-149">Omówienie operatorów standardowej kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="3f94a-149">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [<span data-ttu-id="3f94a-150">from, klauzula</span><span class="sxs-lookup"><span data-stu-id="3f94a-150">from clause</span></span>](../../../../csharp/language-reference/keywords/from-clause.md)  
- [<span data-ttu-id="3f94a-151">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="3f94a-151">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="3f94a-152">Porady: zapytanie w ArrayList za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="3f94a-152">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
