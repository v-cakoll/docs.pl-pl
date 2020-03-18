---
title: Konstruktorzy — przewodnik programowania Języka C#
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 8eedfaed111f01cc2ec55a2f42df66d4588bd42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399792"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="7b21c-102">Konstruktorzy (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="7b21c-102">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="7b21c-103">Za każdym razem, gdy tworzona jest [klasa](../../language-reference/keywords/class.md) lub [struktura,](../../language-reference/builtin-types/struct.md) jego konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="7b21c-103">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="7b21c-104">Klasa lub struktura może mieć wiele konstruktorów, które przyjmują różne argumenty.</span><span class="sxs-lookup"><span data-stu-id="7b21c-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="7b21c-105">Konstruktorzy umożliwiają programisty ustawienie wartości domyślnych, ograniczenie wystąpienia i zapiskodu, który jest elastyczny i łatwy do odczytania.</span><span class="sxs-lookup"><span data-stu-id="7b21c-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="7b21c-106">Aby uzyskać więcej informacji i przykłady, zobacz [Korzystanie z konstruktorów](./using-constructors.md) i [konstruktorów wystąpień](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="7b21c-106">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="7b21c-107">Konstruktory bez parametrów</span><span class="sxs-lookup"><span data-stu-id="7b21c-107">Parameterless constructors</span></span>
  
<span data-ttu-id="7b21c-108">Jeśli nie podasz konstruktora dla klasy, C# tworzy domyślnie jeden, który tworzy obiekt i ustawia zmienne członkowskie do wartości domyślnych, jak wymienione w [wartości domyślne c# typy](../../language-reference/builtin-types/default-values.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="7b21c-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span> <span data-ttu-id="7b21c-109">Jeśli nie podasz konstruktora dla struktury, C# opiera się na *niejawnykonstruktor bezparametrów,* aby automatycznie zainicjować każde pole do jego wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="7b21c-109">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field to its default value.</span></span> <span data-ttu-id="7b21c-110">Aby uzyskać więcej informacji i przykłady, zobacz [Konstruktory wystąpienia](instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="7b21c-110">For more information and examples, see [Instance constructors](instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="7b21c-111">Składnia konstruktora</span><span class="sxs-lookup"><span data-stu-id="7b21c-111">Constructor syntax</span></span>

<span data-ttu-id="7b21c-112">Konstruktor jest metodą, której nazwa jest taka sama jak nazwa jego typu.</span><span class="sxs-lookup"><span data-stu-id="7b21c-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="7b21c-113">Jego podpis metody zawiera tylko nazwę metody i jej listę parametrów; nie zawiera typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="7b21c-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="7b21c-114">W poniższym przykładzie przedstawiono konstruktora dla klasy o nazwie `Person`.</span><span class="sxs-lookup"><span data-stu-id="7b21c-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="7b21c-115">Jeśli konstruktor może być zaimplementowany jako pojedyncza instrukcja, można użyć [definicji treści wyrażenia](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="7b21c-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="7b21c-116">Poniższy przykład definiuje `Location` klasę, której konstruktor ma parametr pojedynczego ciągu *o*nazwie .</span><span class="sxs-lookup"><span data-stu-id="7b21c-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="7b21c-117">Definicja treści wyrażeń `locationName` przypisuje argument do pola.</span><span class="sxs-lookup"><span data-stu-id="7b21c-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="7b21c-118">Konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="7b21c-118">Static constructors</span></span>

<span data-ttu-id="7b21c-119">Poprzednie przykłady mają wszystkie pokazane konstruktory wystąpienia, które tworzą nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="7b21c-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="7b21c-120">Klasa lub struktura może mieć również konstruktora statycznego, który inicjuje statyczne elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="7b21c-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="7b21c-121">Konstruktory statyczne są bezparametrowe.</span><span class="sxs-lookup"><span data-stu-id="7b21c-121">Static constructors are parameterless.</span></span> <span data-ttu-id="7b21c-122">Jeśli konstruktor statyczny nie zostanie zainicjowany przez konstruktor statyczny, kompilator Języka C# inicjuje pola statyczne do ich wartości domyślnej, jak wymieniono w artykule [Wartości domyślne typów Języka C#.](../../language-reference/builtin-types/default-values.md)</span><span class="sxs-lookup"><span data-stu-id="7b21c-122">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span>

<span data-ttu-id="7b21c-123">W poniższym przykładzie użyto konstruktora statycznego do zainicjowania pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="7b21c-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="7b21c-124">Można również zdefiniować konstruktora statycznego z definicji treści wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7b21c-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="7b21c-125">Aby uzyskać więcej informacji i przykładów, zobacz [Konstruktora statyczne](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="7b21c-125">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b21c-126">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7b21c-126">In This Section</span></span>  
 [<span data-ttu-id="7b21c-127">Używanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="7b21c-127">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="7b21c-128">Konstruktory wystąpień</span><span class="sxs-lookup"><span data-stu-id="7b21c-128">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="7b21c-129">Konstruktory prywatne</span><span class="sxs-lookup"><span data-stu-id="7b21c-129">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="7b21c-130">Konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="7b21c-130">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="7b21c-131">Porada: zapisywanie konstruktora kopiującego</span><span class="sxs-lookup"><span data-stu-id="7b21c-131">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="7b21c-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b21c-132">See also</span></span>

- [<span data-ttu-id="7b21c-133">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="7b21c-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7b21c-134">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="7b21c-134">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="7b21c-135">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="7b21c-135">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="7b21c-136">Statyczne</span><span class="sxs-lookup"><span data-stu-id="7b21c-136">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="7b21c-137">Dlaczego inicjatorzy działają w odwrotnym porządku jako konstruktorzy? Część pierwsze</span><span class="sxs-lookup"><span data-stu-id="7b21c-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
