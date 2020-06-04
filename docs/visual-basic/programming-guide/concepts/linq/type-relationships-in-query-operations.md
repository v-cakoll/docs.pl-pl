---
title: Relacje typu w operacjach zapytań LINQ
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
ms.openlocfilehash: 73a287541ddf115510bf6ab5c830eafac370cc3a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406732"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="7a1d6-102">Relacje typu w operacjach zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a1d6-102">Type Relationships in Query Operations (Visual Basic)</span></span>

<span data-ttu-id="7a1d6-103">Zmienne używane w operacjach zapytań programu Language-Integrated Query (LINQ) są silnie wpisywane i muszą być zgodne ze sobą.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-103">Variables used in Language-Integrated Query (LINQ) query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="7a1d6-104">W źródle danych jest używane silne wpisywanie, w samej kwerendzie i w wykonaniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="7a1d6-105">Na poniższej ilustracji przedstawiono terminy używane do opisywania zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-105">The following illustration identifies terms used to describe a LINQ query.</span></span> <span data-ttu-id="7a1d6-106">Aby uzyskać więcej informacji na temat części zapytania, zobacz [podstawowe operacje zapytań (Visual Basic)](basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="7a1d6-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](basic-query-operations.md).</span></span>

![Zrzut ekranu przedstawiający zapytanie pseudokodzie z wyróżnionymi elementami.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

<span data-ttu-id="7a1d6-108">Typ zmiennej zakresu w zapytaniu musi być zgodny z typem elementów w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="7a1d6-109">Typ zmiennej zapytania musi być zgodny z elementem sekwencji zdefiniowanym w `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="7a1d6-110">Na koniec typ elementów sekwencji musi być zgodny z typem zmiennej sterującej pętli, która jest używana w `For Each` instrukcji, która wykonuje zapytanie.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="7a1d6-111">To silne pisanie ułatwia identyfikację błędów typu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-111">This strong typing facilitates identification of type errors at compile time.</span></span>

<span data-ttu-id="7a1d6-112">Visual Basic sprawia, że silne wpisywanie jest wygodne przez implementację lokalnego wnioskowania o typie, znanego również jako *niejawne wpisywanie*.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="7a1d6-113">Ta funkcja jest używana w poprzednim przykładzie i zostanie wyświetlona w całym dokumencie przykłady i dokumentacja LINQ.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-113">That feature is used in the previous example, and you will see it used throughout the LINQ samples and documentation.</span></span> <span data-ttu-id="7a1d6-114">W Visual Basic, wnioskowanie o typie lokalnym jest wykonywane po prostu przy użyciu `Dim` instrukcji bez `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="7a1d6-115">W poniższym przykładzie `city` jest silnie wpisana jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-115">In the following example, `city` is strongly typed as a string.</span></span>

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="7a1d6-116">Wnioskowanie o typie lokalnym działa tylko wtedy `Option Infer` , gdy jest ustawione na `On` .</span><span class="sxs-lookup"><span data-stu-id="7a1d6-116">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="7a1d6-117">Aby uzyskać więcej informacji, zobacz temat [opcja wnioskowanie](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7a1d6-117">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>

<span data-ttu-id="7a1d6-118">Jednak nawet jeśli używasz wnioskowania typu lokalnego w zapytaniu, te same relacje typu są obecne między zmiennymi w źródle danych, zmienną zapytania i pętlą wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="7a1d6-119">Warto zapoznać się z podstawowymi informacjami o tych relacjach typu podczas pisania zapytań LINQ lub pracy z przykładami i przykłady kodu w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-119">It is useful to have a basic understanding of these type relationships when you are writing LINQ queries, or working with the samples and code examples in the documentation.</span></span>

<span data-ttu-id="7a1d6-120">Może być konieczne określenie typu jawnego dla zmiennej zakresu, która nie jest zgodna z typem zwracanym ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="7a1d6-121">Możesz określić typ zmiennej zakresu przy użyciu `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-121">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="7a1d6-122">Jednak spowoduje to błąd, jeśli konwersja jest [konwersją zawężania](../../language-features/data-types/widening-and-narrowing-conversions.md) i `Option Strict` jest ustawiona na `On` .</span><span class="sxs-lookup"><span data-stu-id="7a1d6-122">However, this results in an error if the conversion is a [narrowing conversion](../../language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="7a1d6-123">Dlatego zalecamy przeprowadzenie konwersji na wartości pobrane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="7a1d6-124">Możesz przekonwertować wartości ze źródła danych na jawny typ zmiennej zakresu przy użyciu <xref:System.Linq.Enumerable.Cast%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="7a1d6-125">Możesz również rzutować wartości wybrane w `Select` klauzuli na jawny typ, który jest inny niż typ zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="7a1d6-126">Te punkty są zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-126">These points are illustrated in the following code.</span></span>

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="7a1d6-127">Zapytania, które zwracają wszystkie elementy danych źródłowych</span><span class="sxs-lookup"><span data-stu-id="7a1d6-127">Queries That Return Entire Elements of the Source Data</span></span>

<span data-ttu-id="7a1d6-128">Poniższy przykład pokazuje operację zapytania LINQ, która zwraca sekwencję elementów wybranych z danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-128">The following example shows a LINQ query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="7a1d6-129">Źródło, `names` ,, zawiera tablicę ciągów, a dane wyjściowe zapytania są sekwencją zawierającą ciągi, które zaczynają się literą M.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

<span data-ttu-id="7a1d6-130">Jest to odpowiednik poniższego kodu, ale jest znacznie krótszy i łatwiejszy do zapisu.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-130">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="7a1d6-131">Zależność od lokalnego wnioskowania typu w zapytaniach jest preferowanym stylem w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

<span data-ttu-id="7a1d6-132">Poniższe relacje istnieją w obu powyższych przykładach kodu, niezależnie od tego, czy typy są określane niejawnie czy jawnie.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>

1. <span data-ttu-id="7a1d6-133">Typ elementów w źródle danych, `names` jest typem zmiennej zakresu w `name` zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>

2. <span data-ttu-id="7a1d6-134">Typ wybranego obiektu, `name` , określa typ zmiennej zapytania, `mNames` .</span><span class="sxs-lookup"><span data-stu-id="7a1d6-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="7a1d6-135">Oto `name` ciąg, więc zmienna zapytania to IEnumerable (Of String) w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>

3. <span data-ttu-id="7a1d6-136">Zapytanie zdefiniowane w elemencie `mNames` jest wykonywane w `For Each` pętli.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-136">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="7a1d6-137">Pętla wykonuje iterację w wyniku wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-137">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="7a1d6-138">Ponieważ `mNames` , gdy jest wykonywany, zwróci sekwencję ciągów, Zmienna iteracji pętli, `nm` również jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>

## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="7a1d6-139">Zapytania zwracające jedno pole z wybranych elementów</span><span class="sxs-lookup"><span data-stu-id="7a1d6-139">Queries That Return One Field from Selected Elements</span></span>

<span data-ttu-id="7a1d6-140">Poniższy przykład pokazuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operację zapytania, która zwraca sekwencję zawierającą tylko jedną część każdego elementu wybranego ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="7a1d6-141">Zapytanie pobiera kolekcję `Customer` obiektów jako źródło danych i projektuje tylko `Name` Właściwość w wyniku.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="7a1d6-142">Ponieważ nazwa klienta jest ciągiem, zapytanie tworzy sekwencję ciągów jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-142">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>

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

<span data-ttu-id="7a1d6-143">Relacje między zmiennymi są podobne do tych w prostszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-143">The relationships between variables are like those in the simpler example.</span></span>

1. <span data-ttu-id="7a1d6-144">Typ elementów w źródle danych, `customers` jest typem zmiennej zakresu w `cust` zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="7a1d6-145">Ten typ jest w tym przykładzie `Customer` .</span><span class="sxs-lookup"><span data-stu-id="7a1d6-145">In this example, that type is `Customer`.</span></span>

2. <span data-ttu-id="7a1d6-146">`Select`Instrukcja zwraca `Name` Właściwość każdego `Customer` obiektu, a nie cały obiekt.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="7a1d6-147">Ponieważ `Name` jest ciągiem, zmienna zapytania, ponownie będzie `custNames` IEnumerable (Of String), a nie `Customer` .</span><span class="sxs-lookup"><span data-stu-id="7a1d6-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>

3. <span data-ttu-id="7a1d6-148">Ponieważ `custNames` reprezentuje sekwencję ciągów, `For Each` Zmienna iteracji pętli, `custName` musi być ciągiem.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>

<span data-ttu-id="7a1d6-149">Bez wnioskowania o typie lokalnym poprzedni przykład będzie bardziej skomplikowany do pisania i zrozumienia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>

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

## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="7a1d6-150">Zapytania, które wymagają typów anonimowych</span><span class="sxs-lookup"><span data-stu-id="7a1d6-150">Queries That Require Anonymous Types</span></span>

<span data-ttu-id="7a1d6-151">Poniższy przykład przedstawia bardziej skomplikowaną sytuację.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-151">The following example shows a more complex situation.</span></span> <span data-ttu-id="7a1d6-152">W poprzednim przykładzie było to wygodne do określenia typów dla wszystkich zmiennych jawnie.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="7a1d6-153">W tym przykładzie jest to niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-153">In this example, it is impossible.</span></span> <span data-ttu-id="7a1d6-154">Zamiast wybierać całe `Customer` elementy ze źródła danych lub pojedyncze pole z każdego elementu, `Select` klauzula w tej kwerendzie zwraca dwie właściwości oryginalnego `Customer` obiektu: `Name` i `City` .</span><span class="sxs-lookup"><span data-stu-id="7a1d6-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="7a1d6-155">W odpowiedzi na `Select` klauzulę, kompilator definiuje typ anonimowy, który zawiera te dwie właściwości.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="7a1d6-156">Wynikiem wykonywania `nameCityQuery` w `For Each` pętli jest kolekcja wystąpień nowego typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="7a1d6-157">Ponieważ typ anonimowy nie ma użytecznych nazw, nie można określić typu `nameCityQuery` ani `custInfo` jawnie.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="7a1d6-158">Oznacza to, że z typem anonimowym nie ma nazwy typu do użycia zamiast `String` w `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="7a1d6-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="7a1d6-159">Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="7a1d6-159">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

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

<span data-ttu-id="7a1d6-160">Chociaż nie jest możliwe określenie typów dla wszystkich zmiennych w poprzednim przykładzie, relacje pozostają takie same.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>

1. <span data-ttu-id="7a1d6-161">Typ elementów w źródle danych jest ponownie typem zmiennej zakresu w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-161">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="7a1d6-162">W tym przykładzie `cust` jest wystąpieniem `Customer` .</span><span class="sxs-lookup"><span data-stu-id="7a1d6-162">In this example, `cust` is an instance of `Customer`.</span></span>

2. <span data-ttu-id="7a1d6-163">Ponieważ `Select` instrukcja generuje typ anonimowy, zmienna zapytania, `nameCityQuery` musi być jawnie wpisana jako typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="7a1d6-164">Typ anonimowy nie ma użytecznych nazw i dlatego nie może być określony jawnie.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>

3. <span data-ttu-id="7a1d6-165">Typ zmiennej iteracji w `For Each` pętli jest typu anonimowego utworzonego w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="7a1d6-166">Ponieważ typ nie ma użytecznych nazw, typ zmiennej iteracji pętli musi być określony niejawnie.</span><span class="sxs-lookup"><span data-stu-id="7a1d6-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a1d6-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a1d6-167">See also</span></span>

- [<span data-ttu-id="7a1d6-168">Wprowadzenie do programu LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a1d6-168">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="7a1d6-169">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="7a1d6-169">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="7a1d6-170">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="7a1d6-170">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="7a1d6-171">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a1d6-171">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="7a1d6-172">LINQ</span><span class="sxs-lookup"><span data-stu-id="7a1d6-172">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="7a1d6-173">Zapytania</span><span class="sxs-lookup"><span data-stu-id="7a1d6-173">Queries</span></span>](../../../language-reference/queries/index.md)
