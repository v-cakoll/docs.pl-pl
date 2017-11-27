---
title: "Relacje typu w operacjach zapytań (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b93188475dd2bb00aea044ff178028eb87e00d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="6b4df-102">Relacje typu w operacjach zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b4df-102">Type Relationships in Query Operations (Visual Basic)</span></span>
<span data-ttu-id="6b4df-103">Zmienne używane w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] zapytania operacje są silnie typizowane i muszą być zgodne ze sobą.</span><span class="sxs-lookup"><span data-stu-id="6b4df-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="6b4df-104">Silne wpisywanie jest używany w źródle danych, samą kwerendę i do wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="6b4df-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="6b4df-105">Poniższa ilustracja identyfikuje terminów używanych w celu opisania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="6b4df-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="6b4df-106">Aby uzyskać więcej informacji na temat części zapytania, zobacz [podstawowe operacje zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="6b4df-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>  
  
 <span data-ttu-id="6b4df-107">![Zapytanie pseudocode z wyróżnionym elementów. ] (../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span><span class="sxs-lookup"><span data-stu-id="6b4df-107">![Pseudocode query with elements highlighted.](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span></span>  
<span data-ttu-id="6b4df-108">Części zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="6b4df-108">Parts of a LINQ query</span></span>  
  
 <span data-ttu-id="6b4df-109">Typ zmiennej zakresu w zapytaniu musi być zgodny z typem elementów w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="6b4df-109">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="6b4df-110">Typu zmienną zapytania musi być zgodny z elementem sekwencji zdefiniowane w `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6b4df-110">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="6b4df-111">Na koniec typ elementów sekwencji również musi być zgodny z typem zmienna sterująca pętli, który jest używany w `For Each` instrukcji, która wykonuje zapytania.</span><span class="sxs-lookup"><span data-stu-id="6b4df-111">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="6b4df-112">Silne wpisywanie ułatwia identyfikację typu błędy w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6b4df-112">This strong typing facilitates identification of type errors at compile time.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="6b4df-113">powoduje, że silne wpisywanie wygodne zaimplementowanie wnioskowanie o typie lokalnym, znanej także jako *niejawne wpisując*.</span><span class="sxs-lookup"><span data-stu-id="6b4df-113"> makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="6b4df-114">Funkcja jest używana w poprzednim przykładzie, czy pojawi się on w całym [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przykłady i dokumentacja.</span><span class="sxs-lookup"><span data-stu-id="6b4df-114">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="6b4df-115">W języku Visual Basic wnioskowanie o typie lokalnym odbywa się przy użyciu `Dim` instrukcję bez `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6b4df-115">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="6b4df-116">W poniższym przykładzie `city` jest silnie typizowane jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="6b4df-116">In the following example, `city` is strongly typed as a string.</span></span>  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="6b4df-117">Wnioskowanie o typie lokalnym działa tylko wtedy, gdy `Option Infer` ma ustawioną wartość `On`.</span><span class="sxs-lookup"><span data-stu-id="6b4df-117">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="6b4df-118">Aby uzyskać więcej informacji, zobacz [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6b4df-118">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
 <span data-ttu-id="6b4df-119">Jednak nawet wtedy, gdy używasz wnioskowanie o typie lokalnym w zapytaniu tego samego typu relacji znajdują się między zmiennych w źródle danych, do zmiennej zapytania i pętlę wykonania zapytania.</span><span class="sxs-lookup"><span data-stu-id="6b4df-119">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="6b4df-120">Warto mieć podstawową wiedzę na temat tych relacji typu podczas pisania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania lub Praca z przykładów i przykładów kodu w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="6b4df-120">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>  
  
 <span data-ttu-id="6b4df-121">Może być konieczne określenie jawnego typu dla zmiennej zakresu, który jest niezgodny z typem zwracanym ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="6b4df-121">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="6b4df-122">Typ zmiennej zakresu można określić za pomocą `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6b4df-122">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="6b4df-123">Jednak to powoduje wystąpienie błędu w przypadku konwersji [konwersja zawężająca](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) i `Option Strict` ma ustawioną wartość `On`.</span><span class="sxs-lookup"><span data-stu-id="6b4df-123">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="6b4df-124">Dlatego zaleca się dokonać konwersji wartości pobrane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="6b4df-124">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="6b4df-125">Można przekonwertować wartości ze źródła danych na typ zmiennej jawnej zakresu przy użyciu <xref:System.Linq.Enumerable.Cast%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6b4df-125">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="6b4df-126">Można również rzutowania wartości wybrane w `Select` klauzulę jawnego typu, który różni się od typu zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="6b4df-126">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="6b4df-127">Punkty te zostały przedstawione w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6b4df-127">These points are illustrated in the following code.</span></span>  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="6b4df-128">Zapytań zwracających elementy całego źródła danych</span><span class="sxs-lookup"><span data-stu-id="6b4df-128">Queries That Return Entire Elements of the Source Data</span></span>  
 <span data-ttu-id="6b4df-129">W poniższym przykładzie przedstawiono [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operację, która zwraca sekwencję elementów wybrane źródła danych z zapytania.</span><span class="sxs-lookup"><span data-stu-id="6b4df-129">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="6b4df-130">Źródło, `names`, zawiera tablicę ciągów, i wyników zapytania jest sekwencją zawierającego ciągi rozpoczynające się od litery M.</span><span class="sxs-lookup"><span data-stu-id="6b4df-130">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 <span data-ttu-id="6b4df-131">To jest odpowiednikiem następujący kod, ale jest znacznie krótsze i łatwiejsze do zapisu.</span><span class="sxs-lookup"><span data-stu-id="6b4df-131">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="6b4df-132">Zależność od wnioskowanie o typie lokalnym w zapytaniach jest preferowanym stylu w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6b4df-132">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 <span data-ttu-id="6b4df-133">Następujące relacje istnieje zarówno w poprzednich przykładach kodu, czy typy są określone jawnie lub niejawnie.</span><span class="sxs-lookup"><span data-stu-id="6b4df-133">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>  
  
1.  <span data-ttu-id="6b4df-134">Typ elementów w źródle danych `names`, jest typu zmienną zakresu `name`, w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="6b4df-134">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>  
  
2.  <span data-ttu-id="6b4df-135">Typ obiektu, który jest zaznaczone, `name`, określa typu zmienną zapytania `mNames`.</span><span class="sxs-lookup"><span data-stu-id="6b4df-135">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="6b4df-136">W tym miejscu `name` jest ciągu, więc do zmiennej zapytania jest IEnumerable (Of String) w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6b4df-136">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>  
  
3.  <span data-ttu-id="6b4df-137">Zapytanie określone w `mNames` są wykonywane w `For Each` pętli.</span><span class="sxs-lookup"><span data-stu-id="6b4df-137">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="6b4df-138">Pętla wykonuje iterację na wynik wykonania zapytania.</span><span class="sxs-lookup"><span data-stu-id="6b4df-138">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="6b4df-139">Ponieważ `mNames`po wykonaniu, będzie zwracać sekwencję ciągów, Zmienna iteracji pętli, `nm`, również jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="6b4df-139">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="6b4df-140">Zapytań zwracających jedno pole z wybranych elementów</span><span class="sxs-lookup"><span data-stu-id="6b4df-140">Queries That Return One Field from Selected Elements</span></span>  
 <span data-ttu-id="6b4df-141">W poniższym przykładzie przedstawiono [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zapytania operację, która zwraca sekwencji zawierających tylko jedną część każdego elementu wybrane źródło danych.</span><span class="sxs-lookup"><span data-stu-id="6b4df-141">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="6b4df-142">Zapytanie pobiera zbiór `Customer` obiekty jako źródło danych i tylko projekty `Name` właściwości w wyniku.</span><span class="sxs-lookup"><span data-stu-id="6b4df-142">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="6b4df-143">Ponieważ nazwy klienta jest ciągiem, zapytanie tworzy sekwencję ciągi jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="6b4df-143">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>  
  
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
  
 <span data-ttu-id="6b4df-144">Relacje zmienne są podobnie jak w przykładzie prostsze.</span><span class="sxs-lookup"><span data-stu-id="6b4df-144">The relationships between variables are like those in the simpler example.</span></span>  
  
1.  <span data-ttu-id="6b4df-145">Typ elementów w źródle danych `customers`, jest typu zmienną zakresu `cust`, w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="6b4df-145">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="6b4df-146">W tym przykładzie, który jest typu `Customer`.</span><span class="sxs-lookup"><span data-stu-id="6b4df-146">In this example, that type is `Customer`.</span></span>  
  
2.  <span data-ttu-id="6b4df-147">`Select` Zwraca instrukcji `Name` właściwości każdego `Customer` obiektu, a nie całym obiektem.</span><span class="sxs-lookup"><span data-stu-id="6b4df-147">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="6b4df-148">Ponieważ `Name` to ciąg do zmiennej zapytania `custNames`, ponownie IEnumerable (Of String), nie będzie z `Customer`.</span><span class="sxs-lookup"><span data-stu-id="6b4df-148">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>  
  
3.  <span data-ttu-id="6b4df-149">Ponieważ `custNames` reprezentuje sekwencję ciągów, `For Each` zmiennej iteracji pętli, `custName`, musi być ciągiem.</span><span class="sxs-lookup"><span data-stu-id="6b4df-149">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>  
  
 <span data-ttu-id="6b4df-150">Bez wnioskowanie o typie lokalnym poprzedni przykład będzie bardziej skomplikowane, zapisu i zrozumieć, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6b4df-150">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>  
  
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
  
## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="6b4df-151">Zapytania wymagające typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="6b4df-151">Queries That Require Anonymous Types</span></span>  
 <span data-ttu-id="6b4df-152">W poniższym przykładzie przedstawiono bardziej złożonych sytuacji.</span><span class="sxs-lookup"><span data-stu-id="6b4df-152">The following example shows a more complex situation.</span></span> <span data-ttu-id="6b4df-153">W poprzednim przykładzie został niewygodne jawnie określić typy dla wszystkich zmiennych.</span><span class="sxs-lookup"><span data-stu-id="6b4df-153">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="6b4df-154">W tym przykładzie jest niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="6b4df-154">In this example, it is impossible.</span></span> <span data-ttu-id="6b4df-155">Zamiast zaznaczania całego `Customer` elementy ze źródła danych lub pojedyncze pole z każdego elementu `Select` klauzula w tym zapytaniu zwraca dwie właściwości oryginalnej `Customer` obiekt: `Name` i `City`.</span><span class="sxs-lookup"><span data-stu-id="6b4df-155">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="6b4df-156">W odpowiedzi na `Select` klauzuli, kompilator definiuje typ anonimowy, który zawiera te dwie właściwości.</span><span class="sxs-lookup"><span data-stu-id="6b4df-156">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="6b4df-157">Wynik wykonania `nameCityQuery` w `For Each` pętla jest kolekcja wystąpień nowego typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="6b4df-157">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="6b4df-158">Ponieważ typ anonimowy nie ma używać nazwy, nie można określić typu `nameCityQuery` lub `custInfo` jawnie.</span><span class="sxs-lookup"><span data-stu-id="6b4df-158">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="6b4df-159">Oznacza to, z typu anonimowego, możesz nie mieć typ nazwy do użycia zamiast `String` w `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="6b4df-159">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="6b4df-160">Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="6b4df-160">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
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
  
 <span data-ttu-id="6b4df-161">Chociaż nie jest możliwe określenie typów dla wszystkich zmiennych w poprzednim przykładzie, relacje pozostają takie same.</span><span class="sxs-lookup"><span data-stu-id="6b4df-161">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>  
  
1.  <span data-ttu-id="6b4df-162">Typ elementów w źródle danych, jest ponownie typu zmienną zakresu w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="6b4df-162">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="6b4df-163">W tym przykładzie `cust` jest wystąpieniem `Customer`.</span><span class="sxs-lookup"><span data-stu-id="6b4df-163">In this example, `cust` is an instance of `Customer`.</span></span>  
  
2.  <span data-ttu-id="6b4df-164">Ponieważ `Select` instrukcji tworzy typu anonimowego zmienną zapytania `nameCityQuery`, musi być niejawnie typizowana jako typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="6b4df-164">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="6b4df-165">Typ anonimowy nie ma używać nazwy i dlatego nie może być określona jawnie.</span><span class="sxs-lookup"><span data-stu-id="6b4df-165">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>  
  
3.  <span data-ttu-id="6b4df-166">Typ zmiennej iteracji w `For Each` pętla jest typu anonimowego utworzony w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="6b4df-166">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="6b4df-167">Ponieważ typ nie ma używać nazwy, można niejawnie ustalić typu zmiennej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="6b4df-167">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b4df-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b4df-168">See Also</span></span>  
 [<span data-ttu-id="6b4df-169">Wprowadzenie do korzystania z LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b4df-169">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="6b4df-170">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="6b4df-170">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="6b4df-171">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="6b4df-171">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="6b4df-172">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b4df-172">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="6b4df-173">LINQ</span><span class="sxs-lookup"><span data-stu-id="6b4df-173">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="6b4df-174">Zapytania</span><span class="sxs-lookup"><span data-stu-id="6b4df-174">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)
