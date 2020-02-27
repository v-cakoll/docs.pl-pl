---
title: Bufory o ustalonym rozmiarze — C# Przewodnik programowania
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 9005c425badc5a4ed74e6af3447e563daf61229e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627802"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="9b8c6-102">Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9b8c6-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="9b8c6-103">W C#programie można użyć instrukcji [FIXED](../../language-reference/keywords/fixed-statement.md) do utworzenia buforu z tablicą o stałym rozmiarze w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="9b8c6-104">Bufory o ustalonym rozmiarze są przydatne podczas pisania metod, które współdziałają ze źródłami danych z innych języków lub platform.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="9b8c6-105">Stała tablica może przyjmować wszelkie atrybuty lub modyfikatory, które są dozwolone dla zwykłych elementów członkowskich struktury.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="9b8c6-106">Jedynym ograniczeniem jest to, że typ tablicy musi być `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`lub `double`.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="9b8c6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9b8c6-107">Remarks</span></span>

<span data-ttu-id="9b8c6-108">W bezpiecznym kodzie C# struktura, która zawiera tablicę, nie zawiera elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="9b8c6-109">Zamiast tego, struktura zawiera odwołanie do elementów.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="9b8c6-110">Można osadzić tablicę o stałym rozmiarze w [strukturze](../../language-reference/builtin-types/struct.md) , gdy jest ona używana w [niebezpiecznym](../../language-reference/keywords/unsafe.md) bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="9b8c6-111">Następująca `struct` ma rozmiar 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="9b8c6-112">Tablica `pathName` jest odwołaniem:</span><span class="sxs-lookup"><span data-stu-id="9b8c6-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="9b8c6-113">`struct` może zawierać osadzoną tablicę w niebezpiecznym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="9b8c6-114">W poniższym przykładzie tablica `fixedBuffer` ma stały rozmiar.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="9b8c6-115">Użyj instrukcji `fixed`, aby określić wskaźnik do pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="9b8c6-116">Dostęp do elementów tablicy można uzyskać za pomocą tego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="9b8c6-117">Instrukcja `fixed` przypina pole wystąpienia `fixedBuffer` do określonej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="9b8c6-118">Rozmiar elementu 128 `char` Array to 256 bajtów.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="9b8c6-119">Bufory [znaków](../../language-reference/builtin-types/char.md) o stałym rozmiarze zawsze pobierają dwa bajty na znak, niezależnie od kodowania.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-119">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="9b8c6-120">Jest to prawdziwe nawet wtedy, gdy bufory znaków są organizowane w metodach lub strukturach interfejsu API za pomocą `CharSet = CharSet.Auto` lub `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="9b8c6-121">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="9b8c6-122">W poprzednim przykładzie pokazano dostęp do pól `fixed` bez przypinania, które są dostępne C# od 7,3.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="9b8c6-123">Inna wspólna tablica o stałym rozmiarze jest tablicą [logiczną](../../language-reference/builtin-types/bool.md) .</span><span class="sxs-lookup"><span data-stu-id="9b8c6-123">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="9b8c6-124">Elementy w tablicy `bool` są zawsze w rozmiarze jednego bajtu.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="9b8c6-125">Tablice `bool` nie są odpowiednie do tworzenia tablic bitowych lub buforów.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="9b8c6-126">Z wyjątkiem pamięci utworzonej przy użyciu [stackalloc](../../language-reference/operators/stackalloc.md), C# kompilator i środowisko uruchomieniowe języka wspólnego (CLR) nie wykonują żadnych kontroli przepełnienia buforu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-126">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="9b8c6-127">Podobnie jak w przypadku całego niebezpiecznego kodu, należy zachować ostrożność.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="9b8c6-128">Niebezpieczne bufory różnią się od zwykłych tablic w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9b8c6-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="9b8c6-129">W niebezpiecznym kontekście można używać tylko niebezpiecznych buforów.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="9b8c6-130">Niebezpieczne bufory są zawsze wektorami lub tablicami jednowymiarowymi.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="9b8c6-131">Deklaracja tablicy powinna zawierać liczbę, taką jak `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="9b8c6-132">Nie można użyć `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="9b8c6-133">Niebezpieczne bufory mogą być wystąpieniami tylko pól struktur w niebezpiecznym kontekście.</span><span class="sxs-lookup"><span data-stu-id="9b8c6-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b8c6-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b8c6-134">See also</span></span>

- [<span data-ttu-id="9b8c6-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9b8c6-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9b8c6-136">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="9b8c6-136">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="9b8c6-137">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9b8c6-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="9b8c6-138">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="9b8c6-138">Interoperability</span></span>](../interop/index.md)
