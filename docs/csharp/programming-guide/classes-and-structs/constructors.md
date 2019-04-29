---
title: Konstruktory — C# przewodnik programowania
ms.custom: seodec18
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: becc3fc8a75cd4d2d5e0c1db2858b15b8b61ae20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646543"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="06701-102">Konstruktorzy (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="06701-102">Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="06701-103">Zawsze, gdy [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) jest utworzone, jego konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="06701-103">Whenever a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="06701-104">Klasa lub struktura może mieć wiele konstruktorów, które przyjmują różne argumentów.</span><span class="sxs-lookup"><span data-stu-id="06701-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="06701-105">Konstruktory Włącz programisty należy ustawić wartości domyślne, ograniczyć podczas tworzenia wystąpienia i napisać kod, który jest elastyczny i łatwy do odczytania.</span><span class="sxs-lookup"><span data-stu-id="06701-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="06701-106">Aby uzyskać więcej informacji i przykładów, zobacz [korzystanie z konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) i [konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="06701-106">For more information and examples, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) and [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="06701-107">Konstruktorów bez parametrów</span><span class="sxs-lookup"><span data-stu-id="06701-107">Parameterless constructors</span></span>
  
<span data-ttu-id="06701-108">Jeśli nie podasz konstruktora dla klasy, C# tworzony jest jeden domyślny, który tworzy wystąpienie obiektu i ustawia zmienne składowe do wartości domyślnych, zgodnie z zaleceniami z [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="06701-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="06701-109">Jeśli nie podasz konstruktora dla Twojej struktury C# opiera się na *niejawnego konstruktora bez parametrów* automatycznie zainicjować każdego pola typu wartości do wartości domyślnej, zgodnie z zaleceniami z [wartości domyślne Tabela](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="06701-109">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="06701-110">Aby uzyskać więcej informacji i przykładów, zobacz [konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="06701-110">For more information and examples, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="06701-111">Składnia konstruktora</span><span class="sxs-lookup"><span data-stu-id="06701-111">Constructor syntax</span></span>

<span data-ttu-id="06701-112">Konstruktor jest metodą, którego nazwa jest taka sama jak nazwa ich typu.</span><span class="sxs-lookup"><span data-stu-id="06701-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="06701-113">Jego podpis metody zawiera tylko nazwy metody i jego listy parametrów; nie ma typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="06701-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="06701-114">W poniższym przykładzie pokazano konstruktora dla klasy o nazwie `Person`.</span><span class="sxs-lookup"><span data-stu-id="06701-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="06701-115">Jeśli Konstruktor można zaimplementować jako pojedynczej instrukcji, można użyć [definicja treści wyrażenia](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="06701-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="06701-116">W poniższym przykładzie zdefiniowano `Location` klasy, której Konstruktor ma jeden ciąg parametr o nazwie *nazwa*.</span><span class="sxs-lookup"><span data-stu-id="06701-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="06701-117">Definicja treści wyrażenia przypisuje argument `locationName` pola.</span><span class="sxs-lookup"><span data-stu-id="06701-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="06701-118">Konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="06701-118">Static constructors</span></span>

<span data-ttu-id="06701-119">Poprzednie przykłady ma wszystkie konstruktory pokazywane wystąpienie, które tworzą nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="06701-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="06701-120">Klasa lub struktura może być również statyczny Konstruktor inicjuje statyczne elementy członkowskie tego typu.</span><span class="sxs-lookup"><span data-stu-id="06701-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="06701-121">Konstruktory statyczne są bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="06701-121">Static constructors are parameterless.</span></span> <span data-ttu-id="06701-122">Jeśli nie podasz konstruktora statycznego zainicjować pola statyczne, kompilator języka C# będzie dostarczać statycznego konstruktora domyślnego i inicjuje pola statyczne, aby przywrócić wartości domyślne, zgodnie z zaleceniami z [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="06701-122">If you don't provide a static constructor to initialize static fields, the C# compiler will supply a default static constructor that initializes static fields to their default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> 

<span data-ttu-id="06701-123">W poniższym przykładzie użyto statycznego konstruktora zainicjować pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="06701-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="06701-124">Można również zdefiniować Konstruktor statyczny przy użyciu definicji treści wyrażenia, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="06701-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="06701-125">Aby uzyskać więcej informacji i przykładów, zobacz [konstruktorów statycznych](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="06701-125">For more information and examples, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06701-126">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="06701-126">In This Section</span></span>  
 [<span data-ttu-id="06701-127">Używanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="06701-127">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [<span data-ttu-id="06701-128">Konstruktory wystąpień</span><span class="sxs-lookup"><span data-stu-id="06701-128">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [<span data-ttu-id="06701-129">Konstruktory prywatne</span><span class="sxs-lookup"><span data-stu-id="06701-129">Private Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [<span data-ttu-id="06701-130">Konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="06701-130">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [<span data-ttu-id="06701-131">Instrukcje: Zapisywanie konstruktora kopiującego</span><span class="sxs-lookup"><span data-stu-id="06701-131">How to: Write a Copy Constructor</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="06701-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06701-132">See also</span></span>

- [<span data-ttu-id="06701-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="06701-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="06701-134">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="06701-134">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="06701-135">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="06701-135">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="06701-136">static</span><span class="sxs-lookup"><span data-stu-id="06701-136">static</span></span>](../../../csharp/language-reference/keywords/static.md)
- [<span data-ttu-id="06701-137">Dlaczego są inicjatory uruchamiane w kolejności przeciwnej jako konstruktory? Część 1</span><span class="sxs-lookup"><span data-stu-id="06701-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
