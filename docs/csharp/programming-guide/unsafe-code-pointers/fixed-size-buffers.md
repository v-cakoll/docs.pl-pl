---
title: Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 310c5eed5507f75239efc78b6132fbc91211d29e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339595"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="b22ac-102">Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b22ac-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="b22ac-103">W języku C#, można użyć [stałej](../../language-reference/keywords/fixed-statement.md) instrukcji do utworzenia buforu z tablicą o stałym rozmiarze w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="b22ac-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="b22ac-104">Bufory o ustalonym rozmiarze są przydatne podczas pisania tego współdziałanie ze źródłami danych metody z innych języków lub platformy.</span><span class="sxs-lookup"><span data-stu-id="b22ac-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="b22ac-105">Tablicy o ustalonym może zająć żadnych atrybutów ani modyfikatorów, które są dozwolone w przypadku elementów członkowskich struktury regularne.</span><span class="sxs-lookup"><span data-stu-id="b22ac-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="b22ac-106">Tylko ograniczenie jest, że typ tablicy musi być `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, lub `double`.</span><span class="sxs-lookup"><span data-stu-id="b22ac-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="b22ac-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b22ac-107">Remarks</span></span>

<span data-ttu-id="b22ac-108">W kodzie bezpieczne struktury C#, który zawiera tablicę nie zawiera elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="b22ac-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="b22ac-109">Struktura zawiera odwołania do elementów.</span><span class="sxs-lookup"><span data-stu-id="b22ac-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="b22ac-110">Osadzić tablicy o ustalonym rozmiarze w [struktury](../../language-reference/keywords/struct.md) gdy jest używana w [niebezpieczne](../../language-reference/keywords/unsafe.md) blok kodu.</span><span class="sxs-lookup"><span data-stu-id="b22ac-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="b22ac-111">Następujące `struct` jest rozmiar 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b22ac-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="b22ac-112">`pathName` Tablica jest odwołanie:</span><span class="sxs-lookup"><span data-stu-id="b22ac-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="b22ac-113">A `struct` może zawierać osadzoną tablicę w niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="b22ac-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="b22ac-114">W poniższym przykładzie `fixedBuffer` tablicy ma stały rozmiar.</span><span class="sxs-lookup"><span data-stu-id="b22ac-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="b22ac-115">Możesz użyć `fixed` instrukcji, aby ustanowić wskaźnik do pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="b22ac-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="b22ac-116">Elementy tablicy dostęp przez ten wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="b22ac-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="b22ac-117">`fixed` Numerów PIN instrukcji `fixedBuffer` pole wystąpienia w określonej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b22ac-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="b22ac-118">Rozmiar elementu, 128 `char` tablicy to 256 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b22ac-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="b22ac-119">Stały rozmiar [char](../../language-reference/keywords/char.md) buforów zawsze pobierają dwa bajty na znak, niezależnie od tego, kodowania.</span><span class="sxs-lookup"><span data-stu-id="b22ac-119">Fixed size [char](../../language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="b22ac-120">Dotyczy to nawet, gdy buforów char są przekazywane do metody interfejsu API lub strukturach z `CharSet = CharSet.Auto` lub `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="b22ac-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="b22ac-121">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="b22ac-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="b22ac-122">W poprzednim przykładzie pokazano, uzyskiwanie dostępu do `fixed` pól bez przypinanie, które jest dostępnych w programie 7.3 C#.</span><span class="sxs-lookup"><span data-stu-id="b22ac-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3..</span></span>

<span data-ttu-id="b22ac-123">Innej wspólnej tablicy o stałym rozmiarze jest [bool](../../language-reference/keywords/bool.md) tablicy.</span><span class="sxs-lookup"><span data-stu-id="b22ac-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="b22ac-124">Elementy w `bool` tablicy są zawsze jednego bajtu rozmiar.</span><span class="sxs-lookup"><span data-stu-id="b22ac-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="b22ac-125">`bool` tablice nie są odpowiednie do tworzenia tablic z bitowego lub buforów.</span><span class="sxs-lookup"><span data-stu-id="b22ac-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="b22ac-126">Z wyjątkiem pamięci utworzone za pomocą [stackalloc](../../language-reference/keywords/stackalloc.md), kompilator języka C# i środowisko uruchomieniowe języka wspólnego (CLR) nie wykonuj żadnych kontroli przepełnienie buforu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b22ac-126">Except for memory created by using [stackalloc](../../language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="b22ac-127">Podobnie jak w przypadku wszystkich niebezpieczny kod, należy zachować ostrożność.</span><span class="sxs-lookup"><span data-stu-id="b22ac-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="b22ac-128">Niebezpieczne bufory różnią się od regularne tablice w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b22ac-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="b22ac-129">Niebezpieczne bufory można używać tylko w niebezpiecznym kontekście.</span><span class="sxs-lookup"><span data-stu-id="b22ac-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="b22ac-130">Niebezpieczne bufory są zawsze wektorów lub tablice jednowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="b22ac-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="b22ac-131">Deklaracja tablicy powinna zawierać liczbę, takich jak `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="b22ac-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="b22ac-132">Nie można użyć `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="b22ac-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="b22ac-133">Niebezpieczne bufory można tylko pola wystąpienia struktur w niebezpiecznym kontekście.</span><span class="sxs-lookup"><span data-stu-id="b22ac-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="b22ac-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b22ac-134">See Also</span></span>

[<span data-ttu-id="b22ac-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b22ac-135">C# Programming Guide</span></span>](../index.md)  
[<span data-ttu-id="b22ac-136">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="b22ac-136">Unsafe Code and Pointers</span></span>](index.md)  
[<span data-ttu-id="b22ac-137">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b22ac-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)  
[<span data-ttu-id="b22ac-138">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="b22ac-138">Interoperability</span></span>](../interop/index.md)
