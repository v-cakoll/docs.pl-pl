---
title: 'Porady: deklarowanie obiektu za pomocą inicjatora obiektów'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: cf4954059a4b0bf015bed82a74357ecfd5f5987e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404878"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="2d232-102">Porady: deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d232-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="2d232-103">Inicjatory obiektów umożliwiają zadeklarować wystąpienie klasy w pojedynczej instrukcji i utworzenie ich wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2d232-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="2d232-104">Ponadto można zainicjować co najmniej jeden element członkowski wystąpienia w tym samym czasie, bez wywoływania sparametryzowanego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2d232-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="2d232-105">Gdy używasz inicjatora obiektów do utworzenia wystąpienia nazwanego typu, Konstruktor bez parametrów dla klasy jest wywoływany, a po nim inicjacja wyznaczono członków w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="2d232-105">When you use an object initializer to create an instance of a named type, the parameterless constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="2d232-106">Poniższa procedura pokazuje, jak utworzyć wystąpienie `Student` klasy na trzy różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="2d232-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="2d232-107">Klasa ma imię, nazwisko i właściwości roku klasy, między innymi.</span><span class="sxs-lookup"><span data-stu-id="2d232-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="2d232-108">Każda z trzech deklaracji tworzy nowe wystąpienie `Student` , z właściwością `First` ustawioną na "Michael", właściwość `Last` ustawioną na wartość "Tucker", a wszystkie inne elementy członkowskie mają ustawioną wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="2d232-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="2d232-109">Wynik każdej deklaracji w procedurze jest równoważny do poniższego przykładu, który nie używa inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="2d232-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 <span data-ttu-id="2d232-110">Aby uzyskać implementację `Student` klasy, zobacz [How to: Create a list of Items](../../concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="2d232-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="2d232-111">Możesz skopiować kod z tego tematu, aby skonfigurować klasę i utworzyć listę `Student` obiektów do pracy.</span><span class="sxs-lookup"><span data-stu-id="2d232-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="2d232-112">Aby utworzyć obiekt nazwanej klasy przy użyciu inicjatora obiektów</span><span class="sxs-lookup"><span data-stu-id="2d232-112">To create an object of a named class by using an object initializer</span></span>  
  
1. <span data-ttu-id="2d232-113">Rozpocznij deklarację tak, jakby była planowana użycie konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2d232-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2. <span data-ttu-id="2d232-114">Wpisz słowo kluczowe `With` , a następnie listę inicjalizacji w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="2d232-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. <span data-ttu-id="2d232-115">Na liście inicjalizacji Uwzględnij każdą właściwość, która ma zostać zainicjowana, i przypisz do niej początkową wartość.</span><span class="sxs-lookup"><span data-stu-id="2d232-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="2d232-116">Nazwa właściwości jest poprzedzona kropką.</span><span class="sxs-lookup"><span data-stu-id="2d232-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     <span data-ttu-id="2d232-117">Można zainicjować co najmniej jeden element członkowski klasy.</span><span class="sxs-lookup"><span data-stu-id="2d232-117">You can initialize one or more members of the class.</span></span>  
  
4. <span data-ttu-id="2d232-118">Alternatywnie można zadeklarować nowe wystąpienie klasy, a następnie przypisać do niej wartość.</span><span class="sxs-lookup"><span data-stu-id="2d232-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="2d232-119">Najpierw Zadeklaruj wystąpienie `Student` :</span><span class="sxs-lookup"><span data-stu-id="2d232-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5. <span data-ttu-id="2d232-120">Rozpocznij tworzenie wystąpienia `Student` w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="2d232-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6. <span data-ttu-id="2d232-121">Wpisz `With` , a następnie Inicjator obiektu, aby zainicjować co najmniej jednego członka nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2d232-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. <span data-ttu-id="2d232-122">Można uprościć definicję w poprzednim kroku, pomijając `As Student` .</span><span class="sxs-lookup"><span data-stu-id="2d232-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="2d232-123">Jeśli to zrobisz, kompilator określa, że `student3` jest wystąpieniem przy `Student` użyciu wnioskowania typu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="2d232-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     <span data-ttu-id="2d232-124">Aby uzyskać więcej informacji, zobacz temat [wnioskowanie o typie lokalnym](../variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="2d232-124">For more information, see [Local Type Inference](../variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d232-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d232-125">See also</span></span>

- [<span data-ttu-id="2d232-126">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="2d232-126">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="2d232-127">Instrukcje: tworzenie listy elementów</span><span class="sxs-lookup"><span data-stu-id="2d232-127">How to: Create a List of Items</span></span>](../../concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="2d232-128">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="2d232-128">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="2d232-129">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="2d232-129">Anonymous Types</span></span>](anonymous-types.md)
