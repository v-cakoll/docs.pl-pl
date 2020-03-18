---
title: Potoki We/Wy - .NET
description: Dowiedz się, jak efektywnie używać potoków we/wy w .NET i uniknąć problemów w kodzie.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: b18b2bf31787fa58e614cd4f057fba9037fe8ad8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77627555"
---
# <a name="systemiopipelines-in-net"></a>System.IO.Pipelines w .NET

<xref:System.IO.Pipelines>to nowa biblioteka, która została zaprojektowana, aby ułatwić wykonywanie we/wy o wysokiej wydajności w .NET. Jest to biblioteka kierowana do .NET Standard, która działa na wszystkich implementacjach .NET.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>Jaki problem rozwiązuje System.IO.Pipelines

<!-- corner case doesn't MT (machine translate)   -->
Aplikacje, które analizują dane przesyłania strumieniowego, składają się z standardowego kodu o wielu wyspecjalizowanych i nietypowych przepływach kodu. Standardowy i specjalny kod przypadku jest złożony i trudny w utrzymaniu.

`System.IO.Pipelines`został zaprojektowany tak, aby:

* Mają wysoką wydajność analizowania danych strumieniowych.
* Zmniejsz złożoność kodu.

Poniższy kod jest typowy dla serwera TCP, który odbiera wiadomości `'\n'`rozdzielane wierszem (rozdzielone przez) od klienta:

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
* To ignorowanie wyniku `stream.ReadAsync`. `stream.ReadAsync`zwraca ilość odczytu danych.
* Nie obsługuje przypadku, w którym wiele wierszy `ReadAsync` są odczytywane w jednym wywołaniu.
* Przydziela tablicy `byte` z każdym odczytu.

Aby rozwiązać poprzednie problemy, wymagane są następujące zmiany:

* Buforuj przychodzące dane, dopóki nie zostanie znaleziony nowy wiersz.
* Przeanalizować wszystkie wiersze zwrócone w buforze.
* Możliwe, że linia jest większa niż 1 KB (1024 bajtów). Kod musi zmienić rozmiar buforu wejściowego, dopóki nie zostanie znaleziony ogranicznik, aby dopasować się do pełnego wiersza wewnątrz buforu.

  * Jeśli rozmiar buforu zostanie zmniejszony, więcej kopii buforu jest umieszczanych w miarę pojawiania się dłuższych wierszy na danych wejściowych.
  * Aby zmniejszyć ilość zmarnowanego miejsca, zagęścić bufor używany do odczytu linii.

* Należy rozważyć użycie buforu puli, aby uniknąć przydzielania pamięci wielokrotnie.
* Poniższy kod rozwiązuje niektóre z następujących problemów:

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

Poprzedni kod jest złożony i nie rozwiązuje wszystkich zidentyfikowanych problemów. Sieci o wysokiej wydajności zwykle oznacza pisanie bardzo złożony kod, aby zmaksymalizować wydajność. `System.IO.Pipelines`został zaprojektowany, aby ułatwić pisanie tego typu kodu.

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Rury

Klasa <xref:System.IO.Pipelines.Pipe> może służyć do `PipeWriter/PipeReader` tworzenia pary. Wszystkie dane zapisane `PipeWriter` w zapisie są dostępne w `PipeReader`:

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Podstawowe zastosowanie rury

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

Istnieją dwie pętle:

* `FillPipeAsync`odczytuje `Socket` i zapisuje do `PipeWriter`.
* `ReadPipeAsync`odczytuje `PipeReader` z linii przychodzących i analizuje je.

Nie ma żadnych jawnych buforów przydzielonych. Wszystkie zarządzanie buforem jest `PipeReader` `PipeWriter` delegowane do implementacji i implementacji. Delegowanie zarządzania buforem ułatwia korzystanie z kodu, aby skupić się wyłącznie na logice biznesowej.

W pierwszej pętli:

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>jest wywoływana w celu uzyskania pamięci z podstawowej modułu zapisującego.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>jest wywoływana, `PipeWriter` aby powiedzieć, ile danych zostało zapisanych w buforze.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>jest wywoływana w celu `PipeReader`udostępnienia danych

W drugiej pętli `PipeReader` zużywa bufory zapisane `PipeWriter`przez . Bufory pochodzą z gniazda. Wezwanie do `PipeReader.ReadAsync`:

* Zwraca <xref:System.IO.Pipelines.ReadResult> wartość zawierającą dwie ważne informacje:

  * Dane, które zostały odczytane `ReadOnlySequence<byte>`w formie .
  * Wartość logiczna `IsCompleted` wskazująca, czy osiągnięto koniec danych (EOF).

Po znalezieniu ogranicznika końca linii (EOL) i przeanalizowaniu linii:

* Logika przetwarza bufor, aby pominąć to, co jest już przetworzone.
* `PipeReader.AdvanceTo`jest wywoływana, `PipeReader` aby powiedzieć, ile danych zostało zużytych i zbadanych.

Pętli czytnika i modułu `Complete`zapisującego kończy się wywołaniem . `Complete`umożliwia podstawowej rury zwolnić pamięć, która przydzielił.

### <a name="backpressure-and-flow-control"></a>Ciśnienie wsteczne i sterowanie przepływem

Najlepiej, gdyby czytanie i analizowanie współpracowało:

* Wątek zapisu zużywa dane z sieci i umieszcza go w buforach.
* Wątek analizy jest odpowiedzialny za konstruowanie odpowiednich struktur danych.

Zazwyczaj analizowanie zajmuje więcej czasu niż tylko kopiowanie bloków danych z sieci:

* Wątek odczytu wyprzedza wątek analizy.
* Wątek odczytu musi spowolnić lub przydzielić więcej pamięci do przechowywania danych dla wątku analizy.

Aby zapewnić optymalną wydajność, istnieje równowaga między częstymi przerwami a przydzielaniem większej ilości pamięci.

Aby rozwiązać poprzedni problem, `Pipe` ma dwa ustawienia do sterowania przepływem danych:

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Określa, ile danych powinno być <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> buforowane przed wywołaniami do wstrzymania.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Określa, ile danych czytelnik musi obserwować `PipeWriter.FlushAsync` przed wywołaniem, aby wznowić.

![Diagram z ResumeWriterThreshold i PauseWriterThreshold](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* Zwraca niekompletne, `ValueTask<FlushResult>` gdy ilość danych `Pipe` w `PauseWriterThreshold`krzyżyk .
* Kończy `ValueTask<FlushResult>` się, gdy staje `ResumeWriterThreshold`się niższa niż .

Dwie wartości są używane, aby zapobiec szybkiemu kolanem, który może wystąpić, jeśli używana jest jedna wartość.

### <a name="examples"></a>Przykłady

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>Harmonogram rur

Zazwyczaj podczas `async` używania `await`i , kod asynchroniczny <xref:System.Threading.Tasks.TaskScheduler> wznawia na jednym lub na bieżącym <xref:System.Threading.SynchronizationContext>.

Podczas wykonywania we/wy, ważne jest, aby mieć precyzyjną kontrolę nad tym, gdzie we/wy jest wykonywana. Ten formant pozwala efektywnie korzystać z pamięci podręcznej procesora CPU. Wydajne buforowanie ma kluczowe znaczenie dla aplikacji o wysokiej wydajności, takich jak serwery sieci Web. <xref:System.IO.Pipelines.PipeScheduler>zapewnia kontrolę nad tym, gdzie uruchamiają się asynchroniczne wywołania odwrócone. Domyślnie:

* Używany <xref:System.Threading.SynchronizationContext> jest prąd.
* Jeśli nie ma `SynchronizationContext`, używa puli wątków do uruchamiania wywołań suwnicowych.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) jest <xref:System.IO.Pipelines.PipeScheduler> implementacja, która kolejki wywołań wywołań do puli wątków. `PipeScheduler.ThreadPool`jest domyślnym i ogólnie najlepszym wyborem. [PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) może spowodować niezamierzone konsekwencje, takie jak zakleszczenia.

### <a name="pipe-reset"></a>Resetowanie potoku

Często jest efektywne ponowne użycie `Pipe` obiektu. Aby zresetować potok, zadzwoń, <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> gdy oba `PipeReader` są zakończone. `PipeWriter`

## <a name="pipereader"></a>Czytnik rur

<xref:System.IO.Pipelines.PipeReader>zarządza pamięcią w imieniu obiektu wywołującego. **Zawsze** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> dzwonić <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>po wywołaniu . Dzięki temu `PipeReader` wiadomo, kiedy obiekt wywołujący odbywa się z pamięci, dzięki czemu mogą być śledzone. Zwrócony `ReadOnlySequence<byte>` z `PipeReader.ReadAsync` jest ważny tylko `PipeReader.AdvanceTo`do momentu wywołania . Jest to nielegalne `ReadOnlySequence<byte>` w `PipeReader.AdvanceTo`użyciu po wywołaniu .

`PipeReader.AdvanceTo`przyjmuje <xref:System.SequencePosition> dwa argumenty:

* Pierwszy argument określa, ile pamięci zostało zużyte.
* Drugi argument określa, jaka część bufora została zaobserwowana.

Oznaczanie danych jako zużyte oznacza, że potok może zwrócić pamięć do podstawowej puli buforów. Oznaczanie danych jako obserwowanych kontroluje, co robi następne wywołanie. `PipeReader.ReadAsync` Oznaczanie wszystkiego zgodnie z zastojem oznacza, że następne wywołanie `PipeReader.ReadAsync` nie powróci, dopóki nie będzie więcej danych zapisanych na rurze. Każda inna wartość spowoduje `PipeReader.ReadAsync` następne wywołanie, aby natychmiast zwrócić z obserwowanych *i* nieobserwowanych danych, ale dane, które zostały już wykorzystane.

### <a name="read-streaming-data-scenarios"></a>Odczytywanie scenariuszy przesyłania danych strumieniowych

Istnieje kilka typowych wzorców, które pojawiają się podczas próby odczytu danych strumieniowych:

* Biorąc pod uwagę strumień danych, przeanalizować pojedynczy komunikat.
* Biorąc pod uwagę strumień danych, przeanalizuj wszystkie dostępne wiadomości.

W poniższych przykładach używa się `TryParseMessage` metody `ReadOnlySequence<byte>`analizowania wiadomości z pliku . `TryParseMessage`analizuje pojedynczy komunikat i zaktualizować bufor wejściowy, aby przyciąć przeanalizowany komunikat z buforu. `TryParseMessage`nie jest częścią .NET, jest to metoda napisana przez użytkownika używana w poniższych sekcjach.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Czytanie pojedynczej wiadomości

Poniższy kod odczytuje pojedynczą `PipeReader` wiadomość z a i zwraca go do obiektu wywołującego.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

Powyższy kod ma następujące działanie:

* Analizuje pojedynczą wiadomość.
* Aktualizuje zużyte `SequencePosition` i `SequencePosition` zbadane, aby wskazać początek przyciętego buforu wejściowego.

Dwa `SequencePosition` argumenty są `TryParseMessage` aktualizowane, ponieważ usuwa przeanalizowany komunikat z buforu wejściowego. Ogólnie rzecz biorąc podczas analizowania pojedynczego komunikatu z buforu, badane stanowisko powinno być jedną z następujących czynności:

* Koniec wiadomości.
* Koniec odebranego buforu, jeśli nie znaleziono żadnej wiadomości.

Pojedynczy komunikat ma największe możliwości wystąpienia błędów. Przekazywanie niewłaściwych wartości do *badanego* może spowodować wyjątek braku pamięci lub nieskończoną pętlę. Aby uzyskać więcej informacji, zobacz [PipeReader typowe problemy](#gotchas) sekcji w tym artykule.

### <a name="reading-multiple-messages"></a>Czytanie wielu wiadomości

Poniższy kod odczytuje wszystkie `PipeReader` wiadomości `ProcessMessageAsync` z i wywołuje na każdym.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>Anulowanie

`PipeReader.ReadAsync`:

* Obsługuje przekazywanie <xref:System.Threading.CancellationToken>.
* Zgłasza, <xref:System.OperationCanceledException> jeśli `CancellationToken` jest anulowana, gdy jest odczyt oczekujące.
* Obsługuje sposób anulowania bieżącej operacji <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>odczytu za pośrednictwem , co pozwala uniknąć zgłaszania wyjątku. `PipeReader.CancelPendingRead` Wywołanie powoduje, że `PipeReader.ReadAsync` bieżące lub <xref:System.IO.Pipelines.ReadResult> `IsCanceled` następne `true`wywołanie, aby powrócić z ustawionym na . Może to być przydatne do zatrzymania istniejącej pętli odczytu w sposób nieniszczący i niewyjątkowy.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>Typowe problemy PipeReader

* Przekazywanie niewłaściwych `consumed` wartości `examined` lub może spowodować odczyt już odczytanych danych.
* Zdawanie `buffer.End` w sposób badany może skutkować:

  * Wstrzymane dane
  * Ewentualnie ewentualny wyjątek braku pamięci (OOM), jeśli dane nie są używane. Na przykład `PipeReader.AdvanceTo(position, buffer.End)` podczas przetwarzania pojedynczego komunikatu w czasie z buforu.

* Przekazywanie niewłaściwych `consumed` wartości `examined` do lub może spowodować nieskończoną pętlę. Na przykład `PipeReader.AdvanceTo(buffer.Start)` `buffer.Start` jeśli nie uległa zmianie spowoduje `PipeReader.ReadAsync` następne wywołanie do powrotu bezpośrednio przed nadejścia nowych danych.
* Przekazywanie niewłaściwych `consumed` wartości `examined` do lub może spowodować nieskończone buforowanie (ewentualne OOM).
* Korzystanie `ReadOnlySequence<byte>` z `PipeReader.AdvanceTo` po wywołaniu może spowodować uszkodzenie pamięci (używać po darmo).
* Niewywołanie `PipeReader.Complete/CompleteAsync` może spowodować przeciek pamięci.
* Sprawdzanie <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> i zamykanie logiki odczytu przed przetworzeniem buforu powoduje utratę danych. Stan wyjścia pętli powinien `ReadResult.Buffer.IsEmpty` być `ReadResult.IsCompleted`oparty na i . Wykonanie tego niepoprawnie może spowodować nieskończoną pętlę.

#### <a name="problematic-code"></a>Problematyczny kod

❌**Utrata danych**

Może `ReadResult` zwrócić końcowy segment danych, `IsCompleted` gdy `true`jest ustawiony na . Nieodczytywanie tych danych przed wyjściem z pętli odczytu spowoduje utratę danych.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Nieskończona pętla**

Następująca logika może spowodować `Result.IsCompleted` nieskończoną pętlę, jeśli jest, `true` ale nigdy nie ma pełnego komunikatu w buforze.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Oto kolejny fragment kodu z tym samym problemem. To sprawdzanie niepustego buforu `ReadResult.IsCompleted`przed sprawdzeniem . Ponieważ jest w `else if`, będzie pętli na zawsze, jeśli nigdy nie ma pełnej wiadomości w buforze.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Nieoczekiwane zawieszenie**

Bezwarunkowe `PipeReader.AdvanceTo` wywoływanie `buffer.End` z `examined` w pozycji może spowodować zawiesza się podczas analizowania pojedynczej wiadomości. Następne wywołanie `PipeReader.AdvanceTo` nie wróci, dopóki:

* Jest więcej danych zapisanych na rurze.
* Nowe dane nie zostały wcześniej zbadane.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Brak pamięci (OOM)**

W następujących warunkach następujący kod utrzymuje buforowanie aż do wystąpienia: <xref:System.OutOfMemoryException>

* Nie ma maksymalnego rozmiaru wiadomości.
* Dane zwrócone `PipeReader` z nie tworzą pełnej wiadomości. Na przykład nie zawiera pełnej wiadomości, ponieważ druga strona pisze dużą wiadomość (Na przykład wiadomość 4 GB).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**Uszkodzenie pamięci**

Podczas pisania pomocników, którzy odczytują bufor, wszelkie `Advance`zwrócone ładunku powinny być kopiowane przed wywołaniem . Poniższy przykład zwróci pamięć, która `Pipe` została odrzucona i może użyć jej ponownie do następnej operacji (odczyt/zapis).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>Moduł PipeWriter

Zarządza <xref:System.IO.Pipelines.PipeWriter> buforów do zapisu w imieniu obiektu wywołującego. `PipeWriter`implementuje [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601). `IBufferWriter<byte>`umożliwia uzyskanie dostępu do buforów do wykonywania zapisów bez dodatkowych kopii buforu.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

Poprzedni kod:

* Żąda buforu o co najmniej 5 `PipeWriter` <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>bajtach z using .
* Zapisuje bajty dla ciągu `"Hello"` ASCII do `Memory<byte>`zwróconego pliku .
* Wywołania <xref:System.IO.Pipelines.PipeWriter.Advance%2A> wskazujące, ile bajtów zostało zapisanych w buforze.
* Opróżnia `PipeWriter`, który wysyła bajty do urządzenia źródłowego.

Poprzednia metoda zapisu używa buforów `PipeWriter`dostarczonych przez . Alternatywnie: <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>

* Kopiuje istniejący `PipeWriter`bufor do pliku .
* Połączenia `GetSpan` `Advance` , w <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>stosownych przypadkach i połączenia .

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>Anulowanie

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>obsługuje przekazywanie <xref:System.Threading.CancellationToken>. Przekazywanie `CancellationToken` wyników `OperationCanceledException` w if token jest anulowany, gdy istnieje flush oczekujące. `PipeWriter.FlushAsync`obsługuje sposób anulowania bieżącej operacji <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> opróżniania za pośrednictwem bez zgłaszania wyjątku. `PipeWriter.CancelPendingFlush` Wywołanie powoduje, że `PipeWriter.FlushAsync` bieżące `PipeWriter.WriteAsync` lub <xref:System.IO.Pipelines.FlushResult> następne `IsCanceled` wywołanie lub powrót z ustawionym na `true`. Może to być przydatne do zatrzymania plonowania w sposób nieniszczący i niewyjątkowy.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>Często występujące problemy pipewritera

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>i <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> zwrócić bufor z co najmniej żądaną ilością pamięci. **Nie** zakładaj dokładnych rozmiarów buforu.
* Nie ma żadnej gwarancji, że kolejne wywołania zwróci tego samego buforu lub buforu tego samego rozmiaru.
* Nowy bufor musi być wymagane <xref:System.IO.Pipelines.PipeWriter.Advance%2A> po wywołaniu, aby kontynuować zapisywanie większej ilości danych. Wcześniej nabytego bufora nie można zapisać.
* Dzwonienie `GetMemory` lub `GetSpan` gdy jest niepełne `FlushAsync` połączenie, nie jest bezpieczne.
* `Complete` Wywołanie `CompleteAsync` lub gdy nie są opróżniane dane może spowodować uszkodzenie pamięci.

## <a name="iduplexpipe"></a>IDuplexPipe (IDuplexPipe)

Jest <xref:System.IO.Pipelines.IDuplexPipe> to umowa dla typów, które obsługują zarówno czytania i pisania. Na przykład połączenie sieciowe będzie reprezentowane `IDuplexPipe`przez .

 W `Pipe` przeciwieństwie `PipeReader` do `PipeWriter`tego, który zawiera a i , `IDuplexPipe` reprezentuje jedną stronę pełnego połączenia dupleksu. Oznacza to, że `PipeWriter` to, co jest `PipeReader`napisane do nie będzie odczytywane z .

## <a name="streams"></a>Strumienie

Podczas odczytywania lub zapisywania danych strumienia, zazwyczaj odczytu danych przy użyciu de-serializatora i zapisu danych przy użyciu serializatora. Większość z tych interfejsów API `Stream` strumienia odczytu i zapisu ma parametr. Aby ułatwić integrację z tymi `PipeReader` istniejącymi interfejsami API i `PipeWriter` uwidaczniać . <xref:System.IO.Pipelines.PipeReader.AsStream%2A>  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A>zwraca `Stream` implementację `PipeReader` `PipeWriter`wokół lub .
