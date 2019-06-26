---
title: Zastąp modyfikator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: cedce26373c49d33ee17602b621f71ef6732d145
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401545"
---
# <a name="override-c-reference"></a><span data-ttu-id="fbdb5-102">override (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="fbdb5-102">override (C# Reference)</span></span>

<span data-ttu-id="fbdb5-103">`override` Modyfikator jest wymagane, aby rozszerzyć lub zmodyfikować implementacji abstrakcyjne lub wirtualne dziedziczonej metody, właściwości, indeksatora lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fbdb5-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="fbdb5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fbdb5-104">Example</span></span>

<span data-ttu-id="fbdb5-105">W tym przykładzie `Square` klasa musi dostarczać implementację zgodnym z przesłoniętą `Area` ponieważ `Area` jest dziedziczony z abstrakcyjnej `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="fbdb5-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="fbdb5-106">`override` Metoda dostarcza nową implementację elementu członkowskiego, który jest dziedziczony z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="fbdb5-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="fbdb5-107">Metoda, która została zastąpiona przez `override` deklaracji jest znany jako przesłonięte metody podstawowej.</span><span class="sxs-lookup"><span data-stu-id="fbdb5-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="fbdb5-108">Zastąpione metody podstawowej musi mieć taką samą sygnaturę jak `override` metody.</span><span class="sxs-lookup"><span data-stu-id="fbdb5-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="fbdb5-109">Aby uzyskać informacji na temat dziedziczenia, zobacz [dziedziczenia](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="fbdb5-109">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="fbdb5-110">Nie można zastąpić niewirtualną lub statycznej metody.</span><span class="sxs-lookup"><span data-stu-id="fbdb5-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="fbdb5-111">Zastąpione metody podstawowej musi być `virtual`, `abstract`, lub `override`.</span><span class="sxs-lookup"><span data-stu-id="fbdb5-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="fbdb5-112">`override` Deklaracji nie można zmienić dostępności `virtual` metody.</span><span class="sxs-lookup"><span data-stu-id="fbdb5-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="fbdb5-113">Zarówno `override` metody i `virtual` metoda musi mieć takie same [modyfikator dostępu dla poziomu](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="fbdb5-113">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="fbdb5-114">Nie można użyć `new`, `static`, lub `virtual` Modyfikatory do modyfikowania `override` metody.</span><span class="sxs-lookup"><span data-stu-id="fbdb5-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="fbdb5-115">Przesłanianie deklaracja właściwości należy określić jako właściwość dziedziczona dokładnie tych samych modyfikator dostępu, typ i nazwa i właściwości musi być `virtual`, `abstract`, lub `override`.</span><span class="sxs-lookup"><span data-stu-id="fbdb5-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="fbdb5-116">Aby uzyskać więcej informacji o sposobie używania `override` — słowo kluczowe, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [użycie przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="fbdb5-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="fbdb5-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="fbdb5-117">Example</span></span>

<span data-ttu-id="fbdb5-118">Ten przykład definiuje klasę bazową, o nazwie `Employee`, a klasa pochodna o nazwie `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="fbdb5-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="fbdb5-119">`SalesEmployee` Klasa zawiera dodatkowe pola, `salesbonus`i zastępuje metodę `CalculatePay` niezbędny do konta.</span><span class="sxs-lookup"><span data-stu-id="fbdb5-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="fbdb5-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fbdb5-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fbdb5-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbdb5-121">See also</span></span>

- [<span data-ttu-id="fbdb5-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fbdb5-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fbdb5-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fbdb5-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fbdb5-124">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="fbdb5-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="fbdb5-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="fbdb5-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fbdb5-126">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="fbdb5-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="fbdb5-127">abstract</span><span class="sxs-lookup"><span data-stu-id="fbdb5-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="fbdb5-128">virtual</span><span class="sxs-lookup"><span data-stu-id="fbdb5-128">virtual</span></span>](virtual.md)
- [<span data-ttu-id="fbdb5-129">Nowy (modyfikator)</span><span class="sxs-lookup"><span data-stu-id="fbdb5-129">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="fbdb5-130">Polimorfizm</span><span class="sxs-lookup"><span data-stu-id="fbdb5-130">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
