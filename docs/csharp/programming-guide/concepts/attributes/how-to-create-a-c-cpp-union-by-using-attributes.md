---
title: Jak utworzyć związek C/C++ przy użyciu atrybutów (C#)
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: ff8ce560444581a28b257820573224f89a274cd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141576"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="f7050-102">Jak utworzyć związek C/C++ przy użyciu atrybutów (C#)</span><span class="sxs-lookup"><span data-stu-id="f7050-102">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="f7050-103">Za pomocą atrybutów, można dostosować sposób struktur są rozmieszczone w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f7050-103">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="f7050-104">Na przykład można utworzyć, co jest znane jako unii w `StructLayout(LayoutKind.Explicit)` Języku C++ przy użyciu i `FieldOffset` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f7050-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="f7050-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7050-105">Example</span></span>

<span data-ttu-id="f7050-106">W tym segmencie kodu wszystkie `TestUnion` pola start w tej samej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f7050-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

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

## <a name="example"></a><span data-ttu-id="f7050-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7050-107">Example</span></span>

<span data-ttu-id="f7050-108">Poniżej przedstawiono inny przykład, w którym pola zaczynają się od różnych jawnie ustawionych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="f7050-108">The following is another example where fields start at different explicitly set locations.</span></span>

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

<span data-ttu-id="f7050-109">Dwa pola całkowite `i1` i `i2`, współużytkują te `lg`same lokalizacje pamięci co .</span><span class="sxs-lookup"><span data-stu-id="f7050-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="f7050-110">Ten rodzaj kontroli nad układem struktury jest przydatne podczas korzystania z wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="f7050-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7050-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7050-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="f7050-112">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="f7050-112">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="f7050-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f7050-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="f7050-114">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="f7050-114">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="f7050-115">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="f7050-115">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="f7050-116">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="f7050-116">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="f7050-117">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="f7050-117">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
