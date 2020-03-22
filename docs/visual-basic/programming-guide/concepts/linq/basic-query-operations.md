---
title: Podstawowe operacje zapytań
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266381"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="1fae2-102">Podstawowe operacje zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fae2-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="1fae2-103">Ten temat zawiera krótkie wprowadzenie do wyrażeń linq (Language-Integrated Query) w języku Visual Basic i niektórych typowych rodzajów operacji, które można wykonać w kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="1fae2-103">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="1fae2-104">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="1fae2-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="1fae2-105">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fae2-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="1fae2-106">Zapytania</span><span class="sxs-lookup"><span data-stu-id="1fae2-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="1fae2-107">Wskazówki: Pisanie zapytań w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fae2-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="1fae2-108">Określanie źródła danych (z)</span><span class="sxs-lookup"><span data-stu-id="1fae2-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="1fae2-109">W kwerendzie LINQ pierwszym krokiem jest określenie źródła danych, które chcesz zbadać.</span><span class="sxs-lookup"><span data-stu-id="1fae2-109">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="1fae2-110">W związku `From` z tym klauzuli w kwerendzie zawsze jest na pierwszym miejscu.</span><span class="sxs-lookup"><span data-stu-id="1fae2-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="1fae2-111">Operatorzy kwerend zaznaczają i kształtują wynik na podstawie typu źródła.</span><span class="sxs-lookup"><span data-stu-id="1fae2-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="1fae2-112">Klauzula `From` określa źródło danych `customers`i *zmienną* `cust`zakresu , .</span><span class="sxs-lookup"><span data-stu-id="1fae2-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="1fae2-113">Zmienna zakresu jest jak zmienna iteracji pętli, z tą różnicą, że w wyrażeniu kwerendy nie występuje żadna rzeczywista iteracja.</span><span class="sxs-lookup"><span data-stu-id="1fae2-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="1fae2-114">Gdy kwerenda jest wykonywana, `For Each` często przy użyciu pętli, zmienna zakresu `customers`służy jako odwołanie do każdego kolejnego elementu w .</span><span class="sxs-lookup"><span data-stu-id="1fae2-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="1fae2-115">Ponieważ kompilator można wywnioskować typ `cust`, nie trzeba go jawnie określić.</span><span class="sxs-lookup"><span data-stu-id="1fae2-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="1fae2-116">Aby zapoznać się z przykładami zapytań napisanych z jawnym wpisaniem i bez niego, zobacz [Relacje typów w operacjach kwerend (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="1fae2-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="1fae2-117">Aby uzyskać więcej informacji `From` na temat używania klauzuli w języku Visual Basic, zobacz [Od klauzuli](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1fae2-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="1fae2-118">Filtrowanie danych (gdzie)</span><span class="sxs-lookup"><span data-stu-id="1fae2-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="1fae2-119">Prawdopodobnie najczęstszą operacją kwerendy jest zastosowanie filtru w postaci wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="1fae2-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="1fae2-120">Następnie kwerenda zwraca tylko te elementy, dla których wyrażenie jest prawdziwe.</span><span class="sxs-lookup"><span data-stu-id="1fae2-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="1fae2-121">Klauzula `Where` jest używana do wykonywania filtrowania.</span><span class="sxs-lookup"><span data-stu-id="1fae2-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="1fae2-122">Filtr określa, które elementy w źródle danych mają być uwzględniane w wynikowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1fae2-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="1fae2-123">W poniższym przykładzie uwzględniono tylko tych klientów, którzy mają adres w Londynie.</span><span class="sxs-lookup"><span data-stu-id="1fae2-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="1fae2-124">Operatory logiczne, `And` takie `Or` jak i do `Where` łączenia wyrażeń filtru w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="1fae2-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="1fae2-125">Na przykład, aby zwrócić tylko tych klientów, którzy są z Londynu i których nazwa jest Devon, należy użyć następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="1fae2-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 <span data-ttu-id="1fae2-126">Aby zwrócić klientów z Londynu lub Paryża, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="1fae2-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 <span data-ttu-id="1fae2-127">Aby uzyskać więcej informacji `Where` na temat używania klauzuli w języku Visual Basic, zobacz [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1fae2-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="1fae2-128">Szeregowanie danych (porządkuj wg)</span><span class="sxs-lookup"><span data-stu-id="1fae2-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="1fae2-129">Często jest to wygodne do sortowania zwróconych danych w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="1fae2-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="1fae2-130">Klauzula `Order By` spowoduje, że elementy w zwróconej sekwencji mają być sortowane na określonym polu lub polach.</span><span class="sxs-lookup"><span data-stu-id="1fae2-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="1fae2-131">Na przykład następujące zapytanie sortuje `Name` wyniki na podstawie właściwości.</span><span class="sxs-lookup"><span data-stu-id="1fae2-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="1fae2-132">Ponieważ `Name` jest ciągiem, zwrócone dane zostaną posortowane alfabetycznie, od A do Z.</span><span class="sxs-lookup"><span data-stu-id="1fae2-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="1fae2-133">Aby zamówić wyniki w odwrotnej kolejności, `Order By...Descending` od Z do A, należy użyć klauzuli.</span><span class="sxs-lookup"><span data-stu-id="1fae2-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="1fae2-134">Wartość domyślna `Ascending` jest `Ascending` `Descending` wtedy, gdy ani nie jest określony.</span><span class="sxs-lookup"><span data-stu-id="1fae2-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="1fae2-135">Aby uzyskać więcej informacji `Order By` na temat używania klauzuli w języku Visual Basic, zobacz [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1fae2-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="1fae2-136">Wybieranie danych (wybór)</span><span class="sxs-lookup"><span data-stu-id="1fae2-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="1fae2-137">Klauzula `Select` określa formę i zawartość zwróconych elementów.</span><span class="sxs-lookup"><span data-stu-id="1fae2-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="1fae2-138">Na przykład można określić, czy wyniki `Customer` będą składać `Customer` się z kompletnych obiektów, tylko jedna właściwość, podzbiór właściwości, kombinacja właściwości z różnych źródeł danych lub jakiś nowy typ wyniku na podstawie obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1fae2-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="1fae2-139">Gdy `Select` klauzula tworzy coś innego niż kopia elementu źródłowego, operacja jest nazywana *projekcji*.</span><span class="sxs-lookup"><span data-stu-id="1fae2-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="1fae2-140">Aby pobrać kolekcję, która `Customer` składa się z kompletnych obiektów, wybierz samą zmienną zakresu:</span><span class="sxs-lookup"><span data-stu-id="1fae2-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="1fae2-141">Jeśli `Customer` wystąpienie jest dużym obiektem, który ma wiele pól, a wszystko, `cust.Name`co chcesz pobrać, to nazwa, można wybrać , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1fae2-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="1fae2-142">Wnioskowanie o typie lokalnym rozpoznaje, że `Customer` zmienia to typ wyniku z kolekcji obiektów na kolekcję ciągów.</span><span class="sxs-lookup"><span data-stu-id="1fae2-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="1fae2-143">Aby wybrać wiele pól ze źródła danych, dostępne są dwie opcje:</span><span class="sxs-lookup"><span data-stu-id="1fae2-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="1fae2-144">W `Select` klauzuli określ pola, które mają zostać uwzględnione w wyniku.</span><span class="sxs-lookup"><span data-stu-id="1fae2-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="1fae2-145">Kompilator zdefiniuje typ anonimowy, który ma te pola jako jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="1fae2-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="1fae2-146">Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="1fae2-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="1fae2-147">Ponieważ zwrócone elementy w poniższym przykładzie są wystąpienia typu anonimowego, nie można odwoływać się do typu według nazwy w innym miejscu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1fae2-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="1fae2-148">Nazwa wyznaczona przez kompilator dla tego typu zawiera znaki, które nie są prawidłowe w normalnym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1fae2-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="1fae2-149">W poniższym przykładzie elementy w kolekcji, która `londonCusts4` jest zwracana przez kwerendę w są wystąpienia typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="1fae2-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="1fae2-150">— lub —</span><span class="sxs-lookup"><span data-stu-id="1fae2-150">-or-</span></span>  
  
- <span data-ttu-id="1fae2-151">Zdefiniuj nazwany typ, który zawiera określone pola, które chcesz uwzględnić w wyniku, i utwórz i zainicjalizuj wystąpienia typu w klauzuli. `Select`</span><span class="sxs-lookup"><span data-stu-id="1fae2-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="1fae2-152">Tej opcji należy używać tylko wtedy, gdy trzeba użyć poszczególnych wyników poza kolekcji, w którym są zwracane lub jeśli trzeba przekazać je jako parametry w wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="1fae2-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="1fae2-153">Typ w `londonCusts5` poniższym przykładzie jest IEnumerable(NamePhone).</span><span class="sxs-lookup"><span data-stu-id="1fae2-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="1fae2-154">Aby uzyskać więcej informacji `Select` na temat używania klauzuli w języku Visual Basic, zobacz [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1fae2-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="1fae2-155">Przyłączanie danych (łączenie i łączenie grupy)</span><span class="sxs-lookup"><span data-stu-id="1fae2-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="1fae2-156">Można połączyć więcej niż jedno `From` źródło danych w klauzuli na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="1fae2-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="1fae2-157">Na przykład poniższy kod używa dwóch źródeł danych i niejawnie łączy właściwości z obu z nich w wyniku.</span><span class="sxs-lookup"><span data-stu-id="1fae2-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="1fae2-158">Kwerenda wybiera uczniów, których nazwiska zaczynają się od samogłoski.</span><span class="sxs-lookup"><span data-stu-id="1fae2-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="1fae2-159">Możesz uruchomić ten kod z listą uczniów utworzonych w [jak: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="1fae2-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="1fae2-160">Słowo `Join` kluczowe jest `INNER JOIN` równoważne w sql.</span><span class="sxs-lookup"><span data-stu-id="1fae2-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="1fae2-161">Łączy dwie kolekcje na podstawie dopasowania wartości klucza między elementami w dwóch kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="1fae2-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="1fae2-162">Kwerenda zwraca wszystkie lub część elementów kolekcji, które mają pasujące wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="1fae2-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="1fae2-163">Na przykład poniższy kod powiela akcję poprzedniego sprzężenia niejawnego.</span><span class="sxs-lookup"><span data-stu-id="1fae2-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="1fae2-164">`Group Join`łączy kolekcje w jedną kolekcję hierarchiczną, podobnie jak `LEFT JOIN` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="1fae2-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="1fae2-165">Aby uzyskać więcej informacji, zobacz [Klauzula dołączania](../../../../visual-basic/language-reference/queries/join-clause.md) i [klauzula dołączania do grupy](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1fae2-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="1fae2-166">Grupowanie danych (grupuj według)</span><span class="sxs-lookup"><span data-stu-id="1fae2-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="1fae2-167">Można dodać `Group By` klauzulę do grupy elementów w wyniku kwerendy zgodnie z jednym lub więcej pól elementów.</span><span class="sxs-lookup"><span data-stu-id="1fae2-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="1fae2-168">Na przykład następujący kod grupuje uczniów według roku zajęć.</span><span class="sxs-lookup"><span data-stu-id="1fae2-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="1fae2-169">Jeśli uruchomisz ten kod przy użyciu listy studentów utworzonych w [Jak: Tworzenie listy elementów,](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)dane wyjściowe z `For Each` instrukcji jest:</span><span class="sxs-lookup"><span data-stu-id="1fae2-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="1fae2-170">Rok: Junior</span><span class="sxs-lookup"><span data-stu-id="1fae2-170">Year: Junior</span></span>  
  
 <span data-ttu-id="1fae2-171">Tucker, Michał</span><span class="sxs-lookup"><span data-stu-id="1fae2-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="1fae2-172">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="1fae2-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="1fae2-173">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="1fae2-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="1fae2-174">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="1fae2-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="1fae2-175">Rok: Senior</span><span class="sxs-lookup"><span data-stu-id="1fae2-175">Year: Senior</span></span>  
  
 <span data-ttu-id="1fae2-176">Omelczenko, Swietłana</span><span class="sxs-lookup"><span data-stu-id="1fae2-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="1fae2-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="1fae2-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="1fae2-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="1fae2-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="1fae2-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="1fae2-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="1fae2-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="1fae2-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="1fae2-181">Rok: Freshman</span><span class="sxs-lookup"><span data-stu-id="1fae2-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="1fae2-182">Mortensen</span><span class="sxs-lookup"><span data-stu-id="1fae2-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="1fae2-183">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="1fae2-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="1fae2-184">Zmiana przedstawiona w poniższym kodzie zamówi lata zajęć, a następnie zamawia uczniów w ciągu każdego roku po imieniu.</span><span class="sxs-lookup"><span data-stu-id="1fae2-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="1fae2-185">Aby uzyskać `Group By`więcej informacji na temat , zobacz [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1fae2-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fae2-186">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1fae2-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="1fae2-187">Wprowadzenie do programu LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fae2-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="1fae2-188">Zapytania</span><span class="sxs-lookup"><span data-stu-id="1fae2-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="1fae2-189">Omówienie standardowych operatorów zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fae2-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="1fae2-190">Linq</span><span class="sxs-lookup"><span data-stu-id="1fae2-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
