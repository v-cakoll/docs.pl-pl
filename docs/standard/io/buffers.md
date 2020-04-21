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
# <a name="work-with-buffers-in-net"></a>Praca z buforami w .NET

Ten artykuł zawiera omówienie typów, które pomagają odczytać dane, które są uruchamiane w wielu buforach. Są one używane głównie <xref:System.IO.Pipelines.PipeReader> do obsługi obiektów.

## <a name="ibufferwritert"></a>IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>jest kontraktem na synchroniczowe buforowane pisanie. Na najniższym poziomie interfejs:

- Jest podstawowy i nie jest trudny w użyciu.
- Umożliwia dostęp <xref:System.Memory%601> do <xref:System.Span%601>lub . Lub `Memory<T>` `Span<T>` mogą być zapisywane do i `T` można określić, ile elementów zostały napisane.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

Poprzednia metoda:

- Żąda buforu o rozmiarze co `IBufferWriter<byte>` najmniej `GetSpan(5)`5 bajtów z using .
- Zapisuje bajty dla ciągu ASCII "Hello" do zwracanych `Span<byte>`.
- Wywołania, <xref:System.Buffers.IBufferWriter%601> aby wskazać, ile bajtów zostały zapisane w buforze.

Ta metoda pisania używa `Memory<T>` / `Span<T>` buforu `IBufferWriter<T>`dostarczonego przez . Alternatywnie można <xref:System.Buffers.BuffersExtensions.Write%2A> użyć metody rozszerzenia do kopiowania `IBufferWriter<T>`istniejącego buforu do pliku . `Write`wykonuje pracę wywoływania `GetSpan` / `Advance` w razie potrzeby, więc `Advance` nie ma potrzeby, aby zadzwonić po napisaniu:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601>jest implementacją `IBufferWriter<T>` magazynu zapasowego, którego zapas jest pojedynczą tablicą ciągłą.

### <a name="ibufferwriter-common-problems"></a>IBufferWriter typowe problemy

- `GetSpan`i `GetMemory` zwrócić bufor z co najmniej żądaną ilością pamięci. Nie zakładaj dokładnych rozmiarów buforu.
- Nie ma żadnej gwarancji, że kolejne wywołania zwróci ten sam bufor lub bufor o tym samym rozmiarze.
- Nowy bufor musi być wymagane `Advance` po wywołaniu, aby kontynuować zapisywanie większej ilości danych. Wcześniej nabyty bufor nie może być `Advance` zapisywany po wywołaniu.

## <a name="readonlysequencet"></a>ReadOnlySequence\<T\>

![ReadOnlySequence pokazujące pamięć w rurze i poniżej tej pozycji sekwencji pamięci tylko do odczytu](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601>jest strukturą, która może reprezentować ciągłą lub nieciągłą sekwencję `T`. Może być zbudowany z:

1. Element `T[]`.
1. Element `ReadOnlyMemory<T>`.
1. Para połączonego węzła <xref:System.Buffers.ReadOnlySequenceSegment%601> listy i indeksu do reprezentowania pozycji początkowej i końcowej sekwencji.

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

Z powodu tej mieszanej reprezentacji `ReadOnlySequence<T>` `SequencePosition` udostępnia indeksy jako zamiast liczby całkowitej. A: `SequencePosition`

- Jest nieprzezroczystą wartością `ReadOnlySequence<T>` reprezentującą indeks do miejsca, w którym pochodzi.
- Składa się z dwóch części, liczby całkowitej i obiektu. Co te dwie wartości reprezentują są `ReadOnlySequence<T>`związane z implementacją .

### <a name="access-data"></a>Uzyskiwanie dostępu do danych

Udostępnia `ReadOnlySequence<T>` dane jako wyliczalne `ReadOnlyMemory<T>`. Wyliczanie każdego z segmentów można wykonać za pomocą podstawowego foreach:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

Poprzednia metoda przeszukuje każdy segment w poszukiwaniu określonego bajtu. Jeśli chcesz śledzić każdy `SequencePosition`segment, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> jest bardziej odpowiednie. Następny przykład zmienia poprzedni kod, `SequencePosition` aby zwrócić zamiast liczby całkowitej. Powrót a `SequencePosition` ma zaletę, pozwalając wywołującego, aby uniknąć drugiego skanowania, aby uzyskać dane w określonym indeksie.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

Połączenie `SequencePosition` i `TryGet` działa jak wyliczacz. Pole pozycji jest modyfikowane na początku każdej iteracji, aby `ReadOnlySequence<T>`było początkiem każdego segmentu w pliku .

Poprzednia metoda istnieje jako metoda `ReadOnlySequence<T>`rozszerzenia na . <xref:System.Buffers.BuffersExtensions.PositionOf%2A>może służyć do uproszczenia poprzedniego kodu:

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>Proces ReadOnlySequence\<T\>

Przetwarzanie `ReadOnlySequence<T>` a może być trudne, ponieważ dane mogą być podzielone na wiele segmentów w ramach sekwencji. Aby uzyskać najlepszą wydajność, podziel kod na dwie ścieżki:

- Szybka ścieżka, która dotyczy pojedynczego segmentu.
- Powolna ścieżka, która zajmuje się danymi podzielonymi na segmenty.

Istnieje kilka podejść, które mogą być używane do przetwarzania danych w sekwencjach wielosegmentowych:

- Użyj [`SequenceReader<T>`](#sequencereadert)pliku .
- Analizuj segment danych według segmentów, śledząc `SequencePosition` i indeks w obrębie analizowanego segmentu. Pozwala to uniknąć niepotrzebnych alokacji, ale może być nieefektywne, zwłaszcza w przypadku małych buforów.
- Skopiuj `ReadOnlySequence<T>` do ciągłej tablicy i potraktuj ją jak pojedynczy bufor:
  - Jeśli rozmiar `ReadOnlySequence<T>` jest mały, może być uzasadnione, aby skopiować dane do buforu przydzielonego do stosu przy użyciu [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operatora.
  - Skopiuj do `ReadOnlySequence<T>` <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>tablicy zbiorczej za pomocą programu .
  - Użyj witryny [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A). Nie jest to zalecane w ścieżkach gorących, ponieważ przydziela nowy `T[]` na stosie.

Poniższe przykłady pokazują niektóre `ReadOnlySequence<byte>`typowe przypadki przetwarzania:

##### <a name="process-binary-data"></a>Przetwarzanie danych binarnych

W poniższym przykładzie analizuje 4-bajtową długość całkowitą big-endian `ReadOnlySequence<byte>`od początku .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Przetwarzanie danych tekstowych

Poniższy przykład:

- Znajduje pierwszą nową`\r\n`linię `ReadOnlySequence<byte>` ( ) w i zwraca ją za pomocą out "line" parametru.
- Przycina ten wiersz, `\r\n` z wyłączeniem buforu wejściowego.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Puste segmenty

Prawidłowe jest przechowywanie pustych segmentów `ReadOnlySequence<T>`wewnątrz pliku . Puste segmenty mogą występować podczas jawnego wyliczania segmentów:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

Poprzedni kod tworzy `ReadOnlySequence<byte>` z pustymi segmentami i pokazuje, jak te puste segmenty wpływają na różne interfejsy API:

- `ReadOnlySequence<T>.Slice`z `SequencePosition` wskazywaniem na pusty segment zachowuje ten segment.
- `ReadOnlySequence<T>.Slice`z int przeskakuje nad pustymi segmentami.
- Wyliczanie `ReadOnlySequence<T>` wylicza puste segmenty.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>Potencjalne problemy z ReadOnlySequence\<T> i SequencePosition

Istnieje kilka nietypowych wyników, `ReadOnlySequence<T>` / `SequencePosition` gdy mamy `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int`do czynienia z a. normalne:

- `SequencePosition`jest znacznikiem położenia dla określonej, `ReadOnlySequence<T>`a nie bezwzględnej pozycji. Ponieważ jest to związane `ReadOnlySequence<T>`z określonym , nie ma znaczenia, `ReadOnlySequence<T>` jeśli jest używany poza miejscem, w którym pochodzi.
- Arytmetyka nie może być `SequencePosition` wykonywana `ReadOnlySequence<T>`bez pliku . Oznacza to, że `position++` robi `ReadOnlySequence<T>.GetPosition(position, 1)`podstawowe rzeczy, takie jak jest napisane .
- `GetPosition(long)`**nie** obsługuje indeksów ujemnych. Oznacza to, że nie można uzyskać od drugiego do ostatniego znaku bez chodzenia po wszystkich segmentach.
- Dwóch `SequencePosition` nie można porównać, co utrudnia:
  - Dowiedz się, czy jedna pozycja jest większa lub mniejsza niż inna pozycja.
  - Napisz kilka algorytmów analizowania.
- `ReadOnlySequence<T>`jest większy niż odwołanie do obiektu i powinny być przekazywane przez [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) lub [ref,](../../csharp/language-reference/keywords/ref.md) jeśli to możliwe. Przechodząc `ReadOnlySequence<T>` `in` przez `ref` lub zmniejsza kopie [struktury](../../csharp/language-reference/builtin-types/struct.md).
- Puste segmenty:
  - Są ważne `ReadOnlySequence<T>`w obrębie .
  - Może pojawić się podczas `ReadOnlySequence<T>.TryGet` iteracji przy użyciu metody.
  - Może pojawić się krojenie `ReadOnlySequence<T>.Slice()` sekwencji przy użyciu metody z `SequencePosition` obiektami.

## <a name="sequencereadert"></a>SequenceReader\<T (Czytnik sekwencji T)\>

<xref:System.Buffers.SequenceReader%601>:

- Jest to nowy typ, który został wprowadzony w .NET Core `ReadOnlySequence<T>`3.0 w celu uproszczenia przetwarzania .
- Ujednolica różnice `ReadOnlySequence<T>` między pojedynczym i wielosegmentowym `ReadOnlySequence<T>`.
- Zapewnia pomocników do odczytywania`byte` `char`danych binarnych i tekstowych ( i ), które mogą lub nie mogą być podzielone na segmenty.

Istnieją wbudowane metody radzenia sobie z przetwarzaniem danych binarnych i rozdzielanych. W poniższej sekcji pokazano, jak wyglądają `SequenceReader<T>`te same metody z :

### <a name="access-data"></a>Uzyskiwanie dostępu do danych

`SequenceReader<T>`ma metody wyliczania danych `ReadOnlySequence<T>` wewnątrz bezpośrednio. Poniższy kod jest przykładem `ReadOnlySequence<byte>` `byte` przetwarzania a w czasie:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

Eksponuje `CurrentSpan` bieżącego segmentu `Span`, który jest podobny do tego, co zostało zrobione w metodzie ręcznie.

### <a name="use-position"></a>Użyj pozycji

Poniższy kod jest przykładową implementacją `FindIndexOf` przy `SequenceReader<T>`użyciu:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>Przetwarzanie danych binarnych

W poniższym przykładzie analizuje 4-bajtową długość całkowitą big-endian `ReadOnlySequence<byte>`od początku .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Przetwarzanie danych tekstowych

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SequenceReader\<\> T typowe problemy

- Ponieważ `SequenceReader<T>` jest zmienna struktura, zawsze powinny być przekazywane przez [odwołanie](../../csharp/language-reference/keywords/ref.md).
- `SequenceReader<T>`jest [strukturą ref,](../../csharp/language-reference/builtin-types/struct.md#ref-struct) dzięki czemu może być używana tylko w metodach synchronicznych i nie może być przechowywana w polach. Aby uzyskać więcej informacji, zobacz [Pisanie bezpiecznego i wydajnego kodu języka C#.](../../csharp/write-safe-efficient-code.md)
- `SequenceReader<T>`jest zoptymalizowany do użycia jako czytnik tylko do przodu. `Rewind`jest przeznaczony do małych kopii zapasowych, których `Read` `Peek`nie `IsNext` można rozwiązać z wykorzystaniem innych interfejsów API i interfejsów API.
