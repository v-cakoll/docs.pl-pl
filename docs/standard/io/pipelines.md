---
title: Potoki we/wy — .NET
description: Dowiedz się, jak efektywnie korzystać z potoków we/wy w programie .NET i uniknąć problemów w kodzie.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 9efd7a7581a1e8bd2cb5f544edd1b4c965aa1866
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395932"
---
# <a name="systemiopipelines-in-net"></a>System. IO. potoki w środowisku .NET

<xref:System.IO.Pipelines> to nowa biblioteka, która umożliwia łatwiejsze wykonywanie operacji we/wy na platformie .NET. Jest to biblioteka ukierunkowana .NET Standard, która działa na wszystkich implementacjach platformy .NET.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>Jaki problem rozwiązuje system. IO. potoki

<!-- corner case doesn't MT (machine translate)   -->
Aplikacje, które analizują dane przesyłane strumieniowo, składają się z kodu standardowego, który ma wiele wyspecjalizowanych i nietypowych przepływów kodu. Kod standardowy i szczególny przypadek jest skomplikowany i trudny do utrzymania.

`System.IO.Pipelines` został zaprojektowany z myślą o:

* Przeanalizowanie danych przesyłanych strumieniowo o wysokiej wydajności.
* Zmniejsz złożoność kodu.

Poniższy kod jest typowy dla serwera TCP, który odbiera komunikaty rozdzielane wierszami (ograniczone przez `'\n'`) od klienta:

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

Poprzedni kod zawiera kilka problemów:

* Cały komunikat (koniec wiersza) może nie zostać odebrany w jednym wywołaniu do `ReadAsync`.
* Zostanie zignorowany wynik `stream.ReadAsync`. `stream.ReadAsync` zwraca ilość danych, które zostały odczytane.
* Nie obsługuje przypadku, w którym wiele wierszy jest odczytywanych w pojedynczym wywołaniu `ReadAsync`.
* Przypisuje tablicę `byte` z każdym odczytem.

Aby rozwiązać powyższe problemy, wymagane są następujące zmiany:

* Buforuj dane przychodzące do momentu znalezienia nowego wiersza.
* Przeanalizuj wszystkie wiersze zwrócone w buforze.
* Istnieje możliwość, że wiersz jest większy niż 1 KB (1024 bajtów). Kod musi zmienić rozmiar buforu wejściowego do momentu, w którym zostanie znaleziony ogranicznik, aby dopasować cały wiersz w buforze.

  * Jeśli rozmiar buforu jest zmieniany, w danych wejściowych są umieszczane więcej kopii buforów.
  * Aby zmniejszyć ilość zajętego miejsca, należy skompaktować bufor używany do odczytywania wierszy.

* Rozważ użycie puli buforów, aby uniknąć wielokrotnego przydzielania pamięci.
* Poniższy kod dotyczy niektórych z następujących problemów:

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

Poprzedni kod jest skomplikowany i nie dotyczy wszystkich zidentyfikowanych problemów. Wysoka wydajność sieci zwykle oznacza pisanie bardzo złożonego kodu w celu zmaksymalizowania wydajności. `System.IO.Pipelines` został zaprojektowany, aby ułatwić pisanie tego typu kodu.

## <a name="pipe"></a>Wodzie

Klasy <xref:System.IO.Pipelines.Pipe> można użyć do utworzenia pary `PipeWriter/PipeReader`. Wszystkie dane zapisywane do `PipeWriter` są dostępne w `PipeReader`:

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Podstawowe użycie potoków

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

Istnieją dwie pętle:

* `FillPipeAsync` odczytuje z `Socket` i zapisuje w `PipeWriter`.
* `ReadPipeAsync` odczytuje z `PipeReader` i analizuje linie przychodzące.

Nie ma żadnych jawnie przyznanych buforów. Wszystkie Zarządzanie buforem jest delegowane do implementacji `PipeReader` i `PipeWriter`. Delegowanie zarządzania buforem ułatwia wykorzystywanie kodu do skoncentrowania się wyłącznie na logice biznesowej.

W pierwszej pętli:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> jest wywoływana, aby uzyskać pamięć z bazowego składnika zapisywania.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> jest wywoływana w celu poinformowania o `PipeWriter` ilości danych w buforze.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> jest wywoływana, aby udostępnić dane dla `PipeReader`.

W drugiej pętli `PipeReader` zużywa bufory zapisywane przez `PipeWriter`. Bufory pochodzą z gniazda. Wywołanie `PipeReader.ReadAsync`:

* Zwraca wartość <xref:System.IO.Pipelines.ReadResult> zawierającą dwie ważne informacje:

  * Dane, które zostały odczytane w formie `ReadOnlySequence<byte>`.
  * Wartość logiczna `IsCompleted` wskazuje, czy osiągnięto koniec danych (EOF).

Po znalezieniu ogranicznika końca wiersza (EOL) i przeanalizowaniu wiersza:

* Logika przetwarza bufor, aby pominąć operacje, które zostały już przetworzone.
* `PipeReader.AdvanceTo` jest wywoływana w celu poinformowania `PipeReader` o ilości danych, które zostały zużyte i zbadane.

Pętle czytnika i składnika zapisywania kończą się przez wywołanie `Complete`. `Complete` umożliwia zwolnieniu pamięci podlegającej potoku.

### <a name="backpressure-and-flow-control"></a>Sterowanie ruchem wstecznym i przepływem

Najlepiej, odczytując i przeanalizować współpracę:

* Wątek pisania wykorzystuje dane z sieci i umieszcza je w buforach.
* Wątek analizy jest odpowiedzialny za konstruowanie odpowiednich struktur danych.

Zwykle analiza zajmuje więcej czasu niż tylko kopiowanie bloków danych z sieci:

* Wątek odczytywania pobiera przed wątkiem analizy.
* Wątek odczytu musi spowolnić lub przydzielić więcej pamięci, aby przechowywać dane dla wątku analizy.

W celu uzyskania optymalnej wydajności istnieje równowaga między częste Wstrzymywanie i przydzielania większej ilości pamięci.

Aby rozwiązać ten problem, `Pipe` ma dwa ustawienia do sterowania przepływem danych:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: określa, ile danych ma być buforowanych przed wywołaniami <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> Pause.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: określa, ile danych musi obserwować czytelnik przed wywołaniami `PipeWriter.FlushAsync` wznowić.

![Diagram z ResumeWriterThreshold i PauseWriterThreshold](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* Zwraca niekompletną `ValueTask<FlushResult>`, gdy ilość danych w `Pipe` przekracza `PauseWriterThreshold`.
* Kończy `ValueTask<FlushResult>`, gdy przyjmie mniej niż `ResumeWriterThreshold`.

Dwie wartości są używane, aby zapobiec szybkiemu cyklowi, który może wystąpić w przypadku użycia jednej wartości.

### <a name="examples"></a>Przykłady

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

Zwykle w przypadku używania `async` i `await` kod asynchroniczny zostaje wznowiony na <xref:System.Threading.Tasks.TaskScheduler> lub na bieżącym <xref:System.Threading.SynchronizationContext>.

Podczas wykonywania operacji we/wy należy mieć precyzyjną kontrolę nad tym, gdzie jest wykonywane wykonywanie operacji we/wy. Ta kontrolka umożliwia efektywne wykorzystanie pamięci podręcznych procesora CPU. Wydajne buforowanie ma kluczowe znaczenie dla aplikacji o wysokiej wydajności, takich jak serwery sieci Web. <xref:System.IO.Pipelines.PipeScheduler> zapewnia kontrolę nad miejscem, w którym są uruchamiane asynchroniczne wywołania zwrotne. Domyślnie:

* Bieżąca <xref:System.Threading.SynchronizationContext> jest używana.
* Jeśli nie ma `SynchronizationContext`, używa ona puli wątków do uruchamiania wywołań zwrotnych.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[PipeScheduler.](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) Threading to implementacja <xref:System.IO.Pipelines.PipeScheduler>, która kolejkuje wywołania zwrotne do puli wątków. `PipeScheduler.ThreadPool` jest domyślnym i generalnie najlepszym wyborem. [PipeScheduler. inline](xref:System.IO.Pipelines.PipeScheduler.Inline) może spowodować niezamierzone konsekwencje, takie jak zakleszczenia.

### <a name="pipe-reset"></a>Resetowanie potoku

Często wydajnym rozwiązaniem jest ponowne użycie obiektu `Pipe`. Aby zresetować potok, wywołaj <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> po zakończeniu obu `PipeReader` i `PipeWriter`.

## <a name="pipereader"></a>PipeReader

<xref:System.IO.Pipelines.PipeReader> zarządza pamięcią w imieniu obiektu wywołującego. **Zawsze** wywołuj <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> po wywołaniu <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>. Pozwala to `PipeReader` wiedzieć, kiedy obiekt wywołujący jest wykonywany z pamięcią, tak aby można było go śledzić. Wartość `ReadOnlySequence<byte>` zwracana z `PipeReader.ReadAsync` jest prawidłowa tylko do momentu wywołania `PipeReader.AdvanceTo`. Nie można używać `ReadOnlySequence<byte>` po wywołaniu `PipeReader.AdvanceTo`.

`PipeReader.AdvanceTo` przyjmuje dwa argumenty <xref:System.SequencePosition>:

* Pierwszy argument określa, ile pamięci zostało zużyte.
* Drugi argument określa, jaka część buforu została zaobserwowana.

Oznaczenie danych jako zużyte oznacza, że potok może zwrócić pamięć do źródłowej puli buforów. Oznaczanie danych jako obserwowanych kontroluje, co następne wywołanie `PipeReader.ReadAsync`. Oznaczenie wszystkiego jako zaobserwowane oznacza, że następne wywołanie `PipeReader.ReadAsync` nie zwróci się do momentu zapisania większej ilości danych w potoku. Wszystkie inne wartości spowodują, że następne wywołanie `PipeReader.ReadAsync` zwróci bezpośrednio z obserwowanymi *i* nieobserwowanymi danymi, ale dane, które zostały już zużyte.

### <a name="read-streaming-data-scenarios"></a>Odczytaj scenariusze przesyłania strumieniowego danych

Istnieje kilka typowych wzorców, które nastąpiły podczas próby odczytu danych przesyłanych strumieniowo:

* Przy użyciu strumienia danych Przeanalizuj pojedynczy komunikat.
* Przy użyciu strumienia danych Przeanalizuj wszystkie dostępne komunikaty.

W poniższych przykładach użyto metody `TryParseMessage` do analizowania komunikatów z `ReadOnlySequence<byte>`. `TryParseMessage` analizuje pojedynczy komunikat i aktualizuje bufor wejściowy, aby przyciąć przeanalizowany komunikat z bufora. `TryParseMessage` nie jest częścią programu .NET. jest to metoda zapisywana przez użytkownika używana w poniższych sekcjach.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Odczytaj pojedynczy komunikat

Poniższy kod odczytuje pojedynczy komunikat z `PipeReader` i zwraca go do obiektu wywołującego.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

Poprzedni kod:

* Analizuje pojedynczy komunikat.
* Aktualizuje zużyte `SequencePosition` i zbadane `SequencePosition`, aby wskazywały na początek przyciętego buforu wejściowego.

Dwa argumenty `SequencePosition` są aktualizowane, ponieważ `TryParseMessage` usuwa przeanalizowany komunikat z buforu wejściowego. Ogólnie rzecz biorąc, podczas analizowania pojedynczej wiadomości z bufora pozycja zbadana powinna mieć jedną z następujących wartości:

* Koniec komunikatu.
* Koniec odebranego buforu, jeśli nie odnaleziono komunikatu.

Przypadek z pojedynczym komunikatem ma największą możliwość wystąpienia błędów. Przekazanie nieprawidłowych wartości do *zbadania* może spowodować wyjątek braku pamięci lub nieskończoną pętlę. Aby uzyskać więcej informacji, zobacz sekcję [typowe problemy związane z PipeReader](#gotchas) w tym artykule.

### <a name="reading-multiple-messages"></a>Odczytywanie wielu wiadomości

Poniższy kod odczytuje wszystkie komunikaty z `PipeReader` i wywołuje `ProcessMessageAsync` na każdym z nich.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>Anulowanie

`PipeReader.ReadAsync`:

* Obsługuje przekazywanie <xref:System.Threading.CancellationToken>.
* Zgłasza <xref:System.OperationCanceledException>, jeśli `CancellationToken` zostanie anulowane, gdy istnieje oczekujące odczytanie.
* Obsługuje sposób anulowania bieżącej operacji odczytu za pośrednictwem <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, co pozwala uniknąć wywoływania wyjątku. Wywołanie `PipeReader.CancelPendingRead` powoduje, że bieżące lub następne wywołanie do `PipeReader.ReadAsync` zwróci <xref:System.IO.Pipelines.ReadResult> z `IsCanceled` ustawionym na `true`. Może to być przydatne w przypadku zatrzymania istniejącej pętli odczytu w nieniszczącej i niewyjątkowy sposób.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>PipeReader typowe problemy

* Przekazanie nieprawidłowych wartości do `consumed` lub `examined` może spowodować odczyt danych, które zostały już odczytane.
* Przekazywanie `buffer.End` jako badane może skutkować:

  * Dane wstrzymane
  * Ewentualny wyjątek braku pamięci (OOM), jeśli dane nie są używane. Na przykład `PipeReader.AdvanceTo(position, buffer.End)` podczas przetwarzania pojedynczej wiadomości w czasie z buforu.

* Przekazanie nieprawidłowych wartości do `consumed` lub `examined` może spowodować nieskończoną pętlę. Na przykład `PipeReader.AdvanceTo(buffer.Start)` Jeśli nie zmieniono `buffer.Start`, spowoduje to, że następne wywołanie metody `PipeReader.ReadAsync` zwróci natychmiast przed nadejściem nowych danych.
* Przekazanie nieprawidłowych wartości do `consumed` lub `examined` może spowodować nieskończone buforowanie (ostateczne OOM).
* Użycie `ReadOnlySequence<byte>` po wywołaniu `PipeReader.AdvanceTo` może spowodować uszkodzenie pamięci (za darmo).
* Niepowodzenie wywołania `PipeReader.Complete/CompleteAsync` może spowodować przeciek pamięci.
* Sprawdzanie <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> i wyjście z logiki odczytu przed przetworzeniem buforu spowoduje utratę danych. Warunek zakończenia pętli powinien opierać się na `ReadResult.Buffer.IsEmpty` i `ReadResult.IsCompleted`. Nieprawidłowe działanie może spowodować powstanie pętli nieskończonej.

#### <a name="problematic-code"></a>Problematyczny kod

❌ **utrata danych**

@No__t-0 może zwrócić końcowy segment danych, gdy `IsCompleted` jest ustawiona na `true`. Nie można odczytać tych danych przed wyjściem z pętli odczytu spowoduje utratę danych.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

**nieskończona pętla** ❌

Poniższa logika może spowodować nieskończoną pętlę, jeśli `Result.IsCompleted` jest `true`, ale nigdy nie pełny komunikat w buforze.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Oto inny fragment kodu z tym samym problemem. Przed sprawdzeniem `ReadResult.IsCompleted` sprawdza, czy bufor nie jest pusty. Ponieważ jest ona w `else if`, będzie ona zapętlać w nieskończoność, jeśli w buforze nigdy nie ma kompletnego komunikatu.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

**nieoczekiwane zawieszenie** ❌

Bezwarunkowo wywoływanie `PipeReader.AdvanceTo` z `buffer.End` w pozycji `examined` może spowodować zawieszenie podczas analizowania pojedynczego komunikatu. Następne wywołanie `PipeReader.AdvanceTo` nie zwróci wartości do momentu:

* Więcej danych jest zapisywana w potoku.
* Nowe dane nie były wcześniej badane.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **z pamięci (OOM)**

W następujących warunkach Poniższy kod przechowuje buforowanie do momentu wystąpienia <xref:System.OutOfMemoryException>:

* Nie ma maksymalnego rozmiaru wiadomości.
* Dane zwrócone z `PipeReader` nie pełnią komunikatu. Na przykład nie wykonuje pełnego komunikatu, ponieważ druga strona zapisuje dużą wiadomość (na przykład komunikat 4 GB).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

**uszkodzenie pamięci** ❌

Podczas pisania pomocników odczytujących bufor należy skopiować wszystkie zwrócone ładunki przed wywołaniem `Advance`. Poniższy przykład zwróci pamięć, która `Pipe` została odrzucona i może ponownie użyć dla następnej operacji (odczyt/zapis).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

@No__t-0 zarządza buforami do zapisu w imieniu obiektu wywołującego. `PipeWriter` implementuje [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601). `IBufferWriter<byte>` umożliwia uzyskanie dostępu do buforów w celu wykonywania operacji zapisu bez dodatkowych kopii buforów.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

Poprzedni kod:

* Żąda bufora co najmniej 5 bajtów z `PipeWriter` przy użyciu <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>.
* Zapisuje bajty dla ciągu ASCII `"Hello"` do zwróconego `Span<byte>`.
* Wywołania <xref:System.IO.Pipelines.PipeWriter.Advance%2A> wskazują, ile bajtów Zapisano w buforze.
* Opróżnia `PipeWriter`, który wysyła bajty do urządzenia bazowego.

Poprzednia metoda pisania używa buforów dostarczonych przez `PipeWriter`. Alternatywnie, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:

* Kopiuje istniejący bufor do `PipeWriter`.
* Wywołania `GetSpan`, `Advance`, zgodnie z potrzebami, i wywołań <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>Anulowanie

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> obsługuje przekazywanie <xref:System.Threading.CancellationToken>. Przekazywanie `CancellationToken` powoduje wystąpienie `OperationCanceledException`, jeśli token zostanie anulowany, gdy istnieje oczekująca operacja opróżniania. `PipeWriter.FlushAsync` obsługuje sposób anulowania bieżącej operacji opróżniania za pośrednictwem <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> bez podnoszenia wyjątku. Wywołanie `PipeWriter.CancelPendingFlush` powoduje, że bieżące lub następne wywołanie `PipeWriter.FlushAsync` lub `PipeWriter.WriteAsync` spowoduje zwrócenie <xref:System.IO.Pipelines.FlushResult> z `IsCanceled` ustawionym na `true`. Może to być przydatne w przypadku zatrzymania opróżniania w sposób nieniszczący i niewyjątkowy.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>PipeWriter typowe problemy

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> i <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> zwracają bufor z co najmniej żądaną ilością pamięci. **Nie** zakładaj dokładnie rozmiarów buforów.
* Nie ma gwarancji, że kolejne wywołania będą zwracać ten sam bufor lub bufor o takim samym rozmiarze.
* Przed wywołaniem <xref:System.IO.Pipelines.PipeWriter.Advance%2A> należy zażądać nowego buforu, aby kontynuować zapisywanie większej ilości danych. Nie można zapisać wcześniej uzyskanego buforu.
* Wywołanie `GetMemory` lub `GetSpan`, gdy istnieje niekompletne wywołanie `FlushAsync` nie jest bezpieczne.
* Wywołanie `Complete` lub `CompleteAsync`, gdy nieopróżnione dane mogą spowodować uszkodzenie pamięci.

## <a name="iduplexpipe"></a>IDuplexPipe

@No__t-0 to kontrakt dla typów, które obsługują odczyt i zapis. Na przykład połączenie sieciowe będzie reprezentowane przez `IDuplexPipe`.

 W przeciwieństwie do `Pipe`, który zawiera `PipeReader` i `PipeWriter`, `IDuplexPipe` reprezentuje jedną część połączenia pełnego dupleksu. Oznacza to, co jest zapisywane w `PipeWriter` nie zostanie odczytany z `PipeReader`.

## <a name="streams"></a>Strumienie

Podczas odczytywania lub zapisywania danych strumienia zwykle dane są odczytywane przy użyciu deserializatora i zapisu danych przy użyciu serializatora. Większość z tych interfejsów API odczytu i zapisu ma parametr `Stream`. Aby ułatwić integrację z tymi istniejącymi interfejsami API, `PipeReader` i `PipeWriter` uwidacznia <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A> zwraca implementację `Stream` wokół `PipeReader` lub `PipeWriter`.
