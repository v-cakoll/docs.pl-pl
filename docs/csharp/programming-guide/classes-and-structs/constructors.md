---
title: Konstruktory C# — Przewodnik programowania
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 8eedfaed111f01cc2ec55a2f42df66d4588bd42f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626740"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="dfd10-102">Konstruktorzy (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="dfd10-102">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="dfd10-103">Za każdym razem, gdy tworzona jest [Klasa](../../language-reference/keywords/class.md) lub [Struktura](../../language-reference/builtin-types/struct.md) , jego Konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="dfd10-103">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="dfd10-104">Klasa lub struktura może mieć wiele konstruktorów przyjmujących różne argumenty.</span><span class="sxs-lookup"><span data-stu-id="dfd10-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="dfd10-105">Konstruktory umożliwiają programistom Ustawianie wartości domyślnych, ograniczenie tworzenia wystąpień i pisanie kodu, który jest elastyczny i łatwy do odczytania.</span><span class="sxs-lookup"><span data-stu-id="dfd10-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="dfd10-106">Aby uzyskać więcej informacji i przykładów, zobacz [Używanie konstruktorów](./using-constructors.md) i [konstruktorów wystąpień](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="dfd10-106">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="dfd10-107">Konstruktory bez parametrów</span><span class="sxs-lookup"><span data-stu-id="dfd10-107">Parameterless constructors</span></span>
  
<span data-ttu-id="dfd10-108">Jeśli nie podano konstruktora dla klasy, program C# tworzy jedną z nich domyślnie, tworząc wystąpienie obiektu i ustawia zmienne Członkowskie na wartości domyślne, jak wymieniono w [wartości domyślne C# typów](../../language-reference/builtin-types/default-values.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="dfd10-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span> <span data-ttu-id="dfd10-109">Jeśli nie podano konstruktora dla struktury, zależy on C# od *niejawnego konstruktora bez parametrów* , aby automatycznie inicjować każde pole do wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="dfd10-109">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field to its default value.</span></span> <span data-ttu-id="dfd10-110">Aby uzyskać więcej informacji i przykładów, zobacz [konstruktory wystąpień](instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="dfd10-110">For more information and examples, see [Instance constructors](instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="dfd10-111">Składnia konstruktora</span><span class="sxs-lookup"><span data-stu-id="dfd10-111">Constructor syntax</span></span>

<span data-ttu-id="dfd10-112">Konstruktor jest metodą, której nazwa jest taka sama jak nazwa jej typu.</span><span class="sxs-lookup"><span data-stu-id="dfd10-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="dfd10-113">Podpis metody zawiera tylko nazwę metody i jej listę parametrów; nie zawiera typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="dfd10-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="dfd10-114">Poniższy przykład pokazuje konstruktora dla klasy o nazwie `Person`.</span><span class="sxs-lookup"><span data-stu-id="dfd10-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="dfd10-115">Jeśli Konstruktor można zaimplementować jako pojedynczą instrukcję, można użyć [definicji treści wyrażenia](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="dfd10-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="dfd10-116">W poniższym przykładzie zdefiniowano klasę `Location`, której Konstruktor ma jeden parametr ciągu o nazwie *name*.</span><span class="sxs-lookup"><span data-stu-id="dfd10-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="dfd10-117">Definicja treści wyrażenia przypisuje argument do pola `locationName`.</span><span class="sxs-lookup"><span data-stu-id="dfd10-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="dfd10-118">Konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="dfd10-118">Static constructors</span></span>

<span data-ttu-id="dfd10-119">W poprzednich przykładach są wyświetlane konstruktory wystąpień, które tworzą nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="dfd10-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="dfd10-120">Klasa lub struktura może również mieć Konstruktor statyczny, który inicjuje statyczne elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="dfd10-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="dfd10-121">Konstruktory statyczne są bezparametryczne.</span><span class="sxs-lookup"><span data-stu-id="dfd10-121">Static constructors are parameterless.</span></span> <span data-ttu-id="dfd10-122">Jeśli nie postanowisz statycznego konstruktora do zainicjowania pól statycznych C# , kompilator inicjuje statyczne pola do ich wartości domyślnej, jak wymieniono w [wartości C# domyślne typów](../../language-reference/builtin-types/default-values.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="dfd10-122">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span>

<span data-ttu-id="dfd10-123">Poniższy przykład używa konstruktora statycznego, aby zainicjować pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="dfd10-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="dfd10-124">Można również zdefiniować statyczny Konstruktor z definicją treści wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="dfd10-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="dfd10-125">Aby uzyskać więcej informacji i przykładów, zobacz [statyczne konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="dfd10-125">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dfd10-126">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="dfd10-126">In This Section</span></span>  
 [<span data-ttu-id="dfd10-127">Używanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="dfd10-127">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="dfd10-128">Konstruktory wystąpień</span><span class="sxs-lookup"><span data-stu-id="dfd10-128">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="dfd10-129">Konstruktory prywatne</span><span class="sxs-lookup"><span data-stu-id="dfd10-129">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="dfd10-130">Konstruktory statyczne</span><span class="sxs-lookup"><span data-stu-id="dfd10-130">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="dfd10-131">Jak napisać Konstruktor kopiujący</span><span class="sxs-lookup"><span data-stu-id="dfd10-131">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="dfd10-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfd10-132">See also</span></span>

- [<span data-ttu-id="dfd10-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="dfd10-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dfd10-134">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="dfd10-134">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="dfd10-135">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="dfd10-135">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="dfd10-136">static</span><span class="sxs-lookup"><span data-stu-id="dfd10-136">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="dfd10-137">Dlaczego inicjatory są uruchamiane w kolejności odwrotnej jako konstruktory? Część 1</span><span class="sxs-lookup"><span data-stu-id="dfd10-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
