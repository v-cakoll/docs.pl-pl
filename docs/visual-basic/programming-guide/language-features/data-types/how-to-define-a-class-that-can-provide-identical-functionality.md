---
title: 'Porady: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych (Visual Basic)'
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
ms.openlocfilehash: 3570a1c851bb8fead33f4cd208489c4ae087a68d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650351"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="73042-102">Porady: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73042-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="73042-103">Można zdefiniować klasę z którego można tworzyć obiektów, które zapewnić identyczną funkcjonalność różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="73042-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="73042-104">Aby to zrobić, należy określić co najmniej jeden *parametry typu* w definicji.</span><span class="sxs-lookup"><span data-stu-id="73042-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="73042-105">Klasa może następnie służyć jako szablon dla obiektów, które używają różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="73042-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="73042-106">Klasy określonej w ten sposób jest nazywany *klasy ogólnej*.</span><span class="sxs-lookup"><span data-stu-id="73042-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="73042-107">Zaletą definiowania klasy generycznej jest tylko raz określić, czy kod można go użyć do utworzenia wiele obiektów, które używają różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="73042-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="73042-108">Powoduje to lepszą wydajność niż definiowanie klas z `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="73042-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="73042-109">Oprócz klas można również zdefiniować i używać struktury ogólne, interfejsów, procedury i delegatów.</span><span class="sxs-lookup"><span data-stu-id="73042-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="73042-110">Aby zdefiniować klasę z parametrem typu</span><span class="sxs-lookup"><span data-stu-id="73042-110">To define a class with a type parameter</span></span>  
  
1.  <span data-ttu-id="73042-111">Zdefiniuj klasę w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="73042-111">Define the class in the normal way.</span></span>  
  
2.  <span data-ttu-id="73042-112">Dodaj `(Of` *typeparameter* `)` zaraz po nazwie klasy, aby określić parametr typu.</span><span class="sxs-lookup"><span data-stu-id="73042-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3.  <span data-ttu-id="73042-113">Jeśli masz więcej niż jeden parametr typu należy wewnątrz nawiasów listy rozdzielanej przecinkami.</span><span class="sxs-lookup"><span data-stu-id="73042-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="73042-114">Nie powtarzaj `Of` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="73042-114">Do not repeat the `Of` keyword.</span></span>  
  
4.  <span data-ttu-id="73042-115">Jeśli kod wykonuje operacje na parametr typu innego niż prosty przypisania, wykonaj parametru typu z `As` klauzuli, aby dodać jeden lub więcej *ograniczenia*.</span><span class="sxs-lookup"><span data-stu-id="73042-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="73042-116">Ograniczenie gwarantuje, że podany dla tego parametru typu typ spełnia wymagania, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="73042-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    -   <span data-ttu-id="73042-117">Obsługuje operacji, takich jak `>`, który wykonuje kodu</span><span class="sxs-lookup"><span data-stu-id="73042-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    -   <span data-ttu-id="73042-118">Obsługuje członka, takich jak metoda, która uzyskuje dostęp do kodu</span><span class="sxs-lookup"><span data-stu-id="73042-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    -   <span data-ttu-id="73042-119">Przedstawia konstruktora bez parametrów</span><span class="sxs-lookup"><span data-stu-id="73042-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="73042-120">Jeśli nie określono żadnych ograniczeń, tylko operacje i elementów członkowskich, można użyć kodu są obsługiwanymi przez [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="73042-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="73042-121">Aby uzyskać więcej informacji, zobacz [lista typów](../../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="73042-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5.  <span data-ttu-id="73042-122">Zidentyfikuj co element członkowski klasy, która ma być deklarowany za pomocą podanego typu i Zadeklaruj `As` `typeparameter`.</span><span class="sxs-lookup"><span data-stu-id="73042-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="73042-123">Dotyczy to pamięci wewnętrznej, procedury parametrów i zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="73042-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6.  <span data-ttu-id="73042-124">Pamiętaj, że kod używa tylko operacje i metody, które są obsługiwane przez dowolny typ danych może dostarczyć do `itemType`.</span><span class="sxs-lookup"><span data-stu-id="73042-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="73042-125">W poniższym przykładzie zdefiniowano klasę, która zarządza listą bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="73042-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="73042-126">Przechowuje listy w tablicy wewnętrznej `items`i przy użyciu kodu można zadeklarować typu danych elementów listy.</span><span class="sxs-lookup"><span data-stu-id="73042-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="73042-127">Umożliwia korzystanie z sparametryzowanym konstruktorze kod, aby ustawić górna granica `items`, i ustawia domyślny konstruktor, to do 9 (dla wszystkich elementów 10).</span><span class="sxs-lookup"><span data-stu-id="73042-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the default constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     <span data-ttu-id="73042-128">Można zadeklarować klasy z `simpleList` do przechowywania listy `Integer` wartości inną klasę do przechowywania listy `String` wartości, a druga do przechowywania `Date` wartości.</span><span class="sxs-lookup"><span data-stu-id="73042-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="73042-129">Z wyjątkiem typu danych listy elementów członkowskich obiekty utworzone na podstawie tych klas zachowują się tak samo.</span><span class="sxs-lookup"><span data-stu-id="73042-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="73042-130">Argument typu, który za pomocą kodu dostarcza do `itemType` może być typu wewnętrznego takich jak `Boolean` lub `Double`, struktury, wyliczenia lub dowolnego typu klasy, w tym, który definiuje aplikacji.</span><span class="sxs-lookup"><span data-stu-id="73042-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="73042-131">Można przetestować klasy `simpleList` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="73042-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="73042-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73042-132">See Also</span></span>  
 [<span data-ttu-id="73042-133">Typy danych</span><span class="sxs-lookup"><span data-stu-id="73042-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="73042-134">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73042-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="73042-135">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="73042-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="73042-136">z</span><span class="sxs-lookup"><span data-stu-id="73042-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="73042-137">Lista typów</span><span class="sxs-lookup"><span data-stu-id="73042-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="73042-138">Instrukcje: używanie klasy ogólnej</span><span class="sxs-lookup"><span data-stu-id="73042-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="73042-139">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="73042-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
