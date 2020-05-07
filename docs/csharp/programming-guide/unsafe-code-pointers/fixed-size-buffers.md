---
title: Bufory o ustalonym rozmiarze — Przewodnik programowania w języku C#
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5920dd125ded34969d60feb299568b56402056ab
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140546"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="26b88-102">Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="26b88-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="26b88-103">W języku C# można użyć instrukcji [FIXED](../../language-reference/keywords/fixed-statement.md) do utworzenia buforu z tablicą o stałym rozmiarze w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="26b88-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="26b88-104">Bufory o ustalonym rozmiarze są przydatne podczas pisania metod, które współdziałają ze źródłami danych z innych języków lub platform.</span><span class="sxs-lookup"><span data-stu-id="26b88-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="26b88-105">Stała tablica może przyjmować wszelkie atrybuty lub modyfikatory, które są dozwolone dla zwykłych elementów członkowskich struktury.</span><span class="sxs-lookup"><span data-stu-id="26b88-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="26b88-106">Jedynym ograniczeniem jest to, że typem tablicy musi `bool`być `byte`, `char`, `short` `int` `long`,,, `sbyte`, `ushort`, `uint` `ulong` `float`,,, lub `double`.</span><span class="sxs-lookup"><span data-stu-id="26b88-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="26b88-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26b88-107">Remarks</span></span>

<span data-ttu-id="26b88-108">W bezpiecznym kodzie struktura języka C#, która zawiera tablicę, nie zawiera elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="26b88-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="26b88-109">Zamiast tego, struktura zawiera odwołanie do elementów.</span><span class="sxs-lookup"><span data-stu-id="26b88-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="26b88-110">Można osadzić tablicę o stałym rozmiarze w [strukturze](../../language-reference/builtin-types/struct.md) , gdy jest ona używana w [niebezpiecznym](../../language-reference/keywords/unsafe.md) bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="26b88-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="26b88-111">Poniższe `struct` rozmiary nie zależą od liczby elementów w tablicy, ponieważ `pathName` jest odwołaniem:</span><span class="sxs-lookup"><span data-stu-id="26b88-111">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="26b88-112">`struct` Może zawierać osadzoną tablicę w niebezpiecznym kodzie.</span><span class="sxs-lookup"><span data-stu-id="26b88-112">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="26b88-113">W poniższym przykładzie `fixedBuffer` tablica ma stały rozmiar.</span><span class="sxs-lookup"><span data-stu-id="26b88-113">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="26b88-114">Używasz `fixed` instrukcji, aby nawiązać wskaźnik do pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="26b88-114">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="26b88-115">Dostęp do elementów tablicy można uzyskać za pomocą tego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="26b88-115">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="26b88-116">`fixed` Instrukcja przypina pole `fixedBuffer` wystąpienia do określonej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="26b88-116">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="26b88-117">Rozmiar tablicy elementów `char` 128 wynosi 256 bajtów.</span><span class="sxs-lookup"><span data-stu-id="26b88-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="26b88-118">Bufory [znaków](../../language-reference/builtin-types/char.md) o stałym rozmiarze zawsze pobierają dwa bajty na znak, niezależnie od kodowania.</span><span class="sxs-lookup"><span data-stu-id="26b88-118">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="26b88-119">Jest to prawdziwe nawet wtedy, gdy bufory char są organizowane do metod interfejsu API lub `CharSet = CharSet.Auto` struktur `CharSet = CharSet.Ansi`z lub.</span><span class="sxs-lookup"><span data-stu-id="26b88-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="26b88-120">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="26b88-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="26b88-121">W poprzednim przykładzie pokazano dostęp `fixed` do pól bez przypinania, które są dostępne od języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="26b88-121">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="26b88-122">Inna wspólna tablica o stałym rozmiarze jest tablicą [logiczną](../../language-reference/builtin-types/bool.md) .</span><span class="sxs-lookup"><span data-stu-id="26b88-122">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="26b88-123">Elementy w `bool` tablicy mają zawsze jeden bajt w rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="26b88-123">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="26b88-124">`bool`Tablice nie są odpowiednie do tworzenia tablic bitowych lub buforów.</span><span class="sxs-lookup"><span data-stu-id="26b88-124">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="26b88-125">Bufory o ustalonym rozmiarze są <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>kompilowane przy użyciu, który instruuje środowisko uruchomieniowe języka wspólnego (CLR), że typ zawiera niezarządzaną tablicę, która może być przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="26b88-125">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="26b88-126">Jest to podobne do pamięci utworzonej za pomocą [stackalloc](../../language-reference/operators/stackalloc.md), co powoduje automatyczne włączenie funkcji wykrywania przepełnienia buforu w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="26b88-126">This is similar to memory created using [stackalloc](../../language-reference/operators/stackalloc.md), which automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="26b88-127">W poprzednim przykładzie pokazano, jak bufor o `unsafe struct`ustalonym rozmiarze może istnieć w.</span><span class="sxs-lookup"><span data-stu-id="26b88-127">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="26b88-128">Kompilator wygenerował C# dla `Buffer`, ma następujący atrybut:</span><span class="sxs-lookup"><span data-stu-id="26b88-128">The compiler generated C# for `Buffer`, is attributed as follows:</span></span>

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

<span data-ttu-id="26b88-129">Bufory o ustalonym rozmiarze różnią się od zwykłych tablic w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="26b88-129">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="26b88-130">Może być używany tylko w [niebezpiecznym](../../language-reference/keywords/unsafe.md) kontekście.</span><span class="sxs-lookup"><span data-stu-id="26b88-130">May only be used in an [unsafe](../../language-reference/keywords/unsafe.md) context.</span></span>
- <span data-ttu-id="26b88-131">Mogą to być tylko pola struktur.</span><span class="sxs-lookup"><span data-stu-id="26b88-131">May only be instance fields of structs.</span></span>
- <span data-ttu-id="26b88-132">Są one zawsze wektorami lub tablic jednowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="26b88-132">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="26b88-133">Deklaracja powinna zawierać długość, taką jak `fixed char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="26b88-133">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="26b88-134">Nie można użyć `fixed char id[]`.</span><span class="sxs-lookup"><span data-stu-id="26b88-134">You cannot use `fixed char id[]`.</span></span>

## <a name="see-also"></a><span data-ttu-id="26b88-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26b88-135">See also</span></span>

- [<span data-ttu-id="26b88-136">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="26b88-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="26b88-137">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="26b88-137">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="26b88-138">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="26b88-138">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="26b88-139">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="26b88-139">Interoperability</span></span>](../interop/index.md)
