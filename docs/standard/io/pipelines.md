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
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="6d408-103">System.IO.Pipelines w .NET</span><span class="sxs-lookup"><span data-stu-id="6d408-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="6d408-104"><xref:System.IO.Pipelines>to nowa biblioteka, która ma na celu ułatwienie wykonywania wysokiej wydajności we/wy w .NET.</span><span class="sxs-lookup"><span data-stu-id="6d408-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="6d408-105">Jest to biblioteka docelowa .NET Standard, który działa na wszystkich implementacjach platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="6d408-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="6d408-106">Jaki problem rozwiązuje system.IO.Pipelines</span><span class="sxs-lookup"><span data-stu-id="6d408-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="6d408-107">Aplikacje, które analizują dane strumieniowe, składają się z kodu standardowego o wielu wyspecjalizowanych i nietypowych przepływach kodu.</span><span class="sxs-lookup"><span data-stu-id="6d408-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="6d408-108">Standardowy i specjalny kod przypadku jest złożony i trudny do utrzymania.</span><span class="sxs-lookup"><span data-stu-id="6d408-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="6d408-109">`System.IO.Pipelines`został zaprojektowany w celu:</span><span class="sxs-lookup"><span data-stu-id="6d408-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="6d408-110">Mają wysoką wydajność analizowania danych przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="6d408-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="6d408-111">Zmniejsz złożoność kodu.</span><span class="sxs-lookup"><span data-stu-id="6d408-111">Reduce code complexity.</span></span>

<span data-ttu-id="6d408-112">Następujący kod jest typowy dla serwera TCP, który odbiera wiadomości rozdzielane wierszem (rozdzielone) `'\n'`od klienta:</span><span class="sxs-lookup"><span data-stu-id="6d408-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="6d408-113">Poprzedni kod ma kilka problemów:</span><span class="sxs-lookup"><span data-stu-id="6d408-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="6d408-114">Cała wiadomość (koniec wiersza) może nie zostać `ReadAsync`odebrana w jednym wywołaniu .</span><span class="sxs-lookup"><span data-stu-id="6d408-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="6d408-115">To ignorowanie wyniku `stream.ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="6d408-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="6d408-116">`stream.ReadAsync`zwraca ilość odczytanych danych.</span><span class="sxs-lookup"><span data-stu-id="6d408-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="6d408-117">Nie obsługuje przypadku, w którym wiele wierszy `ReadAsync` są odczytywane w jednym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="6d408-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="6d408-118">Przydziela tablicę `byte` z każdym odczytem.</span><span class="sxs-lookup"><span data-stu-id="6d408-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="6d408-119">Aby rozwiązać poprzednie problemy, wymagane są następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="6d408-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="6d408-120">Buforuj przychodzące dane, dopóki nie zostanie znaleziony nowy wiersz.</span><span class="sxs-lookup"><span data-stu-id="6d408-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="6d408-121">Przeanalizować wszystkie wiersze zwrócone w buforze.</span><span class="sxs-lookup"><span data-stu-id="6d408-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="6d408-122">Możliwe, że linia jest większa niż 1 KB (1024 bajtów).</span><span class="sxs-lookup"><span data-stu-id="6d408-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="6d408-123">Kod musi zmienić rozmiar buforu wejściowego, dopóki ogranicznik zostanie znaleziony w celu dopasowania pełnego wiersza wewnątrz buforu.</span><span class="sxs-lookup"><span data-stu-id="6d408-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="6d408-124">Jeśli rozmiar buforu zostanie zmieniona, więcej kopii buforu jest dokonywanych w miarę pojawiania się dłuższych wierszy w danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6d408-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="6d408-125">Aby zmniejszyć ilość zmarnowanego miejsca, zgłoś bufor używany do odczytu linii.</span><span class="sxs-lookup"><span data-stu-id="6d408-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="6d408-126">Należy rozważyć użycie buforu buforu buforu, aby uniknąć przydzielania pamięci wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="6d408-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="6d408-127">Poniższy kod rozwiązuje niektóre z tych problemów:</span><span class="sxs-lookup"><span data-stu-id="6d408-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="6d408-128">Poprzedni kod jest złożony i nie rozwiązuje wszystkich zidentyfikowanych problemów.</span><span class="sxs-lookup"><span data-stu-id="6d408-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="6d408-129">Sieci o wysokiej wydajności zwykle oznacza pisanie bardzo złożony kod, aby zmaksymalizować wydajność.</span><span class="sxs-lookup"><span data-stu-id="6d408-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="6d408-130">`System.IO.Pipelines`został zaprojektowany, aby ułatwić pisanie tego typu kodu.</span><span class="sxs-lookup"><span data-stu-id="6d408-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="6d408-131">Rury</span><span class="sxs-lookup"><span data-stu-id="6d408-131">Pipe</span></span>

<span data-ttu-id="6d408-132">Klasa <xref:System.IO.Pipelines.Pipe> może służyć do `PipeWriter/PipeReader` tworzenia pary.</span><span class="sxs-lookup"><span data-stu-id="6d408-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="6d408-133">Wszystkie dane zapisane `PipeWriter` w the `PipeReader`jest dostępny w:</span><span class="sxs-lookup"><span data-stu-id="6d408-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="6d408-134">Podstawowe użycie rur</span><span class="sxs-lookup"><span data-stu-id="6d408-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="6d408-135">Istnieją dwie pętle:</span><span class="sxs-lookup"><span data-stu-id="6d408-135">There are two loops:</span></span>

* <span data-ttu-id="6d408-136">`FillPipeAsync`odczytuje `Socket` z i zapisuje do `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="6d408-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="6d408-137">`ReadPipeAsync`odczytuje `PipeReader` z i analizuje wiersze przychodzące.</span><span class="sxs-lookup"><span data-stu-id="6d408-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="6d408-138">Nie ma żadnych jawnych buforów przydzielonych.</span><span class="sxs-lookup"><span data-stu-id="6d408-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="6d408-139">Wszystkie zarządzanie buforem jest `PipeReader` `PipeWriter` delegowane do i implementacji.</span><span class="sxs-lookup"><span data-stu-id="6d408-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="6d408-140">Delegowanie zarządzania buforem ułatwia korzystanie z kodu skupić się wyłącznie na logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="6d408-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="6d408-141">W pierwszej pętli:</span><span class="sxs-lookup"><span data-stu-id="6d408-141">In the first loop:</span></span>

* <span data-ttu-id="6d408-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>jest wywoływana, aby uzyskać pamięć z modułu zapisującego.</span><span class="sxs-lookup"><span data-stu-id="6d408-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="6d408-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>jest wywoływana, `PipeWriter` aby poinformować, ile danych zostało zapisanych w buforze.</span><span class="sxs-lookup"><span data-stu-id="6d408-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="6d408-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>jest wezwany do udostępnienia `PipeReader`danych do .</span><span class="sxs-lookup"><span data-stu-id="6d408-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="6d408-145">W drugiej pętli `PipeReader` zużywa bufory zapisane przez `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="6d408-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="6d408-146">Bufory pochodzą z gniazda.</span><span class="sxs-lookup"><span data-stu-id="6d408-146">The buffers come from the socket.</span></span> <span data-ttu-id="6d408-147">Wezwanie do: `PipeReader.ReadAsync`</span><span class="sxs-lookup"><span data-stu-id="6d408-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="6d408-148">Zwraca <xref:System.IO.Pipelines.ReadResult> zawierający dwie ważne informacje:</span><span class="sxs-lookup"><span data-stu-id="6d408-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="6d408-149">Dane, które zostały odczytane `ReadOnlySequence<byte>`w formie .</span><span class="sxs-lookup"><span data-stu-id="6d408-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="6d408-150">Wartość logiczna `IsCompleted` wskazująca, czy osiągnięto koniec danych (EOF).</span><span class="sxs-lookup"><span data-stu-id="6d408-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="6d408-151">Po znalezieniu ogranicznika końca wiersza (EOL) i przeanalizowaniu wiersza:</span><span class="sxs-lookup"><span data-stu-id="6d408-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="6d408-152">Logika przetwarza bufor, aby pominąć to, co jest już przetworzone.</span><span class="sxs-lookup"><span data-stu-id="6d408-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="6d408-153">`PipeReader.AdvanceTo`jest wywoływana, `PipeReader` aby poinformować, ile danych zostało zużyte i zbadane.</span><span class="sxs-lookup"><span data-stu-id="6d408-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="6d408-154">Pętle czytnika i pisarza kończą się wywołaniem `Complete`.</span><span class="sxs-lookup"><span data-stu-id="6d408-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="6d408-155">`Complete`pozwala podstawowej pipe zwolnić pamięci, które przydzielone.</span><span class="sxs-lookup"><span data-stu-id="6d408-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="6d408-156">Kontrola podciśnienia i przepływu</span><span class="sxs-lookup"><span data-stu-id="6d408-156">Backpressure and flow control</span></span>

<span data-ttu-id="6d408-157">Idealnie, czytanie i analizowanie współpracują ze sobą:</span><span class="sxs-lookup"><span data-stu-id="6d408-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="6d408-158">Wątek zapisu zużywa dane z sieci i umieszcza je w buforach.</span><span class="sxs-lookup"><span data-stu-id="6d408-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="6d408-159">Wątek analizy jest odpowiedzialny za konstruowanie odpowiednich struktur danych.</span><span class="sxs-lookup"><span data-stu-id="6d408-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="6d408-160">Zazwyczaj analizowanie zajmuje więcej czasu niż tylko kopiowanie bloków danych z sieci:</span><span class="sxs-lookup"><span data-stu-id="6d408-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="6d408-161">Wątek odczytu wyprzedza wątku analizowania.</span><span class="sxs-lookup"><span data-stu-id="6d408-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="6d408-162">Wątek odczytu musi spowolnić lub przydzielić więcej pamięci do przechowywania danych dla wątku analizowania.</span><span class="sxs-lookup"><span data-stu-id="6d408-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="6d408-163">Aby uzyskać optymalną wydajność, istnieje równowaga między częstymi przerwami a przydzielaniem większej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="6d408-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="6d408-164">Aby rozwiązać poprzedni problem, `Pipe` ma dwa ustawienia do kontrolowania przepływu danych:</span><span class="sxs-lookup"><span data-stu-id="6d408-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="6d408-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Określa, ile danych powinno być <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> buforowane przed wywołaniem wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="6d408-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="6d408-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Określa, ile danych czytelnik musi obserwować `PipeWriter.FlushAsync` przed wznowieniem połączeń.</span><span class="sxs-lookup"><span data-stu-id="6d408-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![Diagram z ResumeWriterThreshold i PauseWriterThreshold](./media/pipelines/resume-pause.png)

<span data-ttu-id="6d408-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="6d408-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="6d408-169">Zwraca niekompletną, `ValueTask<FlushResult>` gdy ilość `Pipe` danych `PauseWriterThreshold`w krzyżyk .</span><span class="sxs-lookup"><span data-stu-id="6d408-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="6d408-170">Kończy `ValueTask<FlushResult>` się, gdy `ResumeWriterThreshold`staje się niższa niż .</span><span class="sxs-lookup"><span data-stu-id="6d408-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="6d408-171">Dwie wartości są używane, aby zapobiec szybkiej cyklu, które mogą wystąpić, jeśli jedna wartość jest używana.</span><span class="sxs-lookup"><span data-stu-id="6d408-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="6d408-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6d408-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="6d408-173">PipeScheduler (Wychylik rur)</span><span class="sxs-lookup"><span data-stu-id="6d408-173">PipeScheduler</span></span>

<span data-ttu-id="6d408-174">Zazwyczaj podczas `async` używania i `await`, kod asynchroniczne <xref:System.Threading.Tasks.TaskScheduler> wznawia <xref:System.Threading.SynchronizationContext>na albo na lub na bieżącym .</span><span class="sxs-lookup"><span data-stu-id="6d408-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="6d408-175">Podczas wykonywania we/wy, ważne jest, aby mieć szczegółową kontrolę nad tym, gdzie jest wykonywana liczba we/wy.</span><span class="sxs-lookup"><span data-stu-id="6d408-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="6d408-176">Ta kontrola umożliwia efektywne korzystanie z pamięci podręcznej procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="6d408-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="6d408-177">Wydajne buforowanie ma kluczowe znaczenie dla aplikacji o wysokiej wydajności, takich jak serwery sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6d408-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="6d408-178"><xref:System.IO.Pipelines.PipeScheduler>zapewnia kontrolę nad gdzie wywołania zwrotne asynchroniczne uruchomić.</span><span class="sxs-lookup"><span data-stu-id="6d408-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="6d408-179">Domyślnie:</span><span class="sxs-lookup"><span data-stu-id="6d408-179">By default:</span></span>

* <span data-ttu-id="6d408-180">Używany <xref:System.Threading.SynchronizationContext> jest prąd.</span><span class="sxs-lookup"><span data-stu-id="6d408-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="6d408-181">Jeśli nie ma `SynchronizationContext`, używa puli wątków do uruchamiania wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="6d408-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="6d408-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) jest <xref:System.IO.Pipelines.PipeScheduler> implementacją, która kolejkuje wywołania zwrotne do puli wątków.</span><span class="sxs-lookup"><span data-stu-id="6d408-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="6d408-183">`PipeScheduler.ThreadPool`jest domyślnym i ogólnie najlepszym wyborem.</span><span class="sxs-lookup"><span data-stu-id="6d408-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="6d408-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) może powodować niezamierzone konsekwencje, takie jak zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="6d408-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="6d408-185">Resetowanie rur</span><span class="sxs-lookup"><span data-stu-id="6d408-185">Pipe reset</span></span>

<span data-ttu-id="6d408-186">Często jest to skuteczne, aby `Pipe` ponownie użyć obiektu.</span><span class="sxs-lookup"><span data-stu-id="6d408-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="6d408-187">Aby zresetować potok, wywołaj <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> po zakończeniu `PipeReader` i `PipeWriter` zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="6d408-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="6d408-188">Czytnik potoków</span><span class="sxs-lookup"><span data-stu-id="6d408-188">PipeReader</span></span>

<span data-ttu-id="6d408-189"><xref:System.IO.Pipelines.PipeReader>zarządza pamięcią w imieniu osoby dzwoniącej.</span><span class="sxs-lookup"><span data-stu-id="6d408-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="6d408-190">**Zawsze** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> dzwonić <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>po wywołaniu .</span><span class="sxs-lookup"><span data-stu-id="6d408-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6d408-191">Dzięki temu `PipeReader` informuje, kiedy wywołujący jest wykonywana z pamięci, dzięki czemu można go śledzić.</span><span class="sxs-lookup"><span data-stu-id="6d408-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="6d408-192">Zwrócony `ReadOnlySequence<byte>` `PipeReader.ReadAsync` z jest prawidłowy `PipeReader.AdvanceTo`tylko do momentu wywołania .</span><span class="sxs-lookup"><span data-stu-id="6d408-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="6d408-193">Jest to nielegalne `ReadOnlySequence<byte>` w `PipeReader.AdvanceTo`użyciu po wywołaniu .</span><span class="sxs-lookup"><span data-stu-id="6d408-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="6d408-194">`PipeReader.AdvanceTo`przyjmuje <xref:System.SequencePosition> dwa argumenty:</span><span class="sxs-lookup"><span data-stu-id="6d408-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="6d408-195">Pierwszy argument określa, ile pamięci zostało zużyte.</span><span class="sxs-lookup"><span data-stu-id="6d408-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="6d408-196">Drugi argument określa, jaka część buforu została zaobserwowana.</span><span class="sxs-lookup"><span data-stu-id="6d408-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="6d408-197">Oznaczanie danych jako zużyte oznacza, że potok może zwrócić pamięć do podstawowej puli buforów.</span><span class="sxs-lookup"><span data-stu-id="6d408-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="6d408-198">Oznaczanie danych zgodnie z obserwowanymi elementami określa, co `PipeReader.ReadAsync` robi następne wywołanie.</span><span class="sxs-lookup"><span data-stu-id="6d408-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="6d408-199">Oznaczanie wszystkiego, co obserwuje, `PipeReader.ReadAsync` oznacza, że następne wywołanie nie powróci, dopóki nie zostanie zapisanych więcej danych do potoku.</span><span class="sxs-lookup"><span data-stu-id="6d408-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="6d408-200">Każda inna wartość spowoduje, `PipeReader.ReadAsync` że następne wywołanie zostanie natychmiast odesłane z obserwowanymi *i* niezaobionymi danymi, ale nie danymi, które zostały już wykorzystane.</span><span class="sxs-lookup"><span data-stu-id="6d408-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but not data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="6d408-201">Odczytywanie scenariuszy przesyłania strumieniowego danych</span><span class="sxs-lookup"><span data-stu-id="6d408-201">Read streaming data scenarios</span></span>

<span data-ttu-id="6d408-202">Istnieje kilka typowych wzorców, które pojawiają się podczas próby odczytu danych przesyłania strumieniowego:</span><span class="sxs-lookup"><span data-stu-id="6d408-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="6d408-203">Biorąc pod uwagę strumień danych, przeanalizować pojedynczą wiadomość.</span><span class="sxs-lookup"><span data-stu-id="6d408-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="6d408-204">Biorąc pod uwagę strumień danych, przeanalizyj wszystkie dostępne komunikaty.</span><span class="sxs-lookup"><span data-stu-id="6d408-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="6d408-205">W poniższych przykładach użyto `TryParseMessage` metody analizowania wiadomości z pliku `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="6d408-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="6d408-206">`TryParseMessage`analizuje pojedynczy komunikat i aktualizuj bufor wejściowy, aby przyciąć analizowany komunikat z buforu.</span><span class="sxs-lookup"><span data-stu-id="6d408-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="6d408-207">`TryParseMessage`nie jest częścią platformy .NET, jest to metoda napisana przez użytkownika używana w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="6d408-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="6d408-208">Czytanie pojedynczej wiadomości</span><span class="sxs-lookup"><span data-stu-id="6d408-208">Read a single message</span></span>

<span data-ttu-id="6d408-209">Poniższy kod odczytuje pojedynczą wiadomość z a `PipeReader` i zwraca ją do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6d408-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="6d408-210">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="6d408-210">The preceding code:</span></span>

* <span data-ttu-id="6d408-211">Analizuje pojedynczą wiadomość.</span><span class="sxs-lookup"><span data-stu-id="6d408-211">Parses a single message.</span></span>
* <span data-ttu-id="6d408-212">Aktualizuje zużyte `SequencePosition` i zbadane, `SequencePosition` aby wskazać początek przyciętego buforu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="6d408-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="6d408-213">Dwa `SequencePosition` argumenty są `TryParseMessage` aktualizowane, ponieważ usuwa analizowany komunikat z buforu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="6d408-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="6d408-214">Ogólnie rzecz biorąc podczas analizowania pojedynczej wiadomości z bufora, zbadane stanowisko powinno być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="6d408-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="6d408-215">Koniec wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6d408-215">The end of the message.</span></span>
* <span data-ttu-id="6d408-216">Koniec odebranego buforu, jeśli nie znaleziono żadnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6d408-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="6d408-217">Przypadek pojedynczej wiadomości ma największe możliwości błędów.</span><span class="sxs-lookup"><span data-stu-id="6d408-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="6d408-218">Przekazywanie nieprawidłowe wartości do *zbadane* może spowodować wyjątek braku pamięci lub nieskończonej pętli.</span><span class="sxs-lookup"><span data-stu-id="6d408-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="6d408-219">Aby uzyskać więcej informacji, zobacz [PipeReader typowe problemy](#gotchas) sekcji w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="6d408-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="6d408-220">Czytanie wielu wiadomości</span><span class="sxs-lookup"><span data-stu-id="6d408-220">Reading multiple messages</span></span>

<span data-ttu-id="6d408-221">Poniższy kod odczytuje `PipeReader` wszystkie `ProcessMessageAsync` wiadomości z i wywołuje na każdym.</span><span class="sxs-lookup"><span data-stu-id="6d408-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="6d408-222">Anulowanie</span><span class="sxs-lookup"><span data-stu-id="6d408-222">Cancellation</span></span>

<span data-ttu-id="6d408-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="6d408-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="6d408-224">Obsługuje przekazywanie pliku <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="6d408-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="6d408-225"><xref:System.OperationCanceledException> Zgłasza, jeśli `CancellationToken` jest anulowany, gdy jest oczekiwany odczyt.</span><span class="sxs-lookup"><span data-stu-id="6d408-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="6d408-226">Obsługuje sposób anulowania bieżącej <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>operacji odczytu za pośrednictwem , co pozwala uniknąć wywoływania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6d408-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="6d408-227">Wywołanie `PipeReader.CancelPendingRead` powoduje, że `PipeReader.ReadAsync` bieżące <xref:System.IO.Pipelines.ReadResult> lub `IsCanceled` następne `true`wywołanie do zwrócenia z zestawem do .</span><span class="sxs-lookup"><span data-stu-id="6d408-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="6d408-228">Może to być przydatne do zatrzymania istniejącej pętli odczytu w sposób nieniszczący i nie wyjątkowy.</span><span class="sxs-lookup"><span data-stu-id="6d408-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="6d408-229">Typowe problemy pipereader</span><span class="sxs-lookup"><span data-stu-id="6d408-229">PipeReader common problems</span></span>

* <span data-ttu-id="6d408-230">Przekazywanie niewłaściwych `consumed` `examined` wartości do lub może spowodować odczyt już odczytanych danych.</span><span class="sxs-lookup"><span data-stu-id="6d408-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="6d408-231">Przejście `buffer.End` w sposób zbadany może skutkować:</span><span class="sxs-lookup"><span data-stu-id="6d408-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="6d408-232">Dane wstrzymane</span><span class="sxs-lookup"><span data-stu-id="6d408-232">Stalled data</span></span>
  * <span data-ttu-id="6d408-233">Ewentualnie ewentualny wyjątek braku pamięci (OOM), jeśli dane nie są używane.</span><span class="sxs-lookup"><span data-stu-id="6d408-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="6d408-234">Na przykład `PipeReader.AdvanceTo(position, buffer.End)` podczas przetwarzania pojedynczej wiadomości w czasie z buforu.</span><span class="sxs-lookup"><span data-stu-id="6d408-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="6d408-235">Przekazywanie nieprawidłowych `consumed` `examined` wartości do lub może spowodować nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="6d408-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="6d408-236">Na przykład `PipeReader.AdvanceTo(buffer.Start)` `buffer.Start` jeśli nie został zmieniony spowoduje `PipeReader.ReadAsync` następne wywołanie do powrotu bezpośrednio przed nadejściem nowych danych.</span><span class="sxs-lookup"><span data-stu-id="6d408-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="6d408-237">Przekazywanie nieprawidłowych `consumed` `examined` wartości do lub może spowodować nieskończone buforowanie (ewentualne OOM).</span><span class="sxs-lookup"><span data-stu-id="6d408-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="6d408-238">Korzystanie `ReadOnlySequence<byte>` z `PipeReader.AdvanceTo` po wywołaniu może spowodować uszkodzenie pamięci (użycie po wolnym).</span><span class="sxs-lookup"><span data-stu-id="6d408-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="6d408-239">Niepodjęcie połączenia `PipeReader.Complete/CompleteAsync` może spowodować przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="6d408-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="6d408-240">Sprawdzanie <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> i zamykanie logiki odczytu przed przetworzeniem buforu powoduje utratę danych.</span><span class="sxs-lookup"><span data-stu-id="6d408-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="6d408-241">Warunek wyjścia pętli powinien `ReadResult.Buffer.IsEmpty` być `ReadResult.IsCompleted`oparty na i .</span><span class="sxs-lookup"><span data-stu-id="6d408-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="6d408-242">W ten sposób niepoprawnie może spowodować nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="6d408-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="6d408-243">Problematyczny kod</span><span class="sxs-lookup"><span data-stu-id="6d408-243">Problematic code</span></span>

<span data-ttu-id="6d408-244">❌**Utrata danych**</span><span class="sxs-lookup"><span data-stu-id="6d408-244">❌ **Data loss**</span></span>

<span data-ttu-id="6d408-245">Może `ReadResult` zwrócić końcowy segment danych, `IsCompleted` gdy `true`jest ustawiony na .</span><span class="sxs-lookup"><span data-stu-id="6d408-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="6d408-246">Nie odczytywanie tych danych przed zamknięciem pętli odczytu spowoduje utratę danych.</span><span class="sxs-lookup"><span data-stu-id="6d408-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="6d408-247">❌**Nieskończona pętla**</span><span class="sxs-lookup"><span data-stu-id="6d408-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="6d408-248">Następująca logika może spowodować nieskończoną pętlę, `Result.IsCompleted` jeśli jest, ale nigdy nie ma `true` pełnego komunikatu w buforze.</span><span class="sxs-lookup"><span data-stu-id="6d408-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="6d408-249">Oto kolejny fragment kodu z tym samym problemem.</span><span class="sxs-lookup"><span data-stu-id="6d408-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="6d408-250">Przed sprawdzeniem jest sprawdzanie niepustego `ReadResult.IsCompleted`buforu.</span><span class="sxs-lookup"><span data-stu-id="6d408-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="6d408-251">Ponieważ jest w `else if`, będzie pętla na zawsze, jeśli nigdy nie ma pełnego komunikatu w buforze.</span><span class="sxs-lookup"><span data-stu-id="6d408-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="6d408-252">❌**Nieoczekiwane zawieszenie**</span><span class="sxs-lookup"><span data-stu-id="6d408-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="6d408-253">Bezwarunkowo `PipeReader.AdvanceTo` wywołanie `buffer.End` z `examined` w pozycji może spowodować zawiesza się podczas analizowania pojedynczej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6d408-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="6d408-254">Następne połączenie `PipeReader.AdvanceTo` nie powróci, dopóki:</span><span class="sxs-lookup"><span data-stu-id="6d408-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="6d408-255">Więcej danych jest zapisywanych na potoku.</span><span class="sxs-lookup"><span data-stu-id="6d408-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="6d408-256">Nowe dane nie zostały wcześniej zbadane.</span><span class="sxs-lookup"><span data-stu-id="6d408-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="6d408-257">❌**Brak pamięci (OOM)**</span><span class="sxs-lookup"><span data-stu-id="6d408-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="6d408-258">Z następujących warunków, następujący kod utrzymuje <xref:System.OutOfMemoryException> buforowanie, dopóki nie wystąpi:</span><span class="sxs-lookup"><span data-stu-id="6d408-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="6d408-259">Nie ma maksymalnego rozmiaru wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6d408-259">There's no maximum message size.</span></span>
* <span data-ttu-id="6d408-260">Dane zwrócone `PipeReader` z nie tworzą pełny komunikat.</span><span class="sxs-lookup"><span data-stu-id="6d408-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="6d408-261">Na przykład nie robi pełny komunikat, ponieważ druga strona jest pisanie dużej wiadomości (Na przykład, komunikat 4 GB).</span><span class="sxs-lookup"><span data-stu-id="6d408-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="6d408-262">❌**Uszkodzenie pamięci**</span><span class="sxs-lookup"><span data-stu-id="6d408-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="6d408-263">Podczas pisania pomocników, które odczytywali bufor, każdy `Advance`zwrócony ładunek powinien zostać skopiowany przed wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="6d408-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="6d408-264">Poniższy przykład zwróci pamięć, która `Pipe` została odrzucona i może ponownie użyć go do następnej operacji (odczyt/zapis).</span><span class="sxs-lookup"><span data-stu-id="6d408-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="6d408-265">PipeWriter (Pisarz fajek)</span><span class="sxs-lookup"><span data-stu-id="6d408-265">PipeWriter</span></span>

<span data-ttu-id="6d408-266">Zarządza <xref:System.IO.Pipelines.PipeWriter> buforów do pisania w imieniu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6d408-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="6d408-267">`PipeWriter`implementuje [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span><span class="sxs-lookup"><span data-stu-id="6d408-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="6d408-268">`IBufferWriter<byte>`umożliwia uzyskanie dostępu do buforów do wykonywania zapisów bez dodatkowych kopii buforu.</span><span class="sxs-lookup"><span data-stu-id="6d408-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="6d408-269">Poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="6d408-269">The previous code:</span></span>

* <span data-ttu-id="6d408-270">Żąda buforu o rozmiarze co `PipeWriter` najmniej <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>5 bajtów z using .</span><span class="sxs-lookup"><span data-stu-id="6d408-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="6d408-271">Zapisuje bajty dla ciągu `"Hello"` ASCII `Memory<byte>`do zwracanych .</span><span class="sxs-lookup"><span data-stu-id="6d408-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="6d408-272">Wywołania, <xref:System.IO.Pipelines.PipeWriter.Advance%2A> aby wskazać, ile bajtów zostały zapisane w buforze.</span><span class="sxs-lookup"><span data-stu-id="6d408-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="6d408-273">Opróżnia `PipeWriter`, który wysyła bajty do urządzenia źródłowego.</span><span class="sxs-lookup"><span data-stu-id="6d408-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="6d408-274">Poprzednia metoda zapisu używa buforów `PipeWriter`dostarczonych przez .</span><span class="sxs-lookup"><span data-stu-id="6d408-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="6d408-275">Alternatywnie: <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6d408-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="6d408-276">Kopiuje istniejący `PipeWriter`bufor do pliku .</span><span class="sxs-lookup"><span data-stu-id="6d408-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="6d408-277">Połączenia `GetSpan` `Advance` , w <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>razie potrzeby i połączenia .</span><span class="sxs-lookup"><span data-stu-id="6d408-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="6d408-278">Anulowanie</span><span class="sxs-lookup"><span data-stu-id="6d408-278">Cancellation</span></span>

<span data-ttu-id="6d408-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>obsługuje przekazywanie <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="6d408-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="6d408-280">Przekazywanie `CancellationToken` wyników, `OperationCanceledException` jeśli token zostanie anulowany, gdy istnieje spłukiwanie.</span><span class="sxs-lookup"><span data-stu-id="6d408-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="6d408-281">`PipeWriter.FlushAsync`obsługuje sposób, aby anulować <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> bieżącą operację opróżniania za pośrednictwem bez wywoływania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6d408-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="6d408-282">Wywołanie `PipeWriter.CancelPendingFlush` powoduje, że `PipeWriter.FlushAsync` bieżące lub następne wywołanie do lub `PipeWriter.WriteAsync` do zwrócenia z <xref:System.IO.Pipelines.FlushResult> `IsCanceled` zestawem do `true`.</span><span class="sxs-lookup"><span data-stu-id="6d408-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="6d408-283">Może to być przydatne do zatrzymania plonowania równo w sposób nieniszczący i nie-wyjątkowy.</span><span class="sxs-lookup"><span data-stu-id="6d408-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="6d408-284">Typowe problemy PipeWriter</span><span class="sxs-lookup"><span data-stu-id="6d408-284">PipeWriter common problems</span></span>

* <span data-ttu-id="6d408-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>i <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> zwrócić bufor z co najmniej żądaną ilością pamięci.</span><span class="sxs-lookup"><span data-stu-id="6d408-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="6d408-286">**Nie** zakładaj dokładnych rozmiarów buforu.</span><span class="sxs-lookup"><span data-stu-id="6d408-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="6d408-287">Nie ma żadnej gwarancji, że kolejne wywołania zwróci ten sam bufor lub bufor o tym samym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="6d408-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="6d408-288">Nowy bufor musi być wymagane <xref:System.IO.Pipelines.PipeWriter.Advance%2A> po wywołaniu, aby kontynuować zapisywanie większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="6d408-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="6d408-289">Wcześniej nabyty bufor nie może być zapisywany.</span><span class="sxs-lookup"><span data-stu-id="6d408-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="6d408-290">`GetMemory` Dzwonienie `GetSpan` lub gdy istnieje niekompletne `FlushAsync` połączenie, nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="6d408-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="6d408-291">`Complete` Wywołanie `CompleteAsync` lub gdy nie ma niefluchowanych danych może spowodować uszkodzenie pamięci.</span><span class="sxs-lookup"><span data-stu-id="6d408-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="6d408-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="6d408-292">IDuplexPipe</span></span>

<span data-ttu-id="6d408-293">Jest <xref:System.IO.Pipelines.IDuplexPipe> to umowa dla typów, które obsługują zarówno odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="6d408-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="6d408-294">Na przykład połączenie sieciowe będzie reprezentowane przez plik `IDuplexPipe`.</span><span class="sxs-lookup"><span data-stu-id="6d408-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="6d408-295">W `Pipe` przeciwieństwie `PipeReader` do `PipeWriter`tego, który zawiera i a , `IDuplexPipe` reprezentuje jedną stronę połączenia pełnego dupleksu.</span><span class="sxs-lookup"><span data-stu-id="6d408-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="6d408-296">Oznacza to, że to, co jest napisane do `PipeWriter` nie będą odczytywane z `PipeReader`.</span><span class="sxs-lookup"><span data-stu-id="6d408-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="6d408-297">Strumienie</span><span class="sxs-lookup"><span data-stu-id="6d408-297">Streams</span></span>

<span data-ttu-id="6d408-298">Podczas odczytywania lub zapisywania danych strumienia, zazwyczaj odczytywać dane przy użyciu de-serializatora i zapisywać dane przy użyciu serializatora.</span><span class="sxs-lookup"><span data-stu-id="6d408-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="6d408-299">Większość z tych interfejsów API strumienia odczytu i zapisu `Stream` ma parametr.</span><span class="sxs-lookup"><span data-stu-id="6d408-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="6d408-300">Aby ułatwić integrację z tymi istniejącymi `PipeReader` interfejsami API i `PipeWriter` udostępnić program <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d408-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="6d408-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A>zwraca `Stream` implementację `PipeReader` wokół `PipeWriter`lub .</span><span class="sxs-lookup"><span data-stu-id="6d408-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
