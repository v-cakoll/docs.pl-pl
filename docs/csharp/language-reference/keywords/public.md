---
title: Public — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: a68cbf3af2568cd3c197eaece9e2d5a25cdb4a6a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633712"
---
# <a name="public-c-reference"></a><span data-ttu-id="64163-102">public (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="64163-102">public (C# Reference)</span></span>

<span data-ttu-id="64163-103">`public` — Słowo kluczowe jest modyfikatorem dostępu dla typów i elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="64163-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="64163-104">Dostęp publiczny jest restrykcyjny poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="64163-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="64163-105">Istnieją ograniczenia związane z dostępem do publicznych składowych, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="64163-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="64163-106">Zobacz [modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md) i [poziomów ułatwień dostępu](accessibility-levels.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="64163-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="64163-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="64163-107">Example</span></span>

<span data-ttu-id="64163-108">W poniższym przykładzie zadeklarowano dwóch klas, `PointTest` i `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="64163-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="64163-109">Publiczne elementy członkowskie `x` i `y` z `PointTest` są dostępne bezpośrednio z `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="64163-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="64163-110">Jeśli zmienisz `public` poziom dostępu do [prywatnej](private.md) lub [chronione](protected.md), otrzymasz komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="64163-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="64163-111">"PointTest.y" jest niedostępny z powodu swojego poziomu ochrony.</span><span class="sxs-lookup"><span data-stu-id="64163-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="64163-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="64163-112">C# language specification</span></span>  

<span data-ttu-id="64163-113">Aby uzyskać więcej informacji, zobacz [zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="64163-113">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="64163-114">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="64163-114">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="64163-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64163-115">See also</span></span>

- [<span data-ttu-id="64163-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="64163-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="64163-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="64163-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="64163-118">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="64163-118">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="64163-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="64163-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="64163-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="64163-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="64163-121">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="64163-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="64163-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="64163-122">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="64163-123">private</span><span class="sxs-lookup"><span data-stu-id="64163-123">private</span></span>](private.md)
- [<span data-ttu-id="64163-124">protected</span><span class="sxs-lookup"><span data-stu-id="64163-124">protected</span></span>](protected.md)
- [<span data-ttu-id="64163-125">internal</span><span class="sxs-lookup"><span data-stu-id="64163-125">internal</span></span>](internal.md)
