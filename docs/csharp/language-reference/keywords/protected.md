---
title: Protected — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: f25e692430f876ec384971079d6d0aa2c97e967b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577441"
---
# <a name="protected-c-reference"></a><span data-ttu-id="6814d-102">protected (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6814d-102">protected (C# Reference)</span></span>

<span data-ttu-id="6814d-103">`protected` — Słowo kluczowe jest modyfikator dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="6814d-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="6814d-104">Ta strona obejmuje `protected` dostępu.</span><span class="sxs-lookup"><span data-stu-id="6814d-104">This page covers `protected` access.</span></span> <span data-ttu-id="6814d-105">`protected` — Słowo kluczowe jest również częścią [ `protected internal` ](protected-internal.md) i [ `private protected` ](private-protected.md) modyfikatorach dostępu.</span><span class="sxs-lookup"><span data-stu-id="6814d-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="6814d-106">Chroniony element członkowski jest dostępny w ramach swojej klasy i wystąpienia klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6814d-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="6814d-107">Porównanie `protected` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6814d-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="6814d-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6814d-108">Example</span></span>

<span data-ttu-id="6814d-109">Chronione elementy członkowskie klasy bazowej jest dostępna w klasie pochodnej, tylko wtedy, gdy dostęp odbywa się przez typ klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6814d-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="6814d-110">Na przykład rozważmy następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="6814d-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="6814d-111">Wykonywanie instrukcji `a.x = 10` generuje błąd, ponieważ staje się wewnątrz metody statycznej Main, a nie jest wystąpieniem klasy B.</span><span class="sxs-lookup"><span data-stu-id="6814d-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="6814d-112">Składowe struktury nie mogą być chronione, ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="6814d-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="6814d-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="6814d-113">Example</span></span>

<span data-ttu-id="6814d-114">W tym przykładzie klasa `DerivedPoint` jest tworzony na podstawie `Point`.</span><span class="sxs-lookup"><span data-stu-id="6814d-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="6814d-115">W związku z tym dostęp chronionych elementów członkowskich klasy podstawowej, bezpośrednio z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6814d-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="6814d-116">Jeśli zmienisz poziomy dostępu `x` i `y` do [prywatnej](private.md), kompilator zgłosi komunikaty o błędach:</span><span class="sxs-lookup"><span data-stu-id="6814d-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="6814d-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6814d-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6814d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6814d-118">See also</span></span>

- [<span data-ttu-id="6814d-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6814d-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="6814d-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6814d-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6814d-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6814d-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6814d-122">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="6814d-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="6814d-123">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="6814d-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="6814d-124">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="6814d-124">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="6814d-125">public</span><span class="sxs-lookup"><span data-stu-id="6814d-125">public</span></span>](public.md)
- [<span data-ttu-id="6814d-126">private</span><span class="sxs-lookup"><span data-stu-id="6814d-126">private</span></span>](private.md)
- [<span data-ttu-id="6814d-127">internal</span><span class="sxs-lookup"><span data-stu-id="6814d-127">internal</span></span>](internal.md)
- <span data-ttu-id="6814d-128">[Kwestie bezpieczeństwa wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6814d-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>