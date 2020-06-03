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
# <a name="work-with-buffers-in-net"></a>Korzystanie z buforów w środowisku .NET

Ten artykuł zawiera omówienie typów, które ułatwiają odczytywanie danych z różnych buforów. Są one używane głównie do obsługi <xref:System.IO.Pipelines.PipeReader> obiektów.

## <a name="ibufferwritert"></a>IBufferWriter \< T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>jest kontraktem synchronicznie zbuforowanego zapisu. Na najniższym poziomie interfejs:

- Jest podstawowa i nie jest trudna do użycia.
- Zezwala na dostęp do <xref:System.Memory%601> lub <xref:System.Span%601> . `Memory<T>`Lub `Span<T>` można pisać do i można określić liczbę elementów, które `T` zostały zapisaniu.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

Poprzednia metoda:

- Żąda bufora co najmniej 5 bajtów z `IBufferWriter<byte>` polecenia using `GetSpan(5)` .
- Zapisuje bajty dla ciągu ASCII "Hello" jako zwrócone `Span<byte>` .
- Wywołania <xref:System.Buffers.IBufferWriter%601> wskazujące, ile bajtów Zapisano w buforze.

Ta metoda pisania używa `Memory<T>` / `Span<T>` buforu dostarczonego przez `IBufferWriter<T>` . Alternatywnie <xref:System.Buffers.BuffersExtensions.Write%2A> można użyć metody rozszerzenia, aby skopiować istniejący bufor do `IBufferWriter<T>` . `Write`wykonuje `GetSpan` / `Advance` odpowiednie działania, aby nie trzeba było wywoływać `Advance` po zapisaniu:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601>jest implementacją, `IBufferWriter<T>` której magazyn zapasowy jest pojedynczą ciągłą tablicą.

### <a name="ibufferwriter-common-problems"></a>IBufferWriter typowe problemy

- `GetSpan`i `GetMemory` Zwróć bufor z co najmniej żądaną ilością pamięci. Nie zakładaj dokładnie rozmiarów buforów.
- Nie ma gwarancji, że kolejne wywołania będą zwracać ten sam bufor lub bufor o takim samym rozmiarze.
- Należy zażądać nowego buforu po wywołaniu `Advance` , aby kontynuować zapisywanie większej ilości danych. Wcześniej uzyskany bufor nie może zostać zapisany do po `Advance` wywołaniu.

## <a name="readonlysequencet"></a>ReadOnlySequence \< T\>

![ReadOnlySequence pokazujący pamięć w potoku i poniżej tej pozycji sekwencji pamięci tylko do odczytu](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601>jest strukturą, która może reprezentować ciągłą lub nieciągłą sekwencję `T` . Można ją skonstruować z:

1. Element `T[]`.
1. Element `ReadOnlyMemory<T>`.
1. Para węzła połączonej listy <xref:System.Buffers.ReadOnlySequenceSegment%601> i indeksu do reprezentowania pozycji początkowej i końcowej sekwencji.

Trzecia reprezentacja jest najbardziej interesująca, ponieważ ma wpływ na wydajność różnych operacji na `ReadOnlySequence<T>` :

|Reprezentowana|Operacja|Złożoność|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

Ze względu na tę reprezentację mieszaną, `ReadOnlySequence<T>` uwidacznia indeksy jako `SequencePosition` zamiast liczby całkowitej. Odp `SequencePosition` .:

- Jest wartością nieprzezroczystą, która reprezentuje indeks w `ReadOnlySequence<T>` skąd pochodzi.
- Składa się z dwóch części, liczby całkowitej i obiektu. Co reprezentują te dwie wartości są powiązane z implementacją programu `ReadOnlySequence<T>` .

### <a name="access-data"></a>Uzyskiwanie dostępu do danych

`ReadOnlySequence<T>`Uwidacznia dane jako wyliczalne `ReadOnlyMemory<T>` . Wyliczanie poszczególnych segmentów można wykonać przy użyciu podstawowej instrukcji foreach:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

Poprzednia Metoda przeszukuje poszczególne segmenty w określonym bajcie. Jeśli chcesz śledzić poszczególne segmenty `SequencePosition` , <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> jest to bardziej odpowiednie. Następny przykład zmienia poprzedni kod, aby zwrócić zamiast liczby `SequencePosition` całkowitej. Zwracanym `SequencePosition` korzyścią może być umożliwienie obiektowi wywołującemu uniknięcie drugiego skanowania w celu uzyskania danych w określonym indeksie.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

Kombinacja `SequencePosition` i `TryGet` działa jak moduł wyliczający. Pole pozycja jest modyfikowane na początku każdej iteracji, aby można było rozpocząć każdy segment w obrębie `ReadOnlySequence<T>` .

Poprzednia metoda istnieje jako metoda rozszerzająca `ReadOnlySequence<T>` . <xref:System.Buffers.BuffersExtensions.PositionOf%2A>może służyć do uproszczenia poprzedniego kodu:

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>Przetwarzanie ReadOnlySequence \< T\>

Przetwarzanie a `ReadOnlySequence<T>` może być trudne, ponieważ dane mogą być podzielone między wiele segmentów w ramach sekwencji. Aby uzyskać najlepszą wydajność, Podziel kod na dwie ścieżki:

- Szybka ścieżka, która zajmuje się pojedynczym segmentem przypadku.
- Powolna ścieżka, która zajmuje się rozbiciem danych między segmentami.

Istnieje kilka metod, których można użyć do przetwarzania danych w sekwencjach wielosegmentowych:

- Użyj [`SequenceReader<T>`](#sequencereadert) .
- Przeanalizuj segment danych przez segment, śledząc `SequencePosition` przeanalizowany indeks i. Pozwala to uniknąć niepotrzebnych alokacji, ale może być niewydajne, szczególnie w przypadku małych buforów.
- Skopiuj `ReadOnlySequence<T>` do tabeli ciągłej i Traktuj ją jak pojedynczy bufor:
  - Jeśli rozmiar `ReadOnlySequence<T>` jest mały, może być uzasadnione, aby skopiować dane do buforu przydzielonego przez stos przy użyciu operatora [stackalloc](../../csharp/language-reference/operators/stackalloc.md) .
  - Skopiuj do `ReadOnlySequence<T>` tablicy w puli za pomocą polecenia <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType> .
  - Użyj witryny [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A). Nie jest to zalecane w przypadku ścieżek grzewczych, ponieważ przydziela nowe `T[]` na stosie.

W poniższych przykładach przedstawiono niektóre typowe przypadki przetwarzania `ReadOnlySequence<byte>` :

##### <a name="process-binary-data"></a>Przetwarzanie danych binarnych

Poniższy przykład analizuje długość 4-bajtową liczby całkowitej big-endian od początku `ReadOnlySequence<byte>` .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Przetwarzanie danych tekstowych

Poniższy przykład:

- Znajduje pierwszy nowy wiersz ( `\r\n` ) w `ReadOnlySequence<byte>` i zwraca go za pośrednictwem parametru out "line".
- Przycina ten wiersz, z wyłączeniem `\r\n` z bufora wejściowego.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Puste segmenty

Prawidłowe jest przechowywanie pustych segmentów wewnątrz `ReadOnlySequence<T>` . Puste segmenty mogą wystąpić podczas jawnego wyliczania segmentów:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

Poprzedni kod tworzy `ReadOnlySequence<byte>` z pustymi segmentami i pokazuje, jak te puste segmenty wpływają na różne interfejsy API:

- `ReadOnlySequence<T>.Slice`po `SequencePosition` wskazaniu pustego segmentu zachowuje ten segment.
- `ReadOnlySequence<T>.Slice`Dzięki liczbie całkowitej pomija puste segmenty.
- Wyliczenie `ReadOnlySequence<T>` wylicza puste segmenty.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>Potencjalne problemy z ReadOnlySequence \< T> i SequencePosition

Istnieje kilka nietypowych rezultatów podczas pracy z programem a a `ReadOnlySequence<T>` / `SequencePosition` `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int` :

- `SequencePosition`jest znacznikiem położenia dla konkretnej `ReadOnlySequence<T>` , a nie położenia bezwzględnego. Ponieważ jest względem określonego `ReadOnlySequence<T>` , nie ma znaczenia, jeśli jest używany poza miejscem, w `ReadOnlySequence<T>` którym pochodzi.
- Nie można wykonać operacji arytmetycznej `SequencePosition` bez `ReadOnlySequence<T>` . Oznacza to, że `position++` są zapisywane podstawowe elementy `ReadOnlySequence<T>.GetPosition(position, 1)` .
- `GetPosition(long)`nie **obsługuje indeksów** ujemnych. Oznacza to, że nie można pobrać drugiego do ostatniego znaku bez podzielenia wszystkich segmentów.
- `SequencePosition`Nie można porównać dwóch, co utrudnia:
  - Sprawdź, czy jedna pozycja jest większa lub mniejsza od innej pozycji.
  - Napisz niektóre algorytmy analizy.
- `ReadOnlySequence<T>`jest większy niż odwołanie do obiektu i powinno być [przesyłane przez lub](../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../csharp/language-reference/keywords/ref.md) , tam gdzie to możliwe. Przekazywanie `ReadOnlySequence<T>` przez `in` lub `ref` zmniejsza liczbę kopii [struktury](../../csharp/language-reference/builtin-types/struct.md).
- Puste segmenty:
  - Są prawidłowe w `ReadOnlySequence<T>` .
  - Może pojawić się podczas iteracji przy użyciu `ReadOnlySequence<T>.TryGet` metody.
  - Może wydawać się dzielenie sekwencji przy użyciu `ReadOnlySequence<T>.Slice()` metody z `SequencePosition` obiektami.

## <a name="sequencereadert"></a>SequenceReader \< T\>

<xref:System.Buffers.SequenceReader%601>:

- Jest nowym typem wprowadzonym w środowisku .NET Core 3,0, aby uprościć przetwarzanie `ReadOnlySequence<T>` .
- Łączy różnice między pojedynczym segmentem `ReadOnlySequence<T>` a wielosegmentem `ReadOnlySequence<T>` .
- Oferuje pomocnikom do odczytywania danych binarnych i tekstowych ( `byte` oraz `char` ), które mogą lub nie mogą być dzielone między segmentami.

Istnieją wbudowane metody umożliwiające przetworzenie zarówno danych binarnych, jak i rozdzielonych. W poniższej sekcji pokazano, jak wyglądają te same metody z `SequenceReader<T>` :

### <a name="access-data"></a>Uzyskiwanie dostępu do danych

`SequenceReader<T>`ma metody do bezpośredniego wyliczania danych wewnątrz `ReadOnlySequence<T>` . Poniższy kod jest przykładem przetwarzania a `ReadOnlySequence<byte>` `byte` w czasie:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

`CurrentSpan`Uwidacznia bieżący segment `Span` , który jest podobny do tego, co zostało wykonane w metodzie ręcznie.

### <a name="use-position"></a>Użyj pozycji

Poniższy kod stanowi przykład implementacji `FindIndexOf` użycia `SequenceReader<T>` :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>Przetwarzanie danych binarnych

Poniższy przykład analizuje długość 4-bajtową liczby całkowitej big-endian od początku `ReadOnlySequence<byte>` .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Przetwarzanie danych tekstowych

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>\< \> Typowe problemy SequenceReader T

- Ponieważ `SequenceReader<T>` jest strukturą modyfikowalną, powinna być zawsze przenoszona przez [odwołanie](../../csharp/language-reference/keywords/ref.md).
- `SequenceReader<T>`jest [strukturą ref](../../csharp/language-reference/builtin-types/struct.md#ref-struct) , więc może być używana tylko w metodach synchronicznych i nie może być przechowywana w polach. Aby uzyskać więcej informacji, zobacz [Zapisywanie bezpiecznego i wydajnego kodu w języku C#](../../csharp/write-safe-efficient-code.md).
- `SequenceReader<T>`jest zoptymalizowany pod kątem korzystania z programu jako czytnika tylko do przodu. `Rewind`jest przeznaczony dla małych kopii zapasowych, których nie można rozwiązać przy użyciu innych `Read` , `Peek` i `IsNext` interfejsów API.
