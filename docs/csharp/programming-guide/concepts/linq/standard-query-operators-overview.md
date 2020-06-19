---
title: Standardowe operatory zapytań — Omówienie (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 095a0b7a7a8265f235d28a4634ea82cdcd7a60c0
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990006"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="0c807-102">Standardowe operatory zapytań — Omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="0c807-103">*Standardowe operatory zapytań* to metody, które tworzą wzorzec LINQ.</span><span class="sxs-lookup"><span data-stu-id="0c807-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="0c807-104">Większość z tych metod operuje na sekwencjach, gdzie sekwencja jest obiektem, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs lub <xref:System.Linq.IQueryable%601> interfejs.</span><span class="sxs-lookup"><span data-stu-id="0c807-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="0c807-105">Standardowe operatory zapytań zapewniają możliwości zapytań, w tym filtrowanie, projekcję, agregację, sortowanie i inne.</span><span class="sxs-lookup"><span data-stu-id="0c807-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="0c807-106">Istnieją dwa zestawy operatorów standardowego zapytania LINQ: jeden, który działa na obiektach typu <xref:System.Collections.Generic.IEnumerable%601> , inny, który działa na obiektach typu <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="0c807-106">There are two sets of LINQ standard query operators: one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601>, another that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="0c807-107">Metody, które składają się na każdy zestaw są statycznymi elementami członkowskimi <xref:System.Linq.Enumerable> <xref:System.Linq.Queryable> klas i, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="0c807-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="0c807-108">Są one definiowane jako *metody rozszerzające* typ, na którym działają.</span><span class="sxs-lookup"><span data-stu-id="0c807-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="0c807-109">Metody rozszerzające można wywołać za pomocą składni metody statycznej lub składni metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0c807-109">Extension methods can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="0c807-110">Ponadto kilka metod standardowego operatora zapytań działa na typach innych niż te oparte na <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="0c807-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="0c807-111"><xref:System.Linq.Enumerable>Typ definiuje dwie takie metody, które działają na obiektach typu <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="0c807-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="0c807-112">Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> umożliwiają włączenie kolekcji niesparametryzowanej lub nieogólnej, w której będą wysyłane zapytania we wzorcu LINQ.</span><span class="sxs-lookup"><span data-stu-id="0c807-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="0c807-113">W tym celu należy utworzyć kolekcję obiektów o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="0c807-113">They do this by creating a strongly typed collection of objects.</span></span> <span data-ttu-id="0c807-114"><xref:System.Linq.Queryable>Klasa definiuje dwie podobne metody, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> które działają na obiektach typu <xref:System.Linq.Queryable> .</span><span class="sxs-lookup"><span data-stu-id="0c807-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="0c807-115">Standardowe operatory zapytań różnią się w czasie wykonywania, w zależności od tego, czy zwracają wartość singleton, czy sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="0c807-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="0c807-116">Metody, które zwracają pojedyncze wartości (na przykład <xref:System.Linq.Enumerable.Average%2A> i), <xref:System.Linq.Enumerable.Sum%2A> wykonują od razu.</span><span class="sxs-lookup"><span data-stu-id="0c807-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="0c807-117">Metody, które zwracają sekwencję, opóźniają wykonanie zapytania i zwracają wyliczalny obiekt.</span><span class="sxs-lookup"><span data-stu-id="0c807-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="0c807-118">W przypadku metod, które działają na kolekcjach w pamięci, czyli te metody, które przechodzą <xref:System.Collections.Generic.IEnumerable%601> , zwracany wyliczalny obiekt przechwytuje argumenty, które zostały przekazane do metody.</span><span class="sxs-lookup"><span data-stu-id="0c807-118">For methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="0c807-119">Po wyliczeniu tego obiektu jest stosowana logika operatora zapytania, a wyniki zapytania są zwracane.</span><span class="sxs-lookup"><span data-stu-id="0c807-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="0c807-120">W przeciwieństwie do metod, które rozszerzy <xref:System.Linq.IQueryable%601> nie implementują żadnego działania związanego z wykonywaniem zapytań.</span><span class="sxs-lookup"><span data-stu-id="0c807-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> don't implement any querying behavior.</span></span> <span data-ttu-id="0c807-121">Tworzą one drzewo wyrażenia, które reprezentuje zapytanie, które ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="0c807-121">They build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="0c807-122">Przetwarzanie zapytania jest obsługiwane przez <xref:System.Linq.IQueryable%601> obiekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="0c807-122">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="0c807-123">Wywołania metod zapytania można łączyć razem w jednym zapytaniu, co umożliwia zapełnienie zapytań.</span><span class="sxs-lookup"><span data-stu-id="0c807-123">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="0c807-124">Poniższy przykład kodu demonstruje, jak standardowe operatory zapytań mogą służyć do uzyskiwania informacji o sekwencji.</span><span class="sxs-lookup"><span data-stu-id="0c807-124">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="0c807-125">Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="0c807-125">Query Expression Syntax</span></span>  
 <span data-ttu-id="0c807-126">Niektóre z często używanych standardowych operatorów zapytań mają dedykowaną składnię słowa kluczowego języka C# i Visual Basic, która umożliwia ich wywoływanie jako część *query* *wyrażenia*zapytania.</span><span class="sxs-lookup"><span data-stu-id="0c807-126">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="0c807-127">Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które mają dedykowane słowa kluczowe i ich odpowiednie składnie, zobacz [składnia wyrażeń zapytania dla standardowych operatorów zapytań (C#)](./query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="0c807-127">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](./query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="0c807-128">Rozszerzanie standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="0c807-128">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="0c807-129">Zestaw standardowych operatorów zapytań można rozszerzyć przez utworzenie metod specyficznych dla domeny, które są odpowiednie dla domeny docelowej lub technologii.</span><span class="sxs-lookup"><span data-stu-id="0c807-129">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="0c807-130">Możesz również zastąpić standardowe operatory zapytań własnymi implementacjami, które zapewniają dodatkowe usługi, takie jak Ocena zdalna, tłumaczenie zapytań i optymalizacja.</span><span class="sxs-lookup"><span data-stu-id="0c807-130">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="0c807-131">Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> , aby zapoznać się z przykładem.</span><span class="sxs-lookup"><span data-stu-id="0c807-131">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0c807-132">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0c807-132">Related Sections</span></span>  
 <span data-ttu-id="0c807-133">Poniższe linki prowadzą do artykułów, które dostarczają dodatkowych informacji na temat różnych standardowych operatorów zapytań opartych na funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="0c807-133">The following links take you to articles that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="0c807-134">Sortowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-134">Sorting Data (C#)</span></span>](./sorting-data.md)  
  
 [<span data-ttu-id="0c807-135">Operacje Set (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-135">Set Operations (C#)</span></span>](./set-operations.md)  
  
 [<span data-ttu-id="0c807-136">Filtrowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-136">Filtering Data (C#)</span></span>](./filtering-data.md)  
  
 [<span data-ttu-id="0c807-137">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-137">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)  
  
 [<span data-ttu-id="0c807-138">Operacje projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-138">Projection Operations (C#)</span></span>](./projection-operations.md)  
  
 [<span data-ttu-id="0c807-139">Partycjonowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-139">Partitioning Data (C#)</span></span>](./partitioning-data.md)  
  
 [<span data-ttu-id="0c807-140">Operacje join (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-140">Join Operations (C#)</span></span>](./join-operations.md)  
  
 [<span data-ttu-id="0c807-141">Grupowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-141">Grouping Data (C#)</span></span>](./grouping-data.md)  
  
 [<span data-ttu-id="0c807-142">Operacje generacji (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-142">Generation Operations (C#)</span></span>](./generation-operations.md)  
  
 [<span data-ttu-id="0c807-143">Operacje równości (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-143">Equality Operations (C#)</span></span>](./equality-operations.md)  
  
 [<span data-ttu-id="0c807-144">Operacje na elementach (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-144">Element Operations (C#)</span></span>](./element-operations.md)  
  
 [<span data-ttu-id="0c807-145">Konwertowanie typów danych (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-145">Converting Data Types (C#)</span></span>](./converting-data-types.md)  
  
 [<span data-ttu-id="0c807-146">Operacje łączenia (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-146">Concatenation Operations (C#)</span></span>](./concatenation-operations.md)  
  
 [<span data-ttu-id="0c807-147">Operacje agregacji (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-147">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c807-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c807-148">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="0c807-149">Wprowadzenie do kwerend LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-149">Introduction to LINQ Queries (C#)</span></span>](./introduction-to-linq-queries.md)
- [<span data-ttu-id="0c807-150">Składnia wyrażenia zapytania dla standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-150">Query Expression Syntax for Standard Query Operators (C#)</span></span>](./query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="0c807-151">Klasyfikacja standardowych operatorów zapytań według sposobu wykonywania (C#)</span><span class="sxs-lookup"><span data-stu-id="0c807-151">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="0c807-152">Metody rozszerzania</span><span class="sxs-lookup"><span data-stu-id="0c807-152">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
