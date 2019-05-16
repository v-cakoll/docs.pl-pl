---
title: void — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: af79d39282ea38811777ea1f23054120afc39d2c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632957"
---
# <a name="void-c-reference"></a><span data-ttu-id="dadbd-102">void (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="dadbd-102">void (C# Reference)</span></span>

<span data-ttu-id="dadbd-103">Gdy jest używana jako zwracany typ metody `void` Określa, że metoda nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="dadbd-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="dadbd-104">`void` nie jest dozwolona na liście parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="dadbd-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="dadbd-105">Metody, która nie przyjmuje żadnych parametrów i zwraca wartość nie jest zadeklarowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="dadbd-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="dadbd-106">`void` Umożliwia również w niebezpiecznym kontekście deklarowany jest wskaźnik do nieznanego typu.</span><span class="sxs-lookup"><span data-stu-id="dadbd-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="dadbd-107">Aby uzyskać więcej informacji, zobacz [typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="dadbd-107">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="dadbd-108">`void` jest aliasem dla programu .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="dadbd-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dadbd-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dadbd-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="dadbd-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dadbd-110">See also</span></span>

- [<span data-ttu-id="dadbd-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dadbd-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dadbd-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="dadbd-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dadbd-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="dadbd-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dadbd-114">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="dadbd-114">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="dadbd-115">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="dadbd-115">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="dadbd-116">Metody</span><span class="sxs-lookup"><span data-stu-id="dadbd-116">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="dadbd-117">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="dadbd-117">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
