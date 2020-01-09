---
title: Podstawowe operacje zapytań LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: 91c038303c1ad7c2530964d3102aae49090c4c2a
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635941"
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="5664d-102">Podstawowe operacje zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="5664d-102">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="5664d-103">Ten temat zawiera krótkie wprowadzenie do wyrażeń zapytań LINQ i niektórych typowych rodzajów operacji wykonywanych w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="5664d-103">This topic gives a brief introduction to LINQ query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="5664d-104">Bardziej szczegółowe informacje znajdują się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="5664d-104">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="5664d-105">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="5664d-105">LINQ Query Expressions</span></span>](../../../linq/index.md)  
  
 [<span data-ttu-id="5664d-106">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="5664d-106">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)  
  
 [<span data-ttu-id="5664d-107">Przewodnik: Pisanie zapytań wC#</span><span class="sxs-lookup"><span data-stu-id="5664d-107">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> <span data-ttu-id="5664d-108">Jeśli znasz już język zapytań, taki jak SQL lub XQuery, możesz pominąć większość tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5664d-108">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="5664d-109">Przeczytaj temat "`from` klauzula" w następnej sekcji, aby dowiedzieć się więcej o porządku klauzul w wyrażeniach zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="5664d-109">Read about the "`from` clause" in the next section to learn about the order of clauses in LINQ query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="5664d-110">Uzyskanie źródła danych</span><span class="sxs-lookup"><span data-stu-id="5664d-110">Obtaining a Data Source</span></span>  
 <span data-ttu-id="5664d-111">W zapytaniu LINQ pierwszym krokiem jest określenie źródła danych.</span><span class="sxs-lookup"><span data-stu-id="5664d-111">In a LINQ query, the first step is to specify the data source.</span></span> <span data-ttu-id="5664d-112">W C# przypadku większości języków programowania zmienna musi być zadeklarowana, zanim będzie mogła zostać użyta.</span><span class="sxs-lookup"><span data-stu-id="5664d-112">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="5664d-113">W zapytaniu LINQ klauzula `from` jest najpierw w celu wprowadzenia źródła danych (`customers`) i *zmiennej zakresu* (`cust`).</span><span class="sxs-lookup"><span data-stu-id="5664d-113">In a LINQ query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 <span data-ttu-id="5664d-114">Zmienna zakresu jest jak Zmienna iteracji w pętli `foreach`, z wyjątkiem braku rzeczywistej iteracji w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="5664d-114">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="5664d-115">Gdy zapytanie zostanie wykonane, zmienna zakresu będzie traktować jako odwołanie do każdego kolejnego elementu w `customers`.</span><span class="sxs-lookup"><span data-stu-id="5664d-115">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="5664d-116">Ponieważ kompilator może wywnioskować typ `cust`, nie trzeba określać go jawnie.</span><span class="sxs-lookup"><span data-stu-id="5664d-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="5664d-117">Dodatkowe zmienne zakresowe mogą być wprowadzane przez klauzulę `let`.</span><span class="sxs-lookup"><span data-stu-id="5664d-117">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="5664d-118">Aby uzyskać więcej informacji, zobacz [klauzula Let](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5664d-118">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5664d-119">W przypadku nieogólnych źródeł danych, takich jak <xref:System.Collections.ArrayList>, zmienna zakresu musi być jawnie wpisana.</span><span class="sxs-lookup"><span data-stu-id="5664d-119">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="5664d-120">Aby uzyskać więcej informacji, zobacz [How to Query an ArrayList with LINQC#()](./how-to-query-an-arraylist-with-linq.md) i [from](../../../language-reference/keywords/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5664d-120">For more information, see [How to query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) and [from clause](../../../language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="5664d-121">Filtrowanie</span><span class="sxs-lookup"><span data-stu-id="5664d-121">Filtering</span></span>  
 <span data-ttu-id="5664d-122">Prawdopodobnie najbardziej typową operacją zapytania jest stosowanie filtru w postaci wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="5664d-122">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="5664d-123">Filtr powoduje, że zapytanie zwraca tylko te elementy, dla których wyrażenie ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="5664d-123">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="5664d-124">Wynik jest tworzony przy użyciu klauzuli `where`.</span><span class="sxs-lookup"><span data-stu-id="5664d-124">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="5664d-125">Filtr w efekcie określa elementy, które mają zostać wykluczone z sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="5664d-125">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="5664d-126">W poniższym przykładzie zwracane są tylko te `customers`, które mają adres w Londynie.</span><span class="sxs-lookup"><span data-stu-id="5664d-126">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 <span data-ttu-id="5664d-127">Możesz użyć znanych C# operatorów logicznych `AND` i `OR`, aby zastosować dowolną liczbę wyrażeń filtrów w klauzuli `where`.</span><span class="sxs-lookup"><span data-stu-id="5664d-127">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="5664d-128">Aby na przykład zwrócić tylko klientów z "Londyn" `AND`, których nazwa to "Devon", należy napisać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="5664d-128">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 <span data-ttu-id="5664d-129">Aby zwrócić klientów z Londyn lub Paryż, Napisz następujący kod:</span><span class="sxs-lookup"><span data-stu-id="5664d-129">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 <span data-ttu-id="5664d-130">Aby uzyskać więcej informacji, zobacz [klauzula WHERE](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5664d-130">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="5664d-131">Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="5664d-131">Ordering</span></span>  
 <span data-ttu-id="5664d-132">Często wygodnie jest posortować zwrócone dane.</span><span class="sxs-lookup"><span data-stu-id="5664d-132">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="5664d-133">Klauzula `orderby` powoduje, że elementy w zwracanej sekwencji będą sortowane zgodnie z domyślną wartością porównującą dla sortowanego typu.</span><span class="sxs-lookup"><span data-stu-id="5664d-133">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="5664d-134">Na przykład następujące zapytanie można rozszerzyć, aby posortować wyniki na podstawie właściwości `Name`.</span><span class="sxs-lookup"><span data-stu-id="5664d-134">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="5664d-135">Ponieważ `Name` jest ciągiem, domyślna funkcja porównująca wykonuje sortowanie alfabetyczne od A do Z.</span><span class="sxs-lookup"><span data-stu-id="5664d-135">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 <span data-ttu-id="5664d-136">Aby zamówić wyniki w odwrotnej kolejności, od z do A, użyj klauzuli `orderby…descending`.</span><span class="sxs-lookup"><span data-stu-id="5664d-136">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="5664d-137">Aby uzyskać więcej informacji, zobacz [klauzula OrderBy](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5664d-137">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="5664d-138">Grupowanie</span><span class="sxs-lookup"><span data-stu-id="5664d-138">Grouping</span></span>  
 <span data-ttu-id="5664d-139">Klauzula `group` pozwala grupować wyniki na podstawie określonego klucza.</span><span class="sxs-lookup"><span data-stu-id="5664d-139">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="5664d-140">Można na przykład określić, że wyniki mają być pogrupowane według `City` tak, że wszyscy klienci z Londyn lub Paryż są w poszczególnych grupach.</span><span class="sxs-lookup"><span data-stu-id="5664d-140">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="5664d-141">W tym przypadku `cust.City` jest kluczem.</span><span class="sxs-lookup"><span data-stu-id="5664d-141">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 <span data-ttu-id="5664d-142">Po zakończeniu zapytania z klauzulą `group`, wyniki mają postać listy list.</span><span class="sxs-lookup"><span data-stu-id="5664d-142">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="5664d-143">Każdy element na liście jest obiektem, który ma `Key` składową i listę elementów, które są zgrupowane w tym kluczu.</span><span class="sxs-lookup"><span data-stu-id="5664d-143">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="5664d-144">Podczas iteracji w zapytaniu, które tworzy sekwencję grup, należy użyć zagnieżdżonej pętli `foreach`.</span><span class="sxs-lookup"><span data-stu-id="5664d-144">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="5664d-145">Pętla zewnętrzna wykonuje iterację dla każdej grupy, a pętla wewnętrzna wykonuje iterację dla wszystkich członków grupy.</span><span class="sxs-lookup"><span data-stu-id="5664d-145">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="5664d-146">Jeśli musisz odwołać się do wyników operacji grupy, możesz użyć słowa kluczowego `into`, aby utworzyć identyfikator, który może być przeszukiwany w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="5664d-146">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="5664d-147">Następujące zapytanie zwraca tylko te grupy, które zawierają więcej niż dwóch klientów:</span><span class="sxs-lookup"><span data-stu-id="5664d-147">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 <span data-ttu-id="5664d-148">Aby uzyskać więcej informacji, zobacz artykuł [kluzula group](../../../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5664d-148">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="5664d-149">Łączenie</span><span class="sxs-lookup"><span data-stu-id="5664d-149">Joining</span></span>  
 <span data-ttu-id="5664d-150">Operacje Join tworzą skojarzenia między sekwencjami, które nie są jawnie modelowane w źródłach danych.</span><span class="sxs-lookup"><span data-stu-id="5664d-150">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="5664d-151">Na przykład możesz wykonać sprzężenie, aby znaleźć wszystkich klientów i dystrybutorów, którzy mają tę samą lokalizację.</span><span class="sxs-lookup"><span data-stu-id="5664d-151">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="5664d-152">W LINQ klauzula `join` zawsze działa w odniesieniu do kolekcji obiektów, a nie bezpośrednio w tabelach bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5664d-152">In LINQ the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 <span data-ttu-id="5664d-153">W LINQ nie trzeba używać `join` tak często, jak w przypadku bazy danych SQL, ponieważ klucze obce w LINQ są reprezentowane w modelu obiektów jako właściwości, które przechowują kolekcję elementów.</span><span class="sxs-lookup"><span data-stu-id="5664d-153">In LINQ, you do not have to use `join` as often as you do in SQL, because foreign keys in LINQ are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="5664d-154">Na przykład obiekt `Customer` zawiera kolekcję obiektów `Order`.</span><span class="sxs-lookup"><span data-stu-id="5664d-154">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="5664d-155">Zamiast wykonywać sprzężenie, uzyskujesz dostęp do zamówień przy użyciu notacji kropkowej:</span><span class="sxs-lookup"><span data-stu-id="5664d-155">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```csharp
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="5664d-156">Aby uzyskać więcej informacji, zobacz [Klauzula join](../../../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5664d-156">For more information, see [join clause](../../../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="5664d-157">Zaznaczenie (projekcje)</span><span class="sxs-lookup"><span data-stu-id="5664d-157">Selecting (Projections)</span></span>  
 <span data-ttu-id="5664d-158">Klauzula `select` generuje wyniki zapytania i określa "kształt" lub typ każdego zwróconego elementu.</span><span class="sxs-lookup"><span data-stu-id="5664d-158">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="5664d-159">Można na przykład określić, czy wyniki będą składać się z kompletnych `Customer` obiektów, tylko jednego elementu członkowskiego, podzestawu elementów członkowskich, czy pewnego całkowicie innego typu wyników na podstawie obliczenia lub nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5664d-159">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="5664d-160">Gdy klauzula `select` generuje coś innego niż kopia elementu źródłowego, operacja jest nazywana *projekcją*.</span><span class="sxs-lookup"><span data-stu-id="5664d-160">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="5664d-161">Użycie projekcji do przekształcania danych jest zaawansowaną funkcją wyrażeń zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="5664d-161">The use of projections to transform data is a powerful capability of LINQ query expressions.</span></span> <span data-ttu-id="5664d-162">Aby uzyskać więcej informacji, zobacz [przekształcenia danych za pomocąC#LINQ ()](./data-transformations-with-linq.md) i [SELECT](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5664d-162">For more information, see [Data Transformations with LINQ (C#)](./data-transformations-with-linq.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5664d-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5664d-163">See also</span></span>

- [<span data-ttu-id="5664d-164">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="5664d-164">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="5664d-165">Przewodnik: Pisanie zapytań wC#</span><span class="sxs-lookup"><span data-stu-id="5664d-165">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="5664d-166">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="5664d-166">Query Keywords (LINQ)</span></span>](../../../language-reference/keywords/query-keywords.md)
- [<span data-ttu-id="5664d-167">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="5664d-167">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
