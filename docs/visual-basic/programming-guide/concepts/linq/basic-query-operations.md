---
title: "Podstawowe operacje zapytań (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 794d77a18b50cc1667fddbad17c46735ae91be26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="d3e2f-102">Podstawowe operacje zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3e2f-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="d3e2f-103">Ten temat zawiera krótkie wprowadzenie do [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] wyrażenia w Visual Basic i niektórych typowych rodzajów operacji wykonywanych w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="d3e2f-104">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="d3e2f-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="d3e2f-105">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3e2f-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="d3e2f-106">Zapytania</span><span class="sxs-lookup"><span data-stu-id="d3e2f-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [<span data-ttu-id="d3e2f-107">Wskazówki: Pisanie zapytań w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3e2f-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="d3e2f-108">Określanie źródła danych (z)</span><span class="sxs-lookup"><span data-stu-id="d3e2f-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="d3e2f-109">W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, pierwszym krokiem jest określenie źródła danych, które chcesz zbadać.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-109">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="d3e2f-110">W związku z tym `From` podklauzul zawsze zostanie osiągnięty jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="d3e2f-111">Operatory zapytań wybierz i kształt wyniku na podstawie typu źródła.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 <span data-ttu-id="d3e2f-112">`From` Klauzuli Określa źródło danych, `customers`, a *zmiennej zakresu*, `cust`.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="d3e2f-113">Zmienna zakresu przypomina zmiennej iteracji pętli, z wyjątkiem tego, że w wyrażeniu zapytania nie rzeczywiste iteracji występuje.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="d3e2f-114">Podczas wykonywania zapytania, często przy użyciu `For Each` pętli, zmienna zakresu służy jako punkt odniesienia, aby każdy element w `customers`.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="d3e2f-115">Ponieważ kompilator można wywnioskować typu elementu `cust`, nie trzeba określić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="d3e2f-116">Przykłady zapytań zapisywane z i bez wprowadzania jawne, zobacz [relacje typu w operacjach zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2f-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="d3e2f-117">Aby uzyskać więcej informacji o sposobie używania `From` klauzuli w języku Visual Basic, zobacz [klauzuli From](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2f-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="d3e2f-118">Filtrowanie danych (gdzie)</span><span class="sxs-lookup"><span data-stu-id="d3e2f-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="d3e2f-119">Prawdopodobnie najbardziej typowych operacji zapytania jest stosowanie filtru w postaci wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="d3e2f-120">Następnie zapytanie zwraca tylko te elementy, dla których wyrażenie jest prawdziwe.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="d3e2f-121">A `Where` jest używana do wykonywania filtrowania.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="d3e2f-122">Filtr określa elementy, które w źródle danych, aby uwzględnić w wynikowa sekwencja.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="d3e2f-123">W poniższym przykładzie zawarte są tylko klientów, którzy mają adres w Londynie.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 <span data-ttu-id="d3e2f-124">Można użyć operatorów logicznych, takich jak `And` i `Or` do filtru wyrażeń w `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="d3e2f-125">Na przykład aby przywrócić tylko tych klientów, którzy są w Londynie i której nazwa jest Devon, należy użyć poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="d3e2f-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="d3e2f-126">Aby przywrócić klientów w Londynie lub Paryża, należy użyć poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="d3e2f-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="d3e2f-127">Aby uzyskać więcej informacji o sposobie używania `Where` klauzuli w języku Visual Basic, zobacz [klauzuli Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2f-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="d3e2f-128">Szeregowanie danych (porządkuj wg)</span><span class="sxs-lookup"><span data-stu-id="d3e2f-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="d3e2f-129">Często jest wygodne posortuj zwrócone dane w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="d3e2f-130">`Order By` Klauzuli spowoduje, że elementy w sekwencji zwróconego można sortować według określonego pola lub pól.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="d3e2f-131">Na przykład poniższe zapytanie sortujące wyniki na podstawie `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="d3e2f-132">Ponieważ `Name` ciągiem i zwrócone dane są sortowane alfabetycznie, od A do Z.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 <span data-ttu-id="d3e2f-133">Aby w odwrotnej kolejności kolejność wyników z malejąco, należy użyć `Order By...Descending` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="d3e2f-134">Wartość domyślna to `Ascending` podczas ani `Ascending` ani `Descending` jest określona.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="d3e2f-135">Aby uzyskać więcej informacji o sposobie używania `Order By` klauzuli w języku Visual Basic, zobacz [klauzula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2f-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="d3e2f-136">Wybieranie danych (wybór)</span><span class="sxs-lookup"><span data-stu-id="d3e2f-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="d3e2f-137">`Select` Klauzuli określa formularza i zawartości zwracane elementy.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="d3e2f-138">Na przykład można określić, czy wyniki będzie składać się z pełną `Customer` obiektów, co najmniej jeden `Customer` właściwości, podzbiór właściwości, kombinację właściwości z różnych źródeł danych lub nowego typu wyniku w oparciu o obliczenie.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="d3e2f-139">Gdy `Select` klauzuli powoduje inną niż kopię elementu źródła, operacja jest wywoływana *projekcji*.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="d3e2f-140">Aby pobrać kolekcję, która składa się z pełną `Customer` obiektów, zaznacz samej zmiennej zakresu:</span><span class="sxs-lookup"><span data-stu-id="d3e2f-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 <span data-ttu-id="d3e2f-141">Jeśli `Customer` wystąpienie jest dużego obiektu, który ma wiele pól i wszystkie punkty, które ma zostać pobrane to nazwa, możesz wybrać `cust.Name`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="d3e2f-142">Wnioskowanie o typie lokalnym rozpoznaje, spowoduje to zmianę typu wyników z kolekcji `Customer` obiekty do kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 <span data-ttu-id="d3e2f-143">Aby wybrać wiele pól ze źródła danych, dostępne są dwie opcje:</span><span class="sxs-lookup"><span data-stu-id="d3e2f-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
-   <span data-ttu-id="d3e2f-144">W `Select` klauzuli, określ pola, które mają zostać uwzględnione w wynikach.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="d3e2f-145">Kompilator będzie zdefiniować typu anonimowego, który ma te pola z jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="d3e2f-146">Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2f-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="d3e2f-147">Zwracane elementy w poniższym przykładzie są wystąpienia typu anonimowego, użytkownik nie może odwoływać się do typu według nazwy w innym miejscu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="d3e2f-148">Nazwa wyznaczony przez kompilator typu zawiera znaki, które nie są dozwolone w normalnym kod Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="d3e2f-149">W poniższym przykładzie elementów w kolekcji zwracane przez zapytanie w `londonCusts4` wystąpień typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="d3e2f-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     <span data-ttu-id="d3e2f-150">—lub—</span><span class="sxs-lookup"><span data-stu-id="d3e2f-150">-or-</span></span>  
  
-   <span data-ttu-id="d3e2f-151">Zdefiniuj typ nazwany, zawierający określonego pola, które mają być zawarte w wyniku, tworzenie i Inicjowanie wystąpień typu w `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="d3e2f-152">Użyj tej opcji tylko wtedy, gdy należy użyć poszczególnych wyników poza kolekcji, w której są zwracane lub jeśli zajdzie potrzeba przekazywane jako parametry w wywołaniach metody.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="d3e2f-153">Typ `londonCusts5` w poniższym przykładzie jest IEnumerable (Of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="d3e2f-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 <span data-ttu-id="d3e2f-154">Aby uzyskać więcej informacji o sposobie używania `Select` klauzuli w języku Visual Basic, zobacz [wybierz klauzuli](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2f-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="d3e2f-155">Przyłączanie danych (łączenie i łączenie grupy)</span><span class="sxs-lookup"><span data-stu-id="d3e2f-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="d3e2f-156">Możesz łączyć więcej niż jedno źródło danych w `From` klauzuli na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="d3e2f-157">Na przykład poniższy kod używa dwóch źródeł danych i niejawnie łączy właściwości z obu z nich w wyniku.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="d3e2f-158">Zapytanie wybiera studentów, których ostatniego nazwy rozpoczynają się od samogłosek.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="d3e2f-159">Można uruchomić ten kod z listy studentów utworzone w [porady: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2f-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="d3e2f-160">`Join` — Słowo kluczowe jest odpowiednikiem `INNER JOIN` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="d3e2f-161">Łączy dwie kolekcje oparte na pasujących wartości klucza między elementami w dwie kolekcje.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="d3e2f-162">Zapytanie zwraca całość lub część elementy kolekcji, które pasują do wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="d3e2f-163">Na przykład następujący kod stanowi duplikat Akcja poprzedniego niejawne sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 <span data-ttu-id="d3e2f-164">`Group Join`łączy kolekcji do pojedynczego hierarchiczną kolekcję, tak jak `LEFT JOIN` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="d3e2f-165">Aby uzyskać więcej informacji, zobacz [klauzuli Join](../../../../visual-basic/language-reference/queries/join-clause.md) i [klauzuli Join grupy](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2f-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="d3e2f-166">Grupowanie danych (grupuj według)</span><span class="sxs-lookup"><span data-stu-id="d3e2f-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="d3e2f-167">Możesz dodać `Group By` klauzuli grupować elementy znajdujące się w wyniku zapytania, zgodnie z polami co najmniej jeden z elementów.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="d3e2f-168">Na przykład następujący kod grupy studentów przez rok klasy.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 <span data-ttu-id="d3e2f-169">Jeśli możesz uruchomić ten kod przy użyciu listy studentów utworzone w [porady: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), dane wyjściowe z `For Each` instrukcja jest:</span><span class="sxs-lookup"><span data-stu-id="d3e2f-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="d3e2f-170">Rok: inny poziom</span><span class="sxs-lookup"><span data-stu-id="d3e2f-170">Year: Junior</span></span>  
  
 <span data-ttu-id="d3e2f-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="d3e2f-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="d3e2f-172">Kowalski, Hugo</span><span class="sxs-lookup"><span data-stu-id="d3e2f-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="d3e2f-173">Kowalski, Magdalena</span><span class="sxs-lookup"><span data-stu-id="d3e2f-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="d3e2f-174">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="d3e2f-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="d3e2f-175">Rok: starszy</span><span class="sxs-lookup"><span data-stu-id="d3e2f-175">Year: Senior</span></span>  
  
 <span data-ttu-id="d3e2f-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="d3e2f-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="d3e2f-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="d3e2f-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="d3e2f-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="d3e2f-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="d3e2f-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="d3e2f-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="d3e2f-180">Pracownicy, Terry</span><span class="sxs-lookup"><span data-stu-id="d3e2f-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="d3e2f-181">Rok: IV rok</span><span class="sxs-lookup"><span data-stu-id="d3e2f-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="d3e2f-182">Rolecki, Tadeusz</span><span class="sxs-lookup"><span data-stu-id="d3e2f-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="d3e2f-183">Kowalski, Cesarowi</span><span class="sxs-lookup"><span data-stu-id="d3e2f-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="d3e2f-184">Zmiana pokazano w poniższym kodzie porządkuje lat klasy, a następnie zamówienia studentów w ramach co roku przez nazwisko.</span><span class="sxs-lookup"><span data-stu-id="d3e2f-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 <span data-ttu-id="d3e2f-185">Aby uzyskać więcej informacji na temat `Group By`, zobacz [grupy przez klauzuli](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3e2f-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e2f-186">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3e2f-186">See Also</span></span>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="d3e2f-187">Wprowadzenie do korzystania z LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3e2f-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="d3e2f-188">Zapytania</span><span class="sxs-lookup"><span data-stu-id="d3e2f-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="d3e2f-189">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3e2f-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="d3e2f-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="d3e2f-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
