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
ms.openlocfilehash: 76a5c32660c8a08ef34c40f8f4ee9430e5ead5c8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644250"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="2db14-102">Powiązana z pamięcią i zakresu typów</span><span class="sxs-lookup"><span data-stu-id="2db14-102">Memory- and span-related types</span></span>

<span data-ttu-id="2db14-103">Począwszy od platformy .NET Core 2.1 .NET zawiera wiele powiązanych typów, które reprezentują ciągłe, silnie typizowane region dowolnego pamięci.</span><span class="sxs-lookup"><span data-stu-id="2db14-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly-typed region of arbitrary memory.</span></span> <span data-ttu-id="2db14-104">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="2db14-104">These include:</span></span>

- <span data-ttu-id="2db14-105"><xref:System.Span%601?displayProperty=nameWithType>, typ, który umożliwia dostęp do niego ciągły region pamięci.</span><span class="sxs-lookup"><span data-stu-id="2db14-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="2db14-106">A <xref:System.Span%601> wystąpienia może być wspierany przez tablicę typu `T`, <xref:System.String>, bufor przydzielony za pomocą [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), lub wskaźnika do niezarządzanej pamięci.</span><span class="sxs-lookup"><span data-stu-id="2db14-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="2db14-107">Ponieważ ma ona zostać przydzielone na stosie, ma kilku ograniczeniom.</span><span class="sxs-lookup"><span data-stu-id="2db14-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="2db14-108">Na przykład pole w klasie nie może być typu <xref:System.Span%601>, ani zakresu można używać w operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="2db14-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="2db14-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, wersja niezmienne <xref:System.Span%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="2db14-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="2db14-110"><xref:System.Memory%601?displayProperty=nameWithType>, dla niego ciągły region pamięci przydzielonej na zarządzanym stosie, a nie na stosie.</span><span class="sxs-lookup"><span data-stu-id="2db14-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="2db14-111">A <xref:System.Memory%601> wystąpienia może być wspierany przez tablicę typu `T` lub <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="2db14-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="2db14-112">Ponieważ mogą być przechowywane w zarządzanym stosie <xref:System.Memory%601> nie ma żadnego ograniczenia <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="2db14-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="2db14-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, wersja niezmienne <xref:System.Memory%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="2db14-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="2db14-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, który przydziela silnie typizowane bloki pamięci w puli pamięci do elementu owner.</span><span class="sxs-lookup"><span data-stu-id="2db14-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly-typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="2db14-115"><xref:System.Buffers.IMemoryOwner%601> wystąpienia, wypożyczone z puli, wywołując <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> i zwalnia z powrotem do puli, wywołując <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2db14-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="2db14-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, który reprezentuje właściciela bloku pamięci i kontroluje jego Zarządzanie okresem istnienia.</span><span class="sxs-lookup"><span data-stu-id="2db14-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="2db14-117"><xref:System.Buffers.MemoryManager%601>, abstrakcyjna klasa bazowa, która może być używany do zastępowania wdrożenia <xref:System.Memory%601> tak, aby <xref:System.Memory%601> był zabezpieczony za pomocą dodatkowych typów, takich jak bezpieczne dojścia.</span><span class="sxs-lookup"><span data-stu-id="2db14-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="2db14-118"><xref:System.Buffers.MemoryManager%601> jest przeznaczony dla zaawansowanych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="2db14-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="2db14-119"><xref:System.ArraySegment%601>, otoki dla określonej liczby elementów tablicy, zaczynając od określonego indeksu.</span><span class="sxs-lookup"><span data-stu-id="2db14-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="2db14-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, Kolekcja metody rozszerzenia dla konwersji ciągów, tablic i segmentów tablicy do <xref:System.Memory%601> bloków.</span><span class="sxs-lookup"><span data-stu-id="2db14-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="2db14-121">Dla starszych środowisk <xref:System.Span%601> i <xref:System.Memory%601> są dostępne w [pakietu System.Memory NuGet](https://www.nuget.org/packages/System.Memory/).</span><span class="sxs-lookup"><span data-stu-id="2db14-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="2db14-122">Aby uzyskać więcej informacji, zobacz <xref:System.Buffers?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2db14-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="2db14-123">Praca z pamięci i zakresu</span><span class="sxs-lookup"><span data-stu-id="2db14-123">Working with memory and span</span></span>

<span data-ttu-id="2db14-124">Ponieważ typy powiązana z pamięcią i zakresu zwykle są używane do przechowywania danych w potoku przetwarzania, jest ważne, że deweloperzy postępuj zgodnie z zestaw najlepszych rozwiązań, korzystając z <xref:System.Span%601>, <xref:System.Memory%601>i typów pokrewnych.</span><span class="sxs-lookup"><span data-stu-id="2db14-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="2db14-125">Następujące najlepsze rozwiązania są udokumentowane w artykule [pamięci\<T > i zakres\<T > wytyczne dotyczące użycia](memory-t-usage-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="2db14-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2db14-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2db14-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
