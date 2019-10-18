---
title: Relacje typu w operacjach zapytań (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: 6d5d13064cceba10d27901ee95aa8b6731620dbb
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524112"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="ae314-102">Relacje typu w operacjach zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae314-102">Type Relationships in Query Operations (Visual Basic)</span></span>

<span data-ttu-id="ae314-103">Zmienne używane w operacjach zapytania [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] są silnie wpisane i muszą być zgodne ze sobą.</span><span class="sxs-lookup"><span data-stu-id="ae314-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="ae314-104">W źródle danych jest używane silne wpisywanie, w samej kwerendzie i w wykonaniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="ae314-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="ae314-105">Na poniższej ilustracji przedstawiono terminy używane do opisywania zapytania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae314-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="ae314-106">Aby uzyskać więcej informacji na temat części zapytania, zobacz [podstawowe operacje zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ae314-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>

![Zrzut ekranu przedstawiający zapytanie pseudokodzie z wyróżnionymi elementami.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

<span data-ttu-id="ae314-108">Typ zmiennej zakresu w zapytaniu musi być zgodny z typem elementów w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="ae314-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="ae314-109">Typ zmiennej zapytania musi być zgodny z elementem sekwencji zdefiniowanym w klauzuli `Select`.</span><span class="sxs-lookup"><span data-stu-id="ae314-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="ae314-110">Na koniec typ elementów sekwencji musi być zgodny z typem zmiennej sterującej pętli, która jest używana w instrukcji `For Each`, która wykonuje zapytanie.</span><span class="sxs-lookup"><span data-stu-id="ae314-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="ae314-111">To silne pisanie ułatwia identyfikację błędów typu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ae314-111">This strong typing facilitates identification of type errors at compile time.</span></span>

<span data-ttu-id="ae314-112">Visual Basic sprawia, że silne wpisywanie jest wygodne przez implementację lokalnego wnioskowania o typie, znanego również jako *niejawne wpisywanie*.</span><span class="sxs-lookup"><span data-stu-id="ae314-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="ae314-113">Ta funkcja jest używana w poprzednim przykładzie i zostanie wyświetlona w całym [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przykłady i dokumentacja.</span><span class="sxs-lookup"><span data-stu-id="ae314-113">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="ae314-114">W Visual Basic, wnioskowanie typu lokalnego jest wykonywane po prostu przy użyciu instrukcji `Dim` bez klauzuli `As`.</span><span class="sxs-lookup"><span data-stu-id="ae314-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="ae314-115">W poniższym przykładzie `city` jest silnie wpisana jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="ae314-115">In the following example, `city` is strongly typed as a string.</span></span>

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="ae314-116">Wnioskowanie o typie lokalnym działa tylko wtedy, gdy `Option Infer` jest ustawiony na `On`.</span><span class="sxs-lookup"><span data-stu-id="ae314-116">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="ae314-117">Aby uzyskać więcej informacji, zobacz temat [opcja wnioskowanie](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ae314-117">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>

<span data-ttu-id="ae314-118">Jednak nawet jeśli używasz wnioskowania typu lokalnego w zapytaniu, te same relacje typu są obecne między zmiennymi w źródle danych, zmienną zapytania i pętlą wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="ae314-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="ae314-119">Warto zapoznać się z podstawowymi informacjami o tych relacjach typu podczas pisania zapytań [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] lub pracy z przykładami i przykłady kodu w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="ae314-119">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>

<span data-ttu-id="ae314-120">Może być konieczne określenie typu jawnego dla zmiennej zakresu, która nie jest zgodna z typem zwracanym ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ae314-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="ae314-121">Możesz określić typ zmiennej zakresu przy użyciu klauzuli `As`.</span><span class="sxs-lookup"><span data-stu-id="ae314-121">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="ae314-122">Powoduje to jednak błąd, jeśli konwersja jest [konwersją zawężania](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) , a `Option Strict` jest ustawiona na `On`.</span><span class="sxs-lookup"><span data-stu-id="ae314-122">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="ae314-123">Dlatego zalecamy przeprowadzenie konwersji na wartości pobrane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ae314-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="ae314-124">Możesz przekonwertować wartości ze źródła danych na jawny typ zmiennej zakresu przy użyciu metody <xref:System.Linq.Enumerable.Cast%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae314-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="ae314-125">Możesz również rzutować wartości wybrane w klauzuli `Select` na jawny typ, który jest inny niż typ zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="ae314-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="ae314-126">Te punkty są zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ae314-126">These points are illustrated in the following code.</span></span>

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="ae314-127">Zapytania, które zwracają wszystkie elementy danych źródłowych</span><span class="sxs-lookup"><span data-stu-id="ae314-127">Queries That Return Entire Elements of the Source Data</span></span>

<span data-ttu-id="ae314-128">Poniższy przykład pokazuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operacji zapytania, która zwraca sekwencję elementów wybranych z danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="ae314-128">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="ae314-129">Źródło, `names`, zawiera tablicę ciągów, a dane wyjściowe zapytania są sekwencją zawierającą ciągi, które zaczynają się literą M.</span><span class="sxs-lookup"><span data-stu-id="ae314-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

<span data-ttu-id="ae314-130">Jest to odpowiednik poniższego kodu, ale jest znacznie krótszy i łatwiejszy do zapisu.</span><span class="sxs-lookup"><span data-stu-id="ae314-130">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="ae314-131">Zależność od lokalnego wnioskowania typu w zapytaniach jest preferowanym stylem w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ae314-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

<span data-ttu-id="ae314-132">Poniższe relacje istnieją w obu powyższych przykładach kodu, niezależnie od tego, czy typy są określane niejawnie czy jawnie.</span><span class="sxs-lookup"><span data-stu-id="ae314-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>

1. <span data-ttu-id="ae314-133">Typ elementów w źródle danych `names`, jest typem zmiennej zakresu, `name` w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="ae314-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>

2. <span data-ttu-id="ae314-134">Typ obiektu, który jest zaznaczony, `name` określa typ zmiennej zapytania, `mNames`.</span><span class="sxs-lookup"><span data-stu-id="ae314-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="ae314-135">W tym miejscu `name` jest ciągiem, więc zmienna zapytania to IEnumerable (Of String) w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ae314-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>

3. <span data-ttu-id="ae314-136">Zapytanie zdefiniowane w `mNames` jest wykonywane w pętli `For Each`.</span><span class="sxs-lookup"><span data-stu-id="ae314-136">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="ae314-137">Pętla wykonuje iterację w wyniku wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="ae314-137">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="ae314-138">Ponieważ `mNames`, gdy jest wykonywane, zwróci sekwencję ciągów, Zmienna iteracji pętli, `nm`, również jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="ae314-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>

## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="ae314-139">Zapytania zwracające jedno pole z wybranych elementów</span><span class="sxs-lookup"><span data-stu-id="ae314-139">Queries That Return One Field from Selected Elements</span></span>

<span data-ttu-id="ae314-140">Poniższy przykład pokazuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operacji zapytania, która zwraca sekwencję zawierającą tylko jedną część każdego elementu wybranego ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ae314-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="ae314-141">Zapytanie pobiera kolekcję `Customer` obiektów jako źródła danych i projektuje tylko Właściwość `Name` w wyniku.</span><span class="sxs-lookup"><span data-stu-id="ae314-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="ae314-142">Ponieważ nazwa klienta jest ciągiem, zapytanie tworzy sekwencję ciągów jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ae314-142">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim custNames = From cust In customers
                Where cust.City = "London"
                Select cust.Name

For Each custName In custNames
    Console.WriteLine(custName)
Next
```

<span data-ttu-id="ae314-143">Relacje między zmiennymi są podobne do tych w prostszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ae314-143">The relationships between variables are like those in the simpler example.</span></span>

1. <span data-ttu-id="ae314-144">Typ elementów w źródle danych `customers`, jest typem zmiennej zakresu, `cust` w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="ae314-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="ae314-145">W tym przykładzie ten typ jest `Customer`.</span><span class="sxs-lookup"><span data-stu-id="ae314-145">In this example, that type is `Customer`.</span></span>

2. <span data-ttu-id="ae314-146">Instrukcja `Select` zwraca właściwość `Name` każdego obiektu `Customer` zamiast całego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ae314-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="ae314-147">Ponieważ `Name` jest ciągiem, zmienna zapytania, `custNames`, ponownie będzie IEnumerable (Of String), a nie `Customer`.</span><span class="sxs-lookup"><span data-stu-id="ae314-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>

3. <span data-ttu-id="ae314-148">Ponieważ `custNames` reprezentuje sekwencję ciągów, Zmienna iteracji pętli `For Each`, `custName`, musi być ciągiem.</span><span class="sxs-lookup"><span data-stu-id="ae314-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>

<span data-ttu-id="ae314-149">Bez wnioskowania o typie lokalnym poprzedni przykład będzie bardziej skomplikowany do pisania i zrozumienia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ae314-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()
 Dim custNames As IEnumerable(Of String) =
     From cust As Customer In customers
     Where cust.City = "London"
     Select cust.Name

 For Each custName As String In custNames
     Console.WriteLine(custName)
 Next
```

## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="ae314-150">Zapytania, które wymagają typów anonimowych</span><span class="sxs-lookup"><span data-stu-id="ae314-150">Queries That Require Anonymous Types</span></span>

<span data-ttu-id="ae314-151">Poniższy przykład przedstawia bardziej skomplikowaną sytuację.</span><span class="sxs-lookup"><span data-stu-id="ae314-151">The following example shows a more complex situation.</span></span> <span data-ttu-id="ae314-152">W poprzednim przykładzie było to wygodne do określenia typów dla wszystkich zmiennych jawnie.</span><span class="sxs-lookup"><span data-stu-id="ae314-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="ae314-153">W tym przykładzie jest to niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="ae314-153">In this example, it is impossible.</span></span> <span data-ttu-id="ae314-154">Zamiast wybierać całe `Customer` elementy ze źródła danych lub pojedyncze pole z każdego elementu, klauzula `Select` w tym zapytaniu zwraca dwie właściwości oryginalnego obiektu `Customer`: `Name` i `City`.</span><span class="sxs-lookup"><span data-stu-id="ae314-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="ae314-155">W odpowiedzi na klauzulę `Select`, kompilator definiuje typ anonimowy, który zawiera te dwie właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae314-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="ae314-156">Wynikiem wykonywania `nameCityQuery` w pętli `For Each` jest kolekcja wystąpień nowego typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="ae314-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="ae314-157">Ponieważ typ anonimowy nie ma użytecznych nazw, nie można jawnie określić typu `nameCityQuery` lub `custInfo`.</span><span class="sxs-lookup"><span data-stu-id="ae314-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="ae314-158">Oznacza to, że z typem anonimowym nie ma nazwy typu do użycia zamiast `String` w `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="ae314-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="ae314-159">Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="ae314-159">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim nameCityQuery = From cust In customers
                    Where cust.City = "London"
                    Select cust.Name, cust.City

For Each custInfo In nameCityQuery
    Console.WriteLine(custInfo.Name)
Next
```

<span data-ttu-id="ae314-160">Chociaż nie jest możliwe określenie typów dla wszystkich zmiennych w poprzednim przykładzie, relacje pozostają takie same.</span><span class="sxs-lookup"><span data-stu-id="ae314-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>

1. <span data-ttu-id="ae314-161">Typ elementów w źródle danych jest ponownie typem zmiennej zakresu w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="ae314-161">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="ae314-162">W tym przykładzie `cust` jest wystąpieniem `Customer`.</span><span class="sxs-lookup"><span data-stu-id="ae314-162">In this example, `cust` is an instance of `Customer`.</span></span>

2. <span data-ttu-id="ae314-163">Ponieważ instrukcja `Select` generuje typ anonimowy, zmienna zapytania, `nameCityQuery`, musi być jawnie wpisana jako typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="ae314-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="ae314-164">Typ anonimowy nie ma użytecznych nazw i dlatego nie może być określony jawnie.</span><span class="sxs-lookup"><span data-stu-id="ae314-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>

3. <span data-ttu-id="ae314-165">Typ zmiennej iteracji w pętli `For Each` jest typem anonimowym utworzonym w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="ae314-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="ae314-166">Ponieważ typ nie ma użytecznych nazw, typ zmiennej iteracji pętli musi być określony niejawnie.</span><span class="sxs-lookup"><span data-stu-id="ae314-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae314-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae314-167">See also</span></span>

- [<span data-ttu-id="ae314-168">Wprowadzenie ze składnikami LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae314-168">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="ae314-169">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="ae314-169">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="ae314-170">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="ae314-170">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="ae314-171">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae314-171">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ae314-172">LINQ</span><span class="sxs-lookup"><span data-stu-id="ae314-172">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="ae314-173">Zapytania</span><span class="sxs-lookup"><span data-stu-id="ae314-173">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
