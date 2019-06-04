---
title: Omówienie operatorów standardowej kwerendy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 9bfdf2163be52d9016a800d65006bbc4fbf560a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908144"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="0f080-102">Omówienie operatorów standardowej kwerendy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-102">Standard Query Operators Overview (Visual Basic)</span></span>
<span data-ttu-id="0f080-103">*Standardowych operatorów zapytań* metod, które tworzą wzorzec LINQ.</span><span class="sxs-lookup"><span data-stu-id="0f080-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="0f080-104">Większość z tych metod działają na sekwencje, gdzie sekwencji jest obiektem, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub <xref:System.Linq.IQueryable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0f080-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="0f080-105">Standardowe operatory zapytań zapewniają możliwości zapytania, takie jak filtrowanie, projekcji, agregacji, sortowania i innych.</span><span class="sxs-lookup"><span data-stu-id="0f080-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="0f080-106">Istnieją dwa zestawy LINQ standardowych operatorów zapytań, który działa na obiekty typu <xref:System.Collections.Generic.IEnumerable%601> i inne, która operuje na obiekty typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="0f080-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="0f080-107">Metody, które tworzą każdego zestawu są statyczne elementy członkowskie <xref:System.Linq.Enumerable> i <xref:System.Linq.Queryable> klasy, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="0f080-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="0f080-108">Są one definiowane jako *metody rozszerzenia* typu, które działają na.</span><span class="sxs-lookup"><span data-stu-id="0f080-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="0f080-109">Oznacza to, że może być wywoływana przy użyciu składni metody statyczne lub składni metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0f080-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="0f080-110">Ponadto kilka metod standardowych operatorów zapytań działać dla typów innych niż te, na podstawie <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="0f080-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="0f080-111"><xref:System.Linq.Enumerable> Typ definiuje dwa takie metody że działają zarówno w obiektach typu <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="0f080-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="0f080-112">Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>systemowi włączysz bez parametrów lub inną niż ogólna kolekcję we wzorcu LINQ.</span><span class="sxs-lookup"><span data-stu-id="0f080-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="0f080-113">Mogą to zrobić, tworząc silnie typizowaną kolekcją obiektów.</span><span class="sxs-lookup"><span data-stu-id="0f080-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="0f080-114"><xref:System.Linq.Queryable> Klasa definiuje dwie podobne metody, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> i <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, które działają na obiektach typu <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="0f080-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="0f080-115">Standardowe operatory zapytań różnią się w odniesieniu do momentu ich wykonania, w zależności od tego, czy zwracać wartości pojedynczego wystąpienia lub je sekvence hodnot.</span><span class="sxs-lookup"><span data-stu-id="0f080-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="0f080-116">Te metody, które zwracają wartości pojedynczego wystąpienia (na przykład <xref:System.Linq.Enumerable.Average%2A> i <xref:System.Linq.Enumerable.Sum%2A>) od razu.</span><span class="sxs-lookup"><span data-stu-id="0f080-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="0f080-117">Metody, które zwracają sekwencji odroczone do wykonywania zapytania i zwraca obiekt wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="0f080-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="0f080-118">W przypadku metod, które pracują na kolekcji w pamięci, oznacza to, że te metody, które rozszerzają <xref:System.Collections.Generic.IEnumerable%601>, zwracany obiekt wyliczalny przechwytuje argumenty, które zostały przekazane do metody.</span><span class="sxs-lookup"><span data-stu-id="0f080-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="0f080-119">Gdy ten obiekt jest zostanie wyliczonly, logika — operator zapytań są stosowane, a wyniki zapytania są zwracane.</span><span class="sxs-lookup"><span data-stu-id="0f080-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="0f080-120">Z kolei metody które rozszerzają <xref:System.Linq.IQueryable%601> nie implementuje żadnych zapytań zachowania, ale tworzenie drzewo wyrażenia, które reprezentuje zapytanie, które mają zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="0f080-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="0f080-121">Przetwarzanie zapytań odbywa się przez źródło <xref:System.Linq.IQueryable%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0f080-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="0f080-122">Wywołania do metody zapytania można łączyć w łańcuch w jednym zapytaniu, co umożliwia zapytania, aby stać się dowolnie złożone.</span><span class="sxs-lookup"><span data-stu-id="0f080-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="0f080-123">Poniższy przykład kodu pokazuje, jak standardowe operatory zapytań może służyć do uzyskiwania informacji na temat sekwencji.</span><span class="sxs-lookup"><span data-stu-id="0f080-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="0f080-124">Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="0f080-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="0f080-125">Niektóre z często używanych standardowych operatorów zapytań są wyposażone w dedykowane języka C# i Visual Basic składni — słowo kluczowe języka, który pozwoli na można wywołać w ramach *zapytania* *wyrażenie*.</span><span class="sxs-lookup"><span data-stu-id="0f080-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="0f080-126">Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które są wyposażone w dedykowane słów kluczowych i ich odpowiedniej składni zobacz [składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="0f080-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="0f080-127">Rozszerzenie standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="0f080-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="0f080-128">Zbiór standardowych operatorów zapytań można rozszerzyć, aby utworzyć metody specyficznego dla domeny, które są odpowiednie dla Twojej domeny docelowej lub technologii.</span><span class="sxs-lookup"><span data-stu-id="0f080-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="0f080-129">Możesz również zastąpić standardowych operatorów zapytań Twojej własnej implementacji, które zapewnia dodatkowe usługi, takie jak zdalne oceny, translacji zapytania i optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="0f080-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="0f080-130">Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> przykład.</span><span class="sxs-lookup"><span data-stu-id="0f080-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0f080-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0f080-131">Related Sections</span></span>  
 <span data-ttu-id="0f080-132">Poniższe łącza prowadzą do tematów, które zapewniają dodatkowe informacje na temat różnych standardowych operatorów zapytań w oparciu o funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="0f080-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="0f080-133">Sortowanie danych</span><span class="sxs-lookup"><span data-stu-id="0f080-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="0f080-134">Operacje na zestawie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="0f080-135">Filtrowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="0f080-136">Operacje kwantyfikatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="0f080-137">Operacje rzutowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="0f080-138">Partycjonowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="0f080-139">Dołącz do operacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="0f080-140">Grupowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="0f080-141">Operacje generowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="0f080-142">Operacje równości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="0f080-143">Operacje na elementach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="0f080-144">Konwertowanie typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="0f080-145">Operacje łączenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="0f080-146">Operacje agregacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="0f080-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f080-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="0f080-148">Wprowadzenie do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-148">Introduction to LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="0f080-149">Składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="0f080-150">Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f080-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="0f080-151">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="0f080-151">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
