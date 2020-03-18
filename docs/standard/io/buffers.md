---
title: System.Buffers - .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: f939164cd56b2fb2feeeb171236b0e1171327e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160121"
---
# <a name="work-with-buffers-in-net"></a>Praca z buforami w .NET

Ten artykuł zawiera omówienie typów, które pomagają odczytywać dane, które działa w wielu buforach. Są one używane głównie <xref:System.IO.Pipelines.PipeReader> do obsługi obiektów.

## <a name="ibufferwritert"></a>Moduł IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>jest kontraktem na synchroniczne buforowane pisanie. Na najniższym poziomie interfejs:

- Jest podstawowy i nie jest trudny w użyciu.
- Umożliwia dostęp <xref:System.Memory%601> do <xref:System.Span%601>programu lub . Lub `Memory<T>` `Span<T>` mogą być zapisywane i można `T` określić, ile elementów zostały napisane.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

Powyższa metoda:

- Żąda buforu o co najmniej 5 `IBufferWriter<byte>` `GetSpan(5)`bajtach z using .
- Zapisuje bajty dla ciągu ASCII "Hello" do `Span<byte>`zwróconego .
- Wywołania <xref:System.Buffers.IBufferWriter%601> wskazujące, ile bajtów zostało zapisanych w buforze.

Ta metoda zapisu `Memory<T>` / `Span<T>` używa buforu dostarczonego przez plik `IBufferWriter<T>`. Alternatywnie metoda <xref:System.Buffers.BuffersExtensions.Write%2A> rozszerzenia może służyć do kopiowania `IBufferWriter<T>`istniejącego buforu do pliku . `Write`wykonuje pracę wywoływania `GetSpan` / `Advance` w razie potrzeby, więc `Advance` nie ma potrzeby dzwonić po napisaniu:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601>jest implementacją, `IBufferWriter<T>` której magazyn zapasowy jest pojedynczą ciągłą tablicą.

### <a name="ibufferwriter-common-problems"></a>Typowe problemy programu IBufferWriter

- `GetSpan`i `GetMemory` zwrócić bufor z co najmniej żądaną ilością pamięci. Nie zakładaj dokładnych rozmiarów buforu.
- Nie ma żadnej gwarancji, że kolejne wywołania zwróci tego samego buforu lub buforu tego samego rozmiaru.
- Nowy bufor musi być wymagane `Advance` po wywołaniu, aby kontynuować zapisywanie większej ilości danych. Wcześniej nabytych bufornie nie `Advance` można zapisać po został wywołany.

## <a name="readonlysequencet"></a>Sekwencja\<tylko do odczytu T\>

![ReadOnlySequence pokazujący pamięć w potoku i poniżej tej pozycji sekwencji pamięci tylko do odczytu](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601>jest strukturą, która może reprezentować ciągłą lub nieciągłą sekwencję `T`. Może być zbudowany z:

1. Element `T[]`.
1. Element `ReadOnlyMemory<T>`.
1. Para połączonych węzeł <xref:System.Buffers.ReadOnlySequenceSegment%601> listy i indeks do reprezentowania pozycji początkowej i końcowej sekwencji.

Trzecia reprezentacja jest najciekawsza, ponieważ ma `ReadOnlySequence<T>`wpływ na wydajność różnych operacji na:

|Reprezentacja|Operacja|Złożoność|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

Z powodu tej reprezentacji mieszanej `ReadOnlySequence<T>` `SequencePosition` udostępnia indeksy jako zamiast liczby całkowitej. A: `SequencePosition`

- Jest wartością nieprzezroczystą, która reprezentuje `ReadOnlySequence<T>` indeks do miejsca jego pochodzenia.
- Składa się z dwóch części, liczby całkowitej i obiektu. Co te dwie wartości reprezentują są `ReadOnlySequence<T>`związane z realizacją .

### <a name="access-data"></a>Uzyskiwanie dostępu do danych

Udostępnia `ReadOnlySequence<T>` dane jako wyliczanie `ReadOnlyMemory<T>`. Wyliczanie każdego z segmentów można wykonać za pomocą podstawowego foreach:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

Powyższa metoda przeszukuje każdy segment w poszukiwaniu określonego bajtu. Jeśli chcesz śledzić każdego segmentu `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> jest bardziej odpowiednie. Następny przykład zmienia poprzedni kod, `SequencePosition` aby zwrócić zamiast liczby całkowitej. Zwracanie `SequencePosition` ma zaletę, umożliwiając obiektowi wywołującemu, aby uniknąć drugiego skanowania, aby uzyskać dane w określonym indeksie.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

Połączenie `SequencePosition` i `TryGet` działa jak wyliczacz. Pole position jest modyfikowane na początku każdej iteracji, która `ReadOnlySequence<T>`ma być początkiem każdego segmentu w ramach .

Poprzednia metoda istnieje jako metoda `ReadOnlySequence<T>`rozszerzenia na . <xref:System.Buffers.BuffersExtensions.PositionOf%2A>można użyć do uproszczenia poprzedniego kodu:

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>Przetwarzanie readonlysequence\<T\>

Przetwarzanie `ReadOnlySequence<T>` może być trudne, ponieważ dane mogą być podzielone na wiele segmentów w sekwencji. Aby uzyskać najlepszą wydajność, podziel kod na dwie ścieżki:

- Szybka ścieżka, która zajmuje się sprawą pojedynczego segmentu.
- Powolna ścieżka, która dotyczy danych podzielonych na segmenty.

Istnieje kilka metod, które mogą być używane do przetwarzania danych w sekwencjach wielosegmentowych:

- Użyj [`SequenceReader<T>`](#sequencereadert)pliku .
- Analizuj segment danych według segmentów, śledząc `SequencePosition` indeks i indeks w segmencie analizowanym. Pozwala to uniknąć niepotrzebnych przydziałów, ale może być nieefektywne, szczególnie w przypadku małych buforów.
- Skopiuj `ReadOnlySequence<T>` do ciągłej tablicy i traktować go jak pojedynczy bufor:
  - Jeśli rozmiar `ReadOnlySequence<T>` jest mały, może być uzasadnione, aby skopiować dane do buforu przydzielonego stosu przy użyciu operatora [stackalloc.](../../csharp/language-reference/operators/stackalloc.md)
  - Skopiuj `ReadOnlySequence<T>` do <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>tablicy w puli przy użyciu .
  - Użyj [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A). Nie jest to zalecane w gorących ścieżkach, ponieważ przydziela nowy `T[]` na stercie.

Poniższe przykłady pokazują niektóre typowe `ReadOnlySequence<byte>`przypadki przetwarzania:

##### <a name="process-binary-data"></a>Przetwarzanie danych binarnych

Poniższy przykład analizuje 4-bajtową długość całkowitą big-endian od `ReadOnlySequence<byte>`początku .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Przetwarzanie danych tekstowych

Poniższy przykład:

- Wyszukuje`\r\n`pierwszą `ReadOnlySequence<byte>` nową linię ( ) w i zwraca ją za pomocą out 'line' parametru.
- Przycina tę linię, wyłączając `\r\n` bufor wejściowy.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Puste segmenty

Ważne jest przechowywanie pustych segmentów `ReadOnlySequence<T>`wewnątrz pliku . Puste segmenty mogą wystąpić podczas jawnego wyliczania segmentów:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

Poprzedni kod tworzy `ReadOnlySequence<byte>` z pustymi segmentami i pokazuje, jak te puste segmenty wpływają na różne interfejsy API:

- `ReadOnlySequence<T>.Slice`z `SequencePosition` wskazywaniem pustego segmentu zachowuje ten segment.
- `ReadOnlySequence<T>.Slice`z int przeskakuje nad pustymi segmentami.
- Wyliczanie `ReadOnlySequence<T>` wylicza puste segmenty.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>Potencjalne problemy z\<ReadOnlySequence T> i SequencePosition

Istnieje kilka nietypowych wyników `ReadOnlySequence<T>` / `SequencePosition` w kontaktach z vs. normalne: `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int`

- `SequencePosition`jest znacznikiem położenia `ReadOnlySequence<T>`dla określonej, a nie bezwzględnej pozycji. Ponieważ jest to w `ReadOnlySequence<T>`stosunku do konkretnego , nie ma `ReadOnlySequence<T>` znaczenia, jeśli jest używany poza skąd pochodzi.
- Arytmetyka nie może być `SequencePosition` wykonywana `ReadOnlySequence<T>`bez . Oznacza to robienie `position++` podstawowych `ReadOnlySequence<T>.GetPosition(position, 1)`rzeczy, takich jak jest napisane .
- `GetPosition(long)`**nie** obsługuje indeksów ujemnych. Oznacza to, że nie można uzyskać drugiego do ostatniego znaku bez chodzenia po wszystkich segmentach.
- Dwóch `SequencePosition` nie da się porównać, co utrudnia:
  - Dowiedz się, czy jedna pozycja jest większa lub mniejsza niż inna pozycja.
  - Napisz kilka algorytmów analizy.
- `ReadOnlySequence<T>`jest większy niż odwołanie do obiektu i powinny być przekazywane przez [lub](../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref,](../../csharp/language-reference/keywords/ref.md) jeśli to możliwe. `ReadOnlySequence<T>` Przechodzenie `in` `ref` przez lub zmniejsza kopie [.](../../csharp/language-reference/builtin-types/struct.md)
- Puste segmenty:
  - Są ważne `ReadOnlySequence<T>`w ciągu .
  - Może pojawić się podczas `ReadOnlySequence<T>.TryGet` iteracji przy użyciu metody.
  - Może pojawić się sekwencji `ReadOnlySequence<T>.Slice()` przy `SequencePosition` użyciu metody z obiektami.

## <a name="sequencereadert"></a>Czytnik\<sekwencji T\>

<xref:System.Buffers.SequenceReader%601>:

- Jest to nowy typ, który został wprowadzony w .NET `ReadOnlySequence<T>`Core 3.0, aby uprościć przetwarzanie .
- Ujednolice różnice między jednym `ReadOnlySequence<T>` segmentem `ReadOnlySequence<T>`a segmentem wielosegmentowym.
- Zapewnia pomocników do odczytywania`byte` danych `char`binarnych i tekstowych ( i ), które mogą lub nie mogą być podzielone na segmenty.

Istnieją wbudowane metody przetwarzania zarówno danych binarnych, jak i rozdzielanych. W poniższej sekcji przedstawiono, jak wyglądają `SequenceReader<T>`te same metody z:

### <a name="access-data"></a>Uzyskiwanie dostępu do danych

`SequenceReader<T>`ma metody wyliczania danych `ReadOnlySequence<T>` wewnątrz bezpośrednio. Poniższy kod jest przykładem `ReadOnlySequence<byte>` przetwarzania `byte` a na raz:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

Udostępnia `CurrentSpan` bieżącego segmentu `Span`, który jest podobny do tego, co zostało zrobione w metodzie ręcznie.

### <a name="use-position"></a>Użyj pozycji

Poniższy kod jest przykładową `FindIndexOf` implementacją przy `SequenceReader<T>`użyciu:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>Przetwarzanie danych binarnych

Poniższy przykład analizuje 4-bajtową długość całkowitą big-endian od `ReadOnlySequence<byte>`początku .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Przetwarzanie danych tekstowych

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SequenceReader\<\> T typowe problemy

- Ponieważ `SequenceReader<T>` jest zmienna struktura, zawsze powinny być przekazywane przez [odwołanie](../../csharp/language-reference/keywords/ref.md).
- `SequenceReader<T>`jest [strukturą ref,](../../csharp/language-reference/keywords/ref.md#ref-struct-types) dzięki czemu może być używany tylko w metodach synchronicznych i nie może być przechowywany w polach. Aby uzyskać więcej informacji, zobacz [Pisanie bezpiecznego i wydajnego kodu Języka C#.](../../csharp/write-safe-efficient-code.md)
- `SequenceReader<T>`jest zoptymalizowany do użytku jako czytnik tylko do przodu. `Rewind`jest przeznaczony dla małych kopii zapasowych, które `Read`nie `Peek`mogą `IsNext` być rozwiązane przy użyciu innych , i interfejsów API.
