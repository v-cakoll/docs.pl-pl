---
title: Potoki we/wy - .NET
description: Dowiedz się, jak skutecznie używać potoków we/wy w .NET i uniknąć problemów w kodzie.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 8822e731ae805e83d4072c5bd78dff3fcf9a31a1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81462522"
---
# <a name="systemiopipelines-in-net"></a>System.IO.Pipelines w .NET

<xref:System.IO.Pipelines>to nowa biblioteka, która ma na celu ułatwienie wykonywania wysokiej wydajności we/wy w .NET. Jest to biblioteka docelowa .NET Standard, który działa na wszystkich implementacjach platformy .NET.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>Jaki problem rozwiązuje system.IO.Pipelines

<!-- corner case doesn't MT (machine translate)   -->
Aplikacje, które analizują dane strumieniowe, składają się z kodu standardowego o wielu wyspecjalizowanych i nietypowych przepływach kodu. Standardowy i specjalny kod przypadku jest złożony i trudny do utrzymania.

`System.IO.Pipelines`został zaprojektowany w celu:

* Mają wysoką wydajność analizowania danych przesyłania strumieniowego.
* Zmniejsz złożoność kodu.

Następujący kod jest typowy dla serwera TCP, który odbiera wiadomości rozdzielane wierszem (rozdzielone) `'\n'`od klienta:

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

Poprzedni kod ma kilka problemów:

* Cała wiadomość (koniec wiersza) może nie zostać `ReadAsync`odebrana w jednym wywołaniu .
* To ignorowanie wyniku `stream.ReadAsync`. `stream.ReadAsync`zwraca ilość odczytanych danych.
* Nie obsługuje przypadku, w którym wiele wierszy `ReadAsync` są odczytywane w jednym wywołaniu.
* Przydziela tablicę `byte` z każdym odczytem.

Aby rozwiązać poprzednie problemy, wymagane są następujące zmiany:

* Buforuj przychodzące dane, dopóki nie zostanie znaleziony nowy wiersz.
* Przeanalizować wszystkie wiersze zwrócone w buforze.
* Możliwe, że linia jest większa niż 1 KB (1024 bajtów). Kod musi zmienić rozmiar buforu wejściowego, dopóki ogranicznik zostanie znaleziony w celu dopasowania pełnego wiersza wewnątrz buforu.

  * Jeśli rozmiar buforu zostanie zmieniona, więcej kopii buforu jest dokonywanych w miarę pojawiania się dłuższych wierszy w danych wejściowych.
  * Aby zmniejszyć ilość zmarnowanego miejsca, zgłoś bufor używany do odczytu linii.

* Należy rozważyć użycie buforu buforu buforu, aby uniknąć przydzielania pamięci wielokrotnie.
* Poniższy kod rozwiązuje niektóre z tych problemów:

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

Poprzedni kod jest złożony i nie rozwiązuje wszystkich zidentyfikowanych problemów. Sieci o wysokiej wydajności zwykle oznacza pisanie bardzo złożony kod, aby zmaksymalizować wydajność. `System.IO.Pipelines`został zaprojektowany, aby ułatwić pisanie tego typu kodu.

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Rury

Klasa <xref:System.IO.Pipelines.Pipe> może służyć do `PipeWriter/PipeReader` tworzenia pary. Wszystkie dane zapisane `PipeWriter` w the `PipeReader`jest dostępny w:

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Podstawowe użycie rur

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

Istnieją dwie pętle:

* `FillPipeAsync`odczytuje `Socket` z i zapisuje do `PipeWriter`.
* `ReadPipeAsync`odczytuje `PipeReader` z i analizuje wiersze przychodzące.

Nie ma żadnych jawnych buforów przydzielonych. Wszystkie zarządzanie buforem jest `PipeReader` `PipeWriter` delegowane do i implementacji. Delegowanie zarządzania buforem ułatwia korzystanie z kodu skupić się wyłącznie na logiki biznesowej.

W pierwszej pętli:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>jest wywoływana, aby uzyskać pamięć z modułu zapisującego.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>jest wywoływana, `PipeWriter` aby poinformować, ile danych zostało zapisanych w buforze.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>jest wezwany do udostępnienia `PipeReader`danych do .

W drugiej pętli `PipeReader` zużywa bufory zapisane przez `PipeWriter`. Bufory pochodzą z gniazda. Wezwanie do: `PipeReader.ReadAsync`

* Zwraca <xref:System.IO.Pipelines.ReadResult> zawierający dwie ważne informacje:

  * Dane, które zostały odczytane `ReadOnlySequence<byte>`w formie .
  * Wartość logiczna `IsCompleted` wskazująca, czy osiągnięto koniec danych (EOF).

Po znalezieniu ogranicznika końca wiersza (EOL) i przeanalizowaniu wiersza:

* Logika przetwarza bufor, aby pominąć to, co jest już przetworzone.
* `PipeReader.AdvanceTo`jest wywoływana, `PipeReader` aby poinformować, ile danych zostało zużyte i zbadane.

Pętle czytnika i pisarza kończą się wywołaniem `Complete`. `Complete`pozwala podstawowej pipe zwolnić pamięci, które przydzielone.

### <a name="backpressure-and-flow-control"></a>Kontrola podciśnienia i przepływu

Idealnie, czytanie i analizowanie współpracują ze sobą:

* Wątek zapisu zużywa dane z sieci i umieszcza je w buforach.
* Wątek analizy jest odpowiedzialny za konstruowanie odpowiednich struktur danych.

Zazwyczaj analizowanie zajmuje więcej czasu niż tylko kopiowanie bloków danych z sieci:

* Wątek odczytu wyprzedza wątku analizowania.
* Wątek odczytu musi spowolnić lub przydzielić więcej pamięci do przechowywania danych dla wątku analizowania.

Aby uzyskać optymalną wydajność, istnieje równowaga między częstymi przerwami a przydzielaniem większej ilości pamięci.

Aby rozwiązać poprzedni problem, `Pipe` ma dwa ustawienia do kontrolowania przepływu danych:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Określa, ile danych powinno być <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> buforowane przed wywołaniem wstrzymania.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Określa, ile danych czytelnik musi obserwować `PipeWriter.FlushAsync` przed wznowieniem połączeń.

![Diagram z ResumeWriterThreshold i PauseWriterThreshold](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* Zwraca niekompletną, `ValueTask<FlushResult>` gdy ilość `Pipe` danych `PauseWriterThreshold`w krzyżyk .
* Kończy `ValueTask<FlushResult>` się, gdy `ResumeWriterThreshold`staje się niższa niż .

Dwie wartości są używane, aby zapobiec szybkiej cyklu, które mogą wystąpić, jeśli jedna wartość jest używana.

### <a name="examples"></a>Przykłady

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler (Wychylik rur)

Zazwyczaj podczas `async` używania i `await`, kod asynchroniczne <xref:System.Threading.Tasks.TaskScheduler> wznawia <xref:System.Threading.SynchronizationContext>na albo na lub na bieżącym .

Podczas wykonywania we/wy, ważne jest, aby mieć szczegółową kontrolę nad tym, gdzie jest wykonywana liczba we/wy. Ta kontrola umożliwia efektywne korzystanie z pamięci podręcznej procesora CPU. Wydajne buforowanie ma kluczowe znaczenie dla aplikacji o wysokiej wydajności, takich jak serwery sieci Web. <xref:System.IO.Pipelines.PipeScheduler>zapewnia kontrolę nad gdzie wywołania zwrotne asynchroniczne uruchomić. Domyślnie:

* Używany <xref:System.Threading.SynchronizationContext> jest prąd.
* Jeśli nie ma `SynchronizationContext`, używa puli wątków do uruchamiania wywołań zwrotnych.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) jest <xref:System.IO.Pipelines.PipeScheduler> implementacją, która kolejkuje wywołania zwrotne do puli wątków. `PipeScheduler.ThreadPool`jest domyślnym i ogólnie najlepszym wyborem. [PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) może powodować niezamierzone konsekwencje, takie jak zakleszczenia.

### <a name="pipe-reset"></a>Resetowanie rur

Często jest to skuteczne, aby `Pipe` ponownie użyć obiektu. Aby zresetować potok, wywołaj <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> po zakończeniu `PipeReader` i `PipeWriter` zakończeniu.

## <a name="pipereader"></a>Czytnik potoków

<xref:System.IO.Pipelines.PipeReader>zarządza pamięcią w imieniu osoby dzwoniącej. **Zawsze** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> dzwonić <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>po wywołaniu . Dzięki temu `PipeReader` informuje, kiedy wywołujący jest wykonywana z pamięci, dzięki czemu można go śledzić. Zwrócony `ReadOnlySequence<byte>` `PipeReader.ReadAsync` z jest prawidłowy `PipeReader.AdvanceTo`tylko do momentu wywołania . Jest to nielegalne `ReadOnlySequence<byte>` w `PipeReader.AdvanceTo`użyciu po wywołaniu .

`PipeReader.AdvanceTo`przyjmuje <xref:System.SequencePosition> dwa argumenty:

* Pierwszy argument określa, ile pamięci zostało zużyte.
* Drugi argument określa, jaka część buforu została zaobserwowana.

Oznaczanie danych jako zużyte oznacza, że potok może zwrócić pamięć do podstawowej puli buforów. Oznaczanie danych zgodnie z obserwowanymi elementami określa, co `PipeReader.ReadAsync` robi następne wywołanie. Oznaczanie wszystkiego, co obserwuje, `PipeReader.ReadAsync` oznacza, że następne wywołanie nie powróci, dopóki nie zostanie zapisanych więcej danych do potoku. Każda inna wartość spowoduje, `PipeReader.ReadAsync` że następne wywołanie zostanie natychmiast odesłane z obserwowanymi *i* niezaobionymi danymi, ale nie danymi, które zostały już wykorzystane.

### <a name="read-streaming-data-scenarios"></a>Odczytywanie scenariuszy przesyłania strumieniowego danych

Istnieje kilka typowych wzorców, które pojawiają się podczas próby odczytu danych przesyłania strumieniowego:

* Biorąc pod uwagę strumień danych, przeanalizować pojedynczą wiadomość.
* Biorąc pod uwagę strumień danych, przeanalizyj wszystkie dostępne komunikaty.

W poniższych przykładach użyto `TryParseMessage` metody analizowania wiadomości z pliku `ReadOnlySequence<byte>`. `TryParseMessage`analizuje pojedynczy komunikat i aktualizuj bufor wejściowy, aby przyciąć analizowany komunikat z buforu. `TryParseMessage`nie jest częścią platformy .NET, jest to metoda napisana przez użytkownika używana w poniższych sekcjach.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Czytanie pojedynczej wiadomości

Poniższy kod odczytuje pojedynczą wiadomość z a `PipeReader` i zwraca ją do wywołującego.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

Powyższy kod ma następujące działanie:

* Analizuje pojedynczą wiadomość.
* Aktualizuje zużyte `SequencePosition` i zbadane, `SequencePosition` aby wskazać początek przyciętego buforu wejściowego.

Dwa `SequencePosition` argumenty są `TryParseMessage` aktualizowane, ponieważ usuwa analizowany komunikat z buforu wejściowego. Ogólnie rzecz biorąc podczas analizowania pojedynczej wiadomości z bufora, zbadane stanowisko powinno być jedną z następujących czynności:

* Koniec wiadomości.
* Koniec odebranego buforu, jeśli nie znaleziono żadnej wiadomości.

Przypadek pojedynczej wiadomości ma największe możliwości błędów. Przekazywanie nieprawidłowe wartości do *zbadane* może spowodować wyjątek braku pamięci lub nieskończonej pętli. Aby uzyskać więcej informacji, zobacz [PipeReader typowe problemy](#gotchas) sekcji w tym artykule.

### <a name="reading-multiple-messages"></a>Czytanie wielu wiadomości

Poniższy kod odczytuje `PipeReader` wszystkie `ProcessMessageAsync` wiadomości z i wywołuje na każdym.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>Anulowanie

`PipeReader.ReadAsync`:

* Obsługuje przekazywanie pliku <xref:System.Threading.CancellationToken>.
* <xref:System.OperationCanceledException> Zgłasza, jeśli `CancellationToken` jest anulowany, gdy jest oczekiwany odczyt.
* Obsługuje sposób anulowania bieżącej <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>operacji odczytu za pośrednictwem , co pozwala uniknąć wywoływania wyjątku. Wywołanie `PipeReader.CancelPendingRead` powoduje, że `PipeReader.ReadAsync` bieżące <xref:System.IO.Pipelines.ReadResult> lub `IsCanceled` następne `true`wywołanie do zwrócenia z zestawem do . Może to być przydatne do zatrzymania istniejącej pętli odczytu w sposób nieniszczący i nie wyjątkowy.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>Typowe problemy pipereader

* Przekazywanie niewłaściwych `consumed` `examined` wartości do lub może spowodować odczyt już odczytanych danych.
* Przejście `buffer.End` w sposób zbadany może skutkować:

  * Dane wstrzymane
  * Ewentualnie ewentualny wyjątek braku pamięci (OOM), jeśli dane nie są używane. Na przykład `PipeReader.AdvanceTo(position, buffer.End)` podczas przetwarzania pojedynczej wiadomości w czasie z buforu.

* Przekazywanie nieprawidłowych `consumed` `examined` wartości do lub może spowodować nieskończoną pętlę. Na przykład `PipeReader.AdvanceTo(buffer.Start)` `buffer.Start` jeśli nie został zmieniony spowoduje `PipeReader.ReadAsync` następne wywołanie do powrotu bezpośrednio przed nadejściem nowych danych.
* Przekazywanie nieprawidłowych `consumed` `examined` wartości do lub może spowodować nieskończone buforowanie (ewentualne OOM).
* Korzystanie `ReadOnlySequence<byte>` z `PipeReader.AdvanceTo` po wywołaniu może spowodować uszkodzenie pamięci (użycie po wolnym).
* Niepodjęcie połączenia `PipeReader.Complete/CompleteAsync` może spowodować przeciek pamięci.
* Sprawdzanie <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> i zamykanie logiki odczytu przed przetworzeniem buforu powoduje utratę danych. Warunek wyjścia pętli powinien `ReadResult.Buffer.IsEmpty` być `ReadResult.IsCompleted`oparty na i . W ten sposób niepoprawnie może spowodować nieskończoną pętlę.

#### <a name="problematic-code"></a>Problematyczny kod

❌**Utrata danych**

Może `ReadResult` zwrócić końcowy segment danych, `IsCompleted` gdy `true`jest ustawiony na . Nie odczytywanie tych danych przed zamknięciem pętli odczytu spowoduje utratę danych.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Nieskończona pętla**

Następująca logika może spowodować nieskończoną pętlę, `Result.IsCompleted` jeśli jest, ale nigdy nie ma `true` pełnego komunikatu w buforze.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Oto kolejny fragment kodu z tym samym problemem. Przed sprawdzeniem jest sprawdzanie niepustego `ReadResult.IsCompleted`buforu. Ponieważ jest w `else if`, będzie pętla na zawsze, jeśli nigdy nie ma pełnego komunikatu w buforze.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Nieoczekiwane zawieszenie**

Bezwarunkowo `PipeReader.AdvanceTo` wywołanie `buffer.End` z `examined` w pozycji może spowodować zawiesza się podczas analizowania pojedynczej wiadomości. Następne połączenie `PipeReader.AdvanceTo` nie powróci, dopóki:

* Więcej danych jest zapisywanych na potoku.
* Nowe dane nie zostały wcześniej zbadane.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Brak pamięci (OOM)**

Z następujących warunków, następujący kod utrzymuje <xref:System.OutOfMemoryException> buforowanie, dopóki nie wystąpi:

* Nie ma maksymalnego rozmiaru wiadomości.
* Dane zwrócone `PipeReader` z nie tworzą pełny komunikat. Na przykład nie robi pełny komunikat, ponieważ druga strona jest pisanie dużej wiadomości (Na przykład, komunikat 4 GB).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Uszkodzenie pamięci**

Podczas pisania pomocników, które odczytywali bufor, każdy `Advance`zwrócony ładunek powinien zostać skopiowany przed wywołaniem . Poniższy przykład zwróci pamięć, która `Pipe` została odrzucona i może ponownie użyć go do następnej operacji (odczyt/zapis).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter (Pisarz fajek)

Zarządza <xref:System.IO.Pipelines.PipeWriter> buforów do pisania w imieniu wywołującego. `PipeWriter`implementuje [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601). `IBufferWriter<byte>`umożliwia uzyskanie dostępu do buforów do wykonywania zapisów bez dodatkowych kopii buforu.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

Poprzedni kod:

* Żąda buforu o rozmiarze co `PipeWriter` najmniej <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>5 bajtów z using .
* Zapisuje bajty dla ciągu `"Hello"` ASCII `Memory<byte>`do zwracanych .
* Wywołania, <xref:System.IO.Pipelines.PipeWriter.Advance%2A> aby wskazać, ile bajtów zostały zapisane w buforze.
* Opróżnia `PipeWriter`, który wysyła bajty do urządzenia źródłowego.

Poprzednia metoda zapisu używa buforów `PipeWriter`dostarczonych przez . Alternatywnie: <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>

* Kopiuje istniejący `PipeWriter`bufor do pliku .
* Połączenia `GetSpan` `Advance` , w <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>razie potrzeby i połączenia .

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>Anulowanie

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>obsługuje przekazywanie <xref:System.Threading.CancellationToken>. Przekazywanie `CancellationToken` wyników, `OperationCanceledException` jeśli token zostanie anulowany, gdy istnieje spłukiwanie. `PipeWriter.FlushAsync`obsługuje sposób, aby anulować <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> bieżącą operację opróżniania za pośrednictwem bez wywoływania wyjątku. Wywołanie `PipeWriter.CancelPendingFlush` powoduje, że `PipeWriter.FlushAsync` bieżące lub następne wywołanie do lub `PipeWriter.WriteAsync` do zwrócenia z <xref:System.IO.Pipelines.FlushResult> `IsCanceled` zestawem do `true`. Może to być przydatne do zatrzymania plonowania równo w sposób nieniszczący i nie-wyjątkowy.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>Typowe problemy PipeWriter

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>i <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> zwrócić bufor z co najmniej żądaną ilością pamięci. **Nie** zakładaj dokładnych rozmiarów buforu.
* Nie ma żadnej gwarancji, że kolejne wywołania zwróci ten sam bufor lub bufor o tym samym rozmiarze.
* Nowy bufor musi być wymagane <xref:System.IO.Pipelines.PipeWriter.Advance%2A> po wywołaniu, aby kontynuować zapisywanie większej ilości danych. Wcześniej nabyty bufor nie może być zapisywany.
* `GetMemory` Dzwonienie `GetSpan` lub gdy istnieje niekompletne `FlushAsync` połączenie, nie jest bezpieczne.
* `Complete` Wywołanie `CompleteAsync` lub gdy nie ma niefluchowanych danych może spowodować uszkodzenie pamięci.

## <a name="iduplexpipe"></a>IDuplexPipe

Jest <xref:System.IO.Pipelines.IDuplexPipe> to umowa dla typów, które obsługują zarówno odczytu i zapisu. Na przykład połączenie sieciowe będzie reprezentowane przez plik `IDuplexPipe`.

 W `Pipe` przeciwieństwie `PipeReader` do `PipeWriter`tego, który zawiera i a , `IDuplexPipe` reprezentuje jedną stronę połączenia pełnego dupleksu. Oznacza to, że to, co jest napisane do `PipeWriter` nie będą odczytywane z `PipeReader`.

## <a name="streams"></a>Strumienie

Podczas odczytywania lub zapisywania danych strumienia, zazwyczaj odczytywać dane przy użyciu de-serializatora i zapisywać dane przy użyciu serializatora. Większość z tych interfejsów API strumienia odczytu i zapisu `Stream` ma parametr. Aby ułatwić integrację z tymi istniejącymi `PipeReader` interfejsami API i `PipeWriter` udostępnić program <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A>zwraca `Stream` implementację `PipeReader` wokół `PipeWriter`lub .
