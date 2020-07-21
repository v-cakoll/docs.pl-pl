---
title: Konstruktory — Przewodnik programowania w języku C#
description: Konstruktor w języku C# jest wywoływany, gdy tworzona jest Klasa lub struktura. Używaj konstruktorów, aby ustawiać wartości domyślne, ograniczać Tworzenie wystąpień i pisać elastyczne, czytelne kod.
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 4a731e648143f5e0ecf8860625962d8baa29fe26
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474907"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="21dd1-104">Konstruktorzy (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="21dd1-104">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="21dd1-105">Za każdym razem, gdy tworzona jest [Klasa](../../language-reference/keywords/class.md) lub [Struktura](../../language-reference/builtin-types/struct.md) , jego Konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="21dd1-105">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="21dd1-106">Klasa lub struktura może mieć wiele konstruktorów przyjmujących różne argumenty.</span><span class="sxs-lookup"><span data-stu-id="21dd1-106">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="21dd1-107">Konstruktory umożliwiają programistom Ustawianie wartości domyślnych, ograniczenie tworzenia wystąpień i pisanie kodu, który jest elastyczny i łatwy do odczytania.</span><span class="sxs-lookup"><span data-stu-id="21dd1-107">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="21dd1-108">Aby uzyskać więcej informacji i przykładów, zobacz [Używanie konstruktorów](./using-constructors.md) i [konstruktorów wystąpień](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="21dd1-108">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="21dd1-109">Konstruktory bez parametrów</span><span class="sxs-lookup"><span data-stu-id="21dd1-109">Parameterless constructors</span></span>
  
<span data-ttu-id="21dd1-110">Jeśli nie podajesz konstruktora dla klasy, w języku C# domyślnie zostanie utworzona jedna z nich, która tworzy wystąpienie obiektu i ustawia zmienne Członkowskie na wartości domyślne, zgodnie z [wartościami domyślnymi w artykule typy C#](../../language-reference/builtin-types/default-values.md) .</span><span class="sxs-lookup"><span data-stu-id="21dd1-110">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span> <span data-ttu-id="21dd1-111">Jeśli nie podano konstruktora dla struktury, C# opiera się na *niejawnym konstruktorze bez parametrów* , aby automatycznie inicjować każde pole do wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="21dd1-111">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field to its default value.</span></span> <span data-ttu-id="21dd1-112">Aby uzyskać więcej informacji i przykładów, zobacz [konstruktory wystąpień](instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="21dd1-112">For more information and examples, see [Instance constructors](instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="21dd1-113">Składnia konstruktora</span><span class="sxs-lookup"><span data-stu-id="21dd1-113">Constructor syntax</span></span>

<span data-ttu-id="21dd1-114">Konstruktor jest metodą, której nazwa jest taka sama jak nazwa jej typu.</span><span class="sxs-lookup"><span data-stu-id="21dd1-114">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="21dd1-115">Podpis metody zawiera tylko nazwę metody i jej listę parametrów; nie zawiera typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="21dd1-115">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="21dd1-116">Poniższy przykład pokazuje konstruktora dla klasy o nazwie `Person` .</span><span class="sxs-lookup"><span data-stu-id="21dd1-116">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="21dd1-117">Jeśli Konstruktor można zaimplementować jako pojedynczą instrukcję, można użyć [definicji treści wyrażenia](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="21dd1-117">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="21dd1-118">W poniższym przykładzie zdefiniowano `Location` klasę, której Konstruktor ma jeden parametr ciągu o nazwie *name*.</span><span class="sxs-lookup"><span data-stu-id="21dd1-118">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="21dd1-119">Definicja treści wyrażenia przypisuje argument do `locationName` pola.</span><span class="sxs-lookup"><span data-stu-id="21dd1-119">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="21dd1-120">Konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="21dd1-120">Static constructors</span></span>

<span data-ttu-id="21dd1-121">W poprzednich przykładach są wyświetlane konstruktory wystąpień, które tworzą nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="21dd1-121">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="21dd1-122">Klasa lub struktura może również mieć Konstruktor statyczny, który inicjuje statyczne elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="21dd1-122">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="21dd1-123">Konstruktory statyczne są bezparametryczne.</span><span class="sxs-lookup"><span data-stu-id="21dd1-123">Static constructors are parameterless.</span></span> <span data-ttu-id="21dd1-124">Jeśli nie postanowisz statycznego konstruktora do zainicjowania pól statycznych, kompilator języka C# inicjuje statyczne pola do ich wartości domyślnej, jak wymieniono w [domyślnych wartościach typu C#](../../language-reference/builtin-types/default-values.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="21dd1-124">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span>

<span data-ttu-id="21dd1-125">Poniższy przykład używa konstruktora statycznego, aby zainicjować pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="21dd1-125">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="21dd1-126">Można również zdefiniować statyczny Konstruktor z definicją treści wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="21dd1-126">You can also define a static constructor with an expression body definition, as the following example shows.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="21dd1-127">Aby uzyskać więcej informacji i przykładów, zobacz [statyczne konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="21dd1-127">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21dd1-128">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="21dd1-128">In This Section</span></span>  
 [<span data-ttu-id="21dd1-129">Używanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="21dd1-129">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="21dd1-130">Konstruktory wystąpień</span><span class="sxs-lookup"><span data-stu-id="21dd1-130">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="21dd1-131">Konstruktory prywatne</span><span class="sxs-lookup"><span data-stu-id="21dd1-131">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="21dd1-132">Konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="21dd1-132">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="21dd1-133">Porada: zapisywanie konstruktora kopiującego</span><span class="sxs-lookup"><span data-stu-id="21dd1-133">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="21dd1-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21dd1-134">See also</span></span>

- [<span data-ttu-id="21dd1-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="21dd1-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="21dd1-136">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="21dd1-136">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="21dd1-137">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="21dd1-137">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="21dd1-138">static</span><span class="sxs-lookup"><span data-stu-id="21dd1-138">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="21dd1-139">Dlaczego inicjatory są uruchamiane w kolejności odwrotnej jako konstruktory? Część 1</span><span class="sxs-lookup"><span data-stu-id="21dd1-139">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
