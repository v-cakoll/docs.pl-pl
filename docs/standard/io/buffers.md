---
title: System. buffers — .NET
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
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="a4556-102">Korzystanie z buforów w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="a4556-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="a4556-103">Ten artykuł zawiera omówienie typów, które ułatwiają odczytywanie danych z różnych buforów.</span><span class="sxs-lookup"><span data-stu-id="a4556-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="a4556-104">Są one używane głównie do obsługi <xref:System.IO.Pipelines.PipeReader> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a4556-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="a4556-105">IBufferWriter \< T\></span><span class="sxs-lookup"><span data-stu-id="a4556-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="a4556-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>jest kontraktem synchronicznie zbuforowanego zapisu.</span><span class="sxs-lookup"><span data-stu-id="a4556-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="a4556-107">Na najniższym poziomie interfejs:</span><span class="sxs-lookup"><span data-stu-id="a4556-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="a4556-108">Jest podstawowa i nie jest trudna do użycia.</span><span class="sxs-lookup"><span data-stu-id="a4556-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="a4556-109">Zezwala na dostęp do <xref:System.Memory%601> lub <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="a4556-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="a4556-110">`Memory<T>`Lub `Span<T>` można pisać do i można określić liczbę elementów, które `T` zostały zapisaniu.</span><span class="sxs-lookup"><span data-stu-id="a4556-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="a4556-111">Poprzednia metoda:</span><span class="sxs-lookup"><span data-stu-id="a4556-111">The preceding method:</span></span>

- <span data-ttu-id="a4556-112">Żąda bufora co najmniej 5 bajtów z `IBufferWriter<byte>` polecenia using `GetSpan(5)` .</span><span class="sxs-lookup"><span data-stu-id="a4556-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="a4556-113">Zapisuje bajty dla ciągu ASCII "Hello" jako zwrócone `Span<byte>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="a4556-114">Wywołania <xref:System.Buffers.IBufferWriter%601> wskazujące, ile bajtów Zapisano w buforze.</span><span class="sxs-lookup"><span data-stu-id="a4556-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="a4556-115">Ta metoda pisania używa `Memory<T>` / `Span<T>` buforu dostarczonego przez `IBufferWriter<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="a4556-116">Alternatywnie <xref:System.Buffers.BuffersExtensions.Write%2A> można użyć metody rozszerzenia, aby skopiować istniejący bufor do `IBufferWriter<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="a4556-117">`Write`wykonuje `GetSpan` / `Advance` odpowiednie działania, aby nie trzeba było wywoływać `Advance` po zapisaniu:</span><span class="sxs-lookup"><span data-stu-id="a4556-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="a4556-118"><xref:System.Buffers.ArrayBufferWriter%601>jest implementacją, `IBufferWriter<T>` której magazyn zapasowy jest pojedynczą ciągłą tablicą.</span><span class="sxs-lookup"><span data-stu-id="a4556-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="a4556-119">IBufferWriter typowe problemy</span><span class="sxs-lookup"><span data-stu-id="a4556-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="a4556-120">`GetSpan`i `GetMemory` Zwróć bufor z co najmniej żądaną ilością pamięci.</span><span class="sxs-lookup"><span data-stu-id="a4556-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="a4556-121">Nie zakładaj dokładnie rozmiarów buforów.</span><span class="sxs-lookup"><span data-stu-id="a4556-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="a4556-122">Nie ma gwarancji, że kolejne wywołania będą zwracać ten sam bufor lub bufor o takim samym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="a4556-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="a4556-123">Należy zażądać nowego buforu po wywołaniu `Advance` , aby kontynuować zapisywanie większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="a4556-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="a4556-124">Wcześniej uzyskany bufor nie może zostać zapisany do po `Advance` wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="a4556-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="a4556-125">ReadOnlySequence \< T\></span><span class="sxs-lookup"><span data-stu-id="a4556-125">ReadOnlySequence\<T\></span></span>

![ReadOnlySequence pokazujący pamięć w potoku i poniżej tej pozycji sekwencji pamięci tylko do odczytu](media/buffers/ro-sequence.png)

<span data-ttu-id="a4556-127"><xref:System.Buffers.ReadOnlySequence%601>jest strukturą, która może reprezentować ciągłą lub nieciągłą sekwencję `T` .</span><span class="sxs-lookup"><span data-stu-id="a4556-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="a4556-128">Można ją skonstruować z:</span><span class="sxs-lookup"><span data-stu-id="a4556-128">It can be constructed from:</span></span>

1. <span data-ttu-id="a4556-129">Element `T[]`.</span><span class="sxs-lookup"><span data-stu-id="a4556-129">A `T[]`</span></span>
1. <span data-ttu-id="a4556-130">Element `ReadOnlyMemory<T>`.</span><span class="sxs-lookup"><span data-stu-id="a4556-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="a4556-131">Para węzła połączonej listy <xref:System.Buffers.ReadOnlySequenceSegment%601> i indeksu do reprezentowania pozycji początkowej i końcowej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a4556-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="a4556-132">Trzecia reprezentacja jest najbardziej interesująca, ponieważ ma wpływ na wydajność różnych operacji na `ReadOnlySequence<T>` :</span><span class="sxs-lookup"><span data-stu-id="a4556-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="a4556-133">Reprezentowana</span><span class="sxs-lookup"><span data-stu-id="a4556-133">Representation</span></span>|<span data-ttu-id="a4556-134">Operacja</span><span class="sxs-lookup"><span data-stu-id="a4556-134">Operation</span></span>|<span data-ttu-id="a4556-135">Złożoność</span><span class="sxs-lookup"><span data-stu-id="a4556-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="a4556-136">Ze względu na tę reprezentację mieszaną, `ReadOnlySequence<T>` uwidacznia indeksy jako `SequencePosition` zamiast liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="a4556-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="a4556-137">Odp `SequencePosition` .:</span><span class="sxs-lookup"><span data-stu-id="a4556-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="a4556-138">Jest wartością nieprzezroczystą, która reprezentuje indeks w `ReadOnlySequence<T>` skąd pochodzi.</span><span class="sxs-lookup"><span data-stu-id="a4556-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="a4556-139">Składa się z dwóch części, liczby całkowitej i obiektu.</span><span class="sxs-lookup"><span data-stu-id="a4556-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="a4556-140">Co reprezentują te dwie wartości są powiązane z implementacją programu `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="a4556-141">Uzyskiwanie dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="a4556-141">Access data</span></span>

<span data-ttu-id="a4556-142">`ReadOnlySequence<T>`Uwidacznia dane jako wyliczalne `ReadOnlyMemory<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="a4556-143">Wyliczanie poszczególnych segmentów można wykonać przy użyciu podstawowej instrukcji foreach:</span><span class="sxs-lookup"><span data-stu-id="a4556-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="a4556-144">Poprzednia Metoda przeszukuje poszczególne segmenty w określonym bajcie.</span><span class="sxs-lookup"><span data-stu-id="a4556-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="a4556-145">Jeśli chcesz śledzić poszczególne segmenty `SequencePosition` , <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> jest to bardziej odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="a4556-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="a4556-146">Następny przykład zmienia poprzedni kod, aby zwrócić zamiast liczby `SequencePosition` całkowitej.</span><span class="sxs-lookup"><span data-stu-id="a4556-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="a4556-147">Zwracanym `SequencePosition` korzyścią może być umożliwienie obiektowi wywołującemu uniknięcie drugiego skanowania w celu uzyskania danych w określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="a4556-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="a4556-148">Kombinacja `SequencePosition` i `TryGet` działa jak moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="a4556-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="a4556-149">Pole pozycja jest modyfikowane na początku każdej iteracji, aby można było rozpocząć każdy segment w obrębie `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="a4556-150">Poprzednia metoda istnieje jako metoda rozszerzająca `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="a4556-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A>może służyć do uproszczenia poprzedniego kodu:</span><span class="sxs-lookup"><span data-stu-id="a4556-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="a4556-152">Przetwarzanie ReadOnlySequence \< T\></span><span class="sxs-lookup"><span data-stu-id="a4556-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="a4556-153">Przetwarzanie a `ReadOnlySequence<T>` może być trudne, ponieważ dane mogą być podzielone między wiele segmentów w ramach sekwencji.</span><span class="sxs-lookup"><span data-stu-id="a4556-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="a4556-154">Aby uzyskać najlepszą wydajność, Podziel kod na dwie ścieżki:</span><span class="sxs-lookup"><span data-stu-id="a4556-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="a4556-155">Szybka ścieżka, która zajmuje się pojedynczym segmentem przypadku.</span><span class="sxs-lookup"><span data-stu-id="a4556-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="a4556-156">Powolna ścieżka, która zajmuje się rozbiciem danych między segmentami.</span><span class="sxs-lookup"><span data-stu-id="a4556-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="a4556-157">Istnieje kilka metod, których można użyć do przetwarzania danych w sekwencjach wielosegmentowych:</span><span class="sxs-lookup"><span data-stu-id="a4556-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="a4556-158">Użyj [`SequenceReader<T>`](#sequencereadert) .</span><span class="sxs-lookup"><span data-stu-id="a4556-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="a4556-159">Przeanalizuj segment danych przez segment, śledząc `SequencePosition` przeanalizowany indeks i.</span><span class="sxs-lookup"><span data-stu-id="a4556-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="a4556-160">Pozwala to uniknąć niepotrzebnych alokacji, ale może być niewydajne, szczególnie w przypadku małych buforów.</span><span class="sxs-lookup"><span data-stu-id="a4556-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="a4556-161">Skopiuj `ReadOnlySequence<T>` do tabeli ciągłej i Traktuj ją jak pojedynczy bufor:</span><span class="sxs-lookup"><span data-stu-id="a4556-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="a4556-162">Jeśli rozmiar `ReadOnlySequence<T>` jest mały, może być uzasadnione, aby skopiować dane do buforu przydzielonego przez stos przy użyciu operatora [stackalloc](../../csharp/language-reference/operators/stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="a4556-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="a4556-163">Skopiuj do `ReadOnlySequence<T>` tablicy w puli za pomocą polecenia <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a4556-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="a4556-164">Użyj witryny [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span><span class="sxs-lookup"><span data-stu-id="a4556-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="a4556-165">Nie jest to zalecane w przypadku ścieżek grzewczych, ponieważ przydziela nowe `T[]` na stosie.</span><span class="sxs-lookup"><span data-stu-id="a4556-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="a4556-166">W poniższych przykładach przedstawiono niektóre typowe przypadki przetwarzania `ReadOnlySequence<byte>` :</span><span class="sxs-lookup"><span data-stu-id="a4556-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="a4556-167">Przetwarzanie danych binarnych</span><span class="sxs-lookup"><span data-stu-id="a4556-167">Process binary data</span></span>

<span data-ttu-id="a4556-168">Poniższy przykład analizuje długość 4-bajtową liczby całkowitej big-endian od początku `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="a4556-169">Przetwarzanie danych tekstowych</span><span class="sxs-lookup"><span data-stu-id="a4556-169">Process text data</span></span>

<span data-ttu-id="a4556-170">Poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="a4556-170">The following example:</span></span>

- <span data-ttu-id="a4556-171">Znajduje pierwszy nowy wiersz ( `\r\n` ) w `ReadOnlySequence<byte>` i zwraca go za pośrednictwem parametru out "line".</span><span class="sxs-lookup"><span data-stu-id="a4556-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="a4556-172">Przycina ten wiersz, z wyłączeniem `\r\n` z bufora wejściowego.</span><span class="sxs-lookup"><span data-stu-id="a4556-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="a4556-173">Puste segmenty</span><span class="sxs-lookup"><span data-stu-id="a4556-173">Empty segments</span></span>

<span data-ttu-id="a4556-174">Prawidłowe jest przechowywanie pustych segmentów wewnątrz `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="a4556-175">Puste segmenty mogą wystąpić podczas jawnego wyliczania segmentów:</span><span class="sxs-lookup"><span data-stu-id="a4556-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="a4556-176">Poprzedni kod tworzy `ReadOnlySequence<byte>` z pustymi segmentami i pokazuje, jak te puste segmenty wpływają na różne interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="a4556-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="a4556-177">`ReadOnlySequence<T>.Slice`po `SequencePosition` wskazaniu pustego segmentu zachowuje ten segment.</span><span class="sxs-lookup"><span data-stu-id="a4556-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="a4556-178">`ReadOnlySequence<T>.Slice`Dzięki liczbie całkowitej pomija puste segmenty.</span><span class="sxs-lookup"><span data-stu-id="a4556-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="a4556-179">Wyliczenie `ReadOnlySequence<T>` wylicza puste segmenty.</span><span class="sxs-lookup"><span data-stu-id="a4556-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="a4556-180">Potencjalne problemy z ReadOnlySequence \< T> i SequencePosition</span><span class="sxs-lookup"><span data-stu-id="a4556-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="a4556-181">Istnieje kilka nietypowych rezultatów podczas pracy z programem a a `ReadOnlySequence<T>` / `SequencePosition` `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int` :</span><span class="sxs-lookup"><span data-stu-id="a4556-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="a4556-182">`SequencePosition`jest znacznikiem położenia dla konkretnej `ReadOnlySequence<T>` , a nie położenia bezwzględnego.</span><span class="sxs-lookup"><span data-stu-id="a4556-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="a4556-183">Ponieważ jest względem określonego `ReadOnlySequence<T>` , nie ma znaczenia, jeśli jest używany poza miejscem, w `ReadOnlySequence<T>` którym pochodzi.</span><span class="sxs-lookup"><span data-stu-id="a4556-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="a4556-184">Nie można wykonać operacji arytmetycznej `SequencePosition` bez `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="a4556-185">Oznacza to, że `position++` są zapisywane podstawowe elementy `ReadOnlySequence<T>.GetPosition(position, 1)` .</span><span class="sxs-lookup"><span data-stu-id="a4556-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="a4556-186">`GetPosition(long)`nie **obsługuje indeksów** ujemnych.</span><span class="sxs-lookup"><span data-stu-id="a4556-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="a4556-187">Oznacza to, że nie można pobrać drugiego do ostatniego znaku bez podzielenia wszystkich segmentów.</span><span class="sxs-lookup"><span data-stu-id="a4556-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="a4556-188">`SequencePosition`Nie można porównać dwóch, co utrudnia:</span><span class="sxs-lookup"><span data-stu-id="a4556-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="a4556-189">Sprawdź, czy jedna pozycja jest większa lub mniejsza od innej pozycji.</span><span class="sxs-lookup"><span data-stu-id="a4556-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="a4556-190">Napisz niektóre algorytmy analizy.</span><span class="sxs-lookup"><span data-stu-id="a4556-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="a4556-191">`ReadOnlySequence<T>`jest większy niż odwołanie do obiektu i powinno być [przesyłane przez lub](../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../csharp/language-reference/keywords/ref.md) , tam gdzie to możliwe.</span><span class="sxs-lookup"><span data-stu-id="a4556-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="a4556-192">Przekazywanie `ReadOnlySequence<T>` przez `in` lub `ref` zmniejsza liczbę kopii [struktury](../../csharp/language-reference/builtin-types/struct.md).</span><span class="sxs-lookup"><span data-stu-id="a4556-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="a4556-193">Puste segmenty:</span><span class="sxs-lookup"><span data-stu-id="a4556-193">Empty segments:</span></span>
  - <span data-ttu-id="a4556-194">Są prawidłowe w `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="a4556-195">Może pojawić się podczas iteracji przy użyciu `ReadOnlySequence<T>.TryGet` metody.</span><span class="sxs-lookup"><span data-stu-id="a4556-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="a4556-196">Może wydawać się dzielenie sekwencji przy użyciu `ReadOnlySequence<T>.Slice()` metody z `SequencePosition` obiektami.</span><span class="sxs-lookup"><span data-stu-id="a4556-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="a4556-197">SequenceReader \< T\></span><span class="sxs-lookup"><span data-stu-id="a4556-197">SequenceReader\<T\></span></span>

<span data-ttu-id="a4556-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="a4556-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="a4556-199">Jest nowym typem wprowadzonym w środowisku .NET Core 3,0, aby uprościć przetwarzanie `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="a4556-200">Łączy różnice między pojedynczym segmentem `ReadOnlySequence<T>` a wielosegmentem `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="a4556-201">Oferuje pomocnikom do odczytywania danych binarnych i tekstowych ( `byte` oraz `char` ), które mogą lub nie mogą być dzielone między segmentami.</span><span class="sxs-lookup"><span data-stu-id="a4556-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="a4556-202">Istnieją wbudowane metody umożliwiające przetworzenie zarówno danych binarnych, jak i rozdzielonych.</span><span class="sxs-lookup"><span data-stu-id="a4556-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="a4556-203">W poniższej sekcji pokazano, jak wyglądają te same metody z `SequenceReader<T>` :</span><span class="sxs-lookup"><span data-stu-id="a4556-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="a4556-204">Uzyskiwanie dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="a4556-204">Access data</span></span>

<span data-ttu-id="a4556-205">`SequenceReader<T>`ma metody do bezpośredniego wyliczania danych wewnątrz `ReadOnlySequence<T>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="a4556-206">Poniższy kod jest przykładem przetwarzania a `ReadOnlySequence<byte>` `byte` w czasie:</span><span class="sxs-lookup"><span data-stu-id="a4556-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="a4556-207">`CurrentSpan`Uwidacznia bieżący segment `Span` , który jest podobny do tego, co zostało wykonane w metodzie ręcznie.</span><span class="sxs-lookup"><span data-stu-id="a4556-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="a4556-208">Użyj pozycji</span><span class="sxs-lookup"><span data-stu-id="a4556-208">Use position</span></span>

<span data-ttu-id="a4556-209">Poniższy kod stanowi przykład implementacji `FindIndexOf` użycia `SequenceReader<T>` :</span><span class="sxs-lookup"><span data-stu-id="a4556-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="a4556-210">Przetwarzanie danych binarnych</span><span class="sxs-lookup"><span data-stu-id="a4556-210">Process binary data</span></span>

<span data-ttu-id="a4556-211">Poniższy przykład analizuje długość 4-bajtową liczby całkowitej big-endian od początku `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="a4556-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="a4556-212">Przetwarzanie danych tekstowych</span><span class="sxs-lookup"><span data-stu-id="a4556-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="a4556-213">\< \> Typowe problemy SequenceReader T</span><span class="sxs-lookup"><span data-stu-id="a4556-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="a4556-214">Ponieważ `SequenceReader<T>` jest strukturą modyfikowalną, powinna być zawsze przenoszona przez [odwołanie](../../csharp/language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="a4556-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="a4556-215">`SequenceReader<T>`jest [strukturą ref](../../csharp/language-reference/builtin-types/struct.md#ref-struct) , więc może być używana tylko w metodach synchronicznych i nie może być przechowywana w polach.</span><span class="sxs-lookup"><span data-stu-id="a4556-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/builtin-types/struct.md#ref-struct) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="a4556-216">Aby uzyskać więcej informacji, zobacz [Zapisywanie bezpiecznego i wydajnego kodu w języku C#](../../csharp/write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="a4556-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="a4556-217">`SequenceReader<T>`jest zoptymalizowany pod kątem korzystania z programu jako czytnika tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="a4556-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="a4556-218">`Rewind`jest przeznaczony dla małych kopii zapasowych, których nie można rozwiązać przy użyciu innych `Read` , `Peek` i `IsNext` interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="a4556-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
