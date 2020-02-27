---
title: System. buffers — .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 5b98e3e2d41d3e49a28db6393f15f13c3579b06d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628081"
---
# <a name="work-with-buffers-in-net"></a>Korzystanie z buforów w środowisku .NET

Ten artykuł zawiera omówienie typów, które ułatwiają odczytywanie danych z różnych buforów. Są one używane głównie do obsługi obiektów <xref:System.IO.Pipelines.PipeReader>.

## <a name="ibufferwritert"></a>IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> jest kontraktem synchronicznie zbuforowanego zapisu. Na najniższym poziomie interfejs:

- Jest podstawowa i nie jest trudna do użycia.
- Zezwala na dostęp do <xref:System.Memory%601> lub <xref:System.Span%601>. Do `Memory<T>` lub `Span<T>` można pisać i można określić, ile elementów `T` zostało zapisanych.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

Poprzednia metoda:

- Żąda bufora co najmniej 5 bajtów z `IBufferWriter<byte>` przy użyciu `GetSpan(5)`.
- Zapisuje bajty dla ciągu ASCII "Hello" w zwracanej `Span<byte>`.
- Wywołuje <xref:System.Buffers.IBufferWriter%601>, aby wskazać, ile bajtów Zapisano w buforze.

Ta metoda pisania używa `Memory<T>`/`Span<T>` buforu dostarczonego przez `IBufferWriter<T>`. Alternatywnie można skopiować istniejący bufor do `IBufferWriter<T>`za pomocą metody rozszerzenia <xref:System.Buffers.BuffersExtensions.Write%2A>. `Write` wykonuje działania wywołujące `GetSpan`/`Advance` zgodnie z potrzebami, więc nie ma potrzeby wywoływania `Advance` po zapisaniu:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601> jest implementacją `IBufferWriter<T>` której magazyn zapasowy jest pojedynczą ciągłą tablicą.

### <a name="ibufferwriter-common-problems"></a>IBufferWriter typowe problemy

- `GetSpan` i `GetMemory` zwracają bufor z co najmniej żądaną ilością pamięci. Nie zakładaj dokładnie rozmiarów buforów.
- Nie ma gwarancji, że kolejne wywołania będą zwracać ten sam bufor lub bufor o takim samym rozmiarze.
- Należy zażądać nowego buforu po wywołaniu `Advance`, aby kontynuować zapisywanie większej ilości danych. Nie można zapisać wcześniej uzyskanego buforu po wywołaniu `Advance`.

## <a name="readonlysequencet"></a>ReadOnlySequence\<T\>

![ReadOnlySequence pokazujący pamięć w potoku i poniżej tej pozycji sekwencji pamięci tylko do odczytu](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601> to struktura, która może reprezentować ciągłą lub nieciągłą sekwencję `T`. Można ją skonstruować z:

1. Element `T[]`.
1. Element `ReadOnlyMemory<T>`.
1. Para węzła połączonej listy <xref:System.Buffers.ReadOnlySequenceSegment%601> i indeks reprezentujący początkową i końcową pozycję sekwencji.

Trzecia reprezentacja jest najbardziej interesująca, ponieważ ma wpływ na wydajność różnych operacji na `ReadOnlySequence<T>`:

|Reprezentowana|Operacja|Stopień złożoności|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

Ze względu na tę reprezentację mieszaną `ReadOnlySequence<T>` uwidacznia indeksy jako `SequencePosition` zamiast liczby całkowitej. `SequencePosition`:

- Jest wartością nieprzezroczystą, która reprezentuje indeks do `ReadOnlySequence<T>`, skąd pochodzi.
- Składa się z dwóch części, liczby całkowitej i obiektu. Co reprezentują te dwie wartości są powiązane z implementacją `ReadOnlySequence<T>`.

### <a name="access-data"></a>Uzyskiwanie dostępu do danych

`ReadOnlySequence<T>` uwidacznia dane jako wyliczalne `ReadOnlyMemory<T>`. Wyliczanie poszczególnych segmentów można wykonać przy użyciu podstawowej instrukcji foreach:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

Poprzednia Metoda przeszukuje poszczególne segmenty w określonym bajcie. Jeśli chcesz śledzić `SequencePosition`poszczególnych segmentów, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> być bardziej odpowiednie. Następny przykład zmienia poprzedni kod, aby zwrócić `SequencePosition` zamiast liczby całkowitej. Zwrócenie `SequencePosition` umożliwia wywołującemu uniknięcie drugiego skanowania w celu uzyskania danych w określonym indeksie.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

Kombinacja `SequencePosition` i `TryGet` działa jak moduł wyliczający. Pole pozycja jest modyfikowane na początku każdej iteracji, aby można było rozpocząć każdy segment w `ReadOnlySequence<T>`.

Poprzednia metoda istnieje jako metoda rozszerzająca na `ReadOnlySequence<T>`. <xref:System.Buffers.BuffersExtensions.PositionOf%2A> można użyć, aby uprościć poprzedni kod:

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>Przetwarzanie ReadOnlySequence\<T\>

Przetwarzanie `ReadOnlySequence<T>` może być trudne, ponieważ dane mogą być podzielone między wiele segmentów w ramach sekwencji. Aby uzyskać najlepszą wydajność, Podziel kod na dwie ścieżki:

- Szybka ścieżka, która zajmuje się pojedynczym segmentem przypadku.
- Powolna ścieżka, która zajmuje się rozbiciem danych między segmentami.

Istnieje kilka metod, których można użyć do przetwarzania danych w sekwencjach wielosegmentowych:

- Użyj [`SequenceReader<T>`](#sequencereadert).
- Przeanalizuj segment danych według segmentu, śledząc `SequencePosition` i indeks w ramach przeanalizowanego segmentu. Pozwala to uniknąć niepotrzebnych alokacji, ale może być niewydajne, szczególnie w przypadku małych buforów.
- Skopiuj `ReadOnlySequence<T>` do tabeli ciągłej i Traktuj ją jak pojedynczy bufor:
  - Jeśli rozmiar `ReadOnlySequence<T>` jest mały, może być uzasadnione, aby skopiować dane do buforu przydzielonego przez stos przy użyciu operatora [stackalloc](../../csharp/language-reference/operators/stackalloc.md) .
  - Skopiuj `ReadOnlySequence<T>` do tablicy w puli przy użyciu <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.
  - Użyj witryny [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A). Nie jest to zalecane w przypadku ścieżek gorąca, ponieważ przypisuje nowe `T[]` na stosie.

W poniższych przykładach przedstawiono niektóre typowe przypadki przetwarzania `ReadOnlySequence<byte>`:

##### <a name="process-binary-data"></a>Przetwarzanie danych binarnych

Poniższy przykład analizuje długość 4-bajtową liczby całkowitej big-endian od początku `ReadOnlySequence<byte>`.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Przetwarzanie danych tekstowych

Poniższy przykład:

- Znajduje pierwszy nowy wiersz (`\r\n`) w `ReadOnlySequence<byte>` i zwraca go za pośrednictwem parametru out "line".
- Przycina ten wiersz, wykluczając `\r\n` z buforu wejściowego.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Puste segmenty

Prawidłowe jest przechowywanie pustych segmentów wewnątrz `ReadOnlySequence<T>`. Puste segmenty mogą wystąpić podczas jawnego wyliczania segmentów:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

Poprzedni kod tworzy `ReadOnlySequence<byte>` z pustymi segmentami i pokazuje, jak te puste segmenty wpływają na różne interfejsy API:

- `ReadOnlySequence<T>.Slice` z `SequencePosition` wskazujący pusty segment zachowuje ten segment.
- `ReadOnlySequence<T>.Slice` z liczbą całkowitą pomija puste segmenty.
- Wyliczenie `ReadOnlySequence<T>` wylicza puste segmenty.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>Potencjalne problemy z ReadOnlySequence\<T > i SequencePosition

Istnieje kilka nietypowych rezultatów podczas pracy z `ReadOnlySequence<T>`/`SequencePosition` a normalny `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:

- `SequencePosition` jest znacznikiem położenia dla określonego `ReadOnlySequence<T>`, a nie na pozycji absolutnej. Ponieważ jest ono powiązane z konkretną `ReadOnlySequence<T>`, nie ma znaczenia, jeśli jest używane poza `ReadOnlySequence<T>`, z którego pochodzi.
- Nie można wykonać operacji arytmetycznej na `SequencePosition` bez `ReadOnlySequence<T>`. Oznacza to, że `position++` jest zapisywana `ReadOnlySequence<T>.GetPosition(position, 1)`.
- `GetPosition(long)` nie **obsługuje indeksów** ujemnych. Oznacza to, że nie można pobrać drugiego do ostatniego znaku bez podzielenia wszystkich segmentów.
- Nie można porównać dwóch `SequencePosition`, co utrudnia:
  - Sprawdź, czy jedna pozycja jest większa lub mniejsza od innej pozycji.
  - Napisz niektóre algorytmy analizy.
- `ReadOnlySequence<T>` jest większe niż odwołanie do obiektu i powinno być przesyłane przez [lub](../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../csharp/language-reference/keywords/ref.md) , gdzie to możliwe. Przekazywanie `ReadOnlySequence<T>` przez `in` lub `ref` zmniejsza liczbę kopii [struktury](../../csharp/language-reference/builtin-types/struct.md).
- Puste segmenty:
  - Są prawidłowe w ramach `ReadOnlySequence<T>`.
  - Może być wyświetlany podczas iteracji przy użyciu metody `ReadOnlySequence<T>.TryGet`.
  - Może wydawać się dzielenie sekwencji przy użyciu metody `ReadOnlySequence<T>.Slice()` z obiektami `SequencePosition`.

## <a name="sequencereadert"></a>SequenceReader\<T\>

<xref:System.Buffers.SequenceReader%601>:

- Jest nowym typem wprowadzonym w środowisku .NET Core 3,0, aby uprościć przetwarzanie `ReadOnlySequence<T>`.
- Łączy różnice między pojedynczym segmentem `ReadOnlySequence<T>` i `ReadOnlySequence<T>`wiele segmentów.
- Oferuje pomocnikom do odczytywania danych binarnych i tekstowych (`byte` i `char`), które mogą lub nie mogą być dzielone między segmentami.

Istnieją wbudowane metody umożliwiające przetworzenie zarówno danych binarnych, jak i rozdzielonych. W poniższej sekcji pokazano, jak wyglądają te same metody, jak w przypadku `SequenceReader<T>`:

### <a name="access-data"></a>Uzyskiwanie dostępu do danych

`SequenceReader<T>` ma metody wyliczania danych wewnątrz `ReadOnlySequence<T>` bezpośrednio. Poniższy kod stanowi przykład przetwarzania `ReadOnlySequence<byte>` `byte` w danym momencie:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

`CurrentSpan` uwidacznia `Span`bieżącego segmentu, który jest podobny do tego, co zostało wykonane w metodzie ręcznie.

### <a name="use-position"></a>Użyj pozycji

Poniższy kod stanowi przykład implementacji `FindIndexOf` przy użyciu `SequenceReader<T>`:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>Przetwarzanie danych binarnych

Poniższy przykład analizuje długość 4-bajtową liczby całkowitej big-endian od początku `ReadOnlySequence<byte>`.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Przetwarzanie danych tekstowych

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SequenceReader\<T\> typowe problemy

- Ponieważ `SequenceReader<T>` jest strukturą modyfikowalną, powinna być zawsze przenoszona przez [odwołanie](../../csharp/language-reference/keywords/ref.md).
- `SequenceReader<T>` to [Struktura ref](../../csharp/language-reference/keywords/ref.md#ref-struct-types) , dlatego może być używana tylko w metodach synchronicznych i nie może być przechowywana w polach. Aby uzyskać więcej informacji, zobacz [Zapisywanie bezpiecznego i C# wydajnego kodu](../../csharp/write-safe-efficient-code.md).
- `SequenceReader<T>` jest zoptymalizowany pod kątem korzystania z programu jako czytnika tylko do przodu. `Rewind` jest przeznaczony dla małych kopii zapasowych, których nie można rozwiązać przy użyciu innych interfejsów API `Read`, `Peek`i `IsNext`.
