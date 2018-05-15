---
title: void (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: e66efc287fc3ed0fcc15963a827fccb788c38753
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="void-c-reference"></a><span data-ttu-id="ff192-102">void (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ff192-102">void (C# Reference)</span></span>
<span data-ttu-id="ff192-103">Gdy jest używany jako typ zwracany metody, `void` Określa, że metoda nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="ff192-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="ff192-104">`void` nie jest dozwolona na liście parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="ff192-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="ff192-105">Metody, która nie przyjmuje żadnych parametrów i nie zwraca wartości jest zadeklarowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ff192-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="ff192-106">`void` Umożliwia również w niebezpiecznym kontekście zadeklarować wskaźnika do nieznanego typu.</span><span class="sxs-lookup"><span data-stu-id="ff192-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="ff192-107">Aby uzyskać więcej informacji, zobacz [typów wskaźnikowych](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="ff192-107">For more information, see [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="ff192-108">`void` jest to alias dla programu .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="ff192-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ff192-109">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ff192-109">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ff192-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff192-110">See also</span></span>
 [<span data-ttu-id="ff192-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="ff192-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ff192-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ff192-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ff192-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="ff192-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ff192-114">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="ff192-114">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="ff192-115">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="ff192-115">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="ff192-116">Metody</span><span class="sxs-lookup"><span data-stu-id="ff192-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="ff192-117">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="ff192-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
