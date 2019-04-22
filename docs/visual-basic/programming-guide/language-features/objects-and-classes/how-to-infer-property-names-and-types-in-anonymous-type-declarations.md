---
title: 'Instrukcje: Wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: be3c74e8f8c69eb9f0a1d0dda4d6c90dfd7e567a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824731"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="045f4-102">Instrukcje: Wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="045f4-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>
<span data-ttu-id="045f4-103">Typy anonimowe zapewniają żaden mechanizm służący bezpośrednio określać typy danych właściwości.</span><span class="sxs-lookup"><span data-stu-id="045f4-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="045f4-104">Typy wszystkich właściwości są wnioskowane.</span><span class="sxs-lookup"><span data-stu-id="045f4-104">Types of all properties are inferred.</span></span> <span data-ttu-id="045f4-105">W poniższym przykładzie typy `Name` i `Price` są dedukowane bezpośrednio z wartości, które są używane do ich inicjowania.</span><span class="sxs-lookup"><span data-stu-id="045f4-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 <span data-ttu-id="045f4-106">Typy anonimowe można również wnioskowanie nazw właściwości i typów z innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="045f4-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="045f4-107">Sekcje zawierają listę okoliczności, w którym możliwe jest wnioskowania i przykłady sytuacji, gdy nie jest.</span><span class="sxs-lookup"><span data-stu-id="045f4-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>  
  
## <a name="successful-inference"></a><span data-ttu-id="045f4-108">Pomyślne wnioskowania</span><span class="sxs-lookup"><span data-stu-id="045f4-108">Successful Inference</span></span>  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="045f4-109">Typy anonimowe można wnioskowanie nazw właściwości i typów z następujących źródeł:</span><span class="sxs-lookup"><span data-stu-id="045f4-109">Anonymous types can infer property names and types from the following sources:</span></span>  
  
-   <span data-ttu-id="045f4-110">W nazwach zmiennych.</span><span class="sxs-lookup"><span data-stu-id="045f4-110">From variable names.</span></span> <span data-ttu-id="045f4-111">Typ anonimowy `anonProduct` będzie mieć dwie właściwości `productName` i `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="045f4-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="045f4-112">Typy danych będą identyczne ze zmiennych oryginalnego `String` i `Double`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="045f4-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]  
  
-   <span data-ttu-id="045f4-113">Właściwość lub pole nazw innych obiektów.</span><span class="sxs-lookup"><span data-stu-id="045f4-113">From property or field names of other objects.</span></span> <span data-ttu-id="045f4-114">Na przykład, rozważmy `car` obiektu `CarClass` typ, który zawiera `Name` i `ID` właściwości.</span><span class="sxs-lookup"><span data-stu-id="045f4-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="045f4-115">Aby utworzyć nowe wystąpienie typu anonimowego `car1`, za pomocą `Name` i `ID` właściwości, które są inicjowane z wartościami z `car` obiektu, można napisać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="045f4-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]  
  
     <span data-ttu-id="045f4-116">Poprzednie deklaracja jest równoważna dłużej wiersz kodu, który definiuje typ anonimowy `car2`.</span><span class="sxs-lookup"><span data-stu-id="045f4-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]  
  
-   <span data-ttu-id="045f4-117">Od nazw składowych XML.</span><span class="sxs-lookup"><span data-stu-id="045f4-117">From XML member names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]  
  
     <span data-ttu-id="045f4-118">Wynikowy typ `anon` miałby jedną właściwość `Book`, typu <xref:System.Collections.IEnumerable>(z XElement).</span><span class="sxs-lookup"><span data-stu-id="045f4-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>  
  
-   <span data-ttu-id="045f4-119">Z funkcji, która nie ma parametrów, takich jak `SomeFunction` w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="045f4-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     <span data-ttu-id="045f4-120">Zmienna `anon2` w poniższym kodzie jest typ anonimowy, który ma jedną właściwość, znakiem o nazwie `First`.</span><span class="sxs-lookup"><span data-stu-id="045f4-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="045f4-121">Ten kod wyświetli się literą "E", list, który jest zwracany przez funkcję <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="045f4-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]  
  
## <a name="inference-failures"></a><span data-ttu-id="045f4-122">Błędy wnioskowania</span><span class="sxs-lookup"><span data-stu-id="045f4-122">Inference Failures</span></span>  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="045f4-123">Wnioskowanie o nazwie zakończy się niepowodzeniem w wielu sytuacjach, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="045f4-123">Name inference will fail in many circumstances, including the following:</span></span>  
  
-   <span data-ttu-id="045f4-124">Wnioskowanie pochodzi z wywołania metody, Konstruktor lub właściwości sparametryzowane, która wymaga argumentów.</span><span class="sxs-lookup"><span data-stu-id="045f4-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="045f4-125">Poprzednia deklaracja elementu `anon1` zakończy się niepowodzeniem, jeśli `someFunction` ma jeden lub więcej argumentów.</span><span class="sxs-lookup"><span data-stu-id="045f4-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     <span data-ttu-id="045f4-126">Przypisanie do nowej nazwy właściwości rozwiązuje problem.</span><span class="sxs-lookup"><span data-stu-id="045f4-126">Assignment to a new property name solves the problem.</span></span>  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   <span data-ttu-id="045f4-127">Wnioskowanie pochodzi ze złożonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="045f4-127">The inference derives from a complex expression.</span></span>  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     <span data-ttu-id="045f4-128">Ten błąd można rozwiązać, przypisując wynik wyrażenia do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="045f4-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]  
  
-   <span data-ttu-id="045f4-129">Wnioskowanie o wiele właściwości tworzy dwa lub więcej właściwości, które mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="045f4-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="045f4-130">Przywołujący deklaracji w wcześniejszych przykładów, nie możesz wyświetlać listy zarówno `product.Name` i `car1.Name` jako właściwości tego samego typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="045f4-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="045f4-131">Jest to spowodowane wywnioskowane identyfikator dla każdego z nich będzie `Name`.</span><span class="sxs-lookup"><span data-stu-id="045f4-131">This is because the inferred identifier for each of these would be `Name`.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     <span data-ttu-id="045f4-132">Problem można rozwiązać przez przypisywanie wartości do nazw różne właściwości.</span><span class="sxs-lookup"><span data-stu-id="045f4-132">The problem can be solved by assigning the values to distinct property names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]  
  
     <span data-ttu-id="045f4-133">Pamiętaj, że zmiany w przypadku, gdy (zmiany między wielkie i małe litery) nie należy wprowadzać nazwy dwóch odrębnych.</span><span class="sxs-lookup"><span data-stu-id="045f4-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   <span data-ttu-id="045f4-134">Początkowa typu i wartości jedną właściwość zależy od innej właściwości, która nie jest jeszcze nawiązane.</span><span class="sxs-lookup"><span data-stu-id="045f4-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="045f4-135">Na przykład `.IDName = .LastName` nie jest prawidłowy w deklaracji typu anonimowego, chyba że `.LastName` jest już zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="045f4-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     <span data-ttu-id="045f4-136">W tym przykładzie można rozwiązać problem, odwracając kolejność, w którym są zadeklarowane właściwości.</span><span class="sxs-lookup"><span data-stu-id="045f4-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]  
  
-   <span data-ttu-id="045f4-137">Nazwa właściwości typu anonimowego jest taka sama jak nazwa składowej <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="045f4-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="045f4-138">Na przykład następująca deklaracja nie powiedzie się, ponieważ `Equals` to metoda <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="045f4-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     <span data-ttu-id="045f4-139">Aby naprawić ten problem, należy zmienić nazwy właściwości:</span><span class="sxs-lookup"><span data-stu-id="045f4-139">You can fix the problem by changing the property name:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="045f4-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="045f4-140">See also</span></span>

- [<span data-ttu-id="045f4-141">Inicjatory obiektów: Typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="045f4-141">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="045f4-142">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="045f4-142">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="045f4-143">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="045f4-143">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="045f4-144">Key</span><span class="sxs-lookup"><span data-stu-id="045f4-144">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
