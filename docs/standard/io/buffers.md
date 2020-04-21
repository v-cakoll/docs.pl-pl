---
title: System.Bufory - .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: d113def0182dc6a5bcea6c18b2d0e4b475946e31
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739622"
---
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="3dc79-102">Praca z buforami w .NET</span><span class="sxs-lookup"><span data-stu-id="3dc79-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="3dc79-103">Ten artykuł zawiera omówienie typów, które pomagają odczytać dane, które są uruchamiane w wielu buforach.</span><span class="sxs-lookup"><span data-stu-id="3dc79-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="3dc79-104">Są one używane głównie <xref:System.IO.Pipelines.PipeReader> do obsługi obiektów.</span><span class="sxs-lookup"><span data-stu-id="3dc79-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="3dc79-105">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="3dc79-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="3dc79-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>jest kontraktem na synchroniczowe buforowane pisanie.</span><span class="sxs-lookup"><span data-stu-id="3dc79-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="3dc79-107">Na najniższym poziomie interfejs:</span><span class="sxs-lookup"><span data-stu-id="3dc79-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="3dc79-108">Jest podstawowy i nie jest trudny w użyciu.</span><span class="sxs-lookup"><span data-stu-id="3dc79-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="3dc79-109">Umożliwia dostęp <xref:System.Memory%601> do <xref:System.Span%601>lub .</span><span class="sxs-lookup"><span data-stu-id="3dc79-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="3dc79-110">Lub `Memory<T>` `Span<T>` mogą być zapisywane do i `T` można określić, ile elementów zostały napisane.</span><span class="sxs-lookup"><span data-stu-id="3dc79-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="3dc79-111">Poprzednia metoda:</span><span class="sxs-lookup"><span data-stu-id="3dc79-111">The preceding method:</span></span>

- <span data-ttu-id="3dc79-112">Żąda buforu o rozmiarze co `IBufferWriter<byte>` najmniej `GetSpan(5)`5 bajtów z using .</span><span class="sxs-lookup"><span data-stu-id="3dc79-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="3dc79-113">Zapisuje bajty dla ciągu ASCII "Hello" do zwracanych `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="3dc79-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="3dc79-114">Wywołania, <xref:System.Buffers.IBufferWriter%601> aby wskazać, ile bajtów zostały zapisane w buforze.</span><span class="sxs-lookup"><span data-stu-id="3dc79-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="3dc79-115">Ta metoda pisania używa `Memory<T>` / `Span<T>` buforu `IBufferWriter<T>`dostarczonego przez .</span><span class="sxs-lookup"><span data-stu-id="3dc79-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="3dc79-116">Alternatywnie można <xref:System.Buffers.BuffersExtensions.Write%2A> użyć metody rozszerzenia do kopiowania `IBufferWriter<T>`istniejącego buforu do pliku .</span><span class="sxs-lookup"><span data-stu-id="3dc79-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="3dc79-117">`Write`wykonuje pracę wywoływania `GetSpan` / `Advance` w razie potrzeby, więc `Advance` nie ma potrzeby, aby zadzwonić po napisaniu:</span><span class="sxs-lookup"><span data-stu-id="3dc79-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="3dc79-118"><xref:System.Buffers.ArrayBufferWriter%601>jest implementacją `IBufferWriter<T>` magazynu zapasowego, którego zapas jest pojedynczą tablicą ciągłą.</span><span class="sxs-lookup"><span data-stu-id="3dc79-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="3dc79-119">IBufferWriter typowe problemy</span><span class="sxs-lookup"><span data-stu-id="3dc79-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="3dc79-120">`GetSpan`i `GetMemory` zwrócić bufor z co najmniej żądaną ilością pamięci.</span><span class="sxs-lookup"><span data-stu-id="3dc79-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="3dc79-121">Nie zakładaj dokładnych rozmiarów buforu.</span><span class="sxs-lookup"><span data-stu-id="3dc79-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="3dc79-122">Nie ma żadnej gwarancji, że kolejne wywołania zwróci ten sam bufor lub bufor o tym samym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="3dc79-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="3dc79-123">Nowy bufor musi być wymagane `Advance` po wywołaniu, aby kontynuować zapisywanie większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="3dc79-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="3dc79-124">Wcześniej nabyty bufor nie może być `Advance` zapisywany po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="3dc79-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="3dc79-125">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="3dc79-125">ReadOnlySequence\<T\></span></span>

![ReadOnlySequence pokazujące pamięć w rurze i poniżej tej pozycji sekwencji pamięci tylko do odczytu](media/buffers/ro-sequence.png)

<span data-ttu-id="3dc79-127"><xref:System.Buffers.ReadOnlySequence%601>jest strukturą, która może reprezentować ciągłą lub nieciągłą sekwencję `T`.</span><span class="sxs-lookup"><span data-stu-id="3dc79-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="3dc79-128">Może być zbudowany z:</span><span class="sxs-lookup"><span data-stu-id="3dc79-128">It can be constructed from:</span></span>

1. <span data-ttu-id="3dc79-129">Element `T[]`.</span><span class="sxs-lookup"><span data-stu-id="3dc79-129">A `T[]`</span></span>
1. <span data-ttu-id="3dc79-130">Element `ReadOnlyMemory<T>`.</span><span class="sxs-lookup"><span data-stu-id="3dc79-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="3dc79-131">Para połączonego węzła <xref:System.Buffers.ReadOnlySequenceSegment%601> listy i indeksu do reprezentowania pozycji początkowej i końcowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="3dc79-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="3dc79-132">Trzecia reprezentacja jest najciekawsza, ponieważ ma `ReadOnlySequence<T>`wpływ na wydajność różnych operacji na:</span><span class="sxs-lookup"><span data-stu-id="3dc79-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="3dc79-133">Reprezentacja</span><span class="sxs-lookup"><span data-stu-id="3dc79-133">Representation</span></span>|<span data-ttu-id="3dc79-134">Operacja</span><span class="sxs-lookup"><span data-stu-id="3dc79-134">Operation</span></span>|<span data-ttu-id="3dc79-135">Złożoność</span><span class="sxs-lookup"><span data-stu-id="3dc79-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="3dc79-136">Z powodu tej mieszanej reprezentacji `ReadOnlySequence<T>` `SequencePosition` udostępnia indeksy jako zamiast liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="3dc79-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="3dc79-137">A: `SequencePosition`</span><span class="sxs-lookup"><span data-stu-id="3dc79-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="3dc79-138">Jest nieprzezroczystą wartością `ReadOnlySequence<T>` reprezentującą indeks do miejsca, w którym pochodzi.</span><span class="sxs-lookup"><span data-stu-id="3dc79-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="3dc79-139">Składa się z dwóch części, liczby całkowitej i obiektu.</span><span class="sxs-lookup"><span data-stu-id="3dc79-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="3dc79-140">Co te dwie wartości reprezentują są `ReadOnlySequence<T>`związane z implementacją .</span><span class="sxs-lookup"><span data-stu-id="3dc79-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="3dc79-141">Uzyskiwanie dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="3dc79-141">Access data</span></span>

<span data-ttu-id="3dc79-142">Udostępnia `ReadOnlySequence<T>` dane jako wyliczalne `ReadOnlyMemory<T>`.</span><span class="sxs-lookup"><span data-stu-id="3dc79-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="3dc79-143">Wyliczanie każdego z segmentów można wykonać za pomocą podstawowego foreach:</span><span class="sxs-lookup"><span data-stu-id="3dc79-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="3dc79-144">Poprzednia metoda przeszukuje każdy segment w poszukiwaniu określonego bajtu.</span><span class="sxs-lookup"><span data-stu-id="3dc79-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="3dc79-145">Jeśli chcesz śledzić każdy `SequencePosition`segment, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> jest bardziej odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="3dc79-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="3dc79-146">Następny przykład zmienia poprzedni kod, `SequencePosition` aby zwrócić zamiast liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="3dc79-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="3dc79-147">Powrót a `SequencePosition` ma zaletę, pozwalając wywołującego, aby uniknąć drugiego skanowania, aby uzyskać dane w określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="3dc79-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="3dc79-148">Połączenie `SequencePosition` i `TryGet` działa jak wyliczacz.</span><span class="sxs-lookup"><span data-stu-id="3dc79-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="3dc79-149">Pole pozycji jest modyfikowane na początku każdej iteracji, aby `ReadOnlySequence<T>`było początkiem każdego segmentu w pliku .</span><span class="sxs-lookup"><span data-stu-id="3dc79-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="3dc79-150">Poprzednia metoda istnieje jako metoda `ReadOnlySequence<T>`rozszerzenia na .</span><span class="sxs-lookup"><span data-stu-id="3dc79-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="3dc79-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A>może służyć do uproszczenia poprzedniego kodu:</span><span class="sxs-lookup"><span data-stu-id="3dc79-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="3dc79-152">Proces ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="3dc79-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="3dc79-153">Przetwarzanie `ReadOnlySequence<T>` a może być trudne, ponieważ dane mogą być podzielone na wiele segmentów w ramach sekwencji.</span><span class="sxs-lookup"><span data-stu-id="3dc79-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="3dc79-154">Aby uzyskać najlepszą wydajność, podziel kod na dwie ścieżki:</span><span class="sxs-lookup"><span data-stu-id="3dc79-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="3dc79-155">Szybka ścieżka, która dotyczy pojedynczego segmentu.</span><span class="sxs-lookup"><span data-stu-id="3dc79-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="3dc79-156">Powolna ścieżka, która zajmuje się danymi podzielonymi na segmenty.</span><span class="sxs-lookup"><span data-stu-id="3dc79-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="3dc79-157">Istnieje kilka podejść, które mogą być używane do przetwarzania danych w sekwencjach wielosegmentowych:</span><span class="sxs-lookup"><span data-stu-id="3dc79-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="3dc79-158">Użyj [`SequenceReader<T>`](#sequencereadert)pliku .</span><span class="sxs-lookup"><span data-stu-id="3dc79-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="3dc79-159">Analizuj segment danych według segmentów, śledząc `SequencePosition` i indeks w obrębie analizowanego segmentu.</span><span class="sxs-lookup"><span data-stu-id="3dc79-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="3dc79-160">Pozwala to uniknąć niepotrzebnych alokacji, ale może być nieefektywne, zwłaszcza w przypadku małych buforów.</span><span class="sxs-lookup"><span data-stu-id="3dc79-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="3dc79-161">Skopiuj `ReadOnlySequence<T>` do ciągłej tablicy i potraktuj ją jak pojedynczy bufor:</span><span class="sxs-lookup"><span data-stu-id="3dc79-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="3dc79-162">Jeśli rozmiar `ReadOnlySequence<T>` jest mały, może być uzasadnione, aby skopiować dane do buforu przydzielonego do stosu przy użyciu [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="3dc79-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="3dc79-163">Skopiuj do `ReadOnlySequence<T>` <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>tablicy zbiorczej za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="3dc79-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="3dc79-164">Użyj witryny [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span><span class="sxs-lookup"><span data-stu-id="3dc79-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="3dc79-165">Nie jest to zalecane w ścieżkach gorących, ponieważ przydziela nowy `T[]` na stosie.</span><span class="sxs-lookup"><span data-stu-id="3dc79-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="3dc79-166">Poniższe przykłady pokazują niektóre `ReadOnlySequence<byte>`typowe przypadki przetwarzania:</span><span class="sxs-lookup"><span data-stu-id="3dc79-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="3dc79-167">Przetwarzanie danych binarnych</span><span class="sxs-lookup"><span data-stu-id="3dc79-167">Process binary data</span></span>

<span data-ttu-id="3dc79-168">W poniższym przykładzie analizuje 4-bajtową długość całkowitą big-endian `ReadOnlySequence<byte>`od początku .</span><span class="sxs-lookup"><span data-stu-id="3dc79-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="3dc79-169">Przetwarzanie danych tekstowych</span><span class="sxs-lookup"><span data-stu-id="3dc79-169">Process text data</span></span>

<span data-ttu-id="3dc79-170">Poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="3dc79-170">The following example:</span></span>

- <span data-ttu-id="3dc79-171">Znajduje pierwszą nową`\r\n`linię `ReadOnlySequence<byte>` ( ) w i zwraca ją za pomocą out "line" parametru.</span><span class="sxs-lookup"><span data-stu-id="3dc79-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="3dc79-172">Przycina ten wiersz, `\r\n` z wyłączeniem buforu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="3dc79-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="3dc79-173">Puste segmenty</span><span class="sxs-lookup"><span data-stu-id="3dc79-173">Empty segments</span></span>

<span data-ttu-id="3dc79-174">Prawidłowe jest przechowywanie pustych segmentów `ReadOnlySequence<T>`wewnątrz pliku .</span><span class="sxs-lookup"><span data-stu-id="3dc79-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="3dc79-175">Puste segmenty mogą występować podczas jawnego wyliczania segmentów:</span><span class="sxs-lookup"><span data-stu-id="3dc79-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="3dc79-176">Poprzedni kod tworzy `ReadOnlySequence<byte>` z pustymi segmentami i pokazuje, jak te puste segmenty wpływają na różne interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="3dc79-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="3dc79-177">`ReadOnlySequence<T>.Slice`z `SequencePosition` wskazywaniem na pusty segment zachowuje ten segment.</span><span class="sxs-lookup"><span data-stu-id="3dc79-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="3dc79-178">`ReadOnlySequence<T>.Slice`z int przeskakuje nad pustymi segmentami.</span><span class="sxs-lookup"><span data-stu-id="3dc79-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="3dc79-179">Wyliczanie `ReadOnlySequence<T>` wylicza puste segmenty.</span><span class="sxs-lookup"><span data-stu-id="3dc79-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="3dc79-180">Potencjalne problemy z ReadOnlySequence\<T> i SequencePosition</span><span class="sxs-lookup"><span data-stu-id="3dc79-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="3dc79-181">Istnieje kilka nietypowych wyników, `ReadOnlySequence<T>` / `SequencePosition` gdy mamy `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int`do czynienia z a. normalne:</span><span class="sxs-lookup"><span data-stu-id="3dc79-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="3dc79-182">`SequencePosition`jest znacznikiem położenia dla określonej, `ReadOnlySequence<T>`a nie bezwzględnej pozycji.</span><span class="sxs-lookup"><span data-stu-id="3dc79-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="3dc79-183">Ponieważ jest to związane `ReadOnlySequence<T>`z określonym , nie ma znaczenia, `ReadOnlySequence<T>` jeśli jest używany poza miejscem, w którym pochodzi.</span><span class="sxs-lookup"><span data-stu-id="3dc79-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="3dc79-184">Arytmetyka nie może być `SequencePosition` wykonywana `ReadOnlySequence<T>`bez pliku .</span><span class="sxs-lookup"><span data-stu-id="3dc79-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="3dc79-185">Oznacza to, że `position++` robi `ReadOnlySequence<T>.GetPosition(position, 1)`podstawowe rzeczy, takie jak jest napisane .</span><span class="sxs-lookup"><span data-stu-id="3dc79-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="3dc79-186">`GetPosition(long)`**nie** obsługuje indeksów ujemnych.</span><span class="sxs-lookup"><span data-stu-id="3dc79-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="3dc79-187">Oznacza to, że nie można uzyskać od drugiego do ostatniego znaku bez chodzenia po wszystkich segmentach.</span><span class="sxs-lookup"><span data-stu-id="3dc79-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="3dc79-188">Dwóch `SequencePosition` nie można porównać, co utrudnia:</span><span class="sxs-lookup"><span data-stu-id="3dc79-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="3dc79-189">Dowiedz się, czy jedna pozycja jest większa lub mniejsza niż inna pozycja.</span><span class="sxs-lookup"><span data-stu-id="3dc79-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="3dc79-190">Napisz kilka algorytmów analizowania.</span><span class="sxs-lookup"><span data-stu-id="3dc79-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="3dc79-191">`ReadOnlySequence<T>`jest większy niż odwołanie do obiektu i powinny być przekazywane przez [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) lub [ref,](../../csharp/language-reference/keywords/ref.md) jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="3dc79-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="3dc79-192">Przechodząc `ReadOnlySequence<T>` `in` przez `ref` lub zmniejsza kopie [struktury](../../csharp/language-reference/builtin-types/struct.md).</span><span class="sxs-lookup"><span data-stu-id="3dc79-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="3dc79-193">Puste segmenty:</span><span class="sxs-lookup"><span data-stu-id="3dc79-193">Empty segments:</span></span>
  - <span data-ttu-id="3dc79-194">Są ważne `ReadOnlySequence<T>`w obrębie .</span><span class="sxs-lookup"><span data-stu-id="3dc79-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="3dc79-195">Może pojawić się podczas `ReadOnlySequence<T>.TryGet` iteracji przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="3dc79-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="3dc79-196">Może pojawić się krojenie `ReadOnlySequence<T>.Slice()` sekwencji przy użyciu metody z `SequencePosition` obiektami.</span><span class="sxs-lookup"><span data-stu-id="3dc79-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="3dc79-197">SequenceReader\<T (Czytnik sekwencji T)\></span><span class="sxs-lookup"><span data-stu-id="3dc79-197">SequenceReader\<T\></span></span>

<span data-ttu-id="3dc79-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="3dc79-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="3dc79-199">Jest to nowy typ, który został wprowadzony w .NET Core `ReadOnlySequence<T>`3.0 w celu uproszczenia przetwarzania .</span><span class="sxs-lookup"><span data-stu-id="3dc79-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="3dc79-200">Ujednolica różnice `ReadOnlySequence<T>` między pojedynczym i wielosegmentowym `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="3dc79-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="3dc79-201">Zapewnia pomocników do odczytywania`byte` `char`danych binarnych i tekstowych ( i ), które mogą lub nie mogą być podzielone na segmenty.</span><span class="sxs-lookup"><span data-stu-id="3dc79-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="3dc79-202">Istnieją wbudowane metody radzenia sobie z przetwarzaniem danych binarnych i rozdzielanych.</span><span class="sxs-lookup"><span data-stu-id="3dc79-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="3dc79-203">W poniższej sekcji pokazano, jak wyglądają `SequenceReader<T>`te same metody z :</span><span class="sxs-lookup"><span data-stu-id="3dc79-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="3dc79-204">Uzyskiwanie dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="3dc79-204">Access data</span></span>

<span data-ttu-id="3dc79-205">`SequenceReader<T>`ma metody wyliczania danych `ReadOnlySequence<T>` wewnątrz bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="3dc79-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="3dc79-206">Poniższy kod jest przykładem `ReadOnlySequence<byte>` `byte` przetwarzania a w czasie:</span><span class="sxs-lookup"><span data-stu-id="3dc79-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="3dc79-207">Eksponuje `CurrentSpan` bieżącego segmentu `Span`, który jest podobny do tego, co zostało zrobione w metodzie ręcznie.</span><span class="sxs-lookup"><span data-stu-id="3dc79-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="3dc79-208">Użyj pozycji</span><span class="sxs-lookup"><span data-stu-id="3dc79-208">Use position</span></span>

<span data-ttu-id="3dc79-209">Poniższy kod jest przykładową implementacją `FindIndexOf` przy `SequenceReader<T>`użyciu:</span><span class="sxs-lookup"><span data-stu-id="3dc79-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="3dc79-210">Przetwarzanie danych binarnych</span><span class="sxs-lookup"><span data-stu-id="3dc79-210">Process binary data</span></span>

<span data-ttu-id="3dc79-211">W poniższym przykładzie analizuje 4-bajtową długość całkowitą big-endian `ReadOnlySequence<byte>`od początku .</span><span class="sxs-lookup"><span data-stu-id="3dc79-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="3dc79-212">Przetwarzanie danych tekstowych</span><span class="sxs-lookup"><span data-stu-id="3dc79-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="3dc79-213">SequenceReader\<\> T typowe problemy</span><span class="sxs-lookup"><span data-stu-id="3dc79-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="3dc79-214">Ponieważ `SequenceReader<T>` jest zmienna struktura, zawsze powinny być przekazywane przez [odwołanie](../../csharp/language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="3dc79-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="3dc79-215">`SequenceReader<T>`jest [strukturą ref,](../../csharp/language-reference/builtin-types/struct.md#ref-struct) dzięki czemu może być używana tylko w metodach synchronicznych i nie może być przechowywana w polach.</span><span class="sxs-lookup"><span data-stu-id="3dc79-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/builtin-types/struct.md#ref-struct) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="3dc79-216">Aby uzyskać więcej informacji, zobacz [Pisanie bezpiecznego i wydajnego kodu języka C#.](../../csharp/write-safe-efficient-code.md)</span><span class="sxs-lookup"><span data-stu-id="3dc79-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="3dc79-217">`SequenceReader<T>`jest zoptymalizowany do użycia jako czytnik tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="3dc79-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="3dc79-218">`Rewind`jest przeznaczony do małych kopii zapasowych, których `Read` `Peek`nie `IsNext` można rozwiązać z wykorzystaniem innych interfejsów API i interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="3dc79-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
