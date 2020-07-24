---
title: Podstawowe operacje zapytań LINQ (C#)
description: Wprowadź siebie w wyrażeniach zapytań LINQ i niektórych operacji, które możesz wykonać w zapytaniu.
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
ms.openlocfilehash: d9653be8b67ef4d971c157b8dd8d82b2ae3c2287
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105521"
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="cbdc9-103">Podstawowe operacje zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="cbdc9-103">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="cbdc9-104">Ten temat zawiera krótkie wprowadzenie do wyrażeń zapytań LINQ i niektórych typowych rodzajów operacji wykonywanych w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-104">This topic gives a brief introduction to LINQ query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="cbdc9-105">Bardziej szczegółowe informacje znajdują się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="cbdc9-105">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="cbdc9-106">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="cbdc9-106">LINQ Query Expressions</span></span>](../../../linq/index.md)  
  
 [<span data-ttu-id="cbdc9-107">Standardowe operatory zapytań — Omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="cbdc9-107">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)  
  
 [<span data-ttu-id="cbdc9-108">Przewodnik: Pisanie zapytań w języku C #</span><span class="sxs-lookup"><span data-stu-id="cbdc9-108">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> <span data-ttu-id="cbdc9-109">Jeśli znasz już język zapytań, taki jak SQL lub XQuery, możesz pominąć większość tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-109">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="cbdc9-110">Przeczytaj temat " `from` klauzula" w następnej sekcji, aby dowiedzieć się więcej na temat porządku klauzul w wyrażeniach zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-110">Read about the "`from` clause" in the next section to learn about the order of clauses in LINQ query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="cbdc9-111">Uzyskanie źródła danych</span><span class="sxs-lookup"><span data-stu-id="cbdc9-111">Obtaining a Data Source</span></span>  
 <span data-ttu-id="cbdc9-112">W zapytaniu LINQ pierwszym krokiem jest określenie źródła danych.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-112">In a LINQ query, the first step is to specify the data source.</span></span> <span data-ttu-id="cbdc9-113">W języku C#, jak w większości języków programowania, zmienna musi być zadeklarowana, zanim będzie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-113">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="cbdc9-114">W zapytaniu LINQ `from` klauzula jest najpierw w celu wprowadzenia źródła danych ( `customers` ) i *zmiennej zakresu* ( `cust` ).</span><span class="sxs-lookup"><span data-stu-id="cbdc9-114">In a LINQ query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 <span data-ttu-id="cbdc9-115">Zmienna zakresu jest jak Zmienna iteracji w `foreach` pętli, z wyjątkiem tego, że w wyrażeniu zapytania nie ma rzeczywistej iteracji.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-115">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="cbdc9-116">Gdy zapytanie zostanie wykonane, zmienna zakresu będzie traktować jako odwołanie do każdego kolejnego elementu w `customers` .</span><span class="sxs-lookup"><span data-stu-id="cbdc9-116">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="cbdc9-117">Ponieważ kompilator może wywnioskować typ `cust` , nie trzeba określać go jawnie.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-117">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="cbdc9-118">Dodatkowe zmienne zakresów można wprowadzać przez `let` klauzulę.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-118">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="cbdc9-119">Aby uzyskać więcej informacji, zobacz [klauzula Let](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cbdc9-119">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbdc9-120">W przypadku nieogólnych źródeł danych, takich jak <xref:System.Collections.ArrayList> , zmienna zakresu musi być jawnie wpisana.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-120">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="cbdc9-121">Aby uzyskać więcej informacji, zobacz [How to Query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) i [from](../../../language-reference/keywords/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cbdc9-121">For more information, see [How to query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) and [from clause](../../../language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="cbdc9-122">Filtrowanie</span><span class="sxs-lookup"><span data-stu-id="cbdc9-122">Filtering</span></span>  
 <span data-ttu-id="cbdc9-123">Prawdopodobnie najbardziej typową operacją zapytania jest stosowanie filtru w postaci wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-123">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="cbdc9-124">Filtr powoduje, że zapytanie zwraca tylko te elementy, dla których wyrażenie ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-124">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="cbdc9-125">Wynik jest tworzony przy użyciu `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-125">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="cbdc9-126">Filtr w efekcie określa elementy, które mają zostać wykluczone z sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-126">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="cbdc9-127">W poniższym przykładzie zwracane są tylko te `customers` osoby, które mają adres w Londynie.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-127">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 <span data-ttu-id="cbdc9-128">Możesz użyć znanych operatorów logicznych języka C# `AND` , `OR` Aby zastosować dowolną liczbę wyrażeń filtrów w `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-128">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="cbdc9-129">Aby na przykład zwrócić tylko klientów z "Londyn" o `AND` nazwie "Devon", należy napisać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="cbdc9-129">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 <span data-ttu-id="cbdc9-130">Aby zwrócić klientów z Londyn lub Paryż, Napisz następujący kod:</span><span class="sxs-lookup"><span data-stu-id="cbdc9-130">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 <span data-ttu-id="cbdc9-131">Aby uzyskać więcej informacji, zobacz [klauzula WHERE](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cbdc9-131">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="cbdc9-132">Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="cbdc9-132">Ordering</span></span>  
 <span data-ttu-id="cbdc9-133">Często wygodnie jest posortować zwrócone dane.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-133">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="cbdc9-134">`orderby`Klauzula spowoduje, że elementy w zwracanej sekwencji będą sortowane zgodnie z domyślną wartością porównującą dla sortowanego typu.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-134">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="cbdc9-135">Na przykład następujące zapytanie można rozszerzyć, aby posortować wyniki na podstawie `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-135">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="cbdc9-136">Ponieważ `Name` jest ciągiem, domyślna funkcja porównująca wykonuje alfabetyczne sortowanie od a do z.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-136">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 <span data-ttu-id="cbdc9-137">Aby zamówić wyniki w odwrotnej kolejności, od z do A, użyj `orderby…descending` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-137">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="cbdc9-138">Aby uzyskać więcej informacji, zobacz [klauzula OrderBy](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cbdc9-138">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="cbdc9-139">Grupowanie</span><span class="sxs-lookup"><span data-stu-id="cbdc9-139">Grouping</span></span>  
 <span data-ttu-id="cbdc9-140">`group`Klauzula pozwala grupować wyniki na podstawie określonego klucza.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-140">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="cbdc9-141">Można na przykład określić, że wyniki mają być pogrupowane według, `City` aby wszyscy klienci z Londyn lub Paryż w poszczególnych grupach.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-141">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="cbdc9-142">W tym przypadku `cust.City` jest kluczem.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-142">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 <span data-ttu-id="cbdc9-143">Po zakończeniu zapytania z `group` klauzulą wyniki mają postać listy list.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-143">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="cbdc9-144">Każdy element na liście jest obiektem, który ma `Key` element członkowski i listę elementów, które są zgrupowane w tym kluczu.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-144">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="cbdc9-145">Podczas iteracji w zapytaniu, które tworzy sekwencję grup, należy użyć zagnieżdżonej `foreach` pętli.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-145">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="cbdc9-146">Pętla zewnętrzna wykonuje iterację dla każdej grupy, a pętla wewnętrzna wykonuje iterację dla wszystkich członków grupy.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-146">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="cbdc9-147">Jeśli musisz odwołać się do wyników operacji grupy, możesz użyć `into` słowa kluczowego, aby utworzyć identyfikator, który może być przeszukiwany w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-147">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="cbdc9-148">Następujące zapytanie zwraca tylko te grupy, które zawierają więcej niż dwóch klientów:</span><span class="sxs-lookup"><span data-stu-id="cbdc9-148">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 <span data-ttu-id="cbdc9-149">Aby uzyskać więcej informacji, zobacz [klauzula](../../../language-reference/keywords/group-clause.md)Group.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-149">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="cbdc9-150">Dołączenie</span><span class="sxs-lookup"><span data-stu-id="cbdc9-150">Joining</span></span>  
 <span data-ttu-id="cbdc9-151">Operacje Join tworzą skojarzenia między sekwencjami, które nie są jawnie modelowane w źródłach danych.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-151">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="cbdc9-152">Na przykład możesz wykonać sprzężenie, aby znaleźć wszystkich klientów i dystrybutorów, którzy mają tę samą lokalizację.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-152">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="cbdc9-153">W LINQ `join` klauzula zawsze działa w odniesieniu do kolekcji obiektów, a nie bezpośrednio w tabelach bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-153">In LINQ the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 <span data-ttu-id="cbdc9-154">W LINQ nie trzeba używać `join` tak często jak w przypadku programu SQL, ponieważ klucze obce w LINQ są reprezentowane w modelu obiektów jako właściwości, które przechowują kolekcję elementów.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-154">In LINQ, you do not have to use `join` as often as you do in SQL, because foreign keys in LINQ are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="cbdc9-155">Na przykład `Customer` obiekt zawiera kolekcję `Order` obiektów.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-155">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="cbdc9-156">Zamiast wykonywać sprzężenie, uzyskujesz dostęp do zamówień przy użyciu notacji kropkowej:</span><span class="sxs-lookup"><span data-stu-id="cbdc9-156">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```csharp
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="cbdc9-157">Aby uzyskać więcej informacji, zobacz [Klauzula join](../../../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cbdc9-157">For more information, see [join clause](../../../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="cbdc9-158">Zaznaczenie (projekcje)</span><span class="sxs-lookup"><span data-stu-id="cbdc9-158">Selecting (Projections)</span></span>  
 <span data-ttu-id="cbdc9-159">`select`Klauzula tworzy wyniki zapytania i określa "kształt" lub typ każdego zwróconego elementu.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-159">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="cbdc9-160">Można na przykład określić, czy wyniki będą składać się z kompletnych `Customer` obiektów, tylko jednego elementu członkowskiego, podzestawu elementów członkowskich, czy pewnego całkowicie innego typu wyników na podstawie obliczeń lub tworzenia nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-160">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="cbdc9-161">Gdy `select` klauzula generuje coś innego niż kopia elementu źródłowego, operacja jest nazywana *projekcją*.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-161">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="cbdc9-162">Użycie projekcji do przekształcania danych jest zaawansowaną funkcją wyrażeń zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="cbdc9-162">The use of projections to transform data is a powerful capability of LINQ query expressions.</span></span> <span data-ttu-id="cbdc9-163">Aby uzyskać więcej informacji, zobacz [przekształcenia danych za pomocą LINQ (C#)](./data-transformations-with-linq.md) i [SELECT](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cbdc9-163">For more information, see [Data Transformations with LINQ (C#)](./data-transformations-with-linq.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbdc9-164">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbdc9-164">See also</span></span>

- [<span data-ttu-id="cbdc9-165">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="cbdc9-165">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="cbdc9-166">Przewodnik: Pisanie zapytań w języku C #</span><span class="sxs-lookup"><span data-stu-id="cbdc9-166">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="cbdc9-167">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="cbdc9-167">Query Keywords (LINQ)</span></span>](../../../language-reference/keywords/query-keywords.md)
- [<span data-ttu-id="cbdc9-168">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="cbdc9-168">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
