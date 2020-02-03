---
title: odwołanie typu C# void
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 0624b547ee2586334ac35d366ae3c8dfd14963ee
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742761"
---
# <a name="void-c-reference"></a><span data-ttu-id="10946-102">void (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="10946-102">void (C# Reference)</span></span>

<span data-ttu-id="10946-103">Gdy jest używany jako zwracany typ dla metody, `void` określa, że metoda nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="10946-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="10946-104">`void` nie jest dozwolone na liście parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="10946-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="10946-105">Metoda, która nie przyjmuje parametrów i nie zwraca żadnej wartości jest zadeklarowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="10946-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="10946-106">`void` jest również używany w niebezpiecznym kontekście, aby zadeklarować wskaźnik do nieznanego typu.</span><span class="sxs-lookup"><span data-stu-id="10946-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="10946-107">Aby uzyskać więcej informacji, zobacz [typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="10946-107">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="10946-108">`void` jest aliasem dla typu <xref:System.Void?displayProperty=nameWithType> .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="10946-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="10946-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="10946-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="10946-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10946-110">See also</span></span>

- [<span data-ttu-id="10946-111">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="10946-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="10946-112">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="10946-112">C# keywords</span></span>](index.md)
- [<span data-ttu-id="10946-113">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="10946-113">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="10946-114">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="10946-114">Value types</span></span>](../builtin-types/value-types.md)
- [<span data-ttu-id="10946-115">Metody</span><span class="sxs-lookup"><span data-stu-id="10946-115">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="10946-116">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="10946-116">Unsafe code and pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
