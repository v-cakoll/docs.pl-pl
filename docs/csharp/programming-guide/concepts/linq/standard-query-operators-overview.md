---
title: Operatory standardowe zapytań — omówienie (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 36bd5927e64ffacb97beac28b8e7790204e08c5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337327"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="a6e2e-102">Operatory standardowe zapytań — omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="a6e2e-103">*Standardowych operatorów zapytań* metod, które tworzą wzorzec LINQ.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="a6e2e-104">Większość tych metod działają w sekwencji, w którym sekwencja jest obiekt, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub <xref:System.Linq.IQueryable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="a6e2e-105">Standardowe operatory zapytań zapewniają możliwość wykonywania kwerend włącznie z filtrowaniem projekcji, agregacji, sortowania i inne.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="a6e2e-106">Istnieją dwa zestawy LINQ standardowych operatorów zapytań, który działa na obiektach typu <xref:System.Collections.Generic.IEnumerable%601> i inne, który działa na obiektach typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="a6e2e-107">Statyczne elementy członkowskie są metody, wchodzące w skład każdego zestawu <xref:System.Linq.Enumerable> i <xref:System.Linq.Queryable> klasy odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="a6e2e-108">Są one zdefiniowane jako *metody rozszerzenia* typu, które działają na.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="a6e2e-109">Oznacza to, że może być wywoływana za pomocą składni metody statycznej lub składnia metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="a6e2e-110">Ponadto kilka metod operator zapytania standardowe działania dla typów innych niż te, na podstawie <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="a6e2e-111"><xref:System.Linq.Enumerable> Typ definiuje dwie metody takie że działają zarówno na obiektach typu <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="a6e2e-112">Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, pozwalają włączyć bez parametrów lub inny niż ogólny kolekcji w wzorcu LINQ.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="a6e2e-113">Do tworzenia kolekcji silnie typizowanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="a6e2e-114"><xref:System.Linq.Queryable> Klasy definiuje dwie metody podobne, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> i <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, które działają na obiektach typu <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="a6e2e-115">Standardowe operatory zapytań różnią się czas ich działania, w zależności od tego, czy zwracać wartość pojedynczą lub sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="a6e2e-116">Te metody, które zwracają wartości pojedynczego wystąpienia (na przykład <xref:System.Linq.Enumerable.Average%2A> i <xref:System.Linq.Enumerable.Sum%2A>) wykonaj natychmiast.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="a6e2e-117">Metody zwracające sekwencję wstrzymuje wykonywanie zapytania i zwracać obiekt wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="a6e2e-118">W przypadku metod, które pracują na kolekcje w pamięci, czyli tych metod, które rozszerzają <xref:System.Collections.Generic.IEnumerable%601>, zwrócony obiekt wyliczalny przechwytuje argumenty, które zostały przekazane do metody.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="a6e2e-119">Po wyliczeniu tego obiektu jest zastosować logiki — operator zapytań i są zwracane wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="a6e2e-120">Z kolei metody który rozszerzyć <xref:System.Linq.IQueryable%601> nie implementuje wszystkie zachowania podczas badania, ale kompilacji drzewo wyrażenia, które reprezentuje zapytanie do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="a6e2e-121">Przetwarzanie zapytania jest obsługiwane przez źródło <xref:System.Linq.IQueryable%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="a6e2e-122">Wywołania metod zapytania można połączyć ze sobą w jednym zapytaniu, dzięki czemu staną się arbitralnie złożonych zapytań.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="a6e2e-123">W poniższym przykładzie kodu pokazano, jak standardowe operatory kwerend może służyć do uzyskiwania informacji o sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="a6e2e-124">Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="a6e2e-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="a6e2e-125">Niektóre z często używanych standardowych operatorów zapytań są wyposażone w dedykowane C# i Visual Basic składni słowa kluczowego języka, umożliwiający ich można wywołać w ramach *zapytania* *wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="a6e2e-126">Aby uzyskać więcej informacji o standardowych operatorów zapytań, które są wyposażone w dedykowane słów kluczowych i ich odpowiedniej składni, zobacz [składnia wyrażeń dla standardowych operatorów zapytań (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a6e2e-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="a6e2e-127">Rozszerzenie standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="a6e2e-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="a6e2e-128">Zbiór standardowych operatorów zapytań można rozszerzyć, aby tworzenie metod specyficznego dla domeny, które są odpowiednie dla Twojej domeny docelowej lub technologii.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="a6e2e-129">Standardowe operatory zapytań można także zastąpić własne implementacje, które udostępniają dodatkowe usługi, takie jak zdalne oceny, translacja zapytania i optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="a6e2e-130">Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> przykład.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a6e2e-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a6e2e-131">Related Sections</span></span>  
 <span data-ttu-id="a6e2e-132">Poniższe łącza prowadzą do tematów zawierających dodatkowe informacje na temat różnych standardowych operatorów zapytań w oparciu o funkcje.</span><span class="sxs-lookup"><span data-stu-id="a6e2e-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="a6e2e-133">Sortowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-133">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="a6e2e-134">Operacje na zestawie (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-134">Set Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="a6e2e-135">Filtrowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-135">Filtering Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="a6e2e-136">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-136">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="a6e2e-137">Operacje rzutowania (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-137">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="a6e2e-138">Partycjonowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-138">Partitioning Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="a6e2e-139">Dołącz do operacji (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-139">Join Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="a6e2e-140">Grupowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-140">Grouping Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="a6e2e-141">Operacje generowania (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-141">Generation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="a6e2e-142">Operacje równości (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-142">Equality Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="a6e2e-143">Operacje na elementach (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-143">Element Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="a6e2e-144">Konwertowanie typów danych (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-144">Converting Data Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="a6e2e-145">Operacje łączenia (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-145">Concatenation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="a6e2e-146">Operacje agregacji (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-146">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="a6e2e-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6e2e-147">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [<span data-ttu-id="a6e2e-148">Wprowadzenie do kwerend LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-148">Introduction to LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [<span data-ttu-id="a6e2e-149">Składnia wyrażeń dla standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-149">Query Expression Syntax for Standard Query Operators (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [<span data-ttu-id="a6e2e-150">Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (C#)</span><span class="sxs-lookup"><span data-stu-id="a6e2e-150">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [<span data-ttu-id="a6e2e-151">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="a6e2e-151">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
