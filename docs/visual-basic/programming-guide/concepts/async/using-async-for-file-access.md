---
title: Użycie Async do uzyskiwania dostępu do plików (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: e12eaa57d0f7186e9d281b89ec3abd26280e12ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="e515b-102">Użycie Async do uzyskiwania dostępu do plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e515b-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="e515b-103">Funkcja Async dostęp do plików.</span><span class="sxs-lookup"><span data-stu-id="e515b-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="e515b-104">Korzystając z funkcji asynchronicznych, należy wywołać do metod asynchronicznych bez przy użyciu wywołania zwrotne i dzielenia kodu wielu metod lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="e515b-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="e515b-105">Aby wprowadzić kod synchroniczne asynchroniczne, możesz tylko wywołania metody asynchronicznej zamiast metoda synchroniczna i dodać kilka słów kluczowych w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e515b-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="e515b-106">Należy rozważyć następujące przyczyny dodawania asynchrony do wywołania dostępu do pliku:</span><span class="sxs-lookup"><span data-stu-id="e515b-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="e515b-107">Asynchrony sprawia, że aplikacje interfejsu użytkownika usprawnia ponieważ wątku interfejsu użytkownika, który uruchamia operację można wykonywać inne zadania.</span><span class="sxs-lookup"><span data-stu-id="e515b-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="e515b-108">Jeśli kod musi być wykonywany w wątku interfejsu użytkownika który zajmuje dużo czasu (na przykład więcej niż 50 w milisekundach), interfejsu użytkownika może zawieszać się dopiero po zakończeniu operacji We/Wy i wątku interfejsu użytkownika można ponownie przetworzyć klawiatury i myszy zdarzenia wejściowe i inne.</span><span class="sxs-lookup"><span data-stu-id="e515b-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="e515b-109">Asynchrony poprawia skalowalność programu ASP.NET i innych aplikacji serwerowych, zmniejszając potrzebę wątków.</span><span class="sxs-lookup"><span data-stu-id="e515b-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="e515b-110">Jeśli aplikacja używa dedykowanego wątku na odpowiedzi i żądania tysięcy są obsługiwane jednocześnie, potrzebne są tysiące wątków.</span><span class="sxs-lookup"><span data-stu-id="e515b-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="e515b-111">Operacje asynchroniczne często nie trzeba używać wątku podczas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="e515b-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="e515b-112">Istniejące wątku zakończenia We/Wy będzie używać krótko po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="e515b-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="e515b-113">Opóźnienie operacji dostępu do pliku może być bardzo niskich warunkach bieżący, ale opóźnienie może znacznie zwiększyć w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="e515b-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="e515b-114">Na przykład plik może przenieść do serwera, który jest na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="e515b-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="e515b-115">Dodany korzystać z funkcji asynchronicznych jest mała.</span><span class="sxs-lookup"><span data-stu-id="e515b-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="e515b-116">Zadania asynchronicznego łatwo mogą być uruchamiane równolegle.</span><span class="sxs-lookup"><span data-stu-id="e515b-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="e515b-117">Uruchamianie przykładów</span><span class="sxs-lookup"><span data-stu-id="e515b-117">Running the Examples</span></span>  
 <span data-ttu-id="e515b-118">Aby uruchomić przykłady w tym temacie, można utworzyć **aplikacji WPF** lub **aplikacji Windows Forms** , a następnie dodaj **przycisk**.</span><span class="sxs-lookup"><span data-stu-id="e515b-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="e515b-119">Przycisk `Click` zdarzeń, dodaj wywołanie do metody pierwszy w każdym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e515b-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="e515b-120">W poniższych przykładach są następujące `Imports` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="e515b-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="e515b-121">Użyj klasy FileStream</span><span class="sxs-lookup"><span data-stu-id="e515b-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="e515b-122">Przykłady w tym temacie <xref:System.IO.FileStream> klasy, która jest dostępna opcja, która powoduje występowanie asynchroniczne We/Wy na poziomie systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="e515b-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="e515b-123">Przy użyciu tej opcji, można uniknąć, blokuje puli wątków w wielu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="e515b-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="e515b-124">Aby włączyć tę opcję, należy określić `useAsync=true` lub `options=FileOptions.Asynchronous` argument w wywołaniu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e515b-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="e515b-125">Nie można użyć tej opcji z <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> otwarcia bezpośrednio, określając ścieżkę pliku.</span><span class="sxs-lookup"><span data-stu-id="e515b-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="e515b-126">Jednak można użyć tej opcji, jeśli zostaną podane <xref:System.IO.Stream> który <xref:System.IO.FileStream> klasy otwarty.</span><span class="sxs-lookup"><span data-stu-id="e515b-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="e515b-127">Należy zauważyć, że wywołania asynchroniczne szybsze w aplikacjach interfejsu użytkownika, nawet jeśli puli wątków jest zablokowana, ponieważ wątku interfejsu użytkownika nie jest blokowane podczas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="e515b-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="e515b-128">Pisanie tekstu</span><span class="sxs-lookup"><span data-stu-id="e515b-128">Writing Text</span></span>  
 <span data-ttu-id="e515b-129">Poniższy przykład zapisuje tekst w pliku.</span><span class="sxs-lookup"><span data-stu-id="e515b-129">The following example writes text to a file.</span></span> <span data-ttu-id="e515b-130">W każdej await instrukcji, metoda natychmiast kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="e515b-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="e515b-131">Po zakończeniu operacji We/Wy pliku metody wznawia działanie w instrukcji, która wykonuje instrukcję await.</span><span class="sxs-lookup"><span data-stu-id="e515b-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="e515b-132">Należy zauważyć, że w definicji metody, które używają instrukcja await modyfikatora async.</span><span class="sxs-lookup"><span data-stu-id="e515b-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="e515b-133">Przykład oryginalnego ma instrukcji `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, która jest zmniejszenie następujące dwie instrukcje:</span><span class="sxs-lookup"><span data-stu-id="e515b-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="e515b-134">Pierwsza instrukcja zwraca klasę task i powoduje, że przetwarzanie pliku rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="e515b-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="e515b-135">Drugi instrukcji z await powoduje, że metoda natychmiast wyjść i wrócić inne zadanie.</span><span class="sxs-lookup"><span data-stu-id="e515b-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="e515b-136">Po zakończeniu przetwarzania później plików, wykonanie zwraca do instrukcji następującej await.</span><span class="sxs-lookup"><span data-stu-id="e515b-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="e515b-137">Aby uzyskać więcej informacji, zobacz [przepływ sterowania w aplikacjach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="e515b-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="e515b-138">Odczytywanie tekstu</span><span class="sxs-lookup"><span data-stu-id="e515b-138">Reading Text</span></span>  
 <span data-ttu-id="e515b-139">Poniższy przykład odczytuje tekst z pliku.</span><span class="sxs-lookup"><span data-stu-id="e515b-139">The following example reads text from a file.</span></span> <span data-ttu-id="e515b-140">Tekst buforowane i umieszczane w takim przypadku <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="e515b-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="e515b-141">Inaczej niż w poprzednim przykładzie oceny await tworzy wartość.</span><span class="sxs-lookup"><span data-stu-id="e515b-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="e515b-142"><xref:System.IO.Stream.ReadAsync%2A> Metoda zwraca <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, więc tworzy oceny await `Int32` wartość (`numRead`) po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="e515b-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="e515b-143">Aby uzyskać więcej informacji, zobacz [Async zwracać typów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="e515b-143">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="e515b-144">Równoległe asynchroniczne We/Wy</span><span class="sxs-lookup"><span data-stu-id="e515b-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="e515b-145">W poniższym przykładzie pokazano przetwarzanie równoległe pisząc 10 plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="e515b-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="e515b-146">Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> metoda zwraca klasę task, która jest następnie dodawana do listy zadań.</span><span class="sxs-lookup"><span data-stu-id="e515b-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="e515b-147">`Await Task.WhenAll(tasks)` Instrukcji opuszcza metody i wznawia w metodzie podczas przetwarzania pliku jest zakończenie wszystkich zadań.</span><span class="sxs-lookup"><span data-stu-id="e515b-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="e515b-148">Przykład zamyka wszystkie <xref:System.IO.FileStream> wystąpień w `Finally` zablokować po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="e515b-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="e515b-149">Jeśli każda `FileStream` zamiast tego została utworzona w `Imports` instrukcji, `FileStream` może być usunięte przed ukończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="e515b-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="e515b-150">Należy pamiętać, że wszystkie wzrost wydajności prawie całkowicie z przetwarzanie równoległe i przetwarzania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="e515b-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="e515b-151">Zaletą asynchrony jest, aby nie zajmować wiele wątków i że nie blokowały wątek interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e515b-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="e515b-152">Korzystając z <xref:System.IO.Stream.WriteAsync%2A> i <xref:System.IO.Stream.ReadAsync%2A> metod, można określić <xref:System.Threading.CancellationToken>, którego można użyć, aby anulować operację strumienia pośredniej.</span><span class="sxs-lookup"><span data-stu-id="e515b-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="e515b-153">Aby uzyskać więcej informacji, zobacz [Fine-Tuning Twoja aplikacja Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) i [anulowanie w zarządzanych wątkach](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="e515b-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e515b-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e515b-154">See Also</span></span>  
 [<span data-ttu-id="e515b-155">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e515b-155">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="e515b-156">Asynchroniczne typy zwracane (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e515b-156">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="e515b-157">Przepływ sterowania w aplikacjach asynchronicznych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e515b-157">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
