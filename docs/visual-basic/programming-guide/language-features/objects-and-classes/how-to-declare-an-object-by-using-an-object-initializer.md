---
title: 'Instrukcje: Deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: eeaf3b4a611944395269fcae045bab00d25f0167
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561074"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="29d08-102">Instrukcje: Deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29d08-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="29d08-103">Inicjatory obiektów umożliwiają deklarowanie i tworzy wystąpienie klasy w pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="29d08-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="29d08-104">Ponadto należy zainicjować co najmniej jednego członka wystąpienia w tym samym czasie, bez wywoływania sparametryzowania konstruktora.</span><span class="sxs-lookup"><span data-stu-id="29d08-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="29d08-105">Gdy używasz inicjatora obiektu można utworzyć wystąpienia typu nazwanego, wywoływany jest konstruktor domyślny klasy, następuje inicjowanie wyznaczonych członków w kolejności, które określisz.</span><span class="sxs-lookup"><span data-stu-id="29d08-105">When you use an object initializer to create an instance of a named type, the default constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="29d08-106">Poniższa procedura przedstawia sposób tworzenia wystąpienia `Student` klasy na trzy różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="29d08-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="29d08-107">Klasa ma imię, nazwisko i właściwości klas, które roku, między innymi.</span><span class="sxs-lookup"><span data-stu-id="29d08-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="29d08-108">Każdy z trzech deklaracje tworzy nowe wystąpienie klasy `Student`, z właściwością `First` ustawiona na "Jan", właściwość `Last` ustawiona na "Tucker", a wszystkie inne elementy członkowskie zestawu do wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="29d08-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="29d08-109">Wynik każdego zgłoszenia w procedurze jest równoważne z poniższego przykładu, który nie korzysta z inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="29d08-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 <span data-ttu-id="29d08-110">Na implementację `Student` klasy, zobacz [jak: Utwórz listę elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="29d08-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="29d08-111">Możesz skopiować kod z tego tematu, aby skonfigurować klasy i tworzenie listy `Student` pracę z obiektami.</span><span class="sxs-lookup"><span data-stu-id="29d08-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="29d08-112">Aby utworzyć obiekt klasy o nazwie za pomocą inicjatora obiektów</span><span class="sxs-lookup"><span data-stu-id="29d08-112">To create an object of a named class by using an object initializer</span></span>  
  
1.  <span data-ttu-id="29d08-113">Rozpocznij zgłoszenia w tak, jakby planuje użyć konstruktora.</span><span class="sxs-lookup"><span data-stu-id="29d08-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2.  <span data-ttu-id="29d08-114">Wpisz słowo kluczowe `With`, a następnie listy inicjowania w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="29d08-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  <span data-ttu-id="29d08-115">Na liście inicjowania obejmują każdej właściwości, którą chcesz zainicjować i przypisać jej wartość początkową.</span><span class="sxs-lookup"><span data-stu-id="29d08-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="29d08-116">Nazwa właściwości jest poprzedzony przez okres.</span><span class="sxs-lookup"><span data-stu-id="29d08-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     <span data-ttu-id="29d08-117">Można zainicjować co najmniej jednego członka klasy.</span><span class="sxs-lookup"><span data-stu-id="29d08-117">You can initialize one or more members of the class.</span></span>  
  
4.  <span data-ttu-id="29d08-118">Alternatywnie można zadeklarować nowe wystąpienie klasy i następnie przypisać jej wartości.</span><span class="sxs-lookup"><span data-stu-id="29d08-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="29d08-119">Najpierw należy zadeklarować wystąpienie `Student`:</span><span class="sxs-lookup"><span data-stu-id="29d08-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5.  <span data-ttu-id="29d08-120">Rozpocznij tworzenie wystąpienia `Student` w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="29d08-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6.  <span data-ttu-id="29d08-121">Typ `With` i następnie inicjatora obiektu można zainicjować co najmniej jednego członka nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="29d08-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  <span data-ttu-id="29d08-122">Można uprościć definicji w poprzednim kroku, pomijając `As Student`.</span><span class="sxs-lookup"><span data-stu-id="29d08-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="29d08-123">Jeśli to zrobisz, kompilator Określa `student3` jest wystąpieniem `Student` przy użyciu wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="29d08-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     <span data-ttu-id="29d08-124">Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="29d08-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d08-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29d08-125">See also</span></span>
- [<span data-ttu-id="29d08-126">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="29d08-126">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="29d08-127">Instrukcje: Tworzenie listy elementów</span><span class="sxs-lookup"><span data-stu-id="29d08-127">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="29d08-128">Inicjatory obiektów: Typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="29d08-128">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="29d08-129">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="29d08-129">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
