---
title: chronione słowo kluczowe C# — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: a0420dd10d81c4ae893ab0447244a611091ed7b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601975"
---
# <a name="protected-c-reference"></a><span data-ttu-id="bb7f6-102">protected (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="bb7f6-102">protected (C# Reference)</span></span>

<span data-ttu-id="bb7f6-103">`protected` Słowo kluczowe jest modyfikatorem dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="bb7f6-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="bb7f6-104">Ta strona dotyczy `protected` dostępu.</span><span class="sxs-lookup"><span data-stu-id="bb7f6-104">This page covers `protected` access.</span></span> <span data-ttu-id="bb7f6-105">Słowo kluczowe jest również częścią [`protected internal`](protected-internal.md) modyfikatorów [`private protected`](private-protected.md) i dostępu. `protected`</span><span class="sxs-lookup"><span data-stu-id="bb7f6-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="bb7f6-106">Chroniony element członkowski jest dostępny w jego klasie i wystąpieniach klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="bb7f6-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="bb7f6-107">Aby uzyskać porównanie `protected` z innymi modyfikatorami dostępu, zobacz [poziomy dostępności](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="bb7f6-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="bb7f6-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb7f6-108">Example</span></span>

<span data-ttu-id="bb7f6-109">Chroniony element członkowski klasy bazowej jest dostępny w klasie pochodnej tylko wtedy, gdy dostęp odbywa się za pomocą typu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="bb7f6-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="bb7f6-110">Rozważmy na przykład następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="bb7f6-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="bb7f6-111">Instrukcja `a.x = 10` generuje błąd, ponieważ znajduje się w metodzie statycznej Main i nie jest wystąpieniem klasy B.</span><span class="sxs-lookup"><span data-stu-id="bb7f6-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="bb7f6-112">Elementy członkowskie struktury nie mogą być chronione, ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="bb7f6-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="bb7f6-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb7f6-113">Example</span></span>

<span data-ttu-id="bb7f6-114">W tym przykładzie Klasa `DerivedPoint` pochodzi od. `Point`</span><span class="sxs-lookup"><span data-stu-id="bb7f6-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="bb7f6-115">W związku z tym można uzyskać dostęp do chronionych elementów członkowskich klasy bazowej bezpośrednio z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="bb7f6-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="bb7f6-116">Jeśli zmienisz poziomy `x` dostępu dla i `y` na [prywatne](private.md), kompilator będzie wystawiał komunikaty o błędach:</span><span class="sxs-lookup"><span data-stu-id="bb7f6-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="bb7f6-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bb7f6-117">C# language specification</span></span>  

<span data-ttu-id="bb7f6-118">Aby uzyskać więcej informacji, zobacz [zadeklarowane ułatwienia dostępu](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bb7f6-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="bb7f6-119">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="bb7f6-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb7f6-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb7f6-120">See also</span></span>

- [<span data-ttu-id="bb7f6-121">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bb7f6-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bb7f6-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bb7f6-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bb7f6-123">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="bb7f6-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bb7f6-124">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="bb7f6-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="bb7f6-125">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="bb7f6-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="bb7f6-126">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="bb7f6-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="bb7f6-127">public</span><span class="sxs-lookup"><span data-stu-id="bb7f6-127">public</span></span>](public.md)
- [<span data-ttu-id="bb7f6-128">private</span><span class="sxs-lookup"><span data-stu-id="bb7f6-128">private</span></span>](private.md)
- [<span data-ttu-id="bb7f6-129">internal</span><span class="sxs-lookup"><span data-stu-id="bb7f6-129">internal</span></span>](internal.md)
- <span data-ttu-id="bb7f6-130">[Zagadnienia dotyczące zabezpieczeń wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bb7f6-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
