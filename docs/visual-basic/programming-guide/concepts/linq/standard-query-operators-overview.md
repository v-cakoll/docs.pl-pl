---
title: Standardowe operatory zapytań — Omówienie
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 7c229a576f6695282473352d6253d2c699c76604
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406784"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="c184c-102">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-102">Standard Query Operators Overview (Visual Basic)</span></span>

<span data-ttu-id="c184c-103">*Standardowe operatory zapytań* to metody, które tworzą wzorzec LINQ.</span><span class="sxs-lookup"><span data-stu-id="c184c-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="c184c-104">Większość z tych metod operuje na sekwencjach, gdzie sekwencja jest obiektem, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs lub <xref:System.Linq.IQueryable%601> interfejs.</span><span class="sxs-lookup"><span data-stu-id="c184c-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="c184c-105">Standardowe operatory zapytań zapewniają możliwości zapytań, w tym filtrowanie, projekcję, agregację, sortowanie i inne.</span><span class="sxs-lookup"><span data-stu-id="c184c-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>

<span data-ttu-id="c184c-106">Istnieją dwa zestawy operatorów standardowych zapytań LINQ, które działają na obiektach typu <xref:System.Collections.Generic.IEnumerable%601> i innych, które działają na obiektach typu <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="c184c-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="c184c-107">Metody, które składają się na każdy zestaw są statycznymi elementami członkowskimi <xref:System.Linq.Enumerable> <xref:System.Linq.Queryable> klas i, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c184c-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="c184c-108">Są one definiowane jako *metody rozszerzające* typ, na którym działają.</span><span class="sxs-lookup"><span data-stu-id="c184c-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="c184c-109">Oznacza to, że można je wywołać za pomocą składni metody statycznej lub składni metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c184c-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>

<span data-ttu-id="c184c-110">Ponadto kilka metod standardowego operatora zapytań działa na typach innych niż te oparte na <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="c184c-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="c184c-111"><xref:System.Linq.Enumerable>Typ definiuje dwie takie metody, które działają na obiektach typu <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="c184c-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="c184c-112">Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> umożliwiają włączenie kolekcji niesparametryzowanej lub nieogólnej, w której będą wysyłane zapytania we wzorcu LINQ.</span><span class="sxs-lookup"><span data-stu-id="c184c-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="c184c-113">W tym celu należy utworzyć kolekcję obiektów o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="c184c-113">They do this by creating a strongly typed collection of objects.</span></span> <span data-ttu-id="c184c-114"><xref:System.Linq.Queryable>Klasa definiuje dwie podobne metody, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> które działają na obiektach typu <xref:System.Linq.Queryable> .</span><span class="sxs-lookup"><span data-stu-id="c184c-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>

<span data-ttu-id="c184c-115">Standardowe operatory zapytań różnią się w czasie wykonywania, w zależności od tego, czy zwracają wartość singleton, czy sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="c184c-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="c184c-116">Metody, które zwracają pojedyncze wartości (na przykład <xref:System.Linq.Enumerable.Average%2A> i), <xref:System.Linq.Enumerable.Sum%2A> wykonują od razu.</span><span class="sxs-lookup"><span data-stu-id="c184c-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="c184c-117">Metody, które zwracają sekwencję, opóźniają wykonanie zapytania i zwracają wyliczalny obiekt.</span><span class="sxs-lookup"><span data-stu-id="c184c-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>

<span data-ttu-id="c184c-118">W przypadku metod, które działają na kolekcjach w pamięci, czyli te metody, które przechodzą <xref:System.Collections.Generic.IEnumerable%601> , zwracany wyliczalny obiekt przechwytuje argumenty, które zostały przekazane do metody.</span><span class="sxs-lookup"><span data-stu-id="c184c-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="c184c-119">Po wyliczeniu tego obiektu jest stosowana logika operatora zapytania, a wyniki zapytania są zwracane.</span><span class="sxs-lookup"><span data-stu-id="c184c-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>

<span data-ttu-id="c184c-120">W przeciwieństwie do metod, które zwiększają <xref:System.Linq.IQueryable%601> nie zaimplementować żadnego zachowania zapytania, ale kompiluje drzewo wyrażenia, które reprezentuje zapytanie, które ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="c184c-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="c184c-121">Przetwarzanie zapytania jest obsługiwane przez <xref:System.Linq.IQueryable%601> obiekt źródłowy.</span><span class="sxs-lookup"><span data-stu-id="c184c-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>

<span data-ttu-id="c184c-122">Wywołania metod zapytania można łączyć razem w jednym zapytaniu, co umożliwia zapełnienie zapytań.</span><span class="sxs-lookup"><span data-stu-id="c184c-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>

<span data-ttu-id="c184c-123">Poniższy przykład kodu demonstruje, jak standardowe operatory zapytań mogą służyć do uzyskiwania informacji o sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c184c-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>

```vb
Dim sentence = "the quick brown fox jumps over the lazy dog"
' Split the string into individual words to create a collection.
Dim words = sentence.Split(" "c)

Dim query = From word In words
            Group word.ToUpper() By word.Length Into gr = Group
            Order By Length _
            Select Length, GroupedWords = gr

Dim output As New System.Text.StringBuilder
For Each obj In query
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))
    For Each word As String In obj.GroupedWords
        output.AppendLine(word)
    Next
Next

'Display the output
MsgBox(output.ToString())

' This code example produces the following output:
'
' Words of length 3:
' THE
' FOX
' THE
' DOG
' Words of length 4:
' OVER
' LAZY
' Words of length 5:
' QUICK
' BROWN
' JUMPS
```

## <a name="query-expression-syntax"></a><span data-ttu-id="c184c-124">Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="c184c-124">Query Expression Syntax</span></span>

<span data-ttu-id="c184c-125">Niektóre z często używanych standardowych operatorów zapytań mają dedykowaną składnię słowa kluczowego języka C# i Visual Basic, która umożliwia ich wywoływanie jako część *query* *wyrażenia*zapytania.</span><span class="sxs-lookup"><span data-stu-id="c184c-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="c184c-126">Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które mają dedykowane słowa kluczowe i ich odpowiednie składnie, zobacz [składnia wyrażeń zapytania dla standardowych operatorów zapytań (Visual Basic)](query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c184c-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](query-expression-syntax-for-standard-query-operators.md).</span></span>

## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="c184c-127">Rozszerzanie standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="c184c-127">Extending the Standard Query Operators</span></span>

<span data-ttu-id="c184c-128">Zestaw standardowych operatorów zapytań można rozszerzyć przez utworzenie metod specyficznych dla domeny, które są odpowiednie dla domeny docelowej lub technologii.</span><span class="sxs-lookup"><span data-stu-id="c184c-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="c184c-129">Możesz również zastąpić standardowe operatory zapytań własnymi implementacjami, które zapewniają dodatkowe usługi, takie jak Ocena zdalna, tłumaczenie zapytań i optymalizacja.</span><span class="sxs-lookup"><span data-stu-id="c184c-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="c184c-130">Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> , aby zapoznać się z przykładem.</span><span class="sxs-lookup"><span data-stu-id="c184c-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c184c-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c184c-131">Related Sections</span></span>

<span data-ttu-id="c184c-132">Poniższe linki prowadzą do tematów, które dostarczają dodatkowych informacji na temat różnych standardowych operatorów zapytań opartych na funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="c184c-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>

- [<span data-ttu-id="c184c-133">Sortowanie danych</span><span class="sxs-lookup"><span data-stu-id="c184c-133">Sorting Data</span></span>](sorting-data.md)

- [<span data-ttu-id="c184c-134">Operacje Set (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-134">Set Operations (Visual Basic)</span></span>](set-operations.md)

- [<span data-ttu-id="c184c-135">Filtrowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-135">Filtering Data (Visual Basic)</span></span>](filtering-data.md)

- [<span data-ttu-id="c184c-136">Operacje kwantyfikatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-136">Quantifier Operations (Visual Basic)</span></span>](quantifier-operations.md)

- [<span data-ttu-id="c184c-137">Operacje projekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-137">Projection Operations (Visual Basic)</span></span>](projection-operations.md)

- [<span data-ttu-id="c184c-138">Partycjonowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-138">Partitioning Data (Visual Basic)</span></span>](partitioning-data.md)

- [<span data-ttu-id="c184c-139">Operacje join (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-139">Join Operations (Visual Basic)</span></span>](join-operations.md)

- [<span data-ttu-id="c184c-140">Grupowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-140">Grouping Data (Visual Basic)</span></span>](grouping-data.md)

- [<span data-ttu-id="c184c-141">Operacje generacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-141">Generation Operations (Visual Basic)</span></span>](generation-operations.md)

- [<span data-ttu-id="c184c-142">Operacje równości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-142">Equality Operations (Visual Basic)</span></span>](equality-operations.md)

- [<span data-ttu-id="c184c-143">Operacje elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-143">Element Operations (Visual Basic)</span></span>](element-operations.md)

- [<span data-ttu-id="c184c-144">Konwertowanie typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-144">Converting Data Types (Visual Basic)</span></span>](converting-data-types.md)

- [<span data-ttu-id="c184c-145">Operacje łączenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-145">Concatenation Operations (Visual Basic)</span></span>](concatenation-operations.md)

- [<span data-ttu-id="c184c-146">Operacje agregacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-146">Aggregation Operations (Visual Basic)</span></span>](aggregation-operations.md)

## <a name="see-also"></a><span data-ttu-id="c184c-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c184c-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="c184c-148">Wprowadzenie do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-148">Introduction to LINQ (Visual Basic)</span></span>](introduction-to-linq.md)
- [<span data-ttu-id="c184c-149">Składnia wyrażenia zapytania dla standardowych operatorów zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="c184c-150">Klasyfikacja standardowych operatorów zapytań według sposobu wykonywania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c184c-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="c184c-151">Metody rozszerzające</span><span class="sxs-lookup"><span data-stu-id="c184c-151">Extension Methods</span></span>](../../language-features/procedures/extension-methods.md)
