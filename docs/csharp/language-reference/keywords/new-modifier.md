---
title: New modyfikator — odwołanie w C#
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 529d77b0a66a8a3cedfe7a400af0fb34dd653322
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795173"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="58af0-102">New — modyfikator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="58af0-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="58af0-103">Gdy jest używany jako modyfikator deklaracji, `new` słowo kluczowe jawnie ukrywa element członkowski, który jest Dziedziczony z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="58af0-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="58af0-104">W przypadku ukrycia dziedziczonego elementu członkowskiego wersja pochodna elementu członkowskiego zastępuje wersję klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="58af0-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="58af0-105">Chociaż można ukryć składowe bez użycia `new` modyfikatora, zostanie wyświetlone ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="58af0-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="58af0-106">Jeśli używasz `new` , aby jawnie ukryć element członkowski, pomija to ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="58af0-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="58af0-107">Możesz również użyć słowa kluczowego, `new` aby [utworzyć wystąpienie typu](../operators/new-operator.md) lub jako [ograniczenie typu ogólnego](./new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="58af0-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="58af0-108">Aby ukryć dziedziczonego elementu członkowskiego, zadeklaruj go w klasie pochodnej przy użyciu tej samej nazwy elementu członkowskiego i zmodyfikuj `new` go za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="58af0-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="58af0-109">Przykład:</span><span class="sxs-lookup"><span data-stu-id="58af0-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="58af0-110">W tym przykładzie `BaseC.Invoke` jest ukryta przez `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="58af0-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="58af0-111">Nie ma `x` to wpływ na pole, ponieważ nie jest ono ukryte przez podobną nazwę.</span><span class="sxs-lookup"><span data-stu-id="58af0-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="58af0-112">Nazwa ukrywając przy użyciu dziedziczenia ma jedną z następujących form:</span><span class="sxs-lookup"><span data-stu-id="58af0-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="58af0-113">Ogólnie rzecz biorąc, stała, pole, właściwość lub typ, który jest wprowadzany w klasie lub strukturze ukrywa wszystkie elementy członkowskie klasy bazowej, które współdzielą swoją nazwę.</span><span class="sxs-lookup"><span data-stu-id="58af0-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="58af0-114">Istnieją specjalne przypadki.</span><span class="sxs-lookup"><span data-stu-id="58af0-114">There are special cases.</span></span> <span data-ttu-id="58af0-115">Na przykład jeśli zadeklarujesz nowe pole o nazwie `N` , aby miało typ, który nie jest wywoływać, a typ podstawowy deklaruje `N` jako metodę, nowe pole nie ukrywa deklaracji bazowej w składni wywołania.</span><span class="sxs-lookup"><span data-stu-id="58af0-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="58af0-116">Aby uzyskać więcej informacji, zobacz sekcję [Wyszukiwanie elementów członkowskich](~/_csharplang/spec/expressions.md#member-lookup) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="58af0-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="58af0-117">Metoda wprowadzona w klasie lub strukturze ukrywa właściwości, pola i typy, które współużytkują tę nazwę w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="58af0-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="58af0-118">Ukrywa także wszystkie metody klasy bazowej, które mają taki sam podpis.</span><span class="sxs-lookup"><span data-stu-id="58af0-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="58af0-119">Indeksator wprowadzony w klasie lub strukturze ukrywa wszystkie indeksatory klasy bazowej, które mają taki sam podpis.</span><span class="sxs-lookup"><span data-stu-id="58af0-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="58af0-120">Jest to błąd do użycia `new` i [przesłonięcia](override.md) dla tego samego elementu członkowskiego, ponieważ dwa Modyfikatory mają wzajemnie wykluczające się znaczenie.</span><span class="sxs-lookup"><span data-stu-id="58af0-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="58af0-121">`new` Modyfikator tworzy nowy element członkowski o tej samej nazwie i powoduje, że oryginalny element członkowski staje się ukryty.</span><span class="sxs-lookup"><span data-stu-id="58af0-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="58af0-122">`override` Modyfikator rozszerza implementację dziedziczonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="58af0-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="58af0-123">Użycie `new` modyfikatora w deklaracji, która nie ukrywa dziedziczonego elementu członkowskiego, generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="58af0-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="58af0-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="58af0-124">Example</span></span>

<span data-ttu-id="58af0-125">W tym przykładzie Klasa bazowa, `BaseC`, i Klasa `DerivedC`pochodna, używają tej samej nazwy `x`pola, która ukrywa wartość dziedziczonego pola.</span><span class="sxs-lookup"><span data-stu-id="58af0-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="58af0-126">W przykładzie pokazano użycie `new` modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="58af0-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="58af0-127">Pokazano również, jak uzyskać dostęp do ukrytych elementów członkowskich klasy podstawowej przy użyciu ich w pełni kwalifikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="58af0-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="58af0-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="58af0-128">Example</span></span>

<span data-ttu-id="58af0-129">W tym przykładzie Klasa zagnieżdżona ukrywa klasę o tej samej nazwie w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="58af0-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="58af0-130">W przykładzie pokazano, `new` jak za pomocą modyfikatora wyeliminować komunikat ostrzegawczy i jak uzyskać dostęp do ukrytych elementów członkowskich klasy przy użyciu ich w pełni kwalifikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="58af0-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="58af0-131">Jeśli usuniesz `new` modyfikator, program będzie nadal kompilować i uruchamiać, ale otrzymasz następujące ostrzeżenie:</span><span class="sxs-lookup"><span data-stu-id="58af0-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="58af0-132">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="58af0-132">C# language specification</span></span>

<span data-ttu-id="58af0-133">Aby uzyskać więcej informacji, zobacz sekcję [New modyfikator](~/_csharplang/spec/classes.md#the-new-modifier) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="58af0-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="58af0-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58af0-134">See also</span></span>

- [<span data-ttu-id="58af0-135">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="58af0-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="58af0-136">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="58af0-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="58af0-137">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="58af0-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="58af0-138">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="58af0-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="58af0-139">Przechowywanie wersji przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="58af0-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="58af0-140">Użycie zastępowania i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="58af0-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
