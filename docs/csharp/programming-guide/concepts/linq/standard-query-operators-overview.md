---
title: Omówienie standardowych operatorów zapytań (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 76c2c4684f33c3fb30748b5f08efd215548661ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167858"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="da89e-102">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="da89e-103">*Standardowe operatory zapytań* są metody, które tworzą wzorzec LINQ.</span><span class="sxs-lookup"><span data-stu-id="da89e-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="da89e-104">Większość z tych metod działa na sekwencje, gdzie sekwencja <xref:System.Collections.Generic.IEnumerable%601> jest obiektem, którego typ implementuje interfejs lub <xref:System.Linq.IQueryable%601> interfejs.</span><span class="sxs-lookup"><span data-stu-id="da89e-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="da89e-105">Standardowe operatory zapytań zapewniają możliwości zapytania, w tym filtrowanie, projekcję, agregację, sortowanie i inne.</span><span class="sxs-lookup"><span data-stu-id="da89e-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="da89e-106">Istnieją dwa zestawy operatorów standardowych zapytań LINQ, jeden, który działa na obiektach typu, <xref:System.Collections.Generic.IEnumerable%601> a drugi działa na obiektach typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="da89e-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="da89e-107">Metody, które tworzą każdy zestaw są <xref:System.Linq.Enumerable> statyczne <xref:System.Linq.Queryable> elementy członkowskie i klas, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="da89e-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="da89e-108">Są one zdefiniowane jako *metody rozszerzenia* typu, na których działają.</span><span class="sxs-lookup"><span data-stu-id="da89e-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="da89e-109">Oznacza to, że można je wywołać przy użyciu składni metody statycznej lub składni metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="da89e-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="da89e-110">Ponadto kilka standardowych metod operatorkwerendy działają na typach innych niż te oparte na <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="da89e-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="da89e-111">Typ <xref:System.Linq.Enumerable> definiuje dwie takie metody, które działają <xref:System.Collections.IEnumerable>na obiektach typu .</span><span class="sxs-lookup"><span data-stu-id="da89e-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="da89e-112">Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, pozwalają włączyć nieparametryzowane lub nieogólne, kolekcja, które mają być badane w wzorzec LINQ.</span><span class="sxs-lookup"><span data-stu-id="da89e-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="da89e-113">Robią to, tworząc silnie typizyszoną kolekcję obiektów.</span><span class="sxs-lookup"><span data-stu-id="da89e-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="da89e-114">Klasa <xref:System.Linq.Queryable> definiuje dwie podobne metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>i , które działają <xref:System.Linq.Queryable>na obiektach typu .</span><span class="sxs-lookup"><span data-stu-id="da89e-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="da89e-115">Operatory standardowych zapytań różnią się w czasie ich wykonywania, w zależności od tego, czy zwracają one wartość singleton lub sekwencji wartości.</span><span class="sxs-lookup"><span data-stu-id="da89e-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="da89e-116">Te metody, które zwracają wartość singleton <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Sum%2A>(na przykład i ) wykonać natychmiast.</span><span class="sxs-lookup"><span data-stu-id="da89e-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="da89e-117">Metody, które zwracają sekwencję odroczyć wykonanie kwerendy i zwrócić wyliczany obiekt.</span><span class="sxs-lookup"><span data-stu-id="da89e-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="da89e-118">W przypadku metod, które działają na kolekcje w pamięci, to <xref:System.Collections.Generic.IEnumerable%601>znaczy te metody, które rozszerzają , zwracany obiekt wyliczany przechwytuje argumenty, które zostały przekazane do metody.</span><span class="sxs-lookup"><span data-stu-id="da89e-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="da89e-119">Po wyliczeniu tego obiektu jest stosowana logika operatora kwerendy i zwracane są wyniki kwerendy.</span><span class="sxs-lookup"><span data-stu-id="da89e-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="da89e-120">Natomiast metody, które <xref:System.Linq.IQueryable%601> rozszerzają nie implementują żadnego zachowania zapytań, ale tworzą drzewo wyrażeń, które reprezentuje kwerendę do wykonania.</span><span class="sxs-lookup"><span data-stu-id="da89e-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="da89e-121">Przetwarzanie zapytań jest obsługiwane <xref:System.Linq.IQueryable%601> przez obiekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="da89e-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="da89e-122">Wywołania metod kwerendy można połączyć ze sobą w jedną kwerendę, co umożliwia kwerendy stają się arbitralnie złożone.</span><span class="sxs-lookup"><span data-stu-id="da89e-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="da89e-123">Poniższy przykład kodu pokazuje, jak standardowe operatory zapytań mogą służyć do uzyskiwania informacji o sekwencji.</span><span class="sxs-lookup"><span data-stu-id="da89e-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="da89e-124">Składnia wyrażenia kwerendy</span><span class="sxs-lookup"><span data-stu-id="da89e-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="da89e-125">Niektóre z najczęściej używanych standardowych operatorów zapytań mają dedykowaną składnię słów kluczowych języka Języka C# i Języka Visual Basic, która umożliwia wywoływanie ich jako część *wyrażenia* *zapytania.*</span><span class="sxs-lookup"><span data-stu-id="da89e-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="da89e-126">Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które mają dedykowane słowa kluczowe i odpowiadające im składnie, zobacz [Składnia wyrażeń zapytań dla standardowych operatorów zapytań (C#).](./query-expression-syntax-for-standard-query-operators.md)</span><span class="sxs-lookup"><span data-stu-id="da89e-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](./query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="da89e-127">Rozszerzanie standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="da89e-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="da89e-128">Zestaw standardowych operatorów zapytań można rozszerzyć, tworząc metody specyficzne dla domeny, które są odpowiednie dla domeny docelowej lub technologii.</span><span class="sxs-lookup"><span data-stu-id="da89e-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="da89e-129">Można również zastąpić standardowych operatorów zapytań z własnych implementacji, które zapewniają dodatkowe usługi, takie jak zdalnej oceny, tłumaczenia zapytań i optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="da89e-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="da89e-130">Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> przykład.</span><span class="sxs-lookup"><span data-stu-id="da89e-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="da89e-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="da89e-131">Related Sections</span></span>  
 <span data-ttu-id="da89e-132">Poniższe łącza prowadzą do tematów, które zawierają dodatkowe informacje na temat różnych standardowych operatorów zapytań na podstawie funkcji.</span><span class="sxs-lookup"><span data-stu-id="da89e-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="da89e-133">Sortowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-133">Sorting Data (C#)</span></span>](./sorting-data.md)  
  
 [<span data-ttu-id="da89e-134">Ustawianie operacji (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-134">Set Operations (C#)</span></span>](./set-operations.md)  
  
 [<span data-ttu-id="da89e-135">Filtrowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-135">Filtering Data (C#)</span></span>](./filtering-data.md)  
  
 [<span data-ttu-id="da89e-136">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-136">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)  
  
 [<span data-ttu-id="da89e-137">Operacje projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-137">Projection Operations (C#)</span></span>](./projection-operations.md)  
  
 [<span data-ttu-id="da89e-138">Partycjonowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-138">Partitioning Data (C#)</span></span>](./partitioning-data.md)  
  
 [<span data-ttu-id="da89e-139">Dołącz do operacji (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-139">Join Operations (C#)</span></span>](./join-operations.md)  
  
 [<span data-ttu-id="da89e-140">Grupowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-140">Grouping Data (C#)</span></span>](./grouping-data.md)  
  
 [<span data-ttu-id="da89e-141">Operacje wytwarzania (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-141">Generation Operations (C#)</span></span>](./generation-operations.md)  
  
 [<span data-ttu-id="da89e-142">Operacje równości (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-142">Equality Operations (C#)</span></span>](./equality-operations.md)  
  
 [<span data-ttu-id="da89e-143">Operacje elementów (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-143">Element Operations (C#)</span></span>](./element-operations.md)  
  
 [<span data-ttu-id="da89e-144">Konwertowanie typów danych (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-144">Converting Data Types (C#)</span></span>](./converting-data-types.md)  
  
 [<span data-ttu-id="da89e-145">Operacje łączenia (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-145">Concatenation Operations (C#)</span></span>](./concatenation-operations.md)  
  
 [<span data-ttu-id="da89e-146">Operacje agregacji (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-146">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="da89e-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da89e-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="da89e-148">Wprowadzenie do kwerend LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-148">Introduction to LINQ Queries (C#)</span></span>](./introduction-to-linq-queries.md)
- [<span data-ttu-id="da89e-149">Składnia wyrażenia kwerendy dla standardowych operatorów kwerend (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-149">Query Expression Syntax for Standard Query Operators (C#)</span></span>](./query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="da89e-150">Klasyfikacja standardowych operatorów zapytań według sposobu wykonania (C#)</span><span class="sxs-lookup"><span data-stu-id="da89e-150">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="da89e-151">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="da89e-151">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
