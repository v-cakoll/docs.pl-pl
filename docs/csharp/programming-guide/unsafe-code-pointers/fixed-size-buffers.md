---
title: Bufory o stałym rozmiarze — przewodnik programowania C#
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 6770497b23212f1786b4f4a620ed2b650079c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157029"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="da4df-102">Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="da4df-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="da4df-103">W języku C#, można użyć [stałej](../../language-reference/keywords/fixed-statement.md) instrukcji, aby utworzyć bufor z tablicą o stałym rozmiarze w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="da4df-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="da4df-104">Bufory o stałym rozmiarze są przydatne podczas pisania metod, które współgrają ze źródłami danych z innych języków lub platform.</span><span class="sxs-lookup"><span data-stu-id="da4df-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="da4df-105">Tablica stała może przyjmować dowolne atrybuty lub modyfikatory, które są dozwolone dla zwykłych elementów członkowskich struktury.</span><span class="sxs-lookup"><span data-stu-id="da4df-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="da4df-106">Jedynym ograniczeniem jest to, `bool`że `byte` `char`typ `short` `int`tablicy `sbyte` `ushort`musi `uint` `ulong`być `float`, `double`, , `long`, , , , , lub .</span><span class="sxs-lookup"><span data-stu-id="da4df-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="da4df-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da4df-107">Remarks</span></span>

<span data-ttu-id="da4df-108">W bezpiecznym kodzie struktury C#, który zawiera tablicę nie zawiera elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="da4df-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="da4df-109">Zamiast tego struktury zawiera odwołanie do elementów.</span><span class="sxs-lookup"><span data-stu-id="da4df-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="da4df-110">Tablicę o stałym rozmiarze można osadzić w [strukturze,](../../language-reference/builtin-types/struct.md) gdy jest używana w [bloku kodu niebezpiecznego.](../../language-reference/keywords/unsafe.md)</span><span class="sxs-lookup"><span data-stu-id="da4df-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="da4df-111">Rozmiar następujących `struct` nie zależy od liczby elementów w tablicy, ponieważ `pathName` jest odwołanie:</span><span class="sxs-lookup"><span data-stu-id="da4df-111">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="da4df-112">A `struct` może zawierać osadzoną tablicę w niebezpiecznym kodzie.</span><span class="sxs-lookup"><span data-stu-id="da4df-112">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="da4df-113">W poniższym przykładzie `fixedBuffer` tablica ma stały rozmiar.</span><span class="sxs-lookup"><span data-stu-id="da4df-113">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="da4df-114">Instrukcja `fixed` służy do ustanawiania wskaźnika do pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="da4df-114">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="da4df-115">Dostęp do elementów tablicy za pośrednictwem tego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="da4df-115">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="da4df-116">Instrukcja `fixed` przypina `fixedBuffer` pole wystąpienia do określonej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="da4df-116">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="da4df-117">Rozmiar tablicy 128 `char` elementów wynosi 256 bajtów.</span><span class="sxs-lookup"><span data-stu-id="da4df-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="da4df-118">Bufory [znaków](../../language-reference/builtin-types/char.md) o stałym rozmiarze zawsze przyjmują dwa bajty na znak, niezależnie od kodowania.</span><span class="sxs-lookup"><span data-stu-id="da4df-118">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="da4df-119">Jest to prawdą nawet wtedy, gdy bufory char są organizowane `CharSet = CharSet.Auto` `CharSet = CharSet.Ansi`do metod interfejsu API lub struktur z lub .</span><span class="sxs-lookup"><span data-stu-id="da4df-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="da4df-120">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="da4df-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="da4df-121">W poprzednim przykładzie przedstawiono `fixed` dostęp do pól bez przypinania, który jest dostępny począwszy od Języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="da4df-121">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="da4df-122">Inną wspólną tablicą o stałym rozmiarze jest tablica [bool.](../../language-reference/builtin-types/bool.md)</span><span class="sxs-lookup"><span data-stu-id="da4df-122">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="da4df-123">Elementy w `bool` tablicy są zawsze jeden bajt w rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="da4df-123">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="da4df-124">`bool`tablice nie są odpowiednie do tworzenia tablic bitowych lub buforów.</span><span class="sxs-lookup"><span data-stu-id="da4df-124">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="da4df-125">Z wyjątkiem pamięci utworzonej przy użyciu [stackalloc](../../language-reference/operators/stackalloc.md), kompilator C# i wywoływania języka wspólnego (CLR) nie wykonują żadnych kontroli przepełnienia buforu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="da4df-125">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="da4df-126">Podobnie jak w każdym niebezpiecznym kodzie, należy zachować ostrożność.</span><span class="sxs-lookup"><span data-stu-id="da4df-126">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="da4df-127">Niebezpieczne bufory różnią się od zwykłych tablic w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="da4df-127">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="da4df-128">Można używać tylko niebezpieczne bufory w kontekście niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="da4df-128">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="da4df-129">Niebezpieczne bufory są zawsze wektorami lub tablicami jednowymiarowymi.</span><span class="sxs-lookup"><span data-stu-id="da4df-129">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="da4df-130">Deklaracja tablicy powinna zawierać liczbę, `char id[8]`taką jak .</span><span class="sxs-lookup"><span data-stu-id="da4df-130">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="da4df-131">Nie można `char id[]`użyć .</span><span class="sxs-lookup"><span data-stu-id="da4df-131">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="da4df-132">Niebezpieczne bufory mogą być tylko pola wystąpienia struktur w niebezpiecznym kontekście.</span><span class="sxs-lookup"><span data-stu-id="da4df-132">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="da4df-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da4df-133">See also</span></span>

- [<span data-ttu-id="da4df-134">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="da4df-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="da4df-135">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="da4df-135">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="da4df-136">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="da4df-136">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="da4df-137">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="da4df-137">Interoperability</span></span>](../interop/index.md)
