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
ms.openlocfilehash: b9216dba23f49e4d9fd99687e38f5c13addde8fb
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636877"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="cb115-102">Podstawowe operacje zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb115-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="cb115-103">Ten temat zawiera krótkie wprowadzenie do wyrażeń programu Query-Integrated Language (LINQ) w Visual Basic oraz do niektórych typowych rodzajów operacji wykonywanych w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="cb115-103">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="cb115-104">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="cb115-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="cb115-105">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb115-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="cb115-106">Zapytania</span><span class="sxs-lookup"><span data-stu-id="cb115-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="cb115-107">Przewodnik: Pisanie zapytań w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb115-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="cb115-108">Określanie źródła danych (z)</span><span class="sxs-lookup"><span data-stu-id="cb115-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="cb115-109">W zapytaniu LINQ pierwszy krok to określenie źródła danych, które chcesz zbadać.</span><span class="sxs-lookup"><span data-stu-id="cb115-109">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="cb115-110">W związku z tym, klauzula `From` w zapytaniu zawsze jest w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="cb115-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="cb115-111">Operatory zapytań zaznaczają i kształtują wynik w oparciu o typ źródła.</span><span class="sxs-lookup"><span data-stu-id="cb115-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="cb115-112">Klauzula `From` określa źródło danych, `customers`i *zmienną zakresu*, `cust`.</span><span class="sxs-lookup"><span data-stu-id="cb115-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="cb115-113">Zmienna zakresu jest jak Zmienna iteracji pętli, z tą różnicą, że w wyrażeniu zapytania nie występuje rzeczywista iteracja.</span><span class="sxs-lookup"><span data-stu-id="cb115-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="cb115-114">Gdy zapytanie jest wykonywane, często przy użyciu pętli `For Each`, zmienna zakresu służy jako odwołanie do każdego kolejnego elementu w `customers`.</span><span class="sxs-lookup"><span data-stu-id="cb115-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="cb115-115">Ponieważ kompilator może wywnioskować typ `cust`, nie trzeba określać go jawnie.</span><span class="sxs-lookup"><span data-stu-id="cb115-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="cb115-116">Aby zapoznać się z przykładami zapytań pisanych z i bez jawnego wpisywania, zobacz [relacje typu w operacjach zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="cb115-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="cb115-117">Aby uzyskać więcej informacji na temat używania klauzuli `From` w Visual Basic, zobacz [klauzula FROM](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cb115-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="cb115-118">Filtrowanie danych (gdzie)</span><span class="sxs-lookup"><span data-stu-id="cb115-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="cb115-119">Prawdopodobnie najbardziej typowa operacja zapytania stosuje filtr w postaci wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="cb115-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="cb115-120">Zapytanie zwraca następnie tylko te elementy, dla których wyrażenie ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="cb115-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="cb115-121">Klauzula `Where` jest używana do przeprowadzenia filtrowania.</span><span class="sxs-lookup"><span data-stu-id="cb115-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="cb115-122">Filtr określa, które elementy w źródle danych mają być uwzględnione w wyniku sekwencji.</span><span class="sxs-lookup"><span data-stu-id="cb115-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="cb115-123">W poniższym przykładzie uwzględniono tylko tych klientów, którzy mają adres w Londynie.</span><span class="sxs-lookup"><span data-stu-id="cb115-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="cb115-124">Operatory logiczne, takie jak `And` i `Or`, służą do łączenia wyrażeń filtru w klauzuli `Where`.</span><span class="sxs-lookup"><span data-stu-id="cb115-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="cb115-125">Na przykład, aby zwrócić tylko tych klientów, którzy są z Londyn, których nazwa to Devon, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="cb115-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="cb115-126">Aby zwrócić klientów z Londyn lub Paryż, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="cb115-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="cb115-127">Aby uzyskać więcej informacji na temat używania klauzuli `Where` w Visual Basic, zobacz [klauzula WHERE](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cb115-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="cb115-128">Szeregowanie danych (porządkuj wg)</span><span class="sxs-lookup"><span data-stu-id="cb115-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="cb115-129">Często jest wygodne do sortowania zwracanych danych w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="cb115-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="cb115-130">Klauzula `Order By` powoduje, że elementy w zwracanej sekwencji będą sortowane według określonego pola lub pola.</span><span class="sxs-lookup"><span data-stu-id="cb115-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="cb115-131">Na przykład następujące zapytanie sortuje wyniki na podstawie właściwości `Name`.</span><span class="sxs-lookup"><span data-stu-id="cb115-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="cb115-132">Ponieważ `Name` jest ciągiem, zwracane dane zostaną posortowane alfabetycznie, od A do Z.</span><span class="sxs-lookup"><span data-stu-id="cb115-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="cb115-133">Aby zamówić wyniki w odwrotnej kolejności, od z do A, użyj klauzuli `Order By...Descending`.</span><span class="sxs-lookup"><span data-stu-id="cb115-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="cb115-134">Wartość domyślna to `Ascending`, gdy nie `Ascending` ani `Descending` nie została określona.</span><span class="sxs-lookup"><span data-stu-id="cb115-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="cb115-135">Aby uzyskać więcej informacji na temat używania klauzuli `Order By` w Visual Basic, zobacz [klauzula Order by](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cb115-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="cb115-136">Wybieranie danych (wybór)</span><span class="sxs-lookup"><span data-stu-id="cb115-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="cb115-137">Klauzula `Select` określa formę i zawartość zwróconych elementów.</span><span class="sxs-lookup"><span data-stu-id="cb115-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="cb115-138">Można na przykład określić, czy wyniki będą składać się z kompletnych `Customer` obiektów, tylko jednej `Customer` właściwości, podzestawu właściwości, kombinacji właściwości z różnych źródeł danych, czy też nowego typu wyników na podstawie obliczeń.</span><span class="sxs-lookup"><span data-stu-id="cb115-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="cb115-139">Gdy klauzula `Select` generuje coś innego niż kopia elementu źródłowego, operacja jest nazywana *projekcją*.</span><span class="sxs-lookup"><span data-stu-id="cb115-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="cb115-140">Aby pobrać kolekcję, która składa się z kompletnych obiektów `Customer`, wybierz zmienną zakresu:</span><span class="sxs-lookup"><span data-stu-id="cb115-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="cb115-141">Jeśli wystąpienie `Customer` jest dużym obiektem, który ma wiele pól, a wszystkie elementy, które chcesz pobrać, są nazwami, możesz wybrać `cust.Name`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cb115-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="cb115-142">Wnioskowanie typu lokalnego rozpoznaje, że ta zmiana typu wyniku z kolekcji obiektów `Customer` do kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="cb115-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="cb115-143">Aby wybrać wiele pól ze źródła danych, dostępne są dwie opcje:</span><span class="sxs-lookup"><span data-stu-id="cb115-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="cb115-144">W klauzuli `Select` Określ pola, które mają zostać uwzględnione w wyniku.</span><span class="sxs-lookup"><span data-stu-id="cb115-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="cb115-145">Kompilator określi typ anonimowy, który ma te pola jako właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb115-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="cb115-146">Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="cb115-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="cb115-147">Ponieważ zwracane elementy w poniższym przykładzie są wystąpieniami typu anonimowego, nie można odwołać się do typu według nazwy w innym miejscu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="cb115-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="cb115-148">Nazwa oznaczona przez kompilator dla typu zawiera znaki, które nie są prawidłowe w normalnym Visual Basic kodzie.</span><span class="sxs-lookup"><span data-stu-id="cb115-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="cb115-149">W poniższym przykładzie elementy w kolekcji, które są zwracane przez zapytanie w `londonCusts4` są wystąpieniami typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="cb115-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="cb115-150">lub</span><span class="sxs-lookup"><span data-stu-id="cb115-150">-or-</span></span>  
  
- <span data-ttu-id="cb115-151">Zdefiniuj nazwany typ, który zawiera określone pola, które chcesz dołączyć do wyniku, i Utwórz i zainicjuj wystąpienia typu w klauzuli `Select`.</span><span class="sxs-lookup"><span data-stu-id="cb115-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="cb115-152">Użyj tej opcji tylko wtedy, gdy musisz użyć pojedynczych wyników poza kolekcją, w której są zwracane, lub jeśli musisz przekazać je jako parametry w wywołaniach metod.</span><span class="sxs-lookup"><span data-stu-id="cb115-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="cb115-153">Typ `londonCusts5` w poniższym przykładzie to IEnumerable (of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="cb115-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="cb115-154">Aby uzyskać więcej informacji na temat używania klauzuli `Select` w Visual Basic, zobacz [SELECT — klauzula](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cb115-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="cb115-155">Przyłączanie danych (łączenie i łączenie grupy)</span><span class="sxs-lookup"><span data-stu-id="cb115-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="cb115-156">Można połączyć więcej niż jedno źródło danych w klauzuli `From` na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="cb115-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="cb115-157">Na przykład poniższy kod używa dwóch źródeł danych i niejawnie łączy właściwości z obu nich w wyniku.</span><span class="sxs-lookup"><span data-stu-id="cb115-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="cb115-158">Zapytanie wybiera uczniów, których nazwiska zaczynają się od samogłosek.</span><span class="sxs-lookup"><span data-stu-id="cb115-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="cb115-159">Ten kod można uruchomić z listą uczniów utworzonych w temacie [How to: Create a list of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="cb115-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="cb115-160">Słowo kluczowe `Join` jest odpowiednikiem `INNER JOIN` w SQL.</span><span class="sxs-lookup"><span data-stu-id="cb115-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="cb115-161">Łączy dwie kolekcje na podstawie pasujących wartości klucza między elementami w dwóch kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="cb115-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="cb115-162">Zapytanie zwraca wszystkie lub część elementów kolekcji, które mają zgodne wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="cb115-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="cb115-163">Na przykład poniższy kod duplikuje akcję poprzedniego niejawnego sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="cb115-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="cb115-164">`Group Join` łączy kolekcje w jedną hierarchiczną kolekcję, podobnie jak `LEFT JOIN` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="cb115-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="cb115-165">Aby uzyskać więcej informacji, zobacz Klauzula [Join](../../../../visual-basic/language-reference/queries/join-clause.md) i [Klauzula join Group](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cb115-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="cb115-166">Grupowanie danych (grupuj według)</span><span class="sxs-lookup"><span data-stu-id="cb115-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="cb115-167">Można dodać klauzulę `Group By`, aby zgrupować elementy w wyniku zapytania zgodnie z co najmniej jednym polem elementów.</span><span class="sxs-lookup"><span data-stu-id="cb115-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="cb115-168">Na przykład poniższy kod grupuje uczniów według klasy Year.</span><span class="sxs-lookup"><span data-stu-id="cb115-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="cb115-169">Jeśli uruchomisz ten kod przy użyciu listy uczniów utworzonych w [instrukcje: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), dane wyjściowe instrukcji `For Each` są następujące:</span><span class="sxs-lookup"><span data-stu-id="cb115-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="cb115-170">Year: młodszy</span><span class="sxs-lookup"><span data-stu-id="cb115-170">Year: Junior</span></span>  
  
 <span data-ttu-id="cb115-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="cb115-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="cb115-172">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="cb115-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="cb115-173">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="cb115-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="cb115-174">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="cb115-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="cb115-175">Rok: starszy</span><span class="sxs-lookup"><span data-stu-id="cb115-175">Year: Senior</span></span>  
  
 <span data-ttu-id="cb115-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="cb115-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="cb115-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="cb115-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="cb115-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="cb115-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="cb115-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="cb115-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="cb115-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="cb115-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="cb115-181">Year: odświeżacz</span><span class="sxs-lookup"><span data-stu-id="cb115-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="cb115-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="cb115-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="cb115-183">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="cb115-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="cb115-184">Wariant przedstawiony w poniższym kodzie porządkuje lata klasy, a następnie porządkuje uczniów w każdym roku według nazwiska.</span><span class="sxs-lookup"><span data-stu-id="cb115-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="cb115-185">Aby uzyskać więcej informacji na temat `Group By`, zobacz [klauzula GROUP by](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cb115-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb115-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb115-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="cb115-187">Wprowadzenie ze składnikami LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb115-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="cb115-188">Zapytania</span><span class="sxs-lookup"><span data-stu-id="cb115-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="cb115-189">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb115-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="cb115-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="cb115-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
