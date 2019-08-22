---
title: Pamięć i zakresy
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbfd091c821f59febfc8c7a203334454e7b59c12
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666424"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="d2105-102">Typy związane z pamięcią i zakresem</span><span class="sxs-lookup"><span data-stu-id="d2105-102">Memory- and span-related types</span></span>

<span data-ttu-id="d2105-103">Począwszy od platformy .NET Core 2,1, .NET zawiera wiele powiązanych typów, które reprezentują ciągły, silnie określony region wolnej pamięci.</span><span class="sxs-lookup"><span data-stu-id="d2105-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly-typed region of arbitrary memory.</span></span> <span data-ttu-id="d2105-104">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="d2105-104">These include:</span></span>

- <span data-ttu-id="d2105-105"><xref:System.Span%601?displayProperty=nameWithType>, typ, który jest używany w celu uzyskania dostępu do ciągłego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="d2105-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="d2105-106">Wystąpienie może być obsługiwane przez tablicę typu `T`, a <xref:System.String>, bufor alokowany z [stackalloc](../../csharp/language-reference/operators/stackalloc.md)lub wskaźnik do pamięci niezarządzanej. <xref:System.Span%601></span><span class="sxs-lookup"><span data-stu-id="d2105-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="d2105-107">Ponieważ musi być przypisana na stosie, ma wiele ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="d2105-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="d2105-108">Na przykład pole w klasie nie może być typu <xref:System.Span%601>, ani nie może być używane w operacjach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="d2105-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="d2105-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, niezmienna wersja <xref:System.Span%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="d2105-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="d2105-110"><xref:System.Memory%601?displayProperty=nameWithType>, ciągły region pamięci przydzielony na stercie zarządzanym, a nie na stosie.</span><span class="sxs-lookup"><span data-stu-id="d2105-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="d2105-111">Wystąpienie może być obsługiwane przez tablicę typu `T` lub <xref:System.String>. <xref:System.Memory%601></span><span class="sxs-lookup"><span data-stu-id="d2105-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="d2105-112">Ponieważ może być przechowywana na stercie zarządzanym, <xref:System.Memory%601> nie ma żadnych <xref:System.Span%601>ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="d2105-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="d2105-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, niezmienna wersja <xref:System.Memory%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="d2105-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="d2105-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, która przydziela jednoznacznie wpisane bloki pamięci z puli pamięci do właściciela.</span><span class="sxs-lookup"><span data-stu-id="d2105-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly-typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="d2105-115"><xref:System.Buffers.IMemoryOwner%601>wystąpienia mogą być wydzierżawione z puli, wywołując <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> i wywołując z powrotem do puli <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>przez wywołanie.</span><span class="sxs-lookup"><span data-stu-id="d2105-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="d2105-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, który reprezentuje właściciela bloku pamięci i kontroluje jego okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="d2105-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="d2105-117"><xref:System.Buffers.MemoryManager%601>abstrakcyjna klasa bazowa, która może służyć do zastępowania implementacji <xref:System.Memory%601> , która <xref:System.Memory%601> może być wykonywana przez dodatkowe typy, takie jak bezpieczne dojścia.</span><span class="sxs-lookup"><span data-stu-id="d2105-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="d2105-118"><xref:System.Buffers.MemoryManager%601>jest przeznaczony dla zaawansowanych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="d2105-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="d2105-119"><xref:System.ArraySegment%601>, otoka dla określonej liczby elementów tablicy, zaczynając od określonego indeksu.</span><span class="sxs-lookup"><span data-stu-id="d2105-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="d2105-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, kolekcja metod rozszerzających do przekonwertowania ciągów, tablic i segmentów <xref:System.Memory%601> tablicowych.</span><span class="sxs-lookup"><span data-stu-id="d2105-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="d2105-121">W przypadku wcześniejszych platform <xref:System.Span%601> i <xref:System.Memory%601> są dostępne w [pakiecie NuGet system. Memory](https://www.nuget.org/packages/System.Memory/).</span><span class="sxs-lookup"><span data-stu-id="d2105-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="d2105-122">Aby uzyskać więcej informacji, zobacz <xref:System.Buffers?displayProperty=nameWithType> przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="d2105-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="d2105-123">Praca z pamięcią i zakresem</span><span class="sxs-lookup"><span data-stu-id="d2105-123">Working with memory and span</span></span>

<span data-ttu-id="d2105-124">Ponieważ typy związane z pamięcią i zakresem są zwykle używane do przechowywania danych w potoku przetwarzania, ważne jest, aby deweloperzy przestrzegali zestawu najlepszych rozwiązań w przypadku używania <xref:System.Span%601>, <xref:System.Memory%601>i powiązanych typów.</span><span class="sxs-lookup"><span data-stu-id="d2105-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="d2105-125">Te najlepsze rozwiązania opisano w temacie [pamięć\<t > i obejmują\<> Wskazówki dotyczące użycia](memory-t-usage-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="d2105-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2105-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2105-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
