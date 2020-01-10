---
title: Public — słowo C# kluczowe — odwołanie
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 19906d7fd0f7d41ef9e4cdaf951c77825e0bbead
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713173"
---
# <a name="public-c-reference"></a><span data-ttu-id="cfed9-102">public (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cfed9-102">public (C# Reference)</span></span>

<span data-ttu-id="cfed9-103">Słowo kluczowe `public` jest modyfikatorem dostępu dla typów i elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="cfed9-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="cfed9-104">Dostęp publiczny to najwyższy poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="cfed9-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="cfed9-105">Nie ma żadnych ograniczeń dotyczących uzyskiwania dostępu do publicznych członków, jak w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cfed9-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="cfed9-106">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md) i [poziomy dostępności](accessibility-levels.md) .</span><span class="sxs-lookup"><span data-stu-id="cfed9-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="cfed9-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfed9-107">Example</span></span>

<span data-ttu-id="cfed9-108">W poniższym przykładzie są zadeklarowane dwie klasy, `PointTest` i `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="cfed9-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="cfed9-109">Publiczne składowe `x` i `y` `PointTest` są dostępne bezpośrednio z `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="cfed9-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="cfed9-110">W przypadku zmiany poziomu dostępu `public` na [prywatny](private.md) lub [chroniony](protected.md)zostanie wyświetlony komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="cfed9-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="cfed9-111">Element "PointTest. y" jest niedostępny z powodu swojego poziomu ochrony.</span><span class="sxs-lookup"><span data-stu-id="cfed9-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cfed9-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cfed9-112">C# language specification</span></span>  

<span data-ttu-id="cfed9-113">Aby uzyskać więcej informacji, zobacz [zadeklarowane ułatwienia dostępu](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="cfed9-113">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="cfed9-114">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="cfed9-114">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfed9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfed9-115">See also</span></span>

- [<span data-ttu-id="cfed9-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cfed9-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cfed9-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cfed9-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cfed9-118">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="cfed9-118">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="cfed9-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="cfed9-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cfed9-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="cfed9-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="cfed9-121">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="cfed9-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="cfed9-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="cfed9-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="cfed9-123">private</span><span class="sxs-lookup"><span data-stu-id="cfed9-123">private</span></span>](private.md)
- [<span data-ttu-id="cfed9-124">protected</span><span class="sxs-lookup"><span data-stu-id="cfed9-124">protected</span></span>](protected.md)
- [<span data-ttu-id="cfed9-125">internal</span><span class="sxs-lookup"><span data-stu-id="cfed9-125">internal</span></span>](internal.md)
