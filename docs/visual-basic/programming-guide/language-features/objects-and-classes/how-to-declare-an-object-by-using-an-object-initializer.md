---
title: 'Porady: deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 3a372ba91377b53c87c05976e416ca8ed55ccbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649168"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="3cd78-102">Porady: deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cd78-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="3cd78-103">Inicjatory obiektów umożliwiają deklarowanie i tworzy wystąpienie klasy w jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3cd78-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="3cd78-104">Ponadto można zainicjować jednego lub więcej elementów członkowskich wystąpienia w tym samym czasie, bez wywoływania sparametryzowanym konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="3cd78-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="3cd78-105">Gdy używasz inicjatora obiektów można utworzyć wystąpienia typu o nazwie domyślnego konstruktora dla klasy jest wywoływana następuje inicjowania wyznaczonych członków w kolejności, które określisz.</span><span class="sxs-lookup"><span data-stu-id="3cd78-105">When you use an object initializer to create an instance of a named type, the default constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="3cd78-106">Poniższa procedura przedstawia sposób tworzenia wystąpienia `Student` klasy na trzy różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="3cd78-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="3cd78-107">Klasa ma imię, nazwisko i właściwości klas, które roku, między innymi.</span><span class="sxs-lookup"><span data-stu-id="3cd78-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="3cd78-108">Każdy z trzech deklaracje tworzy nowe wystąpienie klasy `Student`, z właściwością `First` ustawioną wartość "Michael", właściwość `Last` ustawioną wartość "Tucker" i ustaw wartości domyślne wszystkich innych członków.</span><span class="sxs-lookup"><span data-stu-id="3cd78-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="3cd78-109">Wynik każdej deklaracji w procedurze jest odpowiednikiem poniższy przykład, który nie korzysta z inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="3cd78-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 <span data-ttu-id="3cd78-110">Dla implementacji `Student` , zobacz [porady: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="3cd78-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="3cd78-111">Możesz skopiować kod z tego tematu, aby skonfigurować klasy i utworzyć listę `Student` pracę z obiektami.</span><span class="sxs-lookup"><span data-stu-id="3cd78-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="3cd78-112">Aby utworzyć obiekt klasy o nazwie za pomocą inicjatora obiektów</span><span class="sxs-lookup"><span data-stu-id="3cd78-112">To create an object of a named class by using an object initializer</span></span>  
  
1.  <span data-ttu-id="3cd78-113">Rozpocznij deklaracji tak, jakby planuje Użyj konstruktora.</span><span class="sxs-lookup"><span data-stu-id="3cd78-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2.  <span data-ttu-id="3cd78-114">Wpisz słowa kluczowego `With`, a następnie listy inicjowanie w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="3cd78-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  <span data-ttu-id="3cd78-115">Na liście inicjowania obejmują każdej właściwości, którą chcesz zainicjować i przypisać wartość początkową.</span><span class="sxs-lookup"><span data-stu-id="3cd78-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="3cd78-116">Nazwa właściwości jest poprzedzona kropką.</span><span class="sxs-lookup"><span data-stu-id="3cd78-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     <span data-ttu-id="3cd78-117">Możesz zainicjować co najmniej jednego członka klasy.</span><span class="sxs-lookup"><span data-stu-id="3cd78-117">You can initialize one or more members of the class.</span></span>  
  
4.  <span data-ttu-id="3cd78-118">Alternatywnie można zadeklarować nowe wystąpienie klasy, a następnie przypisać wartość do niego.</span><span class="sxs-lookup"><span data-stu-id="3cd78-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="3cd78-119">Po pierwsze, Zadeklaruj wystąpienie `Student`:</span><span class="sxs-lookup"><span data-stu-id="3cd78-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5.  <span data-ttu-id="3cd78-120">Rozpocznij tworzenie wystąpienia `Student` w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="3cd78-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6.  <span data-ttu-id="3cd78-121">Typ `With` , a następnie inicjatora obiektów do zainicjowania co najmniej jednego członka nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3cd78-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  <span data-ttu-id="3cd78-122">Można uprościć definicji w poprzednim kroku, pomijając `As Student`.</span><span class="sxs-lookup"><span data-stu-id="3cd78-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="3cd78-123">Jeśli to zrobisz, kompilator Określa `student3` jest wystąpieniem `Student` przy użyciu wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="3cd78-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     <span data-ttu-id="3cd78-124">Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="3cd78-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd78-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3cd78-125">See Also</span></span>  
 [<span data-ttu-id="3cd78-126">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="3cd78-126">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="3cd78-127">Instrukcje: tworzenie listy elementów</span><span class="sxs-lookup"><span data-stu-id="3cd78-127">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)  
 [<span data-ttu-id="3cd78-128">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="3cd78-128">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="3cd78-129">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="3cd78-129">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
