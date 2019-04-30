---
title: Ustalony rozmiar buforów - C# przewodnik programowania
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 7c83b4819975f63c6fc19e5c4783603f37d2a885
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708928"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="a1a42-102">Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a1a42-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="a1a42-103">W języku C#, można użyć [stałej](../../language-reference/keywords/fixed-statement.md) instrukcję, aby utworzyć buforu z tablicą o stałym rozmiarze w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="a1a42-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="a1a42-104">Bufory o ustalonym rozmiarze są przydatne, kiedy piszesz metod tego współdziałania ze źródłami danych z innych języków lub platform.</span><span class="sxs-lookup"><span data-stu-id="a1a42-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="a1a42-105">Naprawiono tablicy może potrwać atrybuty ani modyfikatorów, których można używać do elementów członkowskich struktury regularne.</span><span class="sxs-lookup"><span data-stu-id="a1a42-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="a1a42-106">Jedynym ograniczeniem jest to, że typ tablicy musi być `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, lub `double`.</span><span class="sxs-lookup"><span data-stu-id="a1a42-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="a1a42-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1a42-107">Remarks</span></span>

<span data-ttu-id="a1a42-108">W kodzie bezpiecznym struktury języka C#, która zawiera tablicę nie zawiera elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="a1a42-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="a1a42-109">Struktura zawiera odwołania do elementów.</span><span class="sxs-lookup"><span data-stu-id="a1a42-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="a1a42-110">Możesz osadzić tablicy o stałym rozmiarze w [struktury](../../language-reference/keywords/struct.md) gdy jest używany w [niebezpieczne](../../language-reference/keywords/unsafe.md) bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="a1a42-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="a1a42-111">Następujące `struct` jest 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a1a42-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="a1a42-112">`pathName` Tablica jest odwołanie:</span><span class="sxs-lookup"><span data-stu-id="a1a42-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="a1a42-113">Element `struct` może zawierać osadzoną tablicę w niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="a1a42-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="a1a42-114">W poniższym przykładzie `fixedBuffer` tablica ma stały rozmiar.</span><span class="sxs-lookup"><span data-stu-id="a1a42-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="a1a42-115">Możesz użyć `fixed` instrukcję, aby ustanowić wskaźnik do pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="a1a42-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="a1a42-116">Możesz uzyskać dostęp do elementów tablicy za pomocą tego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="a1a42-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="a1a42-117">`fixed` Numerów PIN instrukcji `fixedBuffer` pola wystąpienia w określonej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a1a42-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="a1a42-118">Rozmiar elementu 128 `char` tablicy to 256 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a1a42-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="a1a42-119">Ustalony rozmiar [char](../../language-reference/keywords/char.md) buforów zawsze pobierają dwóch bajtów na znak, niezależnie od tego, kodowania.</span><span class="sxs-lookup"><span data-stu-id="a1a42-119">Fixed size [char](../../language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="a1a42-120">Ta zasada obowiązuje nawet po buforów char są wysyłane do metody interfejsu API lub struktury z `CharSet = CharSet.Auto` lub `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="a1a42-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="a1a42-121">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="a1a42-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="a1a42-122">W poprzednim przykładzie pokazano, uzyskiwanie dostępu do `fixed` bez przypinania, pola, których jest dostępna, począwszy od C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="a1a42-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="a1a42-123">Innej wspólnej tablicy o stałym rozmiarze jest [bool](../../language-reference/keywords/bool.md) tablicy.</span><span class="sxs-lookup"><span data-stu-id="a1a42-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="a1a42-124">Elementy w `bool` tablicy są zawsze jednobajtowego w rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="a1a42-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="a1a42-125">`bool` tablice nie są odpowiednie do tworzenia tablic bitowe lub buforów.</span><span class="sxs-lookup"><span data-stu-id="a1a42-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="a1a42-126">Z wyjątkiem pamięci utworzone za pomocą [stackalloc](../../language-reference/keywords/stackalloc.md), kompilator języka C# i środowisko uruchomieniowe języka wspólnego (CLR) nie sprawdza zabezpieczeń buforu przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="a1a42-126">Except for memory created by using [stackalloc](../../language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="a1a42-127">Podobnie jak w przypadku wszystkich niebezpieczny kod, należy zachować ostrożność.</span><span class="sxs-lookup"><span data-stu-id="a1a42-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="a1a42-128">Niebezpieczne bufory różnią się od regularnych tablic w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a1a42-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="a1a42-129">Niebezpieczne bufory można używać tylko w niebezpiecznym kontekście.</span><span class="sxs-lookup"><span data-stu-id="a1a42-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="a1a42-130">Niebezpieczne bufory są zawsze wektorów lub tablic jednowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="a1a42-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="a1a42-131">Deklaracja tablicy powinna zawierać liczbę, takich jak `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="a1a42-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="a1a42-132">Nie można użyć `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="a1a42-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="a1a42-133">Niebezpieczne bufory można tylko wystąpienia pól struktur w niebezpiecznym kontekście.</span><span class="sxs-lookup"><span data-stu-id="a1a42-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1a42-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1a42-134">See also</span></span>

- [<span data-ttu-id="a1a42-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a1a42-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a1a42-136">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="a1a42-136">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="a1a42-137">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a1a42-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="a1a42-138">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="a1a42-138">Interoperability</span></span>](../interop/index.md)
