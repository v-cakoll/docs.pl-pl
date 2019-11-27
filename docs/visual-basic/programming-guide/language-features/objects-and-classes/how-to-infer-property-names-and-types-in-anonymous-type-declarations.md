---
title: 'Porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 89a39e8e9cd66b1d774da70be47c7c6824cccef2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350035"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="1900e-102">Porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1900e-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>

<span data-ttu-id="1900e-103">Typy anonimowe nie zapewniają mechanizmu bezpośredniego określania typów danych właściwości.</span><span class="sxs-lookup"><span data-stu-id="1900e-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="1900e-104">Typy wszystkich właściwości są wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="1900e-104">Types of all properties are inferred.</span></span> <span data-ttu-id="1900e-105">W poniższym przykładzie typy `Name` i `Price` są wywnioskowane bezpośrednio z wartości, które są używane do ich zainicjowania.</span><span class="sxs-lookup"><span data-stu-id="1900e-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

<span data-ttu-id="1900e-106">Typy anonimowe mogą również wywnioskować nazwy właściwości i typy z innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="1900e-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="1900e-107">Poniższe sekcje zawierają listę warunków, w których można wywnioskować, oraz przykłady sytuacji, w których nie jest.</span><span class="sxs-lookup"><span data-stu-id="1900e-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>

## <a name="successful-inference"></a><span data-ttu-id="1900e-108">Pomyślne wnioskowanie</span><span class="sxs-lookup"><span data-stu-id="1900e-108">Successful Inference</span></span>

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="1900e-109">Typy anonimowe mogą wywnioskować nazwy właściwości i typy z następujących źródeł:</span><span class="sxs-lookup"><span data-stu-id="1900e-109">Anonymous types can infer property names and types from the following sources:</span></span>

- <span data-ttu-id="1900e-110">Z nazw zmiennych.</span><span class="sxs-lookup"><span data-stu-id="1900e-110">From variable names.</span></span> <span data-ttu-id="1900e-111">`anonProduct` typu anonimowego będą mieć dwie właściwości, `productName` i `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="1900e-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="1900e-112">Ich typy danych będą odpowiednio do oryginalnych zmiennych, `String` i `Double`.</span><span class="sxs-lookup"><span data-stu-id="1900e-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- <span data-ttu-id="1900e-113">Z nazw właściwości lub pól innych obiektów.</span><span class="sxs-lookup"><span data-stu-id="1900e-113">From property or field names of other objects.</span></span> <span data-ttu-id="1900e-114">Rozważmy na przykład obiekt `car` typu `CarClass`, który zawiera `Name` i `ID` właściwości.</span><span class="sxs-lookup"><span data-stu-id="1900e-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="1900e-115">Aby utworzyć nowe wystąpienie typu anonimowego, `car1`, z właściwościami `Name` i `ID`, które są inicjowane za pomocą wartości z obiektu `car`, można napisać następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="1900e-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  <span data-ttu-id="1900e-116">Poprzednia deklaracja jest równoznaczna z dłuższym wierszem kodu, który definiuje typ anonimowy `car2`.</span><span class="sxs-lookup"><span data-stu-id="1900e-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- <span data-ttu-id="1900e-117">Z nazw elementów członkowskich XML.</span><span class="sxs-lookup"><span data-stu-id="1900e-117">From XML member names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  <span data-ttu-id="1900e-118">Typ otrzymany dla `anon` będzie miał jedną właściwość, `Book`, typu <xref:System.Collections.IEnumerable>(z XElement).</span><span class="sxs-lookup"><span data-stu-id="1900e-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>

- <span data-ttu-id="1900e-119">Z funkcji, która nie ma parametrów, takich jak `SomeFunction`, w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1900e-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  <span data-ttu-id="1900e-120">Zmienna `anon2` w poniższym kodzie jest typem anonimowym, który ma jedną właściwość, znak o nazwie `First`.</span><span class="sxs-lookup"><span data-stu-id="1900e-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="1900e-121">Ten kod będzie wyświetlał literę "E", która jest zwracana przez funkcję <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="1900e-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a><span data-ttu-id="1900e-122">Błędy wnioskowania</span><span class="sxs-lookup"><span data-stu-id="1900e-122">Inference Failures</span></span>

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="1900e-123">Wnioskowanie o nazwach zakończy się niepowodzeniem w wielu sytuacjach, w tym:</span><span class="sxs-lookup"><span data-stu-id="1900e-123">Name inference will fail in many circumstances, including the following:</span></span>

- <span data-ttu-id="1900e-124">Wnioskowanie pochodzi z wywołania metody, konstruktora lub właściwości sparametryzowanej, która wymaga argumentów.</span><span class="sxs-lookup"><span data-stu-id="1900e-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="1900e-125">Poprzednia deklaracja `anon1` kończy się niepowodzeniem, jeśli `someFunction` ma jeden lub więcej argumentów.</span><span class="sxs-lookup"><span data-stu-id="1900e-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon3 = New With {Key sc.someFunction(someArg)}
  ```

  <span data-ttu-id="1900e-126">Przypisanie do nowej nazwy właściwości rozwiązuje problem.</span><span class="sxs-lookup"><span data-stu-id="1900e-126">Assignment to a new property name solves the problem.</span></span>

  ```vb
  ' Valid.
  Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
  ```

- <span data-ttu-id="1900e-127">Wnioskowanie pochodzi z wyrażenia złożonego.</span><span class="sxs-lookup"><span data-stu-id="1900e-127">The inference derives from a complex expression.</span></span>

  ```vb
  Dim aString As String = "Act "
  ' Not valid.
  ' Dim label = New With {Key aString & "IV"}
  ```

  <span data-ttu-id="1900e-128">Błąd można rozwiązać, przypisując wynik wyrażenia do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="1900e-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]

- <span data-ttu-id="1900e-129">Wnioskowanie dla wielu właściwości tworzy dwie lub więcej właściwości, które mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="1900e-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="1900e-130">Odwołując się do deklaracji we wcześniejszych przykładach, nie można wyświetlić jednocześnie `product.Name` i `car1.Name` jako właściwości tego samego typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="1900e-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="1900e-131">Wynika to z faktu, że wywnioskowany identyfikator dla każdego z nich będzie `Name`.</span><span class="sxs-lookup"><span data-stu-id="1900e-131">This is because the inferred identifier for each of these would be `Name`.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon5 = New With {Key product.Name, Key car1.Name}
  ```

  <span data-ttu-id="1900e-132">Problem można rozwiązać, przypisując wartości do nazw odrębnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="1900e-132">The problem can be solved by assigning the values to distinct property names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]

  <span data-ttu-id="1900e-133">Należy pamiętać, że zmiany w wielkości liter (zmiany między dużymi i małymi literami) nie tworzą odrębnych nazw.</span><span class="sxs-lookup"><span data-stu-id="1900e-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>

  ```vb
  Dim price = 0
  ' Not valid, because Price and price are the same name.
  ' Dim anon7 = New With {Key product.Price, Key price}
  ```

- <span data-ttu-id="1900e-134">Typ początkowy i wartość jednej właściwości zależy od innej właściwości, która nie została jeszcze ustanowiona.</span><span class="sxs-lookup"><span data-stu-id="1900e-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="1900e-135">Na przykład `.IDName = .LastName` nie jest prawidłowy w deklaracji typu anonimowego, chyba że `.LastName` jest już zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="1900e-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  <span data-ttu-id="1900e-136">W tym przykładzie można rozwiązać ten problem, odwracając kolejność, w której są zadeklarowane właściwości.</span><span class="sxs-lookup"><span data-stu-id="1900e-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- <span data-ttu-id="1900e-137">Nazwa właściwości typu anonimowego jest taka sama jak nazwa elementu członkowskiego <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="1900e-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="1900e-138">Na przykład następująca deklaracja kończy się niepowodzeniem, ponieważ `Equals` jest metodą <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="1900e-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  <span data-ttu-id="1900e-139">Problem można rozwiązać, zmieniając nazwę właściwości:</span><span class="sxs-lookup"><span data-stu-id="1900e-139">You can fix the problem by changing the property name:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a><span data-ttu-id="1900e-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1900e-140">See also</span></span>

- [<span data-ttu-id="1900e-141">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="1900e-141">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="1900e-142">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="1900e-142">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="1900e-143">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="1900e-143">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="1900e-144">Key</span><span class="sxs-lookup"><span data-stu-id="1900e-144">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
