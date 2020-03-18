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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635941"
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="874f9-102">Podstawowe operacje zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="874f9-102">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="874f9-103">W tym temacie przedstawiono krótkie wprowadzenie do wyrażeń zapytań LINQ i niektórych typowych rodzajów operacji wykonywanych w kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="874f9-103">This topic gives a brief introduction to LINQ query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="874f9-104">Bardziej szczegółowe informacje znajdują się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="874f9-104">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="874f9-105">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="874f9-105">LINQ Query Expressions</span></span>](../../../linq/index.md)  
  
 [<span data-ttu-id="874f9-106">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="874f9-106">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)  
  
 [<span data-ttu-id="874f9-107">Instruktaż: Pisanie zapytań w C #</span><span class="sxs-lookup"><span data-stu-id="874f9-107">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> <span data-ttu-id="874f9-108">Jeśli znasz już język zapytania, taki jak SQL lub XQuery, możesz pominąć większość tego tematu.</span><span class="sxs-lookup"><span data-stu-id="874f9-108">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="874f9-109">Przeczytaj o`from` "klauzuli" w następnej sekcji, aby dowiedzieć się o kolejności klauzul w wyrażeniach kwerendlinq.</span><span class="sxs-lookup"><span data-stu-id="874f9-109">Read about the "`from` clause" in the next section to learn about the order of clauses in LINQ query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="874f9-110">Uzyskanie źródła danych</span><span class="sxs-lookup"><span data-stu-id="874f9-110">Obtaining a Data Source</span></span>  
 <span data-ttu-id="874f9-111">W kwerendzie LINQ pierwszym krokiem jest określenie źródła danych.</span><span class="sxs-lookup"><span data-stu-id="874f9-111">In a LINQ query, the first step is to specify the data source.</span></span> <span data-ttu-id="874f9-112">W języku C#, jak w większości języków programowania zmienna musi być zadeklarowana, zanim będzie można użyć.</span><span class="sxs-lookup"><span data-stu-id="874f9-112">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="874f9-113">W kwerendzie LINQ `from` klauzula jest na pierwszym miejscu`customers`w celu wprowadzenia`cust`źródła danych ( ) i *zmiennej zakresu* ( ).</span><span class="sxs-lookup"><span data-stu-id="874f9-113">In a LINQ query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 <span data-ttu-id="874f9-114">Zmienna zakresu jest jak zmienna `foreach` iteracji w pętli, z tą różnicą, że w wyrażeniu kwerendy nie występuje rzeczywista iteracja.</span><span class="sxs-lookup"><span data-stu-id="874f9-114">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="874f9-115">Po wykonaniu kwerendy zmienna zakresu będzie służyć jako odwołanie `customers`do każdego kolejnego elementu w programie .</span><span class="sxs-lookup"><span data-stu-id="874f9-115">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="874f9-116">Ponieważ kompilator można wywnioskować typ `cust`, nie trzeba go jawnie określić.</span><span class="sxs-lookup"><span data-stu-id="874f9-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="874f9-117">Dodatkowe zmienne zakresu mogą być `let` wprowadzone przez klauzulę.</span><span class="sxs-lookup"><span data-stu-id="874f9-117">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="874f9-118">Aby uzyskać więcej informacji, zobacz [klauzulę let](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="874f9-118">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="874f9-119">W przypadku nieogólnych <xref:System.Collections.ArrayList>źródeł danych, takich jak zmienna zakresu, musi być jawnie wpisana.</span><span class="sxs-lookup"><span data-stu-id="874f9-119">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="874f9-120">Aby uzyskać więcej informacji, zobacz [Jak wysyłać zapytania do ArrayList z LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) i [z klauzuli](../../../language-reference/keywords/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="874f9-120">For more information, see [How to query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) and [from clause](../../../language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="874f9-121">Filtrowanie</span><span class="sxs-lookup"><span data-stu-id="874f9-121">Filtering</span></span>  
 <span data-ttu-id="874f9-122">Prawdopodobnie najbardziej popularną operacją kwerendy jest zastosowanie filtru w postaci wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="874f9-122">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="874f9-123">Filtr powoduje, że kwerenda zwraca tylko te elementy, dla których wyrażenie jest prawdziwe.</span><span class="sxs-lookup"><span data-stu-id="874f9-123">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="874f9-124">Wynik jest tworzony przy `where` użyciu klauzuli.</span><span class="sxs-lookup"><span data-stu-id="874f9-124">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="874f9-125">Filtr w efekcie określa, które elementy wykluczyć z sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="874f9-125">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="874f9-126">W poniższym przykładzie `customers` zwracane są tylko osoby, które mają adres w Londynie.</span><span class="sxs-lookup"><span data-stu-id="874f9-126">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 <span data-ttu-id="874f9-127">Za pomocą znanych logicznych `AND` `OR` c# i operatorów, aby zastosować `where` dowolną liczbę wyrażeń filtru, zgodnie z wymogami w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="874f9-127">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="874f9-128">Na przykład, aby zwrócić tylko `AND` klientów z "Londynu", którego nazwa jest "Devon", należy napisać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="874f9-128">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 <span data-ttu-id="874f9-129">Aby zwrócić klientów z Londynu lub Paryża, należy napisać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="874f9-129">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 <span data-ttu-id="874f9-130">Aby uzyskać więcej informacji, zobacz [gdzie klauzula](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="874f9-130">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="874f9-131">Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="874f9-131">Ordering</span></span>  
 <span data-ttu-id="874f9-132">Często wygodnie jest sortować zwrócone dane.</span><span class="sxs-lookup"><span data-stu-id="874f9-132">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="874f9-133">Klauzula `orderby` spowoduje, że elementy w zwróconej sekwencji mają być sortowane zgodnie z domyślnym porównywarka dla typu są sortowane.</span><span class="sxs-lookup"><span data-stu-id="874f9-133">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="874f9-134">Na przykład następującą kwerendę można rozszerzyć, aby `Name` posortować wyniki na podstawie właściwości.</span><span class="sxs-lookup"><span data-stu-id="874f9-134">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="874f9-135">Ponieważ `Name` jest to ciąg, domyślny porównywarka wykonuje sortowanie alfabetyczne od A do Z.</span><span class="sxs-lookup"><span data-stu-id="874f9-135">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 <span data-ttu-id="874f9-136">Aby zamówić wyniki w odwrotnej kolejności, od `orderby…descending` Z do A, użyj klauzuli.</span><span class="sxs-lookup"><span data-stu-id="874f9-136">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="874f9-137">Aby uzyskać więcej informacji, zobacz [orderby klauzuli](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="874f9-137">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="874f9-138">Grupowanie</span><span class="sxs-lookup"><span data-stu-id="874f9-138">Grouping</span></span>  
 <span data-ttu-id="874f9-139">Klauzula `group` umożliwia grupowanie wyników na podstawie klucza, który określisz.</span><span class="sxs-lookup"><span data-stu-id="874f9-139">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="874f9-140">Na przykład można określić, że wyniki powinny `City` być pogrupowane według tak, aby wszyscy klienci z Londynu lub Paryża byli w poszczególnych grupach.</span><span class="sxs-lookup"><span data-stu-id="874f9-140">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="874f9-141">W tym `cust.City` przypadku jest kluczem.</span><span class="sxs-lookup"><span data-stu-id="874f9-141">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 <span data-ttu-id="874f9-142">Po zakończeniu kwerendy `group` z klauzulą, wyniki mają formę listy list.</span><span class="sxs-lookup"><span data-stu-id="874f9-142">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="874f9-143">Każdy element na liście jest obiektem, który ma element członkowski `Key` i listę elementów, które są zgrupowane pod tym kluczem.</span><span class="sxs-lookup"><span data-stu-id="874f9-143">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="874f9-144">Podczas itetenowania za pomocą kwerendy, która tworzy sekwencję `foreach` grup, należy użyć pętli zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="874f9-144">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="874f9-145">Zewnętrzna pętla itere nad każdą grupą, a wewnętrzna pętla iteuje nad członkami każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="874f9-145">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="874f9-146">Jeśli musisz odwołać się do wyników operacji `into` grupy, można użyć słowa kluczowego, aby utworzyć identyfikator, który może być przeszukiwany dalej.</span><span class="sxs-lookup"><span data-stu-id="874f9-146">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="874f9-147">Następująca kwerenda zwraca tylko te grupy, które zawierają więcej niż dwóch klientów:</span><span class="sxs-lookup"><span data-stu-id="874f9-147">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 <span data-ttu-id="874f9-148">Aby uzyskać więcej informacji, zobacz [klauzulę group](../../../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="874f9-148">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="874f9-149">Dołączenie</span><span class="sxs-lookup"><span data-stu-id="874f9-149">Joining</span></span>  
 <span data-ttu-id="874f9-150">Operacje sprzężenia tworzą skojarzenia między sekwencjami, które nie są jawnie modelowane w źródłach danych.</span><span class="sxs-lookup"><span data-stu-id="874f9-150">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="874f9-151">Na przykład można wykonać sprzężenie, aby znaleźć wszystkich klientów i dystrybutorów, którzy mają tę samą lokalizację.</span><span class="sxs-lookup"><span data-stu-id="874f9-151">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="874f9-152">W LINQ `join` klauzula zawsze działa przeciwko kolekcje obiektów zamiast tabel bazy danych bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="874f9-152">In LINQ the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 <span data-ttu-id="874f9-153">W LINQ nie trzeba używać `join` tak często, jak to zrobić w SQL, ponieważ klucze obce w LINQ są reprezentowane w modelu obiektu jako właściwości, które posiadają kolekcję elementów.</span><span class="sxs-lookup"><span data-stu-id="874f9-153">In LINQ, you do not have to use `join` as often as you do in SQL, because foreign keys in LINQ are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="874f9-154">Na przykład `Customer` obiekt zawiera kolekcję `Order` obiektów.</span><span class="sxs-lookup"><span data-stu-id="874f9-154">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="874f9-155">Zamiast wykonywać sprzężenie, można uzyskać dostęp do zamówień za pomocą notacji kropkowej:</span><span class="sxs-lookup"><span data-stu-id="874f9-155">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```csharp
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="874f9-156">Aby uzyskać więcej informacji, zobacz [klauzulę join .](../../../language-reference/keywords/join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="874f9-156">For more information, see [join clause](../../../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="874f9-157">Zaznaczenie (projekcje)</span><span class="sxs-lookup"><span data-stu-id="874f9-157">Selecting (Projections)</span></span>  
 <span data-ttu-id="874f9-158">Klauzula `select` daje wyniki kwerendy i określa "kształt" lub typ każdego zwróconego elementu.</span><span class="sxs-lookup"><span data-stu-id="874f9-158">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="874f9-159">Na przykład można określić, czy wyniki `Customer` będą składać się z kompletnych obiektów, tylko jeden element członkowski, podzbiór elementów członkowskich lub jakiś zupełnie inny typ wyniku na podstawie obliczeń lub tworzenia nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="874f9-159">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="874f9-160">Gdy `select` klauzula tworzy coś innego niż kopia elementu źródłowego, operacja jest wywoływana *projekcji*.</span><span class="sxs-lookup"><span data-stu-id="874f9-160">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="874f9-161">Wykorzystanie projekcji do przekształcania danych jest zaawansowaną możliwością wyrażeń zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="874f9-161">The use of projections to transform data is a powerful capability of LINQ query expressions.</span></span> <span data-ttu-id="874f9-162">Aby uzyskać więcej informacji, zobacz [Transformacje danych z LINQ (C#)](./data-transformations-with-linq.md) i [wybierz klauzulę](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="874f9-162">For more information, see [Data Transformations with LINQ (C#)](./data-transformations-with-linq.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="874f9-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="874f9-163">See also</span></span>

- [<span data-ttu-id="874f9-164">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="874f9-164">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="874f9-165">Instruktaż: Pisanie zapytań w C #</span><span class="sxs-lookup"><span data-stu-id="874f9-165">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="874f9-166">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="874f9-166">Query Keywords (LINQ)</span></span>](../../../language-reference/keywords/query-keywords.md)
- [<span data-ttu-id="874f9-167">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="874f9-167">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
