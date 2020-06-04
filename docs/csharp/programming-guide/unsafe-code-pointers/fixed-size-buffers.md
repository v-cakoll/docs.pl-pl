---
title: Bufory o ustalonym rozmiarze — Przewodnik programowania w języku C#
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 932ff3d57995ce47c4b74e8e888a479f0d09d0ed
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397431"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="c88cf-102">Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c88cf-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="c88cf-103">W języku C# można użyć instrukcji [FIXED](../../language-reference/keywords/fixed-statement.md) do utworzenia buforu z tablicą o stałym rozmiarze w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="c88cf-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="c88cf-104">Bufory o ustalonym rozmiarze są przydatne podczas pisania metod, które współdziałają ze źródłami danych z innych języków lub platform.</span><span class="sxs-lookup"><span data-stu-id="c88cf-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="c88cf-105">Stała tablica może przyjmować wszelkie atrybuty lub modyfikatory, które są dozwolone dla zwykłych elementów członkowskich struktury.</span><span class="sxs-lookup"><span data-stu-id="c88cf-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="c88cf-106">Jedynym ograniczeniem jest to, że typem tablicy musi być,,,,,,,,,, `bool` `byte` `char` `short` `int` `long` `sbyte` `ushort` `uint` `ulong` `float` lub `double` .</span><span class="sxs-lookup"><span data-stu-id="c88cf-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="c88cf-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c88cf-107">Remarks</span></span>

<span data-ttu-id="c88cf-108">W bezpiecznym kodzie struktura języka C#, która zawiera tablicę, nie zawiera elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="c88cf-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="c88cf-109">Zamiast tego, struktura zawiera odwołanie do elementów.</span><span class="sxs-lookup"><span data-stu-id="c88cf-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="c88cf-110">Można osadzić tablicę o stałym rozmiarze w [strukturze](../../language-reference/builtin-types/struct.md) , gdy jest ona używana w [niebezpiecznym](../../language-reference/keywords/unsafe.md) bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="c88cf-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="c88cf-111">Poniższe rozmiary `struct` nie zależą od liczby elementów w tablicy, ponieważ `pathName` jest odwołaniem:</span><span class="sxs-lookup"><span data-stu-id="c88cf-111">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](snippets/FixedKeywordExamples.cs#6)]

<span data-ttu-id="c88cf-112">`struct`Może zawierać osadzoną tablicę w niebezpiecznym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c88cf-112">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="c88cf-113">W poniższym przykładzie `fixedBuffer` Tablica ma stały rozmiar.</span><span class="sxs-lookup"><span data-stu-id="c88cf-113">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="c88cf-114">Używasz instrukcji, `fixed` Aby nawiązać wskaźnik do pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="c88cf-114">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="c88cf-115">Dostęp do elementów tablicy można uzyskać za pomocą tego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="c88cf-115">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="c88cf-116">`fixed`Instrukcja przypina `fixedBuffer` pole wystąpienia do określonej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c88cf-116">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#7)]

<span data-ttu-id="c88cf-117">Rozmiar tablicy elementów 128 `char` wynosi 256 bajtów.</span><span class="sxs-lookup"><span data-stu-id="c88cf-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="c88cf-118">Bufory [znaków](../../language-reference/builtin-types/char.md) o stałym rozmiarze zawsze pobierają dwa bajty na znak, niezależnie od kodowania.</span><span class="sxs-lookup"><span data-stu-id="c88cf-118">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="c88cf-119">Jest to prawdziwe nawet wtedy, gdy bufory char są organizowane do metod interfejsu API lub struktur z `CharSet = CharSet.Auto` lub `CharSet = CharSet.Ansi` .</span><span class="sxs-lookup"><span data-stu-id="c88cf-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="c88cf-120">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="c88cf-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="c88cf-121">W poprzednim przykładzie pokazano dostęp do `fixed` pól bez przypinania, które są dostępne od języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="c88cf-121">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="c88cf-122">Inna wspólna tablica o stałym rozmiarze jest tablicą [logiczną](../../language-reference/builtin-types/bool.md) .</span><span class="sxs-lookup"><span data-stu-id="c88cf-122">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="c88cf-123">Elementy w `bool` tablicy mają zawsze jeden bajt w rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="c88cf-123">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="c88cf-124">`bool`Tablice nie są odpowiednie do tworzenia tablic bitowych lub buforów.</span><span class="sxs-lookup"><span data-stu-id="c88cf-124">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="c88cf-125">Bufory o ustalonym rozmiarze są kompilowane przy użyciu <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType> , który instruuje środowisko uruchomieniowe języka wspólnego (CLR), że typ zawiera niezarządzaną tablicę, która może być przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="c88cf-125">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="c88cf-126">Jest to podobne do pamięci utworzonej za pomocą [stackalloc](../../language-reference/operators/stackalloc.md), co powoduje automatyczne włączenie funkcji wykrywania przepełnienia buforu w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="c88cf-126">This is similar to memory created using [stackalloc](../../language-reference/operators/stackalloc.md), which automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="c88cf-127">W poprzednim przykładzie pokazano, jak bufor o ustalonym rozmiarze może istnieć w `unsafe struct` .</span><span class="sxs-lookup"><span data-stu-id="c88cf-127">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="c88cf-128">Kompilator wygenerował C# dla `Buffer` , ma następujący atrybut:</span><span class="sxs-lookup"><span data-stu-id="c88cf-128">The compiler generated C# for `Buffer`, is attributed as follows:</span></span>

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

<span data-ttu-id="c88cf-129">Bufory o ustalonym rozmiarze różnią się od zwykłych tablic w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c88cf-129">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="c88cf-130">Może być używany tylko w [niebezpiecznym](../../language-reference/keywords/unsafe.md) kontekście.</span><span class="sxs-lookup"><span data-stu-id="c88cf-130">May only be used in an [unsafe](../../language-reference/keywords/unsafe.md) context.</span></span>
- <span data-ttu-id="c88cf-131">Mogą to być tylko pola struktur.</span><span class="sxs-lookup"><span data-stu-id="c88cf-131">May only be instance fields of structs.</span></span>
- <span data-ttu-id="c88cf-132">Są one zawsze wektorami lub tablic jednowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="c88cf-132">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="c88cf-133">Deklaracja powinna zawierać długość, taką jak `fixed char id[8]` .</span><span class="sxs-lookup"><span data-stu-id="c88cf-133">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="c88cf-134">Nie można użyć `fixed char id[]` .</span><span class="sxs-lookup"><span data-stu-id="c88cf-134">You cannot use `fixed char id[]`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c88cf-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c88cf-135">See also</span></span>

- [<span data-ttu-id="c88cf-136">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c88cf-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c88cf-137">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="c88cf-137">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="c88cf-138">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c88cf-138">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="c88cf-139">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="c88cf-139">Interoperability</span></span>](../interop/index.md)
