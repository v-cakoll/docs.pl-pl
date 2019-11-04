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
ms.openlocfilehash: 54b5f97aca131f52b9b5d9f54d7fa5ec00ba3d5b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423675"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="075b4-103">System. IO. potoki w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="075b4-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="075b4-104"><xref:System.IO.Pipelines> to nowa biblioteka, która umożliwia łatwiejsze wykonywanie operacji we/wy na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="075b4-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="075b4-105">Jest to biblioteka ukierunkowana .NET Standard, która działa na wszystkich implementacjach platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="075b4-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="075b4-106">Jaki problem rozwiązuje system. IO. potoki</span><span class="sxs-lookup"><span data-stu-id="075b4-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="075b4-107">Aplikacje, które analizują dane przesyłane strumieniowo, składają się z kodu standardowego, który ma wiele wyspecjalizowanych i nietypowych przepływów kodu.</span><span class="sxs-lookup"><span data-stu-id="075b4-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="075b4-108">Kod standardowy i szczególny przypadek jest skomplikowany i trudny do utrzymania.</span><span class="sxs-lookup"><span data-stu-id="075b4-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="075b4-109">`System.IO.Pipelines` został zaprojektowany z myślą o:</span><span class="sxs-lookup"><span data-stu-id="075b4-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="075b4-110">Przeanalizowanie danych przesyłanych strumieniowo o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="075b4-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="075b4-111">Zmniejsz złożoność kodu.</span><span class="sxs-lookup"><span data-stu-id="075b4-111">Reduce code complexity.</span></span>

<span data-ttu-id="075b4-112">Poniższy kod jest typowy dla serwera TCP, który odbiera komunikaty rozdzielane wierszami (ograniczone przez `'\n'`) od klienta:</span><span class="sxs-lookup"><span data-stu-id="075b4-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="075b4-113">Poprzedni kod zawiera kilka problemów:</span><span class="sxs-lookup"><span data-stu-id="075b4-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="075b4-114">Cały komunikat (koniec wiersza) może nie zostać odebrany w jednym wywołaniu do `ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="075b4-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="075b4-115">Zostanie zignorowany wynik `stream.ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="075b4-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="075b4-116">`stream.ReadAsync` zwraca ilość danych, które zostały odczytane.</span><span class="sxs-lookup"><span data-stu-id="075b4-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="075b4-117">Nie obsługuje przypadku, w którym wiele wierszy jest odczytywanych w pojedynczym wywołaniu `ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="075b4-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="075b4-118">Przypisuje tablicę `byte` z każdym odczytem.</span><span class="sxs-lookup"><span data-stu-id="075b4-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="075b4-119">Aby rozwiązać powyższe problemy, wymagane są następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="075b4-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="075b4-120">Buforuj dane przychodzące do momentu znalezienia nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="075b4-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="075b4-121">Przeanalizuj wszystkie wiersze zwrócone w buforze.</span><span class="sxs-lookup"><span data-stu-id="075b4-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="075b4-122">Istnieje możliwość, że wiersz jest większy niż 1 KB (1024 bajtów).</span><span class="sxs-lookup"><span data-stu-id="075b4-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="075b4-123">Kod musi zmienić rozmiar buforu wejściowego do momentu, w którym zostanie znaleziony ogranicznik, aby dopasować cały wiersz w buforze.</span><span class="sxs-lookup"><span data-stu-id="075b4-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="075b4-124">Jeśli rozmiar buforu jest zmieniany, w danych wejściowych są umieszczane więcej kopii buforów.</span><span class="sxs-lookup"><span data-stu-id="075b4-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="075b4-125">Aby zmniejszyć ilość zajętego miejsca, należy skompaktować bufor używany do odczytywania wierszy.</span><span class="sxs-lookup"><span data-stu-id="075b4-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="075b4-126">Rozważ użycie puli buforów, aby uniknąć wielokrotnego przydzielania pamięci.</span><span class="sxs-lookup"><span data-stu-id="075b4-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="075b4-127">Poniższy kod dotyczy niektórych z następujących problemów:</span><span class="sxs-lookup"><span data-stu-id="075b4-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="075b4-128">Poprzedni kod jest skomplikowany i nie dotyczy wszystkich zidentyfikowanych problemów.</span><span class="sxs-lookup"><span data-stu-id="075b4-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="075b4-129">Wysoka wydajność sieci zwykle oznacza pisanie bardzo złożonego kodu w celu zmaksymalizowania wydajności.</span><span class="sxs-lookup"><span data-stu-id="075b4-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="075b4-130">`System.IO.Pipelines` został zaprojektowany, aby ułatwić pisanie tego typu kodu.</span><span class="sxs-lookup"><span data-stu-id="075b4-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

## <a name="pipe"></a><span data-ttu-id="075b4-131">Wodzie</span><span class="sxs-lookup"><span data-stu-id="075b4-131">Pipe</span></span>

<span data-ttu-id="075b4-132">Klasy <xref:System.IO.Pipelines.Pipe> można użyć do utworzenia pary `PipeWriter/PipeReader`.</span><span class="sxs-lookup"><span data-stu-id="075b4-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="075b4-133">Wszystkie dane zapisywane do `PipeWriter` są dostępne w `PipeReader`:</span><span class="sxs-lookup"><span data-stu-id="075b4-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="075b4-134">Podstawowe użycie potoków</span><span class="sxs-lookup"><span data-stu-id="075b4-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="075b4-135">Istnieją dwie pętle:</span><span class="sxs-lookup"><span data-stu-id="075b4-135">There are two loops:</span></span>

* <span data-ttu-id="075b4-136">`FillPipeAsync` odczytuje z `Socket` i zapisuje w `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="075b4-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="075b4-137">`ReadPipeAsync` odczytuje z `PipeReader` i analizuje linie przychodzące.</span><span class="sxs-lookup"><span data-stu-id="075b4-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="075b4-138">Nie ma żadnych jawnie przyznanych buforów.</span><span class="sxs-lookup"><span data-stu-id="075b4-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="075b4-139">Wszystkie Zarządzanie buforem jest delegowane do implementacji `PipeReader` i `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="075b4-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="075b4-140">Delegowanie zarządzania buforem ułatwia wykorzystywanie kodu do skoncentrowania się wyłącznie na logice biznesowej.</span><span class="sxs-lookup"><span data-stu-id="075b4-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="075b4-141">W pierwszej pętli:</span><span class="sxs-lookup"><span data-stu-id="075b4-141">In the first loop:</span></span>

* <span data-ttu-id="075b4-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> jest wywoływana, aby uzyskać pamięć z bazowego składnika zapisywania.</span><span class="sxs-lookup"><span data-stu-id="075b4-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="075b4-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> jest wywoływana w celu poinformowania o `PipeWriter` ilości danych w buforze.</span><span class="sxs-lookup"><span data-stu-id="075b4-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="075b4-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> jest wywoływana, aby udostępnić dane `PipeReader`.</span><span class="sxs-lookup"><span data-stu-id="075b4-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="075b4-145">W drugiej pętli `PipeReader` zużywa bufory zapisywane przez `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="075b4-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="075b4-146">Bufory pochodzą z gniazda.</span><span class="sxs-lookup"><span data-stu-id="075b4-146">The buffers come from the socket.</span></span> <span data-ttu-id="075b4-147">Wywołanie `PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="075b4-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="075b4-148">Zwraca wartość <xref:System.IO.Pipelines.ReadResult> zawierającą dwie ważne informacje:</span><span class="sxs-lookup"><span data-stu-id="075b4-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="075b4-149">Dane, które zostały odczytane w formie `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="075b4-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="075b4-150">Wartość logiczna `IsCompleted` wskazuje, czy osiągnięto koniec danych (EOF).</span><span class="sxs-lookup"><span data-stu-id="075b4-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="075b4-151">Po znalezieniu ogranicznika końca wiersza (EOL) i przeanalizowaniu wiersza:</span><span class="sxs-lookup"><span data-stu-id="075b4-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="075b4-152">Logika przetwarza bufor, aby pominąć operacje, które zostały już przetworzone.</span><span class="sxs-lookup"><span data-stu-id="075b4-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="075b4-153">`PipeReader.AdvanceTo` jest wywoływana w celu poinformowania `PipeReader` o ilości danych, które zostały zużyte i zbadane.</span><span class="sxs-lookup"><span data-stu-id="075b4-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="075b4-154">Pętle czytnika i składnika zapisywania kończą się przez wywołanie `Complete`.</span><span class="sxs-lookup"><span data-stu-id="075b4-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="075b4-155">`Complete` umożliwia zwolnieniu pamięci podlegającej potoku.</span><span class="sxs-lookup"><span data-stu-id="075b4-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="075b4-156">Sterowanie ruchem wstecznym i przepływem</span><span class="sxs-lookup"><span data-stu-id="075b4-156">Backpressure and flow control</span></span>

<span data-ttu-id="075b4-157">Najlepiej, odczytując i przeanalizować współpracę:</span><span class="sxs-lookup"><span data-stu-id="075b4-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="075b4-158">Wątek pisania wykorzystuje dane z sieci i umieszcza je w buforach.</span><span class="sxs-lookup"><span data-stu-id="075b4-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="075b4-159">Wątek analizy jest odpowiedzialny za konstruowanie odpowiednich struktur danych.</span><span class="sxs-lookup"><span data-stu-id="075b4-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="075b4-160">Zwykle analiza zajmuje więcej czasu niż tylko kopiowanie bloków danych z sieci:</span><span class="sxs-lookup"><span data-stu-id="075b4-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="075b4-161">Wątek odczytywania pobiera przed wątkiem analizy.</span><span class="sxs-lookup"><span data-stu-id="075b4-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="075b4-162">Wątek odczytu musi spowolnić lub przydzielić więcej pamięci, aby przechowywać dane dla wątku analizy.</span><span class="sxs-lookup"><span data-stu-id="075b4-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="075b4-163">W celu uzyskania optymalnej wydajności istnieje równowaga między częste Wstrzymywanie i przydzielania większej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="075b4-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="075b4-164">Aby rozwiązać ten problem, `Pipe` ma dwa ustawienia do sterowania przepływem danych:</span><span class="sxs-lookup"><span data-stu-id="075b4-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="075b4-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: określa, ile danych ma być buforowanych przed wywołaniami <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> wstrzymywania.</span><span class="sxs-lookup"><span data-stu-id="075b4-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="075b4-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: określa, ile danych musi obserwować czytelnik przed wywołaniami `PipeWriter.FlushAsync` wznowić.</span><span class="sxs-lookup"><span data-stu-id="075b4-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![Diagram z ResumeWriterThreshold i PauseWriterThreshold](./media/pipelines/resume-pause.png)

<span data-ttu-id="075b4-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="075b4-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="075b4-169">Zwraca niekompletną `ValueTask<FlushResult>`, gdy ilość danych w `Pipe` przekracza `PauseWriterThreshold`.</span><span class="sxs-lookup"><span data-stu-id="075b4-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="075b4-170">Kończy `ValueTask<FlushResult>`, gdy przyjmie mniej niż `ResumeWriterThreshold`.</span><span class="sxs-lookup"><span data-stu-id="075b4-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="075b4-171">Dwie wartości są używane, aby zapobiec szybkiemu cyklowi, który może wystąpić w przypadku użycia jednej wartości.</span><span class="sxs-lookup"><span data-stu-id="075b4-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="075b4-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="075b4-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="075b4-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="075b4-173">PipeScheduler</span></span>

<span data-ttu-id="075b4-174">Zwykle w przypadku używania `async` i `await` kod asynchroniczny zostaje wznowiony na <xref:System.Threading.Tasks.TaskScheduler> lub na bieżącym <xref:System.Threading.SynchronizationContext>.</span><span class="sxs-lookup"><span data-stu-id="075b4-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="075b4-175">Podczas wykonywania operacji we/wy należy mieć precyzyjną kontrolę nad tym, gdzie jest wykonywane wykonywanie operacji we/wy.</span><span class="sxs-lookup"><span data-stu-id="075b4-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="075b4-176">Ta kontrolka umożliwia efektywne wykorzystanie pamięci podręcznych procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="075b4-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="075b4-177">Wydajne buforowanie ma kluczowe znaczenie dla aplikacji o wysokiej wydajności, takich jak serwery sieci Web.</span><span class="sxs-lookup"><span data-stu-id="075b4-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="075b4-178"><xref:System.IO.Pipelines.PipeScheduler> zapewnia kontrolę nad miejscem, w którym są uruchamiane asynchroniczne wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="075b4-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="075b4-179">Domyślnie:</span><span class="sxs-lookup"><span data-stu-id="075b4-179">By default:</span></span>

* <span data-ttu-id="075b4-180">Bieżąca <xref:System.Threading.SynchronizationContext> jest używana.</span><span class="sxs-lookup"><span data-stu-id="075b4-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="075b4-181">Jeśli nie ma `SynchronizationContext`, używa ona puli wątków do uruchamiania wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="075b4-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="075b4-182">[PipeScheduler.](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) Threading to implementacja <xref:System.IO.Pipelines.PipeScheduler>, która kolejkuje wywołania zwrotne do puli wątków.</span><span class="sxs-lookup"><span data-stu-id="075b4-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="075b4-183">`PipeScheduler.ThreadPool` jest domyślnym i generalnie najlepszym wyborem.</span><span class="sxs-lookup"><span data-stu-id="075b4-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="075b4-184">[PipeScheduler. inline](xref:System.IO.Pipelines.PipeScheduler.Inline) może spowodować niezamierzone konsekwencje, takie jak zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="075b4-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="075b4-185">Resetowanie potoku</span><span class="sxs-lookup"><span data-stu-id="075b4-185">Pipe reset</span></span>

<span data-ttu-id="075b4-186">Często wydajnym rozwiązaniem jest ponowne użycie obiektu `Pipe`.</span><span class="sxs-lookup"><span data-stu-id="075b4-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="075b4-187">Aby zresetować potok, wywołaj <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> po zakończeniu obu `PipeReader` i `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="075b4-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="075b4-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="075b4-188">PipeReader</span></span>

<span data-ttu-id="075b4-189"><xref:System.IO.Pipelines.PipeReader> zarządza pamięcią w imieniu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="075b4-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="075b4-190">**Zawsze** wywołuj <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> po wywołaniu <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="075b4-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="075b4-191">Pozwala to `PipeReader` wiedzieć, kiedy obiekt wywołujący jest wykonywany z pamięcią, tak aby można było go śledzić.</span><span class="sxs-lookup"><span data-stu-id="075b4-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="075b4-192">Wartość `ReadOnlySequence<byte>` zwracana z `PipeReader.ReadAsync` jest prawidłowa tylko do momentu wywołania `PipeReader.AdvanceTo`.</span><span class="sxs-lookup"><span data-stu-id="075b4-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="075b4-193">Nie można używać `ReadOnlySequence<byte>` po wywołaniu `PipeReader.AdvanceTo`.</span><span class="sxs-lookup"><span data-stu-id="075b4-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="075b4-194">`PipeReader.AdvanceTo` przyjmuje dwa argumenty <xref:System.SequencePosition>:</span><span class="sxs-lookup"><span data-stu-id="075b4-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="075b4-195">Pierwszy argument określa, ile pamięci zostało zużyte.</span><span class="sxs-lookup"><span data-stu-id="075b4-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="075b4-196">Drugi argument określa, jaka część buforu została zaobserwowana.</span><span class="sxs-lookup"><span data-stu-id="075b4-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="075b4-197">Oznaczenie danych jako zużyte oznacza, że potok może zwrócić pamięć do źródłowej puli buforów.</span><span class="sxs-lookup"><span data-stu-id="075b4-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="075b4-198">Oznaczanie danych jako obserwowanych kontroluje, co następne wywołanie `PipeReader.ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="075b4-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="075b4-199">Oznaczenie wszystkiego jako zaobserwowane oznacza, że następne wywołanie `PipeReader.ReadAsync` nie zwróci się do momentu zapisania większej ilości danych w potoku.</span><span class="sxs-lookup"><span data-stu-id="075b4-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="075b4-200">Wszystkie inne wartości spowodują, że następne wywołanie `PipeReader.ReadAsync` zwróci bezpośrednio z obserwowanymi *i* nieobserwowanymi danymi, ale dane, które zostały już zużyte.</span><span class="sxs-lookup"><span data-stu-id="075b4-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="075b4-201">Odczytaj scenariusze przesyłania strumieniowego danych</span><span class="sxs-lookup"><span data-stu-id="075b4-201">Read streaming data scenarios</span></span>

<span data-ttu-id="075b4-202">Istnieje kilka typowych wzorców, które nastąpiły podczas próby odczytu danych przesyłanych strumieniowo:</span><span class="sxs-lookup"><span data-stu-id="075b4-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="075b4-203">Przy użyciu strumienia danych Przeanalizuj pojedynczy komunikat.</span><span class="sxs-lookup"><span data-stu-id="075b4-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="075b4-204">Przy użyciu strumienia danych Przeanalizuj wszystkie dostępne komunikaty.</span><span class="sxs-lookup"><span data-stu-id="075b4-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="075b4-205">W poniższych przykładach użyto metody `TryParseMessage` do analizowania komunikatów z `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="075b4-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="075b4-206">`TryParseMessage` analizuje pojedynczy komunikat i aktualizuje bufor wejściowy, aby przyciąć przeanalizowany komunikat z bufora.</span><span class="sxs-lookup"><span data-stu-id="075b4-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="075b4-207">`TryParseMessage` nie jest częścią programu .NET. jest to metoda zapisywana przez użytkownika używana w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="075b4-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="075b4-208">Odczytaj pojedynczy komunikat</span><span class="sxs-lookup"><span data-stu-id="075b4-208">Read a single message</span></span>

<span data-ttu-id="075b4-209">Poniższy kod odczytuje pojedynczy komunikat z `PipeReader` i zwraca go do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="075b4-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="075b4-210">Poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="075b4-210">The preceding code:</span></span>

* <span data-ttu-id="075b4-211">Analizuje pojedynczy komunikat.</span><span class="sxs-lookup"><span data-stu-id="075b4-211">Parses a single message.</span></span>
* <span data-ttu-id="075b4-212">Aktualizuje zużyte `SequencePosition` i zbadane `SequencePosition`, aby wskazywały na początek przyciętego buforu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="075b4-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="075b4-213">Dwa argumenty `SequencePosition` są aktualizowane, ponieważ `TryParseMessage` usuwa przeanalizowany komunikat z buforu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="075b4-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="075b4-214">Ogólnie rzecz biorąc, podczas analizowania pojedynczej wiadomości z bufora pozycja zbadana powinna mieć jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="075b4-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="075b4-215">Koniec komunikatu.</span><span class="sxs-lookup"><span data-stu-id="075b4-215">The end of the message.</span></span>
* <span data-ttu-id="075b4-216">Koniec odebranego buforu, jeśli nie odnaleziono komunikatu.</span><span class="sxs-lookup"><span data-stu-id="075b4-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="075b4-217">Przypadek z pojedynczym komunikatem ma największą możliwość wystąpienia błędów.</span><span class="sxs-lookup"><span data-stu-id="075b4-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="075b4-218">Przekazanie nieprawidłowych wartości do *zbadania* może spowodować wyjątek braku pamięci lub nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="075b4-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="075b4-219">Aby uzyskać więcej informacji, zobacz sekcję [typowe problemy związane z PipeReader](#gotchas) w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="075b4-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="075b4-220">Odczytywanie wielu wiadomości</span><span class="sxs-lookup"><span data-stu-id="075b4-220">Reading multiple messages</span></span>

<span data-ttu-id="075b4-221">Poniższy kod odczytuje wszystkie komunikaty z `PipeReader` i wywołuje `ProcessMessageAsync` na każdym z nich.</span><span class="sxs-lookup"><span data-stu-id="075b4-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="075b4-222">Anulowanie</span><span class="sxs-lookup"><span data-stu-id="075b4-222">Cancellation</span></span>

<span data-ttu-id="075b4-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="075b4-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="075b4-224">Obsługuje przekazywanie <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="075b4-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="075b4-225">Zgłasza <xref:System.OperationCanceledException>, jeśli `CancellationToken` zostanie anulowane, gdy istnieje oczekujące odczytanie.</span><span class="sxs-lookup"><span data-stu-id="075b4-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="075b4-226">Obsługuje sposób anulowania bieżącej operacji odczytu za pośrednictwem <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, co zapobiega wywoływaniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="075b4-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="075b4-227">Wywołanie `PipeReader.CancelPendingRead` powoduje, że bieżące lub następne wywołanie do `PipeReader.ReadAsync` zwróci <xref:System.IO.Pipelines.ReadResult> z `IsCanceled` ustawionym na `true`.</span><span class="sxs-lookup"><span data-stu-id="075b4-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="075b4-228">Może to być przydatne w przypadku zatrzymania istniejącej pętli odczytu w nieniszczącej i niewyjątkowy sposób.</span><span class="sxs-lookup"><span data-stu-id="075b4-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="075b4-229">PipeReader typowe problemy</span><span class="sxs-lookup"><span data-stu-id="075b4-229">PipeReader common problems</span></span>

* <span data-ttu-id="075b4-230">Przekazanie nieprawidłowych wartości do `consumed` lub `examined` może spowodować odczyt danych, które zostały już odczytane.</span><span class="sxs-lookup"><span data-stu-id="075b4-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="075b4-231">Przekazywanie `buffer.End` jako badane może skutkować:</span><span class="sxs-lookup"><span data-stu-id="075b4-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="075b4-232">Dane wstrzymane</span><span class="sxs-lookup"><span data-stu-id="075b4-232">Stalled data</span></span>
  * <span data-ttu-id="075b4-233">Ewentualny wyjątek braku pamięci (OOM), jeśli dane nie są używane.</span><span class="sxs-lookup"><span data-stu-id="075b4-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="075b4-234">Na przykład `PipeReader.AdvanceTo(position, buffer.End)` podczas przetwarzania pojedynczej wiadomości w czasie z buforu.</span><span class="sxs-lookup"><span data-stu-id="075b4-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="075b4-235">Przekazanie nieprawidłowych wartości do `consumed` lub `examined` może spowodować nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="075b4-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="075b4-236">Na przykład `PipeReader.AdvanceTo(buffer.Start)` Jeśli nie zmieniono `buffer.Start`, spowoduje to, że następne wywołanie metody `PipeReader.ReadAsync` zwróci natychmiast przed nadejściem nowych danych.</span><span class="sxs-lookup"><span data-stu-id="075b4-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="075b4-237">Przekazanie nieprawidłowych wartości do `consumed` lub `examined` może spowodować nieskończone buforowanie (ostateczne OOM).</span><span class="sxs-lookup"><span data-stu-id="075b4-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="075b4-238">Użycie `ReadOnlySequence<byte>` po wywołaniu `PipeReader.AdvanceTo` może spowodować uszkodzenie pamięci (za darmo).</span><span class="sxs-lookup"><span data-stu-id="075b4-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="075b4-239">Niepowodzenie wywołania `PipeReader.Complete/CompleteAsync` może spowodować przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="075b4-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="075b4-240">Sprawdzanie <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> i wyjście z logiki odczytu przed przetworzeniem buforu spowoduje utratę danych.</span><span class="sxs-lookup"><span data-stu-id="075b4-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="075b4-241">Warunek zakończenia pętli powinien opierać się na `ReadResult.Buffer.IsEmpty` i `ReadResult.IsCompleted`.</span><span class="sxs-lookup"><span data-stu-id="075b4-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="075b4-242">Nieprawidłowe działanie może spowodować powstanie pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="075b4-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="075b4-243">Problematyczny kod</span><span class="sxs-lookup"><span data-stu-id="075b4-243">Problematic code</span></span>

<span data-ttu-id="075b4-244">❌ **utrata danych**</span><span class="sxs-lookup"><span data-stu-id="075b4-244">❌ **Data loss**</span></span>

<span data-ttu-id="075b4-245">`ReadResult` może zwrócić końcowy segment danych, gdy `IsCompleted` jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="075b4-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="075b4-246">Nie można odczytać tych danych przed wyjściem z pętli odczytu spowoduje utratę danych.</span><span class="sxs-lookup"><span data-stu-id="075b4-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="075b4-247">**nieskończona pętla** ❌</span><span class="sxs-lookup"><span data-stu-id="075b4-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="075b4-248">Poniższa logika może spowodować nieskończoną pętlę, jeśli `Result.IsCompleted` jest `true`, ale nigdy nie pełny komunikat w buforze.</span><span class="sxs-lookup"><span data-stu-id="075b4-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="075b4-249">Oto inny fragment kodu z tym samym problemem.</span><span class="sxs-lookup"><span data-stu-id="075b4-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="075b4-250">Przed sprawdzeniem `ReadResult.IsCompleted` sprawdza, czy bufor nie jest pusty.</span><span class="sxs-lookup"><span data-stu-id="075b4-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="075b4-251">Ponieważ jest ona w `else if`, będzie ona zapętlać w nieskończoność, jeśli w buforze nigdy nie ma kompletnego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="075b4-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="075b4-252">**nieoczekiwane zawieszenie** ❌</span><span class="sxs-lookup"><span data-stu-id="075b4-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="075b4-253">Bezwarunkowo wywoływanie `PipeReader.AdvanceTo` z `buffer.End` w pozycji `examined` może spowodować zawieszenie podczas analizowania pojedynczego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="075b4-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="075b4-254">Następne wywołanie `PipeReader.AdvanceTo` nie zwróci wartości do momentu:</span><span class="sxs-lookup"><span data-stu-id="075b4-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="075b4-255">Więcej danych jest zapisywana w potoku.</span><span class="sxs-lookup"><span data-stu-id="075b4-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="075b4-256">Nowe dane nie były wcześniej badane.</span><span class="sxs-lookup"><span data-stu-id="075b4-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="075b4-257">❌ **z pamięci (OOM)**</span><span class="sxs-lookup"><span data-stu-id="075b4-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="075b4-258">W następujących warunkach Poniższy kod przechowuje buforowanie do momentu wystąpienia <xref:System.OutOfMemoryException>:</span><span class="sxs-lookup"><span data-stu-id="075b4-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="075b4-259">Nie ma maksymalnego rozmiaru wiadomości.</span><span class="sxs-lookup"><span data-stu-id="075b4-259">There's no maximum message size.</span></span>
* <span data-ttu-id="075b4-260">Dane zwrócone z `PipeReader` nie pełnią komunikatu.</span><span class="sxs-lookup"><span data-stu-id="075b4-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="075b4-261">Na przykład nie wykonuje pełnego komunikatu, ponieważ druga strona zapisuje dużą wiadomość (na przykład komunikat 4 GB).</span><span class="sxs-lookup"><span data-stu-id="075b4-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="075b4-262">**uszkodzenie pamięci** ❌</span><span class="sxs-lookup"><span data-stu-id="075b4-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="075b4-263">Podczas pisania pomocników odczytujących bufor należy skopiować wszystkie zwrócone ładunki przed wywołaniem `Advance`.</span><span class="sxs-lookup"><span data-stu-id="075b4-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="075b4-264">Poniższy przykład zwróci pamięć, która `Pipe` została odrzucona i może ponownie użyć dla następnej operacji (odczyt/zapis).</span><span class="sxs-lookup"><span data-stu-id="075b4-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="075b4-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="075b4-265">PipeWriter</span></span>

<span data-ttu-id="075b4-266"><xref:System.IO.Pipelines.PipeWriter> zarządza buforami do zapisu w imieniu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="075b4-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="075b4-267">`PipeWriter` implementuje [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span><span class="sxs-lookup"><span data-stu-id="075b4-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="075b4-268">`IBufferWriter<byte>` umożliwia uzyskanie dostępu do buforów w celu wykonywania operacji zapisu bez dodatkowych kopii buforów.</span><span class="sxs-lookup"><span data-stu-id="075b4-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="075b4-269">Poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="075b4-269">The previous code:</span></span>

* <span data-ttu-id="075b4-270">Żąda bufora co najmniej 5 bajtów z `PipeWriter` przy użyciu <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span><span class="sxs-lookup"><span data-stu-id="075b4-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="075b4-271">Zapisuje bajty dla ciągu ASCII `"Hello"` do zwróconego `Memory<byte>`.</span><span class="sxs-lookup"><span data-stu-id="075b4-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="075b4-272">Wywołuje <xref:System.IO.Pipelines.PipeWriter.Advance%2A>, aby wskazać, ile bajtów Zapisano w buforze.</span><span class="sxs-lookup"><span data-stu-id="075b4-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="075b4-273">Opróżnia `PipeWriter`, który wysyła bajty do urządzenia bazowego.</span><span class="sxs-lookup"><span data-stu-id="075b4-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="075b4-274">Poprzednia metoda pisania używa buforów dostarczonych przez `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="075b4-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="075b4-275">Alternatywnie, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="075b4-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="075b4-276">Kopiuje istniejący bufor do `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="075b4-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="075b4-277">Wywołuje `GetSpan`, `Advance` odpowiednio i wywołuje <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="075b4-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="075b4-278">Anulowanie</span><span class="sxs-lookup"><span data-stu-id="075b4-278">Cancellation</span></span>

<span data-ttu-id="075b4-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> obsługuje przekazywanie <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="075b4-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="075b4-280">Przekazywanie `CancellationToken` powoduje wystąpienie `OperationCanceledException`, jeśli token zostanie anulowany, gdy istnieje oczekująca operacja opróżniania.</span><span class="sxs-lookup"><span data-stu-id="075b4-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="075b4-281">`PipeWriter.FlushAsync` obsługuje sposób anulowania bieżącej operacji opróżniania za pośrednictwem <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> bez podnoszenia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="075b4-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="075b4-282">Wywołanie `PipeWriter.CancelPendingFlush` powoduje, że bieżące lub następne wywołanie `PipeWriter.FlushAsync` lub `PipeWriter.WriteAsync` spowoduje zwrócenie <xref:System.IO.Pipelines.FlushResult> z `IsCanceled` ustawionym na `true`.</span><span class="sxs-lookup"><span data-stu-id="075b4-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="075b4-283">Może to być przydatne w przypadku zatrzymania opróżniania w sposób nieniszczący i niewyjątkowy.</span><span class="sxs-lookup"><span data-stu-id="075b4-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="075b4-284">PipeWriter typowe problemy</span><span class="sxs-lookup"><span data-stu-id="075b4-284">PipeWriter common problems</span></span>

* <span data-ttu-id="075b4-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> i <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> zwracają bufor z co najmniej żądaną ilością pamięci.</span><span class="sxs-lookup"><span data-stu-id="075b4-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="075b4-286">**Nie** zakładaj dokładnie rozmiarów buforów.</span><span class="sxs-lookup"><span data-stu-id="075b4-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="075b4-287">Nie ma gwarancji, że kolejne wywołania będą zwracać ten sam bufor lub bufor o takim samym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="075b4-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="075b4-288">Należy zażądać nowego buforu po wywołaniu <xref:System.IO.Pipelines.PipeWriter.Advance%2A>, aby kontynuować zapisywanie większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="075b4-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="075b4-289">Nie można zapisać wcześniej uzyskanego buforu.</span><span class="sxs-lookup"><span data-stu-id="075b4-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="075b4-290">Wywołanie `GetMemory` lub `GetSpan`, gdy istnieje niekompletne wywołanie `FlushAsync` nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="075b4-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="075b4-291">Wywołanie `Complete` lub `CompleteAsync`, gdy nieopróżnione dane mogą spowodować uszkodzenie pamięci.</span><span class="sxs-lookup"><span data-stu-id="075b4-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="075b4-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="075b4-292">IDuplexPipe</span></span>

<span data-ttu-id="075b4-293"><xref:System.IO.Pipelines.IDuplexPipe> to kontrakt dla typów, które obsługują odczyt i zapis.</span><span class="sxs-lookup"><span data-stu-id="075b4-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="075b4-294">Na przykład połączenie sieciowe będzie reprezentowane przez `IDuplexPipe`.</span><span class="sxs-lookup"><span data-stu-id="075b4-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="075b4-295">W przeciwieństwie do `Pipe`, który zawiera `PipeReader` i `PipeWriter`, `IDuplexPipe` reprezentuje jedną część połączenia pełnego dupleksu.</span><span class="sxs-lookup"><span data-stu-id="075b4-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="075b4-296">Oznacza to, co jest zapisywane w `PipeWriter` nie zostanie odczytany z `PipeReader`.</span><span class="sxs-lookup"><span data-stu-id="075b4-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="075b4-297">Strumienie</span><span class="sxs-lookup"><span data-stu-id="075b4-297">Streams</span></span>

<span data-ttu-id="075b4-298">Podczas odczytywania lub zapisywania danych strumienia zwykle dane są odczytywane przy użyciu deserializatora i zapisu danych przy użyciu serializatora.</span><span class="sxs-lookup"><span data-stu-id="075b4-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="075b4-299">Większość z tych interfejsów API odczytu i zapisu ma parametr `Stream`.</span><span class="sxs-lookup"><span data-stu-id="075b4-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="075b4-300">Aby ułatwić integrację z tymi istniejącymi interfejsami API, `PipeReader` i `PipeWriter` uwidaczniają <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="075b4-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="075b4-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> zwraca implementację `Stream` wokół `PipeReader` lub `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="075b4-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
