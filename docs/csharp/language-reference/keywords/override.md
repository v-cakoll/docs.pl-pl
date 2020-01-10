---
title: Zastąp modyfikator C# -Reference
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: acad3aa3b196c184132ad1acdf52b18a799b0896
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713251"
---
# <a name="override-c-reference"></a><span data-ttu-id="78e89-102">override (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="78e89-102">override (C# Reference)</span></span>

<span data-ttu-id="78e89-103">Modyfikator `override` jest wymagany do rozszerania lub modyfikowania abstrakcyjnej lub wirtualnej implementacji dziedziczonej metody, właściwości, indeksatora lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="78e89-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="78e89-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="78e89-104">Example</span></span>

<span data-ttu-id="78e89-105">W tym przykładzie Klasa `Square` musi udostępniać zastąpioną implementację `GetArea`, ponieważ `GetArea` jest dziedziczona z klasy abstrakcyjnej `Shape`:</span><span class="sxs-lookup"><span data-stu-id="78e89-105">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="78e89-106">Metoda `override` zapewnia nową implementację elementu członkowskiego, który jest Dziedziczony z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="78e89-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="78e89-107">Metoda zastępowana przez deklarację `override` jest znana jako zastąpiona metoda podstawowa.</span><span class="sxs-lookup"><span data-stu-id="78e89-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="78e89-108">Zastąpiona metoda bazowa musi mieć taką samą sygnaturę jak Metoda `override`.</span><span class="sxs-lookup"><span data-stu-id="78e89-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="78e89-109">Aby uzyskać informacje na temat dziedziczenia, zobacz [dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="78e89-109">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="78e89-110">Nie można zastąpić metody niewirtualnej lub statycznej.</span><span class="sxs-lookup"><span data-stu-id="78e89-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="78e89-111">Zastąpiona metoda bazowa musi mieć wartość `virtual`, `abstract`lub `override`.</span><span class="sxs-lookup"><span data-stu-id="78e89-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="78e89-112">Deklaracja `override` nie może zmienić dostępności metody `virtual`.</span><span class="sxs-lookup"><span data-stu-id="78e89-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="78e89-113">Zarówno Metoda `override`, jak i Metoda `virtual` muszą mieć ten sam [modyfikator poziomu dostępu](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="78e89-113">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="78e89-114">Nie można użyć modyfikatora `new`, `static`lub `virtual`, aby zmodyfikować metodę `override`.</span><span class="sxs-lookup"><span data-stu-id="78e89-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="78e89-115">Zastępowanie deklaracji właściwości musi określać dokładnie ten sam modyfikator dostępu, typ i nazwę, co Właściwość dziedziczona, a zastąpiona właściwość musi mieć wartość `virtual`, `abstract`lub `override`.</span><span class="sxs-lookup"><span data-stu-id="78e89-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="78e89-116">Aby uzyskać więcej informacji na temat sposobu używania słowa kluczowego `override`, zobacz [przechowywanie wersji z przesłonięciami i nowymi słowami kluczowymi](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [wiedzą, kiedy używać przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="78e89-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="78e89-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="78e89-117">Example</span></span>

<span data-ttu-id="78e89-118">W tym przykładzie zdefiniowano klasę bazową o nazwie `Employee`i klasę pochodną o nazwie `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="78e89-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="78e89-119">Klasa `SalesEmployee` zawiera dodatkowe pole, `salesbonus`i zastępuje metodę `CalculatePay` w celu uwzględnienia tej metody.</span><span class="sxs-lookup"><span data-stu-id="78e89-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="78e89-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="78e89-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="78e89-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78e89-121">See also</span></span>

- [<span data-ttu-id="78e89-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="78e89-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="78e89-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="78e89-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="78e89-124">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="78e89-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="78e89-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="78e89-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="78e89-126">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="78e89-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="78e89-127">abstract</span><span class="sxs-lookup"><span data-stu-id="78e89-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="78e89-128">virtual</span><span class="sxs-lookup"><span data-stu-id="78e89-128">virtual</span></span>](virtual.md)
- [<span data-ttu-id="78e89-129">New (modyfikator)</span><span class="sxs-lookup"><span data-stu-id="78e89-129">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="78e89-130">Polimorfizm</span><span class="sxs-lookup"><span data-stu-id="78e89-130">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
