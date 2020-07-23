---
title: Jak utworzyć Unię C/C++ za pomocą atrybutów (C#)
description: Dowiedz się, jak używać atrybutów, aby dostosować sposób, w jaki struktury są ułożone w pamięci w języku C#. Ten przykład implementuje odpowiednik Unii z C/C++.
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 766a070105441630dfd8fecf7b9f68fa6818fe50
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925075"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="3fcd0-104">Jak utworzyć Unię C/C++ za pomocą atrybutów (C#)</span><span class="sxs-lookup"><span data-stu-id="3fcd0-104">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="3fcd0-105">Przy użyciu atrybutów można dostosować sposób, w jaki struktury są ułożone w pamięci.</span><span class="sxs-lookup"><span data-stu-id="3fcd0-105">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="3fcd0-106">Na przykład, można utworzyć elementy znane jako Unia w C/C++ za pomocą `StructLayout(LayoutKind.Explicit)` `FieldOffset` atrybutów i.</span><span class="sxs-lookup"><span data-stu-id="3fcd0-106">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="3fcd0-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fcd0-107">Example</span></span>

<span data-ttu-id="3fcd0-108">W tym segmencie kodu wszystkie pola, które są `TestUnion` uruchamiane w tej samej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="3fcd0-108">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestUnion
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public byte b;
}
```

## <a name="example"></a><span data-ttu-id="3fcd0-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fcd0-109">Example</span></span>

<span data-ttu-id="3fcd0-110">Poniżej znajduje się kolejny przykład, w którym pola zaczynają się od różnych jawnie ustawionych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3fcd0-110">The following is another example where fields start at different explicitly set locations.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestExplicit
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public long lg;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i1;

    [System.Runtime.InteropServices.FieldOffset(4)]
    public int i2;

    [System.Runtime.InteropServices.FieldOffset(8)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(12)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(14)]
    public byte b;
}
```

<span data-ttu-id="3fcd0-111">Dwa pola liczb całkowitych `i1` i `i2` , współużytkują te same lokalizacje pamięci co `lg` .</span><span class="sxs-lookup"><span data-stu-id="3fcd0-111">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="3fcd0-112">Ten rodzaj kontroli nad układem struktury jest przydatny podczas korzystania z wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="3fcd0-112">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fcd0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fcd0-113">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="3fcd0-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3fcd0-114">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="3fcd0-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3fcd0-115">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="3fcd0-116">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="3fcd0-116">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="3fcd0-117">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="3fcd0-117">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="3fcd0-118">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="3fcd0-118">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="3fcd0-119">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="3fcd0-119">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
