---
title: 'Instrukcje: Definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych'
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
ms.openlocfilehash: 3b1f47250453c32735d633b98da0bd0ddb1ed5b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393860"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="ec8ab-102">Porady: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec8ab-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="ec8ab-103">Można zdefiniować klasę, z której można tworzyć obiekty, które zapewniają identyczną funkcjonalność dla różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="ec8ab-104">W tym celu należy określić co najmniej jeden *parametr typu* w definicji.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="ec8ab-105">Klasa może następnie służyć jako szablon dla obiektów, które używają różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="ec8ab-106">Klasa zdefiniowana w ten sposób jest nazywana *klasą generyczną*.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="ec8ab-107">Zaletą zdefiniowania klasy generycznej jest to, że definiujesz ją tylko raz, a Twój kod może używać go do tworzenia wielu obiektów, które używają szerokiej gamy typów danych.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="ec8ab-108">Skutkuje to lepszą wydajnością niż Definiowanie klasy z `Object` typem.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="ec8ab-109">Oprócz klas można także definiować struktury ogólne, interfejsy, procedury i Delegaty oraz korzystać z nich.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="ec8ab-110">Aby zdefiniować klasę z parametrem typu</span><span class="sxs-lookup"><span data-stu-id="ec8ab-110">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="ec8ab-111">Zdefiniuj klasę w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-111">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="ec8ab-112">Dodaj `(Of` *typeparameter* `)` natychmiast po nazwie klasy, aby określić parametr typu.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="ec8ab-113">Jeśli masz więcej niż jeden parametr typu, Utwórz listę rozdzieloną przecinkami wewnątrz nawiasów.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="ec8ab-114">Nie powtarzaj `Of` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-114">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="ec8ab-115">Jeśli kod wykonuje operacje na parametrze typu innym niż proste przypisanie, należy użyć tego parametru typu z `As` klauzulą, aby dodać jedno lub więcej *ograniczeń*.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="ec8ab-116">Ograniczenie gwarantuje, że typ dostarczony dla tego parametru typu spełnia wymagania, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="ec8ab-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    - <span data-ttu-id="ec8ab-117">Obsługuje operacje, takie jak `>` , czy kod wykonuje</span><span class="sxs-lookup"><span data-stu-id="ec8ab-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    - <span data-ttu-id="ec8ab-118">Obsługuje składową, taką jak metoda, do której uzyskuje dostęp kod</span><span class="sxs-lookup"><span data-stu-id="ec8ab-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    - <span data-ttu-id="ec8ab-119">Uwidacznia Konstruktor bez parametrów</span><span class="sxs-lookup"><span data-stu-id="ec8ab-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="ec8ab-120">Jeśli nie określisz żadnych ograniczeń, jedyną operacją i elementami członkowskimi, które mogą być używane przez dany kod, są te obsługiwane przez [Typ danych Object](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="ec8ab-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="ec8ab-121">Aby uzyskać więcej informacji, zobacz [Typ listy](../../../language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="ec8ab-121">For more information, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="ec8ab-122">Zidentyfikuj każdy element członkowski klasy, który ma zostać zadeklarowany przy użyciu dostarczonego typu, i Zadeklaruj go `As` `typeparameter` .</span><span class="sxs-lookup"><span data-stu-id="ec8ab-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="ec8ab-123">Dotyczy to magazynu wewnętrznego, parametrów procedury i zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="ec8ab-124">Upewnij się, że kod używa tylko operacji i metod, które są obsługiwane przez każdy typ danych, który może dostarczyć `itemType` .</span><span class="sxs-lookup"><span data-stu-id="ec8ab-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="ec8ab-125">W poniższym przykładzie zdefiniowano klasę, która zarządza prostą listą.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="ec8ab-126">Zawiera listę w tablicy wewnętrznej `items` , a kod przy użyciu może deklarować typ danych elementów listy.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="ec8ab-127">Konstruktor sparametryzowany umożliwia użycie kodu w celu ustawienia górnej granicy `items` , a Konstruktor bez parametrów ustawia tę wartość na 9 (łącznie 10 elementów).</span><span class="sxs-lookup"><span data-stu-id="ec8ab-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the parameterless constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="ec8ab-128">Można zadeklarować klasę z `simpleList` do przechowywania listy `Integer` wartości, innej klasy do przechowywania listy `String` wartości, a druga do przechowywania `Date` wartości.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="ec8ab-129">Z wyjątkiem typu danych członków listy obiekty utworzone na podstawie wszystkich tych klas zachowują się identycznie.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="ec8ab-130">Argument typu, który jest używany przez kod, `itemType` może być typem wewnętrznym, takim jak `Boolean` lub `Double` , strukturą, wyliczeniem lub dowolnym typem klasy, z uwzględnieniem aplikacji zdefiniowanej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="ec8ab-131">Możesz przetestować klasę `simpleList` przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="ec8ab-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="ec8ab-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec8ab-132">See also</span></span>

- [<span data-ttu-id="ec8ab-133">Typy danych</span><span class="sxs-lookup"><span data-stu-id="ec8ab-133">Data Types</span></span>](index.md)
- [<span data-ttu-id="ec8ab-134">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec8ab-134">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="ec8ab-135">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="ec8ab-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="ec8ab-136">Z</span><span class="sxs-lookup"><span data-stu-id="ec8ab-136">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="ec8ab-137">Lista typów</span><span class="sxs-lookup"><span data-stu-id="ec8ab-137">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="ec8ab-138">Instrukcje: Używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="ec8ab-138">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="ec8ab-139">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="ec8ab-139">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
