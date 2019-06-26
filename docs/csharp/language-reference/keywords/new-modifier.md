---
title: New — modyfikator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 675369936b9f90620b03365104255a622855fa9f
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401783"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="0a1d8-102">New — modyfikator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0a1d8-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="0a1d8-103">Stosowania jako modyfikator deklaracji, `new` — słowo kluczowe jawnie ukrywa składową, która jest dziedziczona z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="0a1d8-104">Po ukryciu dziedziczonego członka, pochodna wersja członka zastępuje wersję klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="0a1d8-105">Chociaż można ukryć elementy członkowskie bez korzystania z `new` modyfikator, zostanie wyświetlone ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="0a1d8-106">Jeśli używasz `new` Aby jawnie ukryć członka, powoduje to pominięcie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="0a1d8-107">Można również użyć `new` słowa kluczowego [utworzenia wystąpienia typu](../operators/new-operator.md) lub jako [ograniczenie typu ogólnego](../keywords/new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="0a1d8-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](../keywords/new-constraint.md).</span></span>

<span data-ttu-id="0a1d8-108">Do ukrywania odziedziczonej składowej, Zadeklaruj go w klasie pochodnej przy użyciu tej samej nazwy elementu członkowskiego i zmodyfikuj go za pomocą `new` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="0a1d8-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0a1d8-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="0a1d8-110">W tym przykładzie `BaseC.Invoke` jest ukryta przez `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="0a1d8-111">Pole `x` pozostanie niezmienione, ponieważ nie jest ukryty przez podobną nazwę.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="0a1d8-112">Ukrywanie nazw poprzez dziedziczenie ma jedną z następujących form:</span><span class="sxs-lookup"><span data-stu-id="0a1d8-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="0a1d8-113">Ogólnie rzecz biorąc stała, pole, właściwość lub typ, który został wprowadzony w klasie lub strukturze ukrywa wszystkie składowe klasy podstawowej, które współdzielą jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="0a1d8-114">Istnieją przypadki specjalne.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-114">There are special cases.</span></span> <span data-ttu-id="0a1d8-115">Na przykład, jeśli zadeklarujesz nowe pole o nazwie `N` typu, którego nie można wywołać i typ podstawowy deklaruje `N` jako metodę, nowe pole nie powoduje ukrycia podstawowej deklaracji w składni wywołania.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="0a1d8-116">Aby uzyskać więcej informacji, zobacz [wyszukanie członka](~/_csharplang/spec/expressions.md#member-lookup) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0a1d8-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="0a1d8-117">Metoda wprowadzona w klasie lub strukturze ukrywa właściwości, pola i typy, które współużytkują tę nazwę w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="0a1d8-118">Ukrywa wszystkie metody klasy podstawowej, które mają taki sam podpis.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="0a1d8-119">Indeksator wprowadzony w klasie lub strukturze ukrywa wszystkie indeksatory klas podstawowych, które mają taki sam podpis.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="0a1d8-120">Jest to błąd, można użyć zarówno `new` i [zastąpienia](override.md) na tym samym użytkownikiem, ponieważ modyfikatorów mają znaczenie wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="0a1d8-121">`new` Modyfikator tworzy nowy element członkowski o takiej samej nazwie i powoduje, że oryginalny element członkowski będzie ukryty.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="0a1d8-122">`override` Modyfikator rozszerza implementację dla odziedziczonego członka.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="0a1d8-123">Za pomocą `new` modyfikatora w deklaracji, która nie ukrywa dziedziczonej składowej generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="0a1d8-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a1d8-124">Example</span></span>

<span data-ttu-id="0a1d8-125">W tym przykładzie klasę bazową `BaseC`i klasę pochodną `DerivedC`, użyj tej samej nazwy pola `x`, która ukrywa wartość odziedziczonego pola.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="0a1d8-126">W przykładzie pokazano użycie `new` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="0a1d8-127">Ilustruje też sposób dostępu do ukrytych członków klasy podstawowej za pomocą ich w pełni kwalifikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="0a1d8-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a1d8-128">Example</span></span>

<span data-ttu-id="0a1d8-129">W tym przykładzie klasa zagnieżdżona ukrywa klasę, która ma taką samą nazwę w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="0a1d8-130">W przykładzie pokazano sposób użycia `new` modyfikator, aby wyeliminować komunikat ostrzegawczy i instrukcje dostęp do członków ukrytej klasy za pomocą ich w pełni kwalifikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="0a1d8-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="0a1d8-131">Jeśli usuniesz `new` modyfikator, program się skompiluje i uruchamiania, ale otrzymasz następujące ostrzeżenie:</span><span class="sxs-lookup"><span data-stu-id="0a1d8-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="0a1d8-132">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0a1d8-132">C# language specification</span></span>

<span data-ttu-id="0a1d8-133">Aby uzyskać więcej informacji, zobacz [nowy modyfikator](~/_csharplang/spec/classes.md#the-new-modifier) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0a1d8-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0a1d8-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a1d8-134">See also</span></span>

- [<span data-ttu-id="0a1d8-135">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0a1d8-135">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="0a1d8-136">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0a1d8-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0a1d8-137">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0a1d8-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0a1d8-138">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="0a1d8-138">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="0a1d8-139">Przechowywanie wersji przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="0a1d8-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="0a1d8-140">Użycie przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="0a1d8-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
