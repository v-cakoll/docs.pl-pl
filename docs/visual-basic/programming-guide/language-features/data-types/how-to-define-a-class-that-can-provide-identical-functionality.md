---
title: 'Porady: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych'
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: d80623d9e55358d37aa45f11f1525c80a09b91a6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350042"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="5d662-102">Porady: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d662-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="5d662-103">Można zdefiniować klasę, z której można tworzyć obiekty, które zapewniają identyczną funkcjonalność dla różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="5d662-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="5d662-104">W tym celu należy określić co najmniej jeden *parametr typu* w definicji.</span><span class="sxs-lookup"><span data-stu-id="5d662-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="5d662-105">Klasa może następnie służyć jako szablon dla obiektów, które używają różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="5d662-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="5d662-106">Klasa zdefiniowana w ten sposób jest nazywana *klasą generyczną*.</span><span class="sxs-lookup"><span data-stu-id="5d662-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="5d662-107">Zaletą zdefiniowania klasy generycznej jest to, że definiujesz ją tylko raz, a Twój kod może używać go do tworzenia wielu obiektów, które używają szerokiej gamy typów danych.</span><span class="sxs-lookup"><span data-stu-id="5d662-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="5d662-108">Skutkuje to lepszą wydajnością niż Definiowanie klasy przy użyciu typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="5d662-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="5d662-109">Oprócz klas można także definiować struktury ogólne, interfejsy, procedury i Delegaty oraz korzystać z nich.</span><span class="sxs-lookup"><span data-stu-id="5d662-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="5d662-110">Aby zdefiniować klasę z parametrem typu</span><span class="sxs-lookup"><span data-stu-id="5d662-110">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="5d662-111">Zdefiniuj klasę w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="5d662-111">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="5d662-112">Dodaj `(Of` *typeparameter*`)` natychmiast po nazwie klasy, aby określić parametr typu.</span><span class="sxs-lookup"><span data-stu-id="5d662-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="5d662-113">Jeśli masz więcej niż jeden parametr typu, Utwórz listę rozdzieloną przecinkami wewnątrz nawiasów.</span><span class="sxs-lookup"><span data-stu-id="5d662-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="5d662-114">Nie powtarzaj słowa kluczowego `Of`.</span><span class="sxs-lookup"><span data-stu-id="5d662-114">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="5d662-115">Jeśli kod wykonuje operacje na parametrze typu innym niż proste przypisanie, należy użyć tego parametru typu z klauzulą `As`, aby dodać jedno lub więcej *ograniczeń*.</span><span class="sxs-lookup"><span data-stu-id="5d662-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="5d662-116">Ograniczenie gwarantuje, że typ dostarczony dla tego parametru typu spełnia wymagania, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="5d662-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    - <span data-ttu-id="5d662-117">Obsługuje operacje, takie jak `>`, wykonywane przez kod</span><span class="sxs-lookup"><span data-stu-id="5d662-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    - <span data-ttu-id="5d662-118">Obsługuje składową, taką jak metoda, do której uzyskuje dostęp kod</span><span class="sxs-lookup"><span data-stu-id="5d662-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    - <span data-ttu-id="5d662-119">Uwidacznia Konstruktor bez parametrów</span><span class="sxs-lookup"><span data-stu-id="5d662-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="5d662-120">Jeśli nie określisz żadnych ograniczeń, jedyną operacją i elementami członkowskimi, które mogą być używane przez dany kod, są te obsługiwane przez [Typ danych Object](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="5d662-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="5d662-121">Aby uzyskać więcej informacji, zobacz [Typ listy](../../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="5d662-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="5d662-122">Zidentyfikuj każdy element członkowski klasy, który ma zostać zadeklarowany przy użyciu dostarczonego typu, i Zadeklaruj go `As` `typeparameter`.</span><span class="sxs-lookup"><span data-stu-id="5d662-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="5d662-123">Dotyczy to magazynu wewnętrznego, parametrów procedury i zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="5d662-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="5d662-124">Upewnij się, że kod używa tylko operacji i metod, które są obsługiwane przez dowolny typ danych, który może dostarczyć `itemType`.</span><span class="sxs-lookup"><span data-stu-id="5d662-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="5d662-125">W poniższym przykładzie zdefiniowano klasę, która zarządza prostą listą.</span><span class="sxs-lookup"><span data-stu-id="5d662-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="5d662-126">Zawiera listę w tablicy wewnętrznej `items`, a kod przy użyciu może deklarować typ danych elementów listy.</span><span class="sxs-lookup"><span data-stu-id="5d662-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="5d662-127">Konstruktor sparametryzowany umożliwia użycie kodu w celu ustawienia górnej granicy `items`, a Konstruktor bez parametrów ustawia tę wartość na 9 (łącznie 10 elementów).</span><span class="sxs-lookup"><span data-stu-id="5d662-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the parameterless constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="5d662-128">Można zadeklarować klasę z `simpleList` do przechowywania listy wartości `Integer`, innej klasy do przechowywania listy wartości `String` i innego do przechowywania wartości `Date`.</span><span class="sxs-lookup"><span data-stu-id="5d662-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="5d662-129">Z wyjątkiem typu danych członków listy obiekty utworzone na podstawie wszystkich tych klas zachowują się identycznie.</span><span class="sxs-lookup"><span data-stu-id="5d662-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="5d662-130">Argument typu, który jest używany przez kod, do `itemType` może być typem wewnętrznym, takim jak `Boolean` lub `Double`, strukturą, wyliczeniem lub dowolnym typem klasy, włącznie z tym, że aplikacja definiuje.</span><span class="sxs-lookup"><span data-stu-id="5d662-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="5d662-131">Możesz przetestować klasę `simpleList` przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="5d662-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="5d662-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d662-132">See also</span></span>

- [<span data-ttu-id="5d662-133">Typy danych</span><span class="sxs-lookup"><span data-stu-id="5d662-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="5d662-134">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d662-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="5d662-135">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="5d662-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="5d662-136">Z</span><span class="sxs-lookup"><span data-stu-id="5d662-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="5d662-137">Lista typów</span><span class="sxs-lookup"><span data-stu-id="5d662-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="5d662-138">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="5d662-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="5d662-139">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="5d662-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
