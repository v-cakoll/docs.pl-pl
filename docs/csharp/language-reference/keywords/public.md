---
title: Public — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 84a3bc49b6eea047d518edc01dab7f2301854b6a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484160"
---
# <a name="public-c-reference"></a><span data-ttu-id="1cb22-102">public (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1cb22-102">public (C# Reference)</span></span>

<span data-ttu-id="1cb22-103">`public` — Słowo kluczowe jest modyfikatorem dostępu dla typów i elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="1cb22-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="1cb22-104">Dostęp publiczny jest restrykcyjny poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="1cb22-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="1cb22-105">Istnieją ograniczenia związane z dostępem do publicznych składowych, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1cb22-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="1cb22-106">Zobacz [modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md) i [poziomów ułatwień dostępu](accessibility-levels.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="1cb22-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="1cb22-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1cb22-107">Example</span></span>

<span data-ttu-id="1cb22-108">W poniższym przykładzie zadeklarowano dwóch klas, `PointTest` i `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="1cb22-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="1cb22-109">Publiczne elementy członkowskie `x` i `y` z `PointTest` są dostępne bezpośrednio z `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="1cb22-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="1cb22-110">Jeśli zmienisz `public` poziom dostępu do [prywatnej](private.md) lub [chronione](protected.md), otrzymasz komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="1cb22-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="1cb22-111">"PointTest.y" jest niedostępny z powodu swojego poziomu ochrony.</span><span class="sxs-lookup"><span data-stu-id="1cb22-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1cb22-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1cb22-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1cb22-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cb22-113">See also</span></span>

- [<span data-ttu-id="1cb22-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1cb22-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1cb22-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1cb22-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1cb22-116">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="1cb22-116">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="1cb22-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1cb22-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1cb22-118">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="1cb22-118">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="1cb22-119">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="1cb22-119">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="1cb22-120">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="1cb22-120">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="1cb22-121">private</span><span class="sxs-lookup"><span data-stu-id="1cb22-121">private</span></span>](private.md)
- [<span data-ttu-id="1cb22-122">protected</span><span class="sxs-lookup"><span data-stu-id="1cb22-122">protected</span></span>](protected.md)
- [<span data-ttu-id="1cb22-123">internal</span><span class="sxs-lookup"><span data-stu-id="1cb22-123">internal</span></span>](internal.md)