---
title: odwołanie typu C# void
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 465aaeadca603f14432478a7e5496a9ef4589ebe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712861"
---
# <a name="void-c-reference"></a><span data-ttu-id="44f3c-102">void (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="44f3c-102">void (C# Reference)</span></span>

<span data-ttu-id="44f3c-103">Gdy jest używany jako zwracany typ dla metody, `void` określa, że metoda nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="44f3c-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="44f3c-104">`void` nie jest dozwolone na liście parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="44f3c-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="44f3c-105">Metoda, która nie przyjmuje parametrów i nie zwraca żadnej wartości jest zadeklarowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="44f3c-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="44f3c-106">`void` jest również używany w niebezpiecznym kontekście, aby zadeklarować wskaźnik do nieznanego typu.</span><span class="sxs-lookup"><span data-stu-id="44f3c-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="44f3c-107">Aby uzyskać więcej informacji, zobacz [typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="44f3c-107">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="44f3c-108">`void` jest aliasem dla typu <xref:System.Void?displayProperty=nameWithType> .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44f3c-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="44f3c-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="44f3c-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="44f3c-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44f3c-110">See also</span></span>

- [<span data-ttu-id="44f3c-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="44f3c-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="44f3c-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="44f3c-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="44f3c-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="44f3c-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="44f3c-114">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="44f3c-114">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="44f3c-115">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="44f3c-115">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="44f3c-116">Metody</span><span class="sxs-lookup"><span data-stu-id="44f3c-116">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="44f3c-117">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="44f3c-117">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
