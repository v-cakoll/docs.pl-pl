---
title: 'Porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 80127c05d56162397cfa421122ddd9698750b376
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="5809f-102">Porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5809f-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>
<span data-ttu-id="5809f-103">Typy anonimowe nie zawierają mechanizmu bezpośrednio określająca typy danych właściwości.</span><span class="sxs-lookup"><span data-stu-id="5809f-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="5809f-104">Typy wszystkich właściwości są wywnioskować.</span><span class="sxs-lookup"><span data-stu-id="5809f-104">Types of all properties are inferred.</span></span> <span data-ttu-id="5809f-105">W poniższym przykładzie typy `Name` i `Price` są wywnioskować bezpośrednio z wartości, które są używane do ich inicjowania.</span><span class="sxs-lookup"><span data-stu-id="5809f-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]  
  
 <span data-ttu-id="5809f-106">Typy anonimowe można również wnioskowanie nazw właściwości i typów z innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="5809f-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="5809f-107">W kolejnych sekcjach zawierają listę okoliczności, w którym możliwe jest wnioskowania i przykłady sytuacji, gdy nie jest.</span><span class="sxs-lookup"><span data-stu-id="5809f-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>  
  
## <a name="successful-inference"></a><span data-ttu-id="5809f-108">Pomyślne wnioskowania</span><span class="sxs-lookup"><span data-stu-id="5809f-108">Successful Inference</span></span>  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="5809f-109">Typy anonimowe można wnioskowanie nazw właściwości i typów z następujących źródeł:</span><span class="sxs-lookup"><span data-stu-id="5809f-109">Anonymous types can infer property names and types from the following sources:</span></span>  
  
-   <span data-ttu-id="5809f-110">Z nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5809f-110">From variable names.</span></span> <span data-ttu-id="5809f-111">Typ anonimowy `anonProduct` będzie mieć dwie właściwości `productName` i `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="5809f-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="5809f-112">Typy danych będą te oryginalnego zmiennych `String` i `Double`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="5809f-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]  
  
-   <span data-ttu-id="5809f-113">Właściwość lub pole nazw innych obiektów.</span><span class="sxs-lookup"><span data-stu-id="5809f-113">From property or field names of other objects.</span></span> <span data-ttu-id="5809f-114">Rozważmy na przykład `car` obiektu `CarClass` typ zawierający `Name` i `ID` właściwości.</span><span class="sxs-lookup"><span data-stu-id="5809f-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="5809f-115">Aby utworzyć nowe wystąpienie typu anonimowego, `car1`, z `Name` i `ID` właściwości, które są inicjowane z wartościami z `car` obiektu, można wpisać następujące:</span><span class="sxs-lookup"><span data-stu-id="5809f-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]  
  
     <span data-ttu-id="5809f-116">Poprzednia deklaracja jest odpowiednikiem dłużej wiersz kodu, który definiuje typ anonimowy `car2`.</span><span class="sxs-lookup"><span data-stu-id="5809f-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]  
  
-   <span data-ttu-id="5809f-117">Od nazw elementów członkowskich XML.</span><span class="sxs-lookup"><span data-stu-id="5809f-117">From XML member names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]  
  
     <span data-ttu-id="5809f-118">Wynikowy typ dla `anon` byłyby jedną właściwość `Book`, typu <xref:System.Collections.IEnumerable>(z klasy XElement).</span><span class="sxs-lookup"><span data-stu-id="5809f-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>  
  
-   <span data-ttu-id="5809f-119">Z funkcji, która nie ma parametrów, takich jak `SomeFunction` w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5809f-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     <span data-ttu-id="5809f-120">Zmienna `anon2` w poniższym kodzie jest typu anonimowego, który ma właściwość jeden znak o nazwie `First`.</span><span class="sxs-lookup"><span data-stu-id="5809f-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="5809f-121">Ten kod będzie wyświetlana litery "E","literą, która jest zwracana przez funkcję <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="5809f-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]  
  
## <a name="inference-failures"></a><span data-ttu-id="5809f-122">Błędy wnioskowania</span><span class="sxs-lookup"><span data-stu-id="5809f-122">Inference Failures</span></span>  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="5809f-123">Wnioskowanie nazw zakończy się niepowodzeniem w wielu sytuacjach, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="5809f-123">Name inference will fail in many circumstances, including the following:</span></span>  
  
-   <span data-ttu-id="5809f-124">Wnioskowanie pochodzi z wywołania metody, konstruktora lub sparametryzowane, który wymaga argumentów.</span><span class="sxs-lookup"><span data-stu-id="5809f-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="5809f-125">Z poprzednią deklaracją elementu `anon1` zakończy się niepowodzeniem, jeśli `someFunction` ma co najmniej jeden argument.</span><span class="sxs-lookup"><span data-stu-id="5809f-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     <span data-ttu-id="5809f-126">Przypisanie na nową nazwę właściwości rozwiązuje problem.</span><span class="sxs-lookup"><span data-stu-id="5809f-126">Assignment to a new property name solves the problem.</span></span>  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   <span data-ttu-id="5809f-127">Wnioskowanie pochodzi z wyrażenia złożone.</span><span class="sxs-lookup"><span data-stu-id="5809f-127">The inference derives from a complex expression.</span></span>  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     <span data-ttu-id="5809f-128">Ten błąd można rozwiązać, przypisując wynik wyrażenia do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="5809f-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]  
  
-   <span data-ttu-id="5809f-129">Wnioskowanie dla wielu właściwości tworzy dwa lub więcej właściwości, które mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="5809f-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="5809f-130">Przywołuje deklaracje w przykładach wcześniej, nie możesz wystawiać zarówno `product.Name` i `car1.Name` jako właściwości tego samego typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="5809f-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="5809f-131">Wynika to z faktu wnioskowany identyfikator dla każdego z nich będzie `Name`.</span><span class="sxs-lookup"><span data-stu-id="5809f-131">This is because the inferred identifier for each of these would be `Name`.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     <span data-ttu-id="5809f-132">Problem można rozwiązać przez przypisywanie wartości do właściwości unikatowe nazwy.</span><span class="sxs-lookup"><span data-stu-id="5809f-132">The problem can be solved by assigning the values to distinct property names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]  
  
     <span data-ttu-id="5809f-133">Należy pamiętać, że zmiany w przypadku (zmiany między wielkie i małe litery) nie należy wprowadzać dwie nazwy distinct.</span><span class="sxs-lookup"><span data-stu-id="5809f-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   <span data-ttu-id="5809f-134">Początkowa typu i wartości jedną właściwość zależy od innej właściwości, która nie jest jeszcze ustalony.</span><span class="sxs-lookup"><span data-stu-id="5809f-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="5809f-135">Na przykład `.IDName = .LastName` nie jest prawidłowy w deklaracji typu anonimowego, chyba że `.LastName` jest już zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="5809f-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     <span data-ttu-id="5809f-136">W tym przykładzie można naprawić ten problem, odwracanie kolejności, w którym są zadeklarowane właściwości.</span><span class="sxs-lookup"><span data-stu-id="5809f-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]  
  
-   <span data-ttu-id="5809f-137">Nazwa właściwości typu anonimowego jest taka sama jak nazwa elementu członkowskiego <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5809f-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="5809f-138">Na przykład następujące oświadczenie nie powiedzie się, ponieważ `Equals` jest metoda <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5809f-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     <span data-ttu-id="5809f-139">Aby rozwiązać ten problem, należy zmienić nazwę właściwości:</span><span class="sxs-lookup"><span data-stu-id="5809f-139">You can fix the problem by changing the property name:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5809f-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5809f-140">See Also</span></span>  
 [<span data-ttu-id="5809f-141">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="5809f-141">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="5809f-142">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="5809f-142">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="5809f-143">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="5809f-143">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="5809f-144">Key</span><span class="sxs-lookup"><span data-stu-id="5809f-144">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
