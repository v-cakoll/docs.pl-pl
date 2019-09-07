---
title: Zastąp modyfikator C# -Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: bbdbcaf466e0b4dca4b78902ca9e7a49b02ac718
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394237"
---
# <a name="override-c-reference"></a><span data-ttu-id="aa6eb-102">override (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="aa6eb-102">override (C# Reference)</span></span>

<span data-ttu-id="aa6eb-103">`override` Modyfikator jest wymagany, aby zwiększyć lub zmodyfikować abstrakcyjną lub wirtualną implementację dziedziczonej metody, właściwości, indeksatora lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aa6eb-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="aa6eb-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa6eb-104">Example</span></span>

<span data-ttu-id="aa6eb-105">W tym przykładzie `Square` Klasa musi udostępniać zastąpioną `GetArea` implementację, ponieważ `GetArea` jest dziedziczona z klasy abstrakcyjnej `Shape` :</span><span class="sxs-lookup"><span data-stu-id="aa6eb-105">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="aa6eb-106">`override` Metoda zapewnia nową implementację elementu członkowskiego, który jest Dziedziczony z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="aa6eb-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="aa6eb-107">Metoda zastępowana przez `override` deklarację jest znana jako zastąpiona metoda podstawowa.</span><span class="sxs-lookup"><span data-stu-id="aa6eb-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="aa6eb-108">Zastąpiona metoda bazowa musi mieć taką samą sygnaturę jak `override` Metoda.</span><span class="sxs-lookup"><span data-stu-id="aa6eb-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="aa6eb-109">Aby uzyskać informacje na temat dziedziczenia, zobacz [dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="aa6eb-109">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="aa6eb-110">Nie można zastąpić metody niewirtualnej lub statycznej.</span><span class="sxs-lookup"><span data-stu-id="aa6eb-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="aa6eb-111">Zastąpiona metoda bazowa musi mieć `virtual`wartość `abstract`,, `override`lub.</span><span class="sxs-lookup"><span data-stu-id="aa6eb-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="aa6eb-112">Deklaracja nie może zmienić dostępności `virtual` metody. `override`</span><span class="sxs-lookup"><span data-stu-id="aa6eb-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="aa6eb-113">Obie metody i metody muszą mieć ten sam [modyfikator poziomu dostępu.](access-modifiers.md) `virtual` `override`</span><span class="sxs-lookup"><span data-stu-id="aa6eb-113">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="aa6eb-114">Nie można `new`użyć modyfikatora `static`, lub `virtual` , aby zmodyfikować `override` metodę.</span><span class="sxs-lookup"><span data-stu-id="aa6eb-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="aa6eb-115">Zastępowanie deklaracji właściwości musi określać dokładnie ten sam modyfikator dostępu, typ i nazwę, co Właściwość dziedziczona, a zastąpiona właściwość musi mieć `virtual`wartość `abstract`, lub `override`.</span><span class="sxs-lookup"><span data-stu-id="aa6eb-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="aa6eb-116">Aby uzyskać więcej informacji na temat sposobu używania `override` słowa kluczowego, zobacz [przechowywanie wersji z przesłonięciami i nowymi słowami kluczowymi](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [wiedzą, kiedy używać przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="aa6eb-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="aa6eb-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa6eb-117">Example</span></span>

<span data-ttu-id="aa6eb-118">W tym przykładzie zdefiniowano klasę bazową o nazwie `Employee`i klasę pochodną o nazwie. `SalesEmployee`</span><span class="sxs-lookup"><span data-stu-id="aa6eb-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="aa6eb-119">Klasa zawiera dodatkowe pole, `salesbonus`i zastępuje metodę `CalculatePay` , aby można było ją uwzględnić. `SalesEmployee`</span><span class="sxs-lookup"><span data-stu-id="aa6eb-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="aa6eb-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="aa6eb-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="aa6eb-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa6eb-121">See also</span></span>

- [<span data-ttu-id="aa6eb-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="aa6eb-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aa6eb-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="aa6eb-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aa6eb-124">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="aa6eb-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="aa6eb-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="aa6eb-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="aa6eb-126">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="aa6eb-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="aa6eb-127">abstract</span><span class="sxs-lookup"><span data-stu-id="aa6eb-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="aa6eb-128">virtual</span><span class="sxs-lookup"><span data-stu-id="aa6eb-128">virtual</span></span>](virtual.md)
- [<span data-ttu-id="aa6eb-129">New (modyfikator)</span><span class="sxs-lookup"><span data-stu-id="aa6eb-129">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="aa6eb-130">Polimorfizm</span><span class="sxs-lookup"><span data-stu-id="aa6eb-130">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
