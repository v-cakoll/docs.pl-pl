---
title: "Konstruktorzy (Przewodnik programowania w języku C#)"
ms.date: 05/05/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5897dd1c843633d38707112850a4be1151626185
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="f4c3a-102">Konstruktorzy (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f4c3a-102">Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="f4c3a-103">Zawsze, gdy [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) jest utworzona, jest nazywany jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-103">Whenever a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="f4c3a-104">Klasy lub struktury może mieć wiele konstruktorów przyjmujących różnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="f4c3a-105">Konstruktory Włącz programisty ustawić wartości domyślne, ograniczyć wystąpienia i pisania kodu, który jest elastyczny i łatwy do odczytania.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="f4c3a-106">Aby uzyskać dodatkowe informacje i przykłady, zobacz [za pomocą konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) i [konstruktorów wystąpienia](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="f4c3a-106">For more information and examples, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) and [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="default-constructors"></a><span data-ttu-id="f4c3a-107">Konstruktory domyślne</span><span class="sxs-lookup"><span data-stu-id="f4c3a-107">Default constructors</span></span>
  
<span data-ttu-id="f4c3a-108">Jeśli nie podasz konstruktora dla klasy, C# tworzy domyślnie tworzy wystąpienie obiektu, który ustawia wartości domyślne zmienne Członkowskie wymienionych w [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="f4c3a-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="f4c3a-109">Jeśli nie podasz konstruktora dla Twojego struktury, C# zależy od *niejawne domyślnego konstruktora* automatycznie zainicjować każdego pola typu wartości na wartość domyślną wymienionych w [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="f4c3a-109">If you don't provide a constructor for your struct, C# relies on an *implicit default constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="f4c3a-110">Aby uzyskać dodatkowe informacje i przykłady, zobacz [konstruktorów wystąpienia](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="f4c3a-110">For more information and examples, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="f4c3a-111">Składni konstruktora</span><span class="sxs-lookup"><span data-stu-id="f4c3a-111">Constructor syntax</span></span>

<span data-ttu-id="f4c3a-112">Konstruktor jest metoda, którego nazwa jest taka sama jak nazwa ich typu.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="f4c3a-113">Podpis metody zawiera nazwę metody i jej listy parametrów; nie ma zwracanego typu.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="f4c3a-114">W poniższym przykładzie przedstawiono konstruktora dla klasy o nazwie `Person`.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="f4c3a-115">Jeśli za pomocą jednej instrukcji można implementować konstruktora, możesz użyć [definicja treść wyrażenia](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="f4c3a-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="f4c3a-116">W poniższym przykładzie zdefiniowano `Location` klasy, których Konstruktor ma jeden ciąg parametru o nazwie *nazwa*.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="f4c3a-117">Definicja treść wyrażenia przypisuje argument `locationName` pola.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="f4c3a-118">Konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="f4c3a-118">Static constructors</span></span>

<span data-ttu-id="f4c3a-119">Poprzednich przykładach ma wszystkie konstruktory wystąpień pokazano, co spowoduje utworzenie nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="f4c3a-120">Klasy lub struktury ma także statycznego konstruktora, który inicjuje statyczne elementy członkowskie tego typu.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="f4c3a-121">Konstruktory statyczne są bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-121">Static constructors are parameterless.</span></span> <span data-ttu-id="f4c3a-122">Jeśli nie podasz Konstruktor statyczny zainicjować pól statycznych, kompilator języka C# będzie dostarczać statycznego konstruktora domyślnego i inicjuje pola statyczne przywrócić wartości domyślne, których listę zamieszczono w [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="f4c3a-122">If you don't provide a static constructor to initialize static fields, the C# compiler will supply a default static constructor that initializes static fields to their default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> 

<span data-ttu-id="f4c3a-123">W poniższym przykładzie użyto Konstruktor statyczny zainicjować pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="f4c3a-124">Można również zdefiniować Konstruktor statyczny z definicją treść wyrażenia, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f4c3a-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="f4c3a-125">Aby uzyskać dodatkowe informacje i przykłady, zobacz [konstruktory statyczne](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="f4c3a-125">For more information and examples, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4c3a-126">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f4c3a-126">In This Section</span></span>  
 [<span data-ttu-id="f4c3a-127">Używanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="f4c3a-127">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [<span data-ttu-id="f4c3a-128">Konstruktory wystąpień</span><span class="sxs-lookup"><span data-stu-id="f4c3a-128">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [<span data-ttu-id="f4c3a-129">Konstruktory prywatne</span><span class="sxs-lookup"><span data-stu-id="f4c3a-129">Private Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [<span data-ttu-id="f4c3a-130">Konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="f4c3a-130">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [<span data-ttu-id="f4c3a-131">Instrukcje: zapisywanie konstruktora kopiowania</span><span class="sxs-lookup"><span data-stu-id="f4c3a-131">How to: Write a Copy Constructor</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="f4c3a-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4c3a-132">See Also</span></span>  
 [<span data-ttu-id="f4c3a-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f4c3a-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f4c3a-134">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="f4c3a-134">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="f4c3a-135">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="f4c3a-135">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [<span data-ttu-id="f4c3a-136">static</span><span class="sxs-lookup"><span data-stu-id="f4c3a-136">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
 [<span data-ttu-id="f4c3a-137">Dlaczego są inicjatory uruchamiane w kolejności przeciwną jako konstruktorów? Część 1</span><span class="sxs-lookup"><span data-stu-id="f4c3a-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
