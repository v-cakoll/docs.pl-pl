---
title: Pamięć i zakresy
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: b61b1dbbedf4658fe113986fbb4a792a2f574534
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121989"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="d917a-102">Typy związane z pamięcią i zakresem</span><span class="sxs-lookup"><span data-stu-id="d917a-102">Memory- and span-related types</span></span>

<span data-ttu-id="d917a-103">Począwszy od .NET Core 2.1, .NET zawiera szereg powiązanych ze sobą typów, które reprezentują ciągły, silnie typizany region dowolnej pamięci.</span><span class="sxs-lookup"><span data-stu-id="d917a-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly-typed region of arbitrary memory.</span></span> <span data-ttu-id="d917a-104">Należą do nich:</span><span class="sxs-lookup"><span data-stu-id="d917a-104">These include:</span></span>

- <span data-ttu-id="d917a-105"><xref:System.Span%601?displayProperty=nameWithType>, typ, który jest używany do uzyskiwania dostępu do ciągłego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="d917a-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="d917a-106">Wystąpienie <xref:System.Span%601> może być wspierane przez tablicę `T` <xref:System.String>typu , a , bufor przydzielony z [stackalloc](../../csharp/language-reference/operators/stackalloc.md)lub wskaźnik do pamięci niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="d917a-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="d917a-107">Ponieważ musi być przydzielona na stosie, ma szereg ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="d917a-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="d917a-108">Na przykład pole w klasie nie <xref:System.Span%601>może być typu , ani zakres nie może być używany w operacjach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="d917a-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="d917a-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, niezmienną <xref:System.Span%601> wersję konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="d917a-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="d917a-110"><xref:System.Memory%601?displayProperty=nameWithType>, ciągły region pamięci, który jest przydzielany na zarządzanym stosie, a nie na stosie.</span><span class="sxs-lookup"><span data-stu-id="d917a-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="d917a-111">Wystąpienie <xref:System.Memory%601> może być wspierane przez tablicę `T` <xref:System.String>typu lub .</span><span class="sxs-lookup"><span data-stu-id="d917a-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="d917a-112">Ponieważ może być przechowywany na zarządzanym stercie, <xref:System.Memory%601> nie <xref:System.Span%601>ma żadnych ograniczeń .</span><span class="sxs-lookup"><span data-stu-id="d917a-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="d917a-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, niezmienną <xref:System.Memory%601> wersję konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="d917a-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="d917a-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, który przydziela silnie typizowane bloki pamięci z puli pamięci do właściciela.</span><span class="sxs-lookup"><span data-stu-id="d917a-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly-typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="d917a-115"><xref:System.Buffers.IMemoryOwner%601>można wypożyczyć z puli, <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> dzwoniąc i wypuszczono <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>je z powrotem do puli, dzwoniąc.</span><span class="sxs-lookup"><span data-stu-id="d917a-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="d917a-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, który reprezentuje właściciela bloku pamięci i kontroluje jego zarządzanie okresem istnienia.</span><span class="sxs-lookup"><span data-stu-id="d917a-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="d917a-117"><xref:System.Buffers.MemoryManager%601>, abstrakcyjna klasa podstawowa, która może <xref:System.Memory%601> służyć <xref:System.Memory%601> do zastąpienia implementacji, dzięki czemu mogą być wspierane przez dodatkowe typy, takie jak bezpieczne dojścia.</span><span class="sxs-lookup"><span data-stu-id="d917a-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="d917a-118"><xref:System.Buffers.MemoryManager%601>jest przeznaczony dla zaawansowanych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="d917a-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="d917a-119"><xref:System.ArraySegment%601>, otoka dla określonej liczby elementów tablicy rozpoczynających się od określonego indeksu.</span><span class="sxs-lookup"><span data-stu-id="d917a-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="d917a-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, zbiór metod rozszerzenia do konwertowania ciągów, tablic i <xref:System.Memory%601> segmentów tablicy na bloki.</span><span class="sxs-lookup"><span data-stu-id="d917a-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="d917a-121">Dla wcześniejszych struktur <xref:System.Span%601> <xref:System.Memory%601> i są dostępne w [pakiecie System.Memory NuGet](https://www.nuget.org/packages/System.Memory/).</span><span class="sxs-lookup"><span data-stu-id="d917a-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="d917a-122">Aby uzyskać więcej <xref:System.Buffers?displayProperty=nameWithType> informacji, zobacz obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="d917a-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="d917a-123">Praca z pamięcią i zakresem</span><span class="sxs-lookup"><span data-stu-id="d917a-123">Working with memory and span</span></span>

<span data-ttu-id="d917a-124">Ponieważ typy związane z pamięcią i zakresem są zwykle używane do przechowywania danych w potoku przetwarzania, ważne jest, aby deweloperzy postępowali zgodnie z zestawem najlepszych rozwiązań podczas korzystania z <xref:System.Span%601>typów <xref:System.Memory%601>i powiązanych.</span><span class="sxs-lookup"><span data-stu-id="d917a-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="d917a-125">Te najlepsze rozwiązania są udokumentowane w [\<memory\<T> i Span T> wskazówki dotyczące użytkowania](memory-t-usage-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="d917a-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d917a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d917a-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
