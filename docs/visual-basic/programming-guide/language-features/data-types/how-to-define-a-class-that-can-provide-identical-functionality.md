---
title: 'Instrukcje: Definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych (Visual Basic)'
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
ms.openlocfilehash: 9f6faf7b9ba2338784fda2cec2efc2b3991d415e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667482"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="35f87-102">Instrukcje: Definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35f87-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="35f87-103">Można zdefiniować klasę, w którym możesz tworzyć obiekty, które zapewnić identyczną funkcjonalność różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="35f87-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="35f87-104">Aby to zrobić, należy określić co najmniej jeden *parametry typu* w definicji.</span><span class="sxs-lookup"><span data-stu-id="35f87-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="35f87-105">Klasy mogą następnie służyć jako szablon dla obiektów, które używają różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="35f87-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="35f87-106">Nosi nazwę klasy zdefiniowanej w ten sposób *klasy generycznej*.</span><span class="sxs-lookup"><span data-stu-id="35f87-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="35f87-107">Zaletą definiowania klasy ogólnej jest, że można określić tylko raz, a kod służy do tworzenia wielu obiektów, które używają różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="35f87-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="35f87-108">Skutkuje to lepszą wydajność niż Definiowanie klasy za pomocą `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="35f87-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="35f87-109">Oprócz klas można również zdefiniować i używać struktury ogólne, interfejsy, procedury i delegatów.</span><span class="sxs-lookup"><span data-stu-id="35f87-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="35f87-110">Aby zdefiniować klasę z parametrem typu</span><span class="sxs-lookup"><span data-stu-id="35f87-110">To define a class with a type parameter</span></span>  
  
1.  <span data-ttu-id="35f87-111">Zdefiniuj klasę w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="35f87-111">Define the class in the normal way.</span></span>  
  
2.  <span data-ttu-id="35f87-112">Dodaj `(Of` *typeparameter* `)` zaraz po nazwie klasy, aby określić parametr typu.</span><span class="sxs-lookup"><span data-stu-id="35f87-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3.  <span data-ttu-id="35f87-113">Jeśli masz więcej niż jeden parametr typu, należy utworzyć listę rozdzielonych przecinkami wewnątrz nawiasów.</span><span class="sxs-lookup"><span data-stu-id="35f87-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="35f87-114">Nie powtarzaj `Of` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="35f87-114">Do not repeat the `Of` keyword.</span></span>  
  
4.  <span data-ttu-id="35f87-115">Jeśli Twój kod wykonuje operacje na parametr typu innego niż przypisanie proste, postępuj zgodnie z tego parametru typu z `As` klauzuli, aby dodać co najmniej jedno *ograniczenia*.</span><span class="sxs-lookup"><span data-stu-id="35f87-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="35f87-116">Ograniczenie gwarantuje, że podany dla tego parametru typu typ spełnia wymagania, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="35f87-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    -   <span data-ttu-id="35f87-117">Obsługuje operacji, takich jak `>`, który wykonuje kod</span><span class="sxs-lookup"><span data-stu-id="35f87-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    -   <span data-ttu-id="35f87-118">Obsługuje elementu członkowskiego, takie jak metody, która uzyskuje dostęp do kodu</span><span class="sxs-lookup"><span data-stu-id="35f87-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    -   <span data-ttu-id="35f87-119">Udostępnia konstruktora bez parametrów</span><span class="sxs-lookup"><span data-stu-id="35f87-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="35f87-120">Jeśli nie określisz żadnych ograniczeń, tylko operacji i kod użytkownika może używać elementów członkowskich są obsługiwane przez [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="35f87-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="35f87-121">Aby uzyskać więcej informacji, zobacz [lista typów](../../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="35f87-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5.  <span data-ttu-id="35f87-122">Identyfikowanie każdy członek klasy, która ma być deklarowany za pomocą podanego typu i Zadeklaruj go `As` `typeparameter`.</span><span class="sxs-lookup"><span data-stu-id="35f87-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="35f87-123">Dotyczy to pamięci wewnętrznej, procedury parametrów i zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="35f87-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6.  <span data-ttu-id="35f87-124">Pamiętaj, że kod używa tylko operacje i metody, które są obsługiwane przez dowolny typ danych, można dostarczyć do `itemType`.</span><span class="sxs-lookup"><span data-stu-id="35f87-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="35f87-125">W poniższym przykładzie zdefiniowano klasę, która zarządza listą bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="35f87-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="35f87-126">Przechowuje listę w tablicy wewnętrznej `items`oraz przy użyciu kodu można zadeklarować typ danych elementów listy.</span><span class="sxs-lookup"><span data-stu-id="35f87-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="35f87-127">Sparametryzowania konstruktora umożliwia przy użyciu kodu, aby ustawić górną granicę `items`, i ustawia domyślny konstruktor, to do 9 (w sumie 10 elementów).</span><span class="sxs-lookup"><span data-stu-id="35f87-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the default constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     <span data-ttu-id="35f87-128">Można zadeklarować klasy z `simpleList` do przechowywania listy `Integer` wartości innej klasy do przechowywania listy `String` wartości, a druga do przechowywania `Date` wartości.</span><span class="sxs-lookup"><span data-stu-id="35f87-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="35f87-129">Z wyjątkiem typu danych listy elementów członkowskich obiekty utworzone na podstawie tych klas zachowują się identycznie.</span><span class="sxs-lookup"><span data-stu-id="35f87-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="35f87-130">Argument typu, który używając kodu dostarcza do `itemType` może być typu wewnętrznego taką jak `Boolean` lub `Double`, struktury, wyliczenia lub dowolnego typu klasy, w tym taki, który jest określane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="35f87-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="35f87-131">Możesz przetestować klasy `simpleList` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="35f87-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="35f87-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35f87-132">See also</span></span>
- [<span data-ttu-id="35f87-133">Typy danych</span><span class="sxs-lookup"><span data-stu-id="35f87-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="35f87-134">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35f87-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="35f87-135">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="35f87-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="35f87-136">z</span><span class="sxs-lookup"><span data-stu-id="35f87-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="35f87-137">Lista typów</span><span class="sxs-lookup"><span data-stu-id="35f87-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="35f87-138">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="35f87-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="35f87-139">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="35f87-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
