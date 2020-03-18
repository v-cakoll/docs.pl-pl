---
title: nowy modyfikator — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 6c4fedd469efb79f91780dff26da89b586de2d1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713343"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="51d29-102">nowy modyfikator (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="51d29-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="51d29-103">Gdy jest używany jako modyfikator deklaracji, `new` słowo kluczowe jawnie ukrywa element członkowski, który jest dziedziczony z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="51d29-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="51d29-104">Po ukryciu dziedziczonego elementu członkowskiego pochodna wersja elementu członkowskiego zastępuje wersję klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="51d29-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="51d29-105">Mimo że można ukryć `new` członków bez użycia modyfikatora, otrzymasz ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="51d29-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="51d29-106">Jeśli używasz `new` jawnie ukryć element członkowski, pomija to ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="51d29-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="51d29-107">Za pomocą słowa `new` kluczowego można również [utworzyć wystąpienie typu](../operators/new-operator.md) lub jako ograniczenie typu [ogólnego](./new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="51d29-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="51d29-108">Aby ukryć dziedziczonego elementu członkowskiego, zadeklarować go w klasie pochodnej `new` przy użyciu tej samej nazwy elementu członkowskiego i zmodyfikować go za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="51d29-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="51d29-109">Przykład:</span><span class="sxs-lookup"><span data-stu-id="51d29-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="51d29-110">W tym `BaseC.Invoke` przykładzie jest `DerivedC.Invoke`ukryty przez .</span><span class="sxs-lookup"><span data-stu-id="51d29-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="51d29-111">Nie `x` ma to wpływu na to pole, ponieważ nie jest ukryte pod podobną nazwą.</span><span class="sxs-lookup"><span data-stu-id="51d29-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="51d29-112">Ukrywanie nazw w dziedziczeniu przyjmuje jedną z następujących form:</span><span class="sxs-lookup"><span data-stu-id="51d29-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="51d29-113">Ogólnie rzecz biorąc stała, pole, właściwość lub typ, który jest wprowadzany w klasie lub struktury ukrywa wszystkie elementy członkowskie klasy podstawowej, które współużytkują jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="51d29-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="51d29-114">Istnieją szczególne przypadki.</span><span class="sxs-lookup"><span data-stu-id="51d29-114">There are special cases.</span></span> <span data-ttu-id="51d29-115">Na przykład jeśli ogłosisz nowe `N` pole o nazwie, które ma typ, który `N` nie jest inwolny, a typ podstawowy deklaruje się jako metoda, nowe pole nie ukrywa deklaracji podstawowej w składni wywołania.</span><span class="sxs-lookup"><span data-stu-id="51d29-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="51d29-116">Aby uzyskać więcej informacji, zobacz sekcję [wyszukiwania elementów członkowskich](~/_csharplang/spec/expressions.md#member-lookup) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="51d29-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="51d29-117">Metoda wprowadzona w klasie lub strukturze ukrywa właściwości, pola i typy, które współużytkują tę nazwę w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="51d29-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="51d29-118">Ukrywa również wszystkie metody klasy podstawowej, które mają ten sam podpis.</span><span class="sxs-lookup"><span data-stu-id="51d29-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="51d29-119">Indeksator wprowadzony w klasie lub struktury ukrywa wszystkie indeksatory klasy podstawowej, które mają ten sam podpis.</span><span class="sxs-lookup"><span data-stu-id="51d29-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="51d29-120">Jest to błąd, `new` aby użyć obu i [zastąpić](override.md) na tym samym e-elementczłonko, ponieważ dwa modyfikatory mają wzajemnie wykluczające się znaczenia.</span><span class="sxs-lookup"><span data-stu-id="51d29-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="51d29-121">Modyfikator `new` tworzy nowy element członkowski o tej samej nazwie i powoduje, że oryginalny element członkowski staje się ukryty.</span><span class="sxs-lookup"><span data-stu-id="51d29-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="51d29-122">Modyfikator `override` rozszerza implementację dla dziedziczonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="51d29-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="51d29-123">Za `new` pomocą modyfikatora w deklaracji, która nie ukrywa dziedziczonego elementu członkowskiego generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="51d29-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="51d29-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="51d29-124">Example</span></span>

<span data-ttu-id="51d29-125">W tym przykładzie klasa `BaseC`podstawowa i klasa `DerivedC`pochodna używają tej `x`samej nazwy pola , która ukrywa wartość odziedziczonego pola.</span><span class="sxs-lookup"><span data-stu-id="51d29-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="51d29-126">W przykładzie przedstawiono użycie `new` modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="51d29-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="51d29-127">Pokazuje również, jak uzyskać dostęp do ukrytych elementów członkowskich klasy podstawowej przy użyciu ich w pełni kwalifikowane nazwy.</span><span class="sxs-lookup"><span data-stu-id="51d29-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="51d29-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="51d29-128">Example</span></span>

<span data-ttu-id="51d29-129">W tym przykładzie klasa zagnieżdżona ukrywa klasę, która ma taką samą nazwę w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="51d29-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="51d29-130">W przykładzie pokazano, `new` jak używać modyfikatora, aby wyeliminować komunikat ostrzegawczy i jak uzyskać dostęp do ukrytych elementów członkowskich klasy przy użyciu ich w pełni kwalifikowane nazwy.</span><span class="sxs-lookup"><span data-stu-id="51d29-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="51d29-131">Jeśli usuniesz `new` modyfikator, program będzie nadal kompilować i uruchamiać, ale pojawi się następujące ostrzeżenie:</span><span class="sxs-lookup"><span data-stu-id="51d29-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="51d29-132">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="51d29-132">C# language specification</span></span>

<span data-ttu-id="51d29-133">Aby uzyskać więcej informacji, zobacz [Sekcję modyfikatora](~/_csharplang/spec/classes.md#the-new-modifier) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="51d29-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="51d29-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51d29-134">See also</span></span>

- [<span data-ttu-id="51d29-135">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="51d29-135">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="51d29-136">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="51d29-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="51d29-137">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="51d29-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="51d29-138">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="51d29-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="51d29-139">Przechowywanie wersji przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="51d29-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="51d29-140">Użycie zastępowania i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="51d29-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
