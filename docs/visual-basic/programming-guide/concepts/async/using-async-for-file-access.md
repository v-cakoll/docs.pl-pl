---
title: Użycie Async do uzyskiwania dostępu do plików
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: 2ee1efa69f4b13224be65fe802ebf5f834c941aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400774"
---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="2e733-102">Używanie Async na potrzeby dostępu do plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e733-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="2e733-103">Do uzyskiwania dostępu do plików można użyć funkcji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="2e733-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="2e733-104">Za pomocą funkcji asynchronicznej można wywołać metody asynchroniczne bez używania wywołań zwrotnych lub dzieląc kod w wielu metodach lub wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="2e733-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="2e733-105">Aby przeprowadzić synchroniczne asynchroniczne kod, wystarczy wywołać metodę asynchroniczną zamiast metody synchronicznej i dodać kilka słów kluczowych do kodu.</span><span class="sxs-lookup"><span data-stu-id="2e733-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="2e733-106">Aby dodać asynchroniczności do wywołań dostępu do plików, należy wziąć pod uwagę następujące przyczyny:</span><span class="sxs-lookup"><span data-stu-id="2e733-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="2e733-107">Asynchroniczności sprawia, że aplikacje interfejsu użytkownika działają szybciej, ponieważ wątek interfejsu użytkownika uruchamiający operację może wykonać inne czynności.</span><span class="sxs-lookup"><span data-stu-id="2e733-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="2e733-108">Jeśli wątek interfejsu użytkownika musi wykonać kod, który zajmuje dużo czasu (na przykład więcej niż 50 milisekund), interfejs użytkownika może się zamrozić do momentu zakończenia operacji we/wy, a wątek interfejsu użytkownika może ponownie przetwarzać dane wejściowe klawiatury i myszy oraz inne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2e733-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="2e733-109">Asynchroniczności poprawia skalowalność ASP.NET i innych aplikacji opartych na serwerze, zmniejszając potrzebę wątków.</span><span class="sxs-lookup"><span data-stu-id="2e733-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="2e733-110">Jeśli aplikacja korzysta z dedykowanego wątku na odpowiedź i jednocześnie są obsługiwane tysiące żądań, są zbędne tysiące wątków.</span><span class="sxs-lookup"><span data-stu-id="2e733-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="2e733-111">Operacje asynchroniczne często nie muszą używać wątku podczas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="2e733-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="2e733-112">Z chwilą korzystają z istniejącego wątku zakończenia operacji we/wy.</span><span class="sxs-lookup"><span data-stu-id="2e733-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="2e733-113">Opóźnienie operacji dostępu do pliku może być bardzo niskie w bieżących warunkach, ale opóźnienie może znacznie wzrosnąć w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="2e733-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="2e733-114">Na przykład plik można przenieść na serwer, na którym znajduje się na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="2e733-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="2e733-115">Dodatkowe obciążenie związane z korzystaniem z funkcji asynchronicznej jest małe.</span><span class="sxs-lookup"><span data-stu-id="2e733-115">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="2e733-116">Zadania asynchroniczne można łatwo uruchomić równolegle.</span><span class="sxs-lookup"><span data-stu-id="2e733-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="2e733-117">Uruchamianie przykładów</span><span class="sxs-lookup"><span data-stu-id="2e733-117">Running the Examples</span></span>  
 <span data-ttu-id="2e733-118">Aby uruchomić przykłady w tym temacie, można utworzyć **aplikację WPF** lub **aplikację Windows Forms** , a następnie dodać **przycisk**.</span><span class="sxs-lookup"><span data-stu-id="2e733-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="2e733-119">W `Click` zdarzeniu przycisku Dodaj wywołanie do pierwszej metody w każdym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2e733-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="2e733-120">W poniższych przykładach Uwzględnij poniższe `Imports` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="2e733-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="2e733-121">Użycie klasy FileStream</span><span class="sxs-lookup"><span data-stu-id="2e733-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="2e733-122">Przykłady w tym temacie używają <xref:System.IO.FileStream> klasy, która powoduje wystąpienie asynchroniczne we/wy na poziomie systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2e733-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="2e733-123">Korzystając z tej opcji, można uniknąć zablokowania wątku puli wątków w wielu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="2e733-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="2e733-124">Aby włączyć tę opcję, należy określić `useAsync=true` argument or `options=FileOptions.Asynchronous` w wywołaniu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2e733-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="2e733-125">Nie można użyć tej opcji razem z <xref:System.IO.StreamReader> i, <xref:System.IO.StreamWriter> Jeśli otworzysz je bezpośrednio, określając ścieżkę pliku.</span><span class="sxs-lookup"><span data-stu-id="2e733-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="2e733-126">Można jednak użyć tej opcji, jeśli podajesz im <xref:System.IO.Stream> , że została <xref:System.IO.FileStream> otwarta Klasa.</span><span class="sxs-lookup"><span data-stu-id="2e733-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="2e733-127">Należy zauważyć, że wywołania asynchroniczne są szybsze w aplikacjach interfejsu użytkownika, nawet jeśli wątek puli wątków jest zablokowany, ponieważ wątek interfejsu użytkownika nie jest blokowany podczas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="2e733-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="2e733-128">Pisanie tekstu</span><span class="sxs-lookup"><span data-stu-id="2e733-128">Writing Text</span></span>  
 <span data-ttu-id="2e733-129">Poniższy przykład zapisuje tekst do pliku.</span><span class="sxs-lookup"><span data-stu-id="2e733-129">The following example writes text to a file.</span></span> <span data-ttu-id="2e733-130">W każdej instrukcji Await Metoda natychmiast opuszcza.</span><span class="sxs-lookup"><span data-stu-id="2e733-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="2e733-131">Po zakończeniu operacji we/wy pliku Metoda zostaje wznowiona przy użyciu instrukcji, która następuje po instrukcji Await.</span><span class="sxs-lookup"><span data-stu-id="2e733-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="2e733-132">Należy zauważyć, że modyfikator Async jest w definicji metod, które używają instrukcji Await.</span><span class="sxs-lookup"><span data-stu-id="2e733-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 <span data-ttu-id="2e733-133">Oryginalny przykład zawiera instrukcję `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)` , która jest umową obejmującą następujące dwie instrukcje:</span><span class="sxs-lookup"><span data-stu-id="2e733-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="2e733-134">Pierwsza instrukcja zwraca zadanie i powoduje uruchomienie przetwarzania plików.</span><span class="sxs-lookup"><span data-stu-id="2e733-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="2e733-135">Druga instrukcja z Await powoduje, że metoda natychmiast zakończy działanie i zwróci inne zadanie.</span><span class="sxs-lookup"><span data-stu-id="2e733-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="2e733-136">Po późniejszym zakończeniu przetwarzania plików wykonanie powraca do instrukcji, która następuje po oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="2e733-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="2e733-137">Aby uzyskać więcej informacji, zobacz [sterowanie przepływem w programach asynchronicznych (Visual Basic)](control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="2e733-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="2e733-138">Odczytywanie tekstu</span><span class="sxs-lookup"><span data-stu-id="2e733-138">Reading Text</span></span>  
 <span data-ttu-id="2e733-139">Poniższy przykład odczytuje tekst z pliku.</span><span class="sxs-lookup"><span data-stu-id="2e733-139">The following example reads text from a file.</span></span> <span data-ttu-id="2e733-140">Tekst jest buforowany i, w tym przypadku, umieszczony w <xref:System.Text.StringBuilder> .</span><span class="sxs-lookup"><span data-stu-id="2e733-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="2e733-141">W przeciwieństwie do poprzedniego przykładu, obliczanie oczekiwania powoduje utworzenie wartości.</span><span class="sxs-lookup"><span data-stu-id="2e733-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="2e733-142"><xref:System.IO.Stream.ReadAsync%2A>Metoda zwraca <xref:System.Threading.Tasks.Task> \<<xref:System.Int32>>, więc Ocena await generuje `Int32` wartość ( `numRead` ) po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="2e733-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="2e733-143">Aby uzyskać więcej informacji, zobacz [asynchroniczne typy zwracane (Visual Basic)](async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="2e733-143">For more information, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="2e733-144">Równoległe asynchroniczne operacje we/wy</span><span class="sxs-lookup"><span data-stu-id="2e733-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="2e733-145">Poniższy przykład ilustruje przetwarzanie równoległe, pisząc 10 plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="2e733-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="2e733-146">Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> Metoda zwraca zadanie, które jest następnie dodawane do listy zadań.</span><span class="sxs-lookup"><span data-stu-id="2e733-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="2e733-147">`Await Task.WhenAll(tasks)`Instrukcja kończy metodę i wznawia działanie w ramach metody po zakończeniu przetwarzania plików dla wszystkich zadań.</span><span class="sxs-lookup"><span data-stu-id="2e733-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="2e733-148">Przykład zamyka wszystkie <xref:System.IO.FileStream> wystąpienia w `Finally` bloku po zakończeniu zadań.</span><span class="sxs-lookup"><span data-stu-id="2e733-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="2e733-149">Jeśli każdy z `FileStream` nich został utworzony w `Imports` instrukcji, `FileStream` może zostać usunięty przed ukończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="2e733-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="2e733-150">Należy pamiętać, że zwiększenie wydajności jest niemal całkowicie wynikiem przetwarzania równoległego, a nie przetwarzania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="2e733-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="2e733-151">Zalety asynchroniczności są takie same, że nie wiążą się z wieloma wątkami i nie wiążą się z wątkiem interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e733-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="2e733-152">W przypadku korzystania <xref:System.IO.Stream.WriteAsync%2A> z <xref:System.IO.Stream.ReadAsync%2A> metod i można określić <xref:System.Threading.CancellationToken> , której można użyć do anulowania strumienia średniej operacji.</span><span class="sxs-lookup"><span data-stu-id="2e733-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="2e733-153">Aby uzyskać więcej informacji, zobacz [dostrajanie aplikacji asynchronicznej (Visual Basic)](fine-tuning-your-async-application.md) i [Anulowanie w zarządzanych wątkach](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="2e733-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e733-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e733-154">See also</span></span>

- [<span data-ttu-id="2e733-155">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e733-155">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="2e733-156">Asynchroniczne typy zwracane (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e733-156">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="2e733-157">Przepływ sterowania w programach asynchronicznych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e733-157">Control Flow in Async Programs (Visual Basic)</span></span>](control-flow-in-async-programs.md)
