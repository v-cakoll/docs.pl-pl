---
title: Podstawowe operacje zapytań (Visual Basic)
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
ms.openlocfilehash: ed5ed56366911c3676c4413711207ac0a8f85765
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826200"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="82227-102">Podstawowe operacje zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82227-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="82227-103">Ten temat zawiera krótkie wprowadzenie do [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] wyrażenia w języku Visual Basic i niektóre typowe rodzaje operacji, które można wykonywać w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="82227-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="82227-104">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="82227-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="82227-105">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82227-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="82227-106">Zapytania</span><span class="sxs-lookup"><span data-stu-id="82227-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="82227-107">Przewodnik: Pisanie zapytań w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82227-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="82227-108">Określanie źródła danych (z)</span><span class="sxs-lookup"><span data-stu-id="82227-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="82227-109">W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, pierwszym krokiem jest określenie źródła danych, które chcesz zbadać.</span><span class="sxs-lookup"><span data-stu-id="82227-109">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="82227-110">W związku z tym `From` podklauzul zawsze wykorzystasz.</span><span class="sxs-lookup"><span data-stu-id="82227-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="82227-111">Operatory zapytań wybierz i kształtów wyników na podstawie typu źródła.</span><span class="sxs-lookup"><span data-stu-id="82227-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="82227-112">`From` Klauzula Określa źródło danych `customers`, a *zmiennej zakresu*, `cust`.</span><span class="sxs-lookup"><span data-stu-id="82227-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="82227-113">Zmienna zakresu przypomina Zmienna iteracji pętli, z tą różnicą, że w wyrażeniu zapytania wystąpi nie rzeczywiste iteracji.</span><span class="sxs-lookup"><span data-stu-id="82227-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="82227-114">Jeśli zapytanie jest wykonywane, często za pomocą `For Each` pętli, zmienna zakresu służy jako punkt odniesienia, aby każdy element w `customers`.</span><span class="sxs-lookup"><span data-stu-id="82227-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="82227-115">Ponieważ kompilator może wywnioskować typ `cust`, nie trzeba określić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="82227-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="82227-116">Przykłady zapytań napisane i bez jawnych typowań, zobacz [relacje typu w operacjach zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="82227-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="82227-117">Aby uzyskać więcej informacji o sposobie używania `From` klauzuli w języku Visual Basic, zobacz [klauzuli From](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="82227-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="82227-118">Filtrowanie danych (gdzie)</span><span class="sxs-lookup"><span data-stu-id="82227-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="82227-119">Prawdopodobnie najbardziej typowych operacji zapytania jest stosowanie filtru w postaci wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="82227-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="82227-120">Zapytanie jest następnie zwraca tylko te elementy, dla których wyrażenie jest prawdziwe.</span><span class="sxs-lookup"><span data-stu-id="82227-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="82227-121">Element `Where` jest używana do wykonywania filtrowania.</span><span class="sxs-lookup"><span data-stu-id="82227-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="82227-122">Filtr określa, które elementy w źródle danych, które mają zostać objęte wynikowa sekwencja.</span><span class="sxs-lookup"><span data-stu-id="82227-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="82227-123">W poniższym przykładzie dołączono tych klientów, którzy mają adres w Londynie.</span><span class="sxs-lookup"><span data-stu-id="82227-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="82227-124">Można użyć operatorów logicznych, takich jak `And` i `Or` połączyć wyrażenia filtru w `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="82227-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="82227-125">Na przykład aby zwrócić tylko tych klientów, którzy są z Londynu, i której nazwa to Devon, należy użyć następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="82227-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="82227-126">Aby zwrócić klienci z Londynu lub Paryż, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="82227-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="82227-127">Aby uzyskać więcej informacji o sposobie używania `Where` klauzuli w języku Visual Basic, zobacz [klauzuli Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="82227-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="82227-128">Szeregowanie danych (porządkuj wg)</span><span class="sxs-lookup"><span data-stu-id="82227-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="82227-129">Często jest wygodne posortować dane zwrócone w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="82227-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="82227-130">`Order By` Klauzuli spowoduje, że elementy w zwracanej sekwencji sortowania na określone pole lub pola.</span><span class="sxs-lookup"><span data-stu-id="82227-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="82227-131">Na przykład poniższe zapytanie sortuje wyniki na podstawie `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="82227-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="82227-132">Ponieważ `Name` jest ciągiem, zwrócone dane zostaną posortowane alfabetycznie, od A do Z.</span><span class="sxs-lookup"><span data-stu-id="82227-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="82227-133">Aby uporządkować wyniki w odwrotnej kolejności od Z do A, należy użyć `Order By...Descending` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="82227-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="82227-134">Wartość domyślna to `Ascending` podczas ani `Ascending` ani `Descending` jest określony.</span><span class="sxs-lookup"><span data-stu-id="82227-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="82227-135">Aby uzyskać więcej informacji o sposobie używania `Order By` klauzuli w języku Visual Basic, zobacz [klauzula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="82227-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="82227-136">Wybieranie danych (wybór)</span><span class="sxs-lookup"><span data-stu-id="82227-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="82227-137">`Select` Klauzula określa formularza i zawartości zwróconych elementów.</span><span class="sxs-lookup"><span data-stu-id="82227-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="82227-138">Na przykład można określić, czy wyniki będą zawierać pełną `Customer` obiektów, co najmniej jeden `Customer` właściwości, podzbiór właściwości, kombinacja właściwości z różnych źródeł danych lub nowego typu wyniku w oparciu o obliczenie.</span><span class="sxs-lookup"><span data-stu-id="82227-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="82227-139">Gdy `Select` klauzuli tworzy coś innego niż kopię elementu źródłowego, operacja jest nazywana *projekcji*.</span><span class="sxs-lookup"><span data-stu-id="82227-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="82227-140">Aby pobrać kolekcję, która składa się z pełną `Customer` obiektów, zaznacz sama zmienna zakresu:</span><span class="sxs-lookup"><span data-stu-id="82227-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="82227-141">Jeśli `Customer` wystąpienie jest dużego obiektu, który ma wiele pól i wszystkie opcje, które mają zostać pobrane to nazwa, możesz wybrać `cust.Name`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="82227-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="82227-142">Wnioskowanie o typie lokalnym rozpoznaje, spowoduje to zmianę typu wyniku z kolekcji `Customer` obiekty kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="82227-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="82227-143">Aby wybrać wiele pól ze źródła danych, dostępne są dwie opcje:</span><span class="sxs-lookup"><span data-stu-id="82227-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
-   <span data-ttu-id="82227-144">W `Select` klauzuli, określ pola, które chcesz uwzględnić w wyniku.</span><span class="sxs-lookup"><span data-stu-id="82227-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="82227-145">Kompilator określi typ anonimowy, który ma te pola z jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="82227-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="82227-146">Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="82227-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="82227-147">Ponieważ zwróconych elementów w poniższym przykładzie są wystąpieniami typu anonimowego, nie możesz odwołać się do typu według nazwy innym miejscu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="82227-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="82227-148">Nazwy wyznaczony przez kompilator typu zawiera znaki, które nie są dozwolone w normalnym kodu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="82227-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="82227-149">W poniższym przykładzie elementów w kolekcji, który jest zwracany przez zapytanie w `londonCusts4` są wystąpieniami typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="82227-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="82227-150">—lub—</span><span class="sxs-lookup"><span data-stu-id="82227-150">-or-</span></span>  
  
-   <span data-ttu-id="82227-151">Definiowanie typu nazwanego, który zawiera określonego pola, które chcesz uwzględnić w wyniku i tworzenie i Inicjowanie wystąpienia typu w `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="82227-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="82227-152">Użyj tej opcji tylko wtedy, gdy trzeba użyć poszczególnych wyników spoza kolekcji, w której są zwracane, lub jeśli trzeba przekazać je jako parametry w wywołaniach metod.</span><span class="sxs-lookup"><span data-stu-id="82227-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="82227-153">Typ `londonCusts5` w poniższym przykładzie jest IEnumerable (Of NamePhone).</span><span class="sxs-lookup"><span data-stu-id="82227-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="82227-154">Aby uzyskać więcej informacji o sposobie używania `Select` klauzuli w języku Visual Basic, zobacz [wybierz klauzuli](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="82227-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="82227-155">Przyłączanie danych (łączenie i łączenie grupy)</span><span class="sxs-lookup"><span data-stu-id="82227-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="82227-156">Można połączyć więcej niż jednego źródła danych w `From` klauzuli na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="82227-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="82227-157">Na przykład poniższy kod używa dwóch źródeł danych i niejawnie łączy właściwości z obu z nich w wyniku.</span><span class="sxs-lookup"><span data-stu-id="82227-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="82227-158">Zapytanie wybiera studentów, w których nazwiska rozpoczynać się od samogłosek.</span><span class="sxs-lookup"><span data-stu-id="82227-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
>  <span data-ttu-id="82227-159">Ten kod można uruchomić za pomocą listy studentów utworzone w [jak: Utwórz listę elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="82227-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="82227-160">`Join` — Słowo kluczowe jest odpowiednikiem `INNER JOIN` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="82227-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="82227-161">Łączy dwie kolekcje na podstawie dopasowania wartości kluczy między elementami w dwóch kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="82227-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="82227-162">Zapytanie zwraca całości lub części elementów kolekcji, które pasują do wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="82227-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="82227-163">Na przykład poniższy kod duplikuje Akcja poprzedniego łączenia niejawnego.</span><span class="sxs-lookup"><span data-stu-id="82227-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="82227-164">`Group Join` Podobnie jak łączy kolekcje w jedną hierarchiczną kolekcję `LEFT JOIN` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="82227-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="82227-165">Aby uzyskać więcej informacji, zobacz [klauzuli Join](../../../../visual-basic/language-reference/queries/join-clause.md) i [Group Join — klauzula](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="82227-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="82227-166">Grupowanie danych (grupuj według)</span><span class="sxs-lookup"><span data-stu-id="82227-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="82227-167">Możesz dodać `Group By` klauzuli do grupowania elementów w wyniku zapytania zgodnie z co najmniej jednego pola elementów.</span><span class="sxs-lookup"><span data-stu-id="82227-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="82227-168">Na przykład poniższy kod grupy uczniów według klasy, roku.</span><span class="sxs-lookup"><span data-stu-id="82227-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="82227-169">Jeśli można uruchomić ten kod przy użyciu listy studentów utworzone w [jak: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), dane wyjściowe z `For Each` instrukcja jest:</span><span class="sxs-lookup"><span data-stu-id="82227-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="82227-170">Rok: Inny poziom</span><span class="sxs-lookup"><span data-stu-id="82227-170">Year: Junior</span></span>  
  
 <span data-ttu-id="82227-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="82227-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="82227-172">Garcia-Hugo</span><span class="sxs-lookup"><span data-stu-id="82227-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="82227-173">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="82227-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="82227-174">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="82227-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="82227-175">Rok: Starszy</span><span class="sxs-lookup"><span data-stu-id="82227-175">Year: Senior</span></span>  
  
 <span data-ttu-id="82227-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="82227-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="82227-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="82227-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="82227-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="82227-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="82227-179">We Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="82227-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="82227-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="82227-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="82227-181">Rok: IV rok</span><span class="sxs-lookup"><span data-stu-id="82227-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="82227-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="82227-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="82227-183">Garcia-Cesarowi</span><span class="sxs-lookup"><span data-stu-id="82227-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="82227-184">Odmiany pokazano w poniższym kodzie porządkuje lat klasy, a następnie porządkuje według nazwiska uczniów w każdym roku.</span><span class="sxs-lookup"><span data-stu-id="82227-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="82227-185">Aby uzyskać więcej informacji na temat `Group By`, zobacz [grupy przez klauzulę](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="82227-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82227-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82227-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="82227-187">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82227-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="82227-188">Zapytania</span><span class="sxs-lookup"><span data-stu-id="82227-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="82227-189">Omówienie operatorów standardowej kwerendy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82227-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="82227-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="82227-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
