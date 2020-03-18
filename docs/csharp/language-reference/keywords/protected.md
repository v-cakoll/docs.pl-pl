---
title: chronione słowo kluczowe - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: bec619d4f49bd26daa742c18c830909c14948adf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713186"
---
# <a name="protected-c-reference"></a><span data-ttu-id="2a67f-102">protected (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2a67f-102">protected (C# Reference)</span></span>

<span data-ttu-id="2a67f-103">Słowo `protected` kluczowe jest modyfikatorem dostępu do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="2a67f-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="2a67f-104">Ta strona `protected` obejmuje dostęp.</span><span class="sxs-lookup"><span data-stu-id="2a67f-104">This page covers `protected` access.</span></span> <span data-ttu-id="2a67f-105">Słowo `protected` kluczowe jest również [`protected internal`](protected-internal.md) [`private protected`](private-protected.md) częścią modyfikatorów i dostępu.</span><span class="sxs-lookup"><span data-stu-id="2a67f-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="2a67f-106">Chroniony element członkowski jest dostępny w jego klasie i przez wystąpienia klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="2a67f-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="2a67f-107">Aby porównać `protected` inne modyfikatory dostępu, zobacz [Poziomy ułatwień dostępu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2a67f-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="2a67f-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a67f-108">Example</span></span>

<span data-ttu-id="2a67f-109">Chroniony element członkowski klasy podstawowej jest dostępny w klasie pochodnej tylko wtedy, gdy dostęp występuje za pośrednictwem typu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="2a67f-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="2a67f-110">Rozważmy na przykład następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="2a67f-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="2a67f-111">Instrukcja `a.x = 10` generuje błąd, ponieważ jest wykonany w ramach metody statycznej Main, a nie wystąpienie klasy B.</span><span class="sxs-lookup"><span data-stu-id="2a67f-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="2a67f-112">Elementy członkowskie struktury nie mogą być chronione, ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="2a67f-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="2a67f-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a67f-113">Example</span></span>

<span data-ttu-id="2a67f-114">W tym przykładzie `DerivedPoint` klasa pochodzi `Point`od .</span><span class="sxs-lookup"><span data-stu-id="2a67f-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="2a67f-115">W związku z tym można uzyskać dostęp do chronionych elementów członkowskich klasy podstawowej bezpośrednio z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="2a67f-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="2a67f-116">Jeśli zmienisz poziomy `x` dostępu `y` i [prywatne,](private.md)kompilator wyda komunikaty o błędach:</span><span class="sxs-lookup"><span data-stu-id="2a67f-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="2a67f-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2a67f-117">C# language specification</span></span>  

<span data-ttu-id="2a67f-118">Aby uzyskać więcej informacji, zobacz [Zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="2a67f-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="2a67f-119">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="2a67f-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a67f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a67f-120">See also</span></span>

- [<span data-ttu-id="2a67f-121">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="2a67f-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2a67f-122">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="2a67f-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2a67f-123">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2a67f-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2a67f-124">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="2a67f-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="2a67f-125">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="2a67f-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="2a67f-126">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="2a67f-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="2a67f-127">Publicznego</span><span class="sxs-lookup"><span data-stu-id="2a67f-127">public</span></span>](public.md)
- [<span data-ttu-id="2a67f-128">Prywatny</span><span class="sxs-lookup"><span data-stu-id="2a67f-128">private</span></span>](private.md)
- [<span data-ttu-id="2a67f-129">Wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="2a67f-129">internal</span></span>](internal.md)
- <span data-ttu-id="2a67f-130">[Obawy dotyczące zabezpieczeń wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2a67f-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
