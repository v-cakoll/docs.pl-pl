---
title: Standardowe operatory zapytań — Omówienie (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 22ae1f89379deff0436177d792382c434348b2d4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524026"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="31012-102">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-102">Standard Query Operators Overview (Visual Basic)</span></span>

<span data-ttu-id="31012-103">*Standardowe operatory zapytań* to metody, które tworzą wzorzec LINQ.</span><span class="sxs-lookup"><span data-stu-id="31012-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="31012-104">Większość z tych metod operuje na sekwencjach, gdzie sekwencja jest obiektem, którego typ implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601> lub interfejs <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="31012-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="31012-105">Standardowe operatory zapytań zapewniają możliwości zapytań, w tym filtrowanie, projekcję, agregację, sortowanie i inne.</span><span class="sxs-lookup"><span data-stu-id="31012-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>

<span data-ttu-id="31012-106">Istnieją dwa zestawy standardowych operatorów zapytań LINQ, które działają na obiektach typu <xref:System.Collections.Generic.IEnumerable%601> i innych, które działają na obiektach typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="31012-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="31012-107">Metody, które tworzą każdy zestaw są statycznymi elementami członkowskimi klas <xref:System.Linq.Enumerable> i <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="31012-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="31012-108">Są one definiowane jako *metody rozszerzające* typ, na którym działają.</span><span class="sxs-lookup"><span data-stu-id="31012-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="31012-109">Oznacza to, że można je wywołać za pomocą składni metody statycznej lub składni metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="31012-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>

<span data-ttu-id="31012-110">Ponadto kilka metod standardowego operatora zapytań działa na typach innych niż te oparte na <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="31012-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="31012-111">Typ <xref:System.Linq.Enumerable> definiuje dwie takie metody, które działają na obiektach typu <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="31012-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="31012-112">Te metody, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, umożliwiają włączenie kolekcji niesparametryzowanej lub nieogólnej, w której będą wysyłane zapytania we wzorcu LINQ.</span><span class="sxs-lookup"><span data-stu-id="31012-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="31012-113">W tym celu należy utworzyć kolekcję obiektów o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="31012-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="31012-114">Klasa <xref:System.Linq.Queryable> definiuje dwie podobne metody, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> i <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, które działają na obiektach typu <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="31012-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>

<span data-ttu-id="31012-115">Standardowe operatory zapytań różnią się w czasie wykonywania, w zależności od tego, czy zwracają wartość singleton, czy sekwencję wartości.</span><span class="sxs-lookup"><span data-stu-id="31012-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="31012-116">Metody, które zwracają pojedyncze wartości (na przykład <xref:System.Linq.Enumerable.Average%2A> i <xref:System.Linq.Enumerable.Sum%2A>), są wykonywane natychmiastowo.</span><span class="sxs-lookup"><span data-stu-id="31012-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="31012-117">Metody, które zwracają sekwencję, opóźniają wykonanie zapytania i zwracają wyliczalny obiekt.</span><span class="sxs-lookup"><span data-stu-id="31012-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>

<span data-ttu-id="31012-118">W przypadku metod, które działają na kolekcjach w pamięci, czyli te metody, które zwiększają <xref:System.Collections.Generic.IEnumerable%601>, zwracany wyliczalny obiekt przechwytuje argumenty, które zostały przekazane do metody.</span><span class="sxs-lookup"><span data-stu-id="31012-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="31012-119">Po wyliczeniu tego obiektu jest stosowana logika operatora zapytania, a wyniki zapytania są zwracane.</span><span class="sxs-lookup"><span data-stu-id="31012-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>

<span data-ttu-id="31012-120">W przeciwieństwie do metod, które zwiększają <xref:System.Linq.IQueryable%601> nie implementuje żadnego zachowania zapytania, ale kompiluje drzewo wyrażenia, które reprezentuje zapytanie, które ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="31012-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="31012-121">Przetwarzanie zapytania jest obsługiwane przez obiekt źródłowy <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="31012-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>

<span data-ttu-id="31012-122">Wywołania metod zapytania można łączyć razem w jednym zapytaniu, co umożliwia zapełnienie zapytań.</span><span class="sxs-lookup"><span data-stu-id="31012-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>

<span data-ttu-id="31012-123">Poniższy przykład kodu demonstruje, jak standardowe operatory zapytań mogą służyć do uzyskiwania informacji o sekwencji.</span><span class="sxs-lookup"><span data-stu-id="31012-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>

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

## <a name="query-expression-syntax"></a><span data-ttu-id="31012-124">Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="31012-124">Query Expression Syntax</span></span>

<span data-ttu-id="31012-125">Niektóre często używane standardowe operatory zapytań mają dedykowaną C# składnię słowa kluczowego i Visual Basic języka, która umożliwia ich wywoływanie jako część *wyrażenia* *zapytania* .</span><span class="sxs-lookup"><span data-stu-id="31012-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="31012-126">Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które mają dedykowane słowa kluczowe i ich odpowiednie składnie, zobacz [składnia wyrażeń zapytania dla standardowych operatorów zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="31012-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>

## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="31012-127">Rozszerzanie standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="31012-127">Extending the Standard Query Operators</span></span>

<span data-ttu-id="31012-128">Zestaw standardowych operatorów zapytań można rozszerzyć przez utworzenie metod specyficznych dla domeny, które są odpowiednie dla domeny docelowej lub technologii.</span><span class="sxs-lookup"><span data-stu-id="31012-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="31012-129">Możesz również zastąpić standardowe operatory zapytań własnymi implementacjami, które zapewniają dodatkowe usługi, takie jak Ocena zdalna, tłumaczenie zapytań i optymalizacja.</span><span class="sxs-lookup"><span data-stu-id="31012-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="31012-130">Zapoznaj się z przykładem <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="31012-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>

## <a name="related-sections"></a><span data-ttu-id="31012-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="31012-131">Related Sections</span></span>

<span data-ttu-id="31012-132">Poniższe linki prowadzą do tematów, które dostarczają dodatkowych informacji na temat różnych standardowych operatorów zapytań opartych na funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="31012-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>

- [<span data-ttu-id="31012-133">Sortowanie danych</span><span class="sxs-lookup"><span data-stu-id="31012-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)

- [<span data-ttu-id="31012-134">Operacje Set (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)

- [<span data-ttu-id="31012-135">Filtrowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)

- [<span data-ttu-id="31012-136">Operacje kwantyfikatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)

- [<span data-ttu-id="31012-137">Operacje projekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)

- [<span data-ttu-id="31012-138">Partycjonowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)

- [<span data-ttu-id="31012-139">Operacje join (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)

- [<span data-ttu-id="31012-140">Grupowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)

- [<span data-ttu-id="31012-141">Operacje generacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)

- [<span data-ttu-id="31012-142">Operacje równości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)

- [<span data-ttu-id="31012-143">Operacje elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)

- [<span data-ttu-id="31012-144">Konwertowanie typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)

- [<span data-ttu-id="31012-145">Operacje łączenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)

- [<span data-ttu-id="31012-146">Operacje agregacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)

## <a name="see-also"></a><span data-ttu-id="31012-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31012-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="31012-148">Wprowadzenie do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-148">Introduction to LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="31012-149">Składnia wyrażenia zapytania dla standardowych operatorów zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="31012-150">Klasyfikacja standardowych operatorów zapytań według sposobu wykonywania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31012-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="31012-151">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="31012-151">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
