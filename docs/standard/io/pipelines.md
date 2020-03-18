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
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="4f144-103">System.IO.Pipelines w .NET</span><span class="sxs-lookup"><span data-stu-id="4f144-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="4f144-104"><xref:System.IO.Pipelines>to nowa biblioteka, która została zaprojektowana, aby ułatwić wykonywanie we/wy o wysokiej wydajności w .NET.</span><span class="sxs-lookup"><span data-stu-id="4f144-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="4f144-105">Jest to biblioteka kierowana do .NET Standard, która działa na wszystkich implementacjach .NET.</span><span class="sxs-lookup"><span data-stu-id="4f144-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="4f144-106">Jaki problem rozwiązuje System.IO.Pipelines</span><span class="sxs-lookup"><span data-stu-id="4f144-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="4f144-107">Aplikacje, które analizują dane przesyłania strumieniowego, składają się z standardowego kodu o wielu wyspecjalizowanych i nietypowych przepływach kodu.</span><span class="sxs-lookup"><span data-stu-id="4f144-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="4f144-108">Standardowy i specjalny kod przypadku jest złożony i trudny w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="4f144-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="4f144-109">`System.IO.Pipelines`został zaprojektowany tak, aby:</span><span class="sxs-lookup"><span data-stu-id="4f144-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="4f144-110">Mają wysoką wydajność analizowania danych strumieniowych.</span><span class="sxs-lookup"><span data-stu-id="4f144-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="4f144-111">Zmniejsz złożoność kodu.</span><span class="sxs-lookup"><span data-stu-id="4f144-111">Reduce code complexity.</span></span>

<span data-ttu-id="4f144-112">Poniższy kod jest typowy dla serwera TCP, który odbiera wiadomości `'\n'`rozdzielane wierszem (rozdzielone przez) od klienta:</span><span class="sxs-lookup"><span data-stu-id="4f144-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="4f144-113">Poprzedni kod ma kilka problemów:</span><span class="sxs-lookup"><span data-stu-id="4f144-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="4f144-114">Cała wiadomość (koniec wiersza) może nie zostać `ReadAsync`odebrana w jednym wywołaniu .</span><span class="sxs-lookup"><span data-stu-id="4f144-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="4f144-115">To ignorowanie wyniku `stream.ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="4f144-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="4f144-116">`stream.ReadAsync`zwraca ilość odczytu danych.</span><span class="sxs-lookup"><span data-stu-id="4f144-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="4f144-117">Nie obsługuje przypadku, w którym wiele wierszy `ReadAsync` są odczytywane w jednym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="4f144-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="4f144-118">Przydziela tablicy `byte` z każdym odczytu.</span><span class="sxs-lookup"><span data-stu-id="4f144-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="4f144-119">Aby rozwiązać poprzednie problemy, wymagane są następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="4f144-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="4f144-120">Buforuj przychodzące dane, dopóki nie zostanie znaleziony nowy wiersz.</span><span class="sxs-lookup"><span data-stu-id="4f144-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="4f144-121">Przeanalizować wszystkie wiersze zwrócone w buforze.</span><span class="sxs-lookup"><span data-stu-id="4f144-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="4f144-122">Możliwe, że linia jest większa niż 1 KB (1024 bajtów).</span><span class="sxs-lookup"><span data-stu-id="4f144-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="4f144-123">Kod musi zmienić rozmiar buforu wejściowego, dopóki nie zostanie znaleziony ogranicznik, aby dopasować się do pełnego wiersza wewnątrz buforu.</span><span class="sxs-lookup"><span data-stu-id="4f144-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="4f144-124">Jeśli rozmiar buforu zostanie zmniejszony, więcej kopii buforu jest umieszczanych w miarę pojawiania się dłuższych wierszy na danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="4f144-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="4f144-125">Aby zmniejszyć ilość zmarnowanego miejsca, zagęścić bufor używany do odczytu linii.</span><span class="sxs-lookup"><span data-stu-id="4f144-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="4f144-126">Należy rozważyć użycie buforu puli, aby uniknąć przydzielania pamięci wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="4f144-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="4f144-127">Poniższy kod rozwiązuje niektóre z następujących problemów:</span><span class="sxs-lookup"><span data-stu-id="4f144-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="4f144-128">Poprzedni kod jest złożony i nie rozwiązuje wszystkich zidentyfikowanych problemów.</span><span class="sxs-lookup"><span data-stu-id="4f144-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="4f144-129">Sieci o wysokiej wydajności zwykle oznacza pisanie bardzo złożony kod, aby zmaksymalizować wydajność.</span><span class="sxs-lookup"><span data-stu-id="4f144-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="4f144-130">`System.IO.Pipelines`został zaprojektowany, aby ułatwić pisanie tego typu kodu.</span><span class="sxs-lookup"><span data-stu-id="4f144-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="4f144-131">Rury</span><span class="sxs-lookup"><span data-stu-id="4f144-131">Pipe</span></span>

<span data-ttu-id="4f144-132">Klasa <xref:System.IO.Pipelines.Pipe> może służyć do `PipeWriter/PipeReader` tworzenia pary.</span><span class="sxs-lookup"><span data-stu-id="4f144-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="4f144-133">Wszystkie dane zapisane `PipeWriter` w zapisie są dostępne w `PipeReader`:</span><span class="sxs-lookup"><span data-stu-id="4f144-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="4f144-134">Podstawowe zastosowanie rury</span><span class="sxs-lookup"><span data-stu-id="4f144-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="4f144-135">Istnieją dwie pętle:</span><span class="sxs-lookup"><span data-stu-id="4f144-135">There are two loops:</span></span>

* <span data-ttu-id="4f144-136">`FillPipeAsync`odczytuje `Socket` i zapisuje do `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="4f144-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="4f144-137">`ReadPipeAsync`odczytuje `PipeReader` z linii przychodzących i analizuje je.</span><span class="sxs-lookup"><span data-stu-id="4f144-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="4f144-138">Nie ma żadnych jawnych buforów przydzielonych.</span><span class="sxs-lookup"><span data-stu-id="4f144-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="4f144-139">Wszystkie zarządzanie buforem jest `PipeReader` `PipeWriter` delegowane do implementacji i implementacji.</span><span class="sxs-lookup"><span data-stu-id="4f144-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="4f144-140">Delegowanie zarządzania buforem ułatwia korzystanie z kodu, aby skupić się wyłącznie na logice biznesowej.</span><span class="sxs-lookup"><span data-stu-id="4f144-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="4f144-141">W pierwszej pętli:</span><span class="sxs-lookup"><span data-stu-id="4f144-141">In the first loop:</span></span>

* <span data-ttu-id="4f144-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>jest wywoływana w celu uzyskania pamięci z podstawowej modułu zapisującego.</span><span class="sxs-lookup"><span data-stu-id="4f144-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="4f144-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>jest wywoływana, `PipeWriter` aby powiedzieć, ile danych zostało zapisanych w buforze.</span><span class="sxs-lookup"><span data-stu-id="4f144-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="4f144-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>jest wywoływana w celu `PipeReader`udostępnienia danych</span><span class="sxs-lookup"><span data-stu-id="4f144-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="4f144-145">W drugiej pętli `PipeReader` zużywa bufory zapisane `PipeWriter`przez .</span><span class="sxs-lookup"><span data-stu-id="4f144-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="4f144-146">Bufory pochodzą z gniazda.</span><span class="sxs-lookup"><span data-stu-id="4f144-146">The buffers come from the socket.</span></span> <span data-ttu-id="4f144-147">Wezwanie do `PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="4f144-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="4f144-148">Zwraca <xref:System.IO.Pipelines.ReadResult> wartość zawierającą dwie ważne informacje:</span><span class="sxs-lookup"><span data-stu-id="4f144-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="4f144-149">Dane, które zostały odczytane `ReadOnlySequence<byte>`w formie .</span><span class="sxs-lookup"><span data-stu-id="4f144-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="4f144-150">Wartość logiczna `IsCompleted` wskazująca, czy osiągnięto koniec danych (EOF).</span><span class="sxs-lookup"><span data-stu-id="4f144-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="4f144-151">Po znalezieniu ogranicznika końca linii (EOL) i przeanalizowaniu linii:</span><span class="sxs-lookup"><span data-stu-id="4f144-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="4f144-152">Logika przetwarza bufor, aby pominąć to, co jest już przetworzone.</span><span class="sxs-lookup"><span data-stu-id="4f144-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="4f144-153">`PipeReader.AdvanceTo`jest wywoływana, `PipeReader` aby powiedzieć, ile danych zostało zużytych i zbadanych.</span><span class="sxs-lookup"><span data-stu-id="4f144-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="4f144-154">Pętli czytnika i modułu `Complete`zapisującego kończy się wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="4f144-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="4f144-155">`Complete`umożliwia podstawowej rury zwolnić pamięć, która przydzielił.</span><span class="sxs-lookup"><span data-stu-id="4f144-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="4f144-156">Ciśnienie wsteczne i sterowanie przepływem</span><span class="sxs-lookup"><span data-stu-id="4f144-156">Backpressure and flow control</span></span>

<span data-ttu-id="4f144-157">Najlepiej, gdyby czytanie i analizowanie współpracowało:</span><span class="sxs-lookup"><span data-stu-id="4f144-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="4f144-158">Wątek zapisu zużywa dane z sieci i umieszcza go w buforach.</span><span class="sxs-lookup"><span data-stu-id="4f144-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="4f144-159">Wątek analizy jest odpowiedzialny za konstruowanie odpowiednich struktur danych.</span><span class="sxs-lookup"><span data-stu-id="4f144-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="4f144-160">Zazwyczaj analizowanie zajmuje więcej czasu niż tylko kopiowanie bloków danych z sieci:</span><span class="sxs-lookup"><span data-stu-id="4f144-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="4f144-161">Wątek odczytu wyprzedza wątek analizy.</span><span class="sxs-lookup"><span data-stu-id="4f144-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="4f144-162">Wątek odczytu musi spowolnić lub przydzielić więcej pamięci do przechowywania danych dla wątku analizy.</span><span class="sxs-lookup"><span data-stu-id="4f144-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="4f144-163">Aby zapewnić optymalną wydajność, istnieje równowaga między częstymi przerwami a przydzielaniem większej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="4f144-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="4f144-164">Aby rozwiązać poprzedni problem, `Pipe` ma dwa ustawienia do sterowania przepływem danych:</span><span class="sxs-lookup"><span data-stu-id="4f144-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="4f144-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Określa, ile danych powinno być <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> buforowane przed wywołaniami do wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="4f144-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="4f144-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Określa, ile danych czytelnik musi obserwować `PipeWriter.FlushAsync` przed wywołaniem, aby wznowić.</span><span class="sxs-lookup"><span data-stu-id="4f144-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![Diagram z ResumeWriterThreshold i PauseWriterThreshold](./media/pipelines/resume-pause.png)

<span data-ttu-id="4f144-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="4f144-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="4f144-169">Zwraca niekompletne, `ValueTask<FlushResult>` gdy ilość danych `Pipe` w `PauseWriterThreshold`krzyżyk .</span><span class="sxs-lookup"><span data-stu-id="4f144-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="4f144-170">Kończy `ValueTask<FlushResult>` się, gdy staje `ResumeWriterThreshold`się niższa niż .</span><span class="sxs-lookup"><span data-stu-id="4f144-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="4f144-171">Dwie wartości są używane, aby zapobiec szybkiemu kolanem, który może wystąpić, jeśli używana jest jedna wartość.</span><span class="sxs-lookup"><span data-stu-id="4f144-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="4f144-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="4f144-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="4f144-173">Harmonogram rur</span><span class="sxs-lookup"><span data-stu-id="4f144-173">PipeScheduler</span></span>

<span data-ttu-id="4f144-174">Zazwyczaj podczas `async` używania `await`i , kod asynchroniczny <xref:System.Threading.Tasks.TaskScheduler> wznawia na jednym lub na bieżącym <xref:System.Threading.SynchronizationContext>.</span><span class="sxs-lookup"><span data-stu-id="4f144-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="4f144-175">Podczas wykonywania we/wy, ważne jest, aby mieć precyzyjną kontrolę nad tym, gdzie we/wy jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="4f144-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="4f144-176">Ten formant pozwala efektywnie korzystać z pamięci podręcznej procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="4f144-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="4f144-177">Wydajne buforowanie ma kluczowe znaczenie dla aplikacji o wysokiej wydajności, takich jak serwery sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4f144-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="4f144-178"><xref:System.IO.Pipelines.PipeScheduler>zapewnia kontrolę nad tym, gdzie uruchamiają się asynchroniczne wywołania odwrócone.</span><span class="sxs-lookup"><span data-stu-id="4f144-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="4f144-179">Domyślnie:</span><span class="sxs-lookup"><span data-stu-id="4f144-179">By default:</span></span>

* <span data-ttu-id="4f144-180">Używany <xref:System.Threading.SynchronizationContext> jest prąd.</span><span class="sxs-lookup"><span data-stu-id="4f144-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="4f144-181">Jeśli nie ma `SynchronizationContext`, używa puli wątków do uruchamiania wywołań suwnicowych.</span><span class="sxs-lookup"><span data-stu-id="4f144-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="4f144-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) jest <xref:System.IO.Pipelines.PipeScheduler> implementacja, która kolejki wywołań wywołań do puli wątków.</span><span class="sxs-lookup"><span data-stu-id="4f144-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="4f144-183">`PipeScheduler.ThreadPool`jest domyślnym i ogólnie najlepszym wyborem.</span><span class="sxs-lookup"><span data-stu-id="4f144-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="4f144-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) może spowodować niezamierzone konsekwencje, takie jak zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="4f144-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="4f144-185">Resetowanie potoku</span><span class="sxs-lookup"><span data-stu-id="4f144-185">Pipe reset</span></span>

<span data-ttu-id="4f144-186">Często jest efektywne ponowne użycie `Pipe` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4f144-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="4f144-187">Aby zresetować potok, zadzwoń, <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> gdy oba `PipeReader` są zakończone. `PipeWriter`</span><span class="sxs-lookup"><span data-stu-id="4f144-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="4f144-188">Czytnik rur</span><span class="sxs-lookup"><span data-stu-id="4f144-188">PipeReader</span></span>

<span data-ttu-id="4f144-189"><xref:System.IO.Pipelines.PipeReader>zarządza pamięcią w imieniu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4f144-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="4f144-190">**Zawsze** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> dzwonić <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>po wywołaniu .</span><span class="sxs-lookup"><span data-stu-id="4f144-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4f144-191">Dzięki temu `PipeReader` wiadomo, kiedy obiekt wywołujący odbywa się z pamięci, dzięki czemu mogą być śledzone.</span><span class="sxs-lookup"><span data-stu-id="4f144-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="4f144-192">Zwrócony `ReadOnlySequence<byte>` z `PipeReader.ReadAsync` jest ważny tylko `PipeReader.AdvanceTo`do momentu wywołania .</span><span class="sxs-lookup"><span data-stu-id="4f144-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="4f144-193">Jest to nielegalne `ReadOnlySequence<byte>` w `PipeReader.AdvanceTo`użyciu po wywołaniu .</span><span class="sxs-lookup"><span data-stu-id="4f144-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="4f144-194">`PipeReader.AdvanceTo`przyjmuje <xref:System.SequencePosition> dwa argumenty:</span><span class="sxs-lookup"><span data-stu-id="4f144-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="4f144-195">Pierwszy argument określa, ile pamięci zostało zużyte.</span><span class="sxs-lookup"><span data-stu-id="4f144-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="4f144-196">Drugi argument określa, jaka część bufora została zaobserwowana.</span><span class="sxs-lookup"><span data-stu-id="4f144-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="4f144-197">Oznaczanie danych jako zużyte oznacza, że potok może zwrócić pamięć do podstawowej puli buforów.</span><span class="sxs-lookup"><span data-stu-id="4f144-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="4f144-198">Oznaczanie danych jako obserwowanych kontroluje, co robi następne wywołanie. `PipeReader.ReadAsync`</span><span class="sxs-lookup"><span data-stu-id="4f144-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="4f144-199">Oznaczanie wszystkiego zgodnie z zastojem oznacza, że następne wywołanie `PipeReader.ReadAsync` nie powróci, dopóki nie będzie więcej danych zapisanych na rurze.</span><span class="sxs-lookup"><span data-stu-id="4f144-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="4f144-200">Każda inna wartość spowoduje `PipeReader.ReadAsync` następne wywołanie, aby natychmiast zwrócić z obserwowanych *i* nieobserwowanych danych, ale dane, które zostały już wykorzystane.</span><span class="sxs-lookup"><span data-stu-id="4f144-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="4f144-201">Odczytywanie scenariuszy przesyłania danych strumieniowych</span><span class="sxs-lookup"><span data-stu-id="4f144-201">Read streaming data scenarios</span></span>

<span data-ttu-id="4f144-202">Istnieje kilka typowych wzorców, które pojawiają się podczas próby odczytu danych strumieniowych:</span><span class="sxs-lookup"><span data-stu-id="4f144-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="4f144-203">Biorąc pod uwagę strumień danych, przeanalizować pojedynczy komunikat.</span><span class="sxs-lookup"><span data-stu-id="4f144-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="4f144-204">Biorąc pod uwagę strumień danych, przeanalizuj wszystkie dostępne wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4f144-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="4f144-205">W poniższych przykładach używa się `TryParseMessage` metody `ReadOnlySequence<byte>`analizowania wiadomości z pliku .</span><span class="sxs-lookup"><span data-stu-id="4f144-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="4f144-206">`TryParseMessage`analizuje pojedynczy komunikat i zaktualizować bufor wejściowy, aby przyciąć przeanalizowany komunikat z buforu.</span><span class="sxs-lookup"><span data-stu-id="4f144-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="4f144-207">`TryParseMessage`nie jest częścią .NET, jest to metoda napisana przez użytkownika używana w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="4f144-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="4f144-208">Czytanie pojedynczej wiadomości</span><span class="sxs-lookup"><span data-stu-id="4f144-208">Read a single message</span></span>

<span data-ttu-id="4f144-209">Poniższy kod odczytuje pojedynczą `PipeReader` wiadomość z a i zwraca go do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4f144-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="4f144-210">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="4f144-210">The preceding code:</span></span>

* <span data-ttu-id="4f144-211">Analizuje pojedynczą wiadomość.</span><span class="sxs-lookup"><span data-stu-id="4f144-211">Parses a single message.</span></span>
* <span data-ttu-id="4f144-212">Aktualizuje zużyte `SequencePosition` i `SequencePosition` zbadane, aby wskazać początek przyciętego buforu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="4f144-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="4f144-213">Dwa `SequencePosition` argumenty są `TryParseMessage` aktualizowane, ponieważ usuwa przeanalizowany komunikat z buforu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="4f144-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="4f144-214">Ogólnie rzecz biorąc podczas analizowania pojedynczego komunikatu z buforu, badane stanowisko powinno być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4f144-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="4f144-215">Koniec wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4f144-215">The end of the message.</span></span>
* <span data-ttu-id="4f144-216">Koniec odebranego buforu, jeśli nie znaleziono żadnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4f144-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="4f144-217">Pojedynczy komunikat ma największe możliwości wystąpienia błędów.</span><span class="sxs-lookup"><span data-stu-id="4f144-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="4f144-218">Przekazywanie niewłaściwych wartości do *badanego* może spowodować wyjątek braku pamięci lub nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="4f144-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="4f144-219">Aby uzyskać więcej informacji, zobacz [PipeReader typowe problemy](#gotchas) sekcji w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="4f144-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="4f144-220">Czytanie wielu wiadomości</span><span class="sxs-lookup"><span data-stu-id="4f144-220">Reading multiple messages</span></span>

<span data-ttu-id="4f144-221">Poniższy kod odczytuje wszystkie `PipeReader` wiadomości `ProcessMessageAsync` z i wywołuje na każdym.</span><span class="sxs-lookup"><span data-stu-id="4f144-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="4f144-222">Anulowanie</span><span class="sxs-lookup"><span data-stu-id="4f144-222">Cancellation</span></span>

<span data-ttu-id="4f144-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="4f144-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="4f144-224">Obsługuje przekazywanie <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="4f144-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="4f144-225">Zgłasza, <xref:System.OperationCanceledException> jeśli `CancellationToken` jest anulowana, gdy jest odczyt oczekujące.</span><span class="sxs-lookup"><span data-stu-id="4f144-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="4f144-226">Obsługuje sposób anulowania bieżącej operacji <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>odczytu za pośrednictwem , co pozwala uniknąć zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4f144-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="4f144-227">`PipeReader.CancelPendingRead` Wywołanie powoduje, że `PipeReader.ReadAsync` bieżące lub <xref:System.IO.Pipelines.ReadResult> `IsCanceled` następne `true`wywołanie, aby powrócić z ustawionym na .</span><span class="sxs-lookup"><span data-stu-id="4f144-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="4f144-228">Może to być przydatne do zatrzymania istniejącej pętli odczytu w sposób nieniszczący i niewyjątkowy.</span><span class="sxs-lookup"><span data-stu-id="4f144-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="4f144-229">Typowe problemy PipeReader</span><span class="sxs-lookup"><span data-stu-id="4f144-229">PipeReader common problems</span></span>

* <span data-ttu-id="4f144-230">Przekazywanie niewłaściwych `consumed` wartości `examined` lub może spowodować odczyt już odczytanych danych.</span><span class="sxs-lookup"><span data-stu-id="4f144-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="4f144-231">Zdawanie `buffer.End` w sposób badany może skutkować:</span><span class="sxs-lookup"><span data-stu-id="4f144-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="4f144-232">Wstrzymane dane</span><span class="sxs-lookup"><span data-stu-id="4f144-232">Stalled data</span></span>
  * <span data-ttu-id="4f144-233">Ewentualnie ewentualny wyjątek braku pamięci (OOM), jeśli dane nie są używane.</span><span class="sxs-lookup"><span data-stu-id="4f144-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="4f144-234">Na przykład `PipeReader.AdvanceTo(position, buffer.End)` podczas przetwarzania pojedynczego komunikatu w czasie z buforu.</span><span class="sxs-lookup"><span data-stu-id="4f144-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="4f144-235">Przekazywanie niewłaściwych `consumed` wartości `examined` do lub może spowodować nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="4f144-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="4f144-236">Na przykład `PipeReader.AdvanceTo(buffer.Start)` `buffer.Start` jeśli nie uległa zmianie spowoduje `PipeReader.ReadAsync` następne wywołanie do powrotu bezpośrednio przed nadejścia nowych danych.</span><span class="sxs-lookup"><span data-stu-id="4f144-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="4f144-237">Przekazywanie niewłaściwych `consumed` wartości `examined` do lub może spowodować nieskończone buforowanie (ewentualne OOM).</span><span class="sxs-lookup"><span data-stu-id="4f144-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="4f144-238">Korzystanie `ReadOnlySequence<byte>` z `PipeReader.AdvanceTo` po wywołaniu może spowodować uszkodzenie pamięci (używać po darmo).</span><span class="sxs-lookup"><span data-stu-id="4f144-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="4f144-239">Niewywołanie `PipeReader.Complete/CompleteAsync` może spowodować przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="4f144-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="4f144-240">Sprawdzanie <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> i zamykanie logiki odczytu przed przetworzeniem buforu powoduje utratę danych.</span><span class="sxs-lookup"><span data-stu-id="4f144-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="4f144-241">Stan wyjścia pętli powinien `ReadResult.Buffer.IsEmpty` być `ReadResult.IsCompleted`oparty na i .</span><span class="sxs-lookup"><span data-stu-id="4f144-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="4f144-242">Wykonanie tego niepoprawnie może spowodować nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="4f144-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="4f144-243">Problematyczny kod</span><span class="sxs-lookup"><span data-stu-id="4f144-243">Problematic code</span></span>

<span data-ttu-id="4f144-244">❌**Utrata danych**</span><span class="sxs-lookup"><span data-stu-id="4f144-244">❌ **Data loss**</span></span>

<span data-ttu-id="4f144-245">Może `ReadResult` zwrócić końcowy segment danych, `IsCompleted` gdy `true`jest ustawiony na .</span><span class="sxs-lookup"><span data-stu-id="4f144-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="4f144-246">Nieodczytywanie tych danych przed wyjściem z pętli odczytu spowoduje utratę danych.</span><span class="sxs-lookup"><span data-stu-id="4f144-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="4f144-247">❌**Nieskończona pętla**</span><span class="sxs-lookup"><span data-stu-id="4f144-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="4f144-248">Następująca logika może spowodować `Result.IsCompleted` nieskończoną pętlę, jeśli jest, `true` ale nigdy nie ma pełnego komunikatu w buforze.</span><span class="sxs-lookup"><span data-stu-id="4f144-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="4f144-249">Oto kolejny fragment kodu z tym samym problemem.</span><span class="sxs-lookup"><span data-stu-id="4f144-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="4f144-250">To sprawdzanie niepustego buforu `ReadResult.IsCompleted`przed sprawdzeniem .</span><span class="sxs-lookup"><span data-stu-id="4f144-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="4f144-251">Ponieważ jest w `else if`, będzie pętli na zawsze, jeśli nigdy nie ma pełnej wiadomości w buforze.</span><span class="sxs-lookup"><span data-stu-id="4f144-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="4f144-252">❌**Nieoczekiwane zawieszenie**</span><span class="sxs-lookup"><span data-stu-id="4f144-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="4f144-253">Bezwarunkowe `PipeReader.AdvanceTo` wywoływanie `buffer.End` z `examined` w pozycji może spowodować zawiesza się podczas analizowania pojedynczej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4f144-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="4f144-254">Następne wywołanie `PipeReader.AdvanceTo` nie wróci, dopóki:</span><span class="sxs-lookup"><span data-stu-id="4f144-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="4f144-255">Jest więcej danych zapisanych na rurze.</span><span class="sxs-lookup"><span data-stu-id="4f144-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="4f144-256">Nowe dane nie zostały wcześniej zbadane.</span><span class="sxs-lookup"><span data-stu-id="4f144-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="4f144-257">❌**Brak pamięci (OOM)**</span><span class="sxs-lookup"><span data-stu-id="4f144-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="4f144-258">W następujących warunkach następujący kod utrzymuje buforowanie aż do wystąpienia: <xref:System.OutOfMemoryException></span><span class="sxs-lookup"><span data-stu-id="4f144-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="4f144-259">Nie ma maksymalnego rozmiaru wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4f144-259">There's no maximum message size.</span></span>
* <span data-ttu-id="4f144-260">Dane zwrócone `PipeReader` z nie tworzą pełnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4f144-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="4f144-261">Na przykład nie zawiera pełnej wiadomości, ponieważ druga strona pisze dużą wiadomość (Na przykład wiadomość 4 GB).</span><span class="sxs-lookup"><span data-stu-id="4f144-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="4f144-262">❌**Uszkodzenie pamięci**</span><span class="sxs-lookup"><span data-stu-id="4f144-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="4f144-263">Podczas pisania pomocników, którzy odczytują bufor, wszelkie `Advance`zwrócone ładunku powinny być kopiowane przed wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="4f144-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="4f144-264">Poniższy przykład zwróci pamięć, która `Pipe` została odrzucona i może użyć jej ponownie do następnej operacji (odczyt/zapis).</span><span class="sxs-lookup"><span data-stu-id="4f144-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="4f144-265">Moduł PipeWriter</span><span class="sxs-lookup"><span data-stu-id="4f144-265">PipeWriter</span></span>

<span data-ttu-id="4f144-266">Zarządza <xref:System.IO.Pipelines.PipeWriter> buforów do zapisu w imieniu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4f144-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="4f144-267">`PipeWriter`implementuje [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span><span class="sxs-lookup"><span data-stu-id="4f144-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="4f144-268">`IBufferWriter<byte>`umożliwia uzyskanie dostępu do buforów do wykonywania zapisów bez dodatkowych kopii buforu.</span><span class="sxs-lookup"><span data-stu-id="4f144-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="4f144-269">Poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="4f144-269">The previous code:</span></span>

* <span data-ttu-id="4f144-270">Żąda buforu o co najmniej 5 `PipeWriter` <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>bajtach z using .</span><span class="sxs-lookup"><span data-stu-id="4f144-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="4f144-271">Zapisuje bajty dla ciągu `"Hello"` ASCII do `Memory<byte>`zwróconego pliku .</span><span class="sxs-lookup"><span data-stu-id="4f144-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="4f144-272">Wywołania <xref:System.IO.Pipelines.PipeWriter.Advance%2A> wskazujące, ile bajtów zostało zapisanych w buforze.</span><span class="sxs-lookup"><span data-stu-id="4f144-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="4f144-273">Opróżnia `PipeWriter`, który wysyła bajty do urządzenia źródłowego.</span><span class="sxs-lookup"><span data-stu-id="4f144-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="4f144-274">Poprzednia metoda zapisu używa buforów `PipeWriter`dostarczonych przez .</span><span class="sxs-lookup"><span data-stu-id="4f144-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="4f144-275">Alternatywnie: <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4f144-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="4f144-276">Kopiuje istniejący `PipeWriter`bufor do pliku .</span><span class="sxs-lookup"><span data-stu-id="4f144-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="4f144-277">Połączenia `GetSpan` `Advance` , w <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>stosownych przypadkach i połączenia .</span><span class="sxs-lookup"><span data-stu-id="4f144-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="4f144-278">Anulowanie</span><span class="sxs-lookup"><span data-stu-id="4f144-278">Cancellation</span></span>

<span data-ttu-id="4f144-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>obsługuje przekazywanie <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="4f144-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="4f144-280">Przekazywanie `CancellationToken` wyników `OperationCanceledException` w if token jest anulowany, gdy istnieje flush oczekujące.</span><span class="sxs-lookup"><span data-stu-id="4f144-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="4f144-281">`PipeWriter.FlushAsync`obsługuje sposób anulowania bieżącej operacji <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> opróżniania za pośrednictwem bez zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4f144-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="4f144-282">`PipeWriter.CancelPendingFlush` Wywołanie powoduje, że `PipeWriter.FlushAsync` bieżące `PipeWriter.WriteAsync` lub <xref:System.IO.Pipelines.FlushResult> następne `IsCanceled` wywołanie lub powrót z ustawionym na `true`.</span><span class="sxs-lookup"><span data-stu-id="4f144-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="4f144-283">Może to być przydatne do zatrzymania plonowania w sposób nieniszczący i niewyjątkowy.</span><span class="sxs-lookup"><span data-stu-id="4f144-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="4f144-284">Często występujące problemy pipewritera</span><span class="sxs-lookup"><span data-stu-id="4f144-284">PipeWriter common problems</span></span>

* <span data-ttu-id="4f144-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>i <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> zwrócić bufor z co najmniej żądaną ilością pamięci.</span><span class="sxs-lookup"><span data-stu-id="4f144-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="4f144-286">**Nie** zakładaj dokładnych rozmiarów buforu.</span><span class="sxs-lookup"><span data-stu-id="4f144-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="4f144-287">Nie ma żadnej gwarancji, że kolejne wywołania zwróci tego samego buforu lub buforu tego samego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="4f144-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="4f144-288">Nowy bufor musi być wymagane <xref:System.IO.Pipelines.PipeWriter.Advance%2A> po wywołaniu, aby kontynuować zapisywanie większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="4f144-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="4f144-289">Wcześniej nabytego bufora nie można zapisać.</span><span class="sxs-lookup"><span data-stu-id="4f144-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="4f144-290">Dzwonienie `GetMemory` lub `GetSpan` gdy jest niepełne `FlushAsync` połączenie, nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="4f144-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="4f144-291">`Complete` Wywołanie `CompleteAsync` lub gdy nie są opróżniane dane może spowodować uszkodzenie pamięci.</span><span class="sxs-lookup"><span data-stu-id="4f144-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="4f144-292">IDuplexPipe (IDuplexPipe)</span><span class="sxs-lookup"><span data-stu-id="4f144-292">IDuplexPipe</span></span>

<span data-ttu-id="4f144-293">Jest <xref:System.IO.Pipelines.IDuplexPipe> to umowa dla typów, które obsługują zarówno czytania i pisania.</span><span class="sxs-lookup"><span data-stu-id="4f144-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="4f144-294">Na przykład połączenie sieciowe będzie reprezentowane `IDuplexPipe`przez .</span><span class="sxs-lookup"><span data-stu-id="4f144-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="4f144-295">W `Pipe` przeciwieństwie `PipeReader` do `PipeWriter`tego, który zawiera a i , `IDuplexPipe` reprezentuje jedną stronę pełnego połączenia dupleksu.</span><span class="sxs-lookup"><span data-stu-id="4f144-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="4f144-296">Oznacza to, że `PipeWriter` to, co jest `PipeReader`napisane do nie będzie odczytywane z .</span><span class="sxs-lookup"><span data-stu-id="4f144-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="4f144-297">Strumienie</span><span class="sxs-lookup"><span data-stu-id="4f144-297">Streams</span></span>

<span data-ttu-id="4f144-298">Podczas odczytywania lub zapisywania danych strumienia, zazwyczaj odczytu danych przy użyciu de-serializatora i zapisu danych przy użyciu serializatora.</span><span class="sxs-lookup"><span data-stu-id="4f144-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="4f144-299">Większość z tych interfejsów API `Stream` strumienia odczytu i zapisu ma parametr.</span><span class="sxs-lookup"><span data-stu-id="4f144-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="4f144-300">Aby ułatwić integrację z tymi `PipeReader` istniejącymi interfejsami API i `PipeWriter` uwidaczniać . <xref:System.IO.Pipelines.PipeReader.AsStream%2A></span><span class="sxs-lookup"><span data-stu-id="4f144-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="4f144-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A>zwraca `Stream` implementację `PipeReader` `PipeWriter`wokół lub .</span><span class="sxs-lookup"><span data-stu-id="4f144-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
