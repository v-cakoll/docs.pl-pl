---
title: Użycie Async do uzyskiwania dostępu do plików (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 083a9113fc75c9e18646953a144b9e3d1bfd90ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328292"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="2682d-102">Użycie Async do uzyskiwania dostępu do plików (C#)</span><span class="sxs-lookup"><span data-stu-id="2682d-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="2682d-103">Funkcja async dostęp do plików.</span><span class="sxs-lookup"><span data-stu-id="2682d-103">You can use the async feature to access files.</span></span> <span data-ttu-id="2682d-104">Korzystając z funkcji asynchronicznych, należy wywołać do metod asynchronicznych bez przy użyciu wywołania zwrotne i dzielenia kodu wielu metod lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="2682d-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="2682d-105">Aby wprowadzić kod synchroniczne asynchroniczne, możesz tylko wywołania metody asynchronicznej zamiast metoda synchroniczna i dodać kilka słów kluczowych w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2682d-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="2682d-106">Należy rozważyć następujące przyczyny dodawania asynchrony do wywołania dostępu do pliku:</span><span class="sxs-lookup"><span data-stu-id="2682d-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="2682d-107">Asynchrony sprawia, że aplikacje interfejsu użytkownika usprawnia ponieważ wątku interfejsu użytkownika, który uruchamia operację można wykonywać inne zadania.</span><span class="sxs-lookup"><span data-stu-id="2682d-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="2682d-108">Jeśli kod musi być wykonywany w wątku interfejsu użytkownika który zajmuje dużo czasu (na przykład więcej niż 50 w milisekundach), interfejsu użytkownika może zawieszać się dopiero po zakończeniu operacji We/Wy i wątku interfejsu użytkownika można ponownie przetworzyć klawiatury i myszy zdarzenia wejściowe i inne.</span><span class="sxs-lookup"><span data-stu-id="2682d-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="2682d-109">Asynchrony poprawia skalowalność programu ASP.NET i innych aplikacji serwerowych, zmniejszając potrzebę wątków.</span><span class="sxs-lookup"><span data-stu-id="2682d-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="2682d-110">Jeśli aplikacja używa dedykowanego wątku na odpowiedzi i żądania tysięcy są obsługiwane jednocześnie, potrzebne są tysiące wątków.</span><span class="sxs-lookup"><span data-stu-id="2682d-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="2682d-111">Operacje asynchroniczne często nie trzeba używać wątku podczas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="2682d-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="2682d-112">Istniejące wątku zakończenia We/Wy będzie używać krótko po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="2682d-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="2682d-113">Opóźnienie operacji dostępu do pliku może być bardzo niskich warunkach bieżący, ale opóźnienie może znacznie zwiększyć w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="2682d-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="2682d-114">Na przykład plik może przenieść do serwera, który jest na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="2682d-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="2682d-115">Dodany korzystać z funkcji asynchronicznych jest mała.</span><span class="sxs-lookup"><span data-stu-id="2682d-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="2682d-116">Zadania asynchronicznego łatwo mogą być uruchamiane równolegle.</span><span class="sxs-lookup"><span data-stu-id="2682d-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="2682d-117">Uruchamianie przykładów</span><span class="sxs-lookup"><span data-stu-id="2682d-117">Running the Examples</span></span>  
 <span data-ttu-id="2682d-118">Aby uruchomić przykłady w tym temacie, można utworzyć **aplikacji WPF** lub **aplikacji Windows Forms** , a następnie dodaj **przycisk**.</span><span class="sxs-lookup"><span data-stu-id="2682d-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="2682d-119">Przycisk `Click` zdarzeń, dodaj wywołanie do metody pierwszy w każdym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2682d-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="2682d-120">W poniższych przykładach są następujące `using` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="2682d-120">In the following examples, include the following `using` statements.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="2682d-121">Użyj klasy FileStream</span><span class="sxs-lookup"><span data-stu-id="2682d-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="2682d-122">Przykłady w tym temacie <xref:System.IO.FileStream> klasy, która jest dostępna opcja, która powoduje występowanie asynchroniczne We/Wy na poziomie systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2682d-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="2682d-123">Przy użyciu tej opcji, można uniknąć, blokuje puli wątków w wielu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="2682d-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="2682d-124">Aby włączyć tę opcję, należy określić `useAsync=true` lub `options=FileOptions.Asynchronous` argument w wywołaniu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2682d-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="2682d-125">Nie można użyć tej opcji z <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> otwarcia bezpośrednio, określając ścieżkę pliku.</span><span class="sxs-lookup"><span data-stu-id="2682d-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="2682d-126">Jednak można użyć tej opcji, jeśli zostaną podane <xref:System.IO.Stream> który <xref:System.IO.FileStream> klasy otwarty.</span><span class="sxs-lookup"><span data-stu-id="2682d-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="2682d-127">Należy zauważyć, że wywołania asynchroniczne szybsze w aplikacjach interfejsu użytkownika, nawet jeśli puli wątków jest zablokowana, ponieważ wątku interfejsu użytkownika nie jest blokowane podczas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="2682d-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="2682d-128">Pisanie tekstu</span><span class="sxs-lookup"><span data-stu-id="2682d-128">Writing Text</span></span>  
 <span data-ttu-id="2682d-129">Poniższy przykład zapisuje tekst w pliku.</span><span class="sxs-lookup"><span data-stu-id="2682d-129">The following example writes text to a file.</span></span> <span data-ttu-id="2682d-130">W każdej await instrukcji, metoda natychmiast kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="2682d-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="2682d-131">Po zakończeniu operacji We/Wy pliku metody wznawia działanie w instrukcji, która wykonuje instrukcję await.</span><span class="sxs-lookup"><span data-stu-id="2682d-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="2682d-132">Należy zauważyć, że w definicji metody, które używają instrukcja await modyfikatora async.</span><span class="sxs-lookup"><span data-stu-id="2682d-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async void ProcessWrite()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 <span data-ttu-id="2682d-133">Przykład oryginalnego ma instrukcji `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, która jest zmniejszenie następujące dwie instrukcje:</span><span class="sxs-lookup"><span data-stu-id="2682d-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="2682d-134">Pierwsza instrukcja zwraca klasę task i powoduje, że przetwarzanie pliku rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="2682d-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="2682d-135">Drugi instrukcji z await powoduje, że metoda natychmiast wyjść i wrócić inne zadanie.</span><span class="sxs-lookup"><span data-stu-id="2682d-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="2682d-136">Po zakończeniu przetwarzania później plików, wykonanie zwraca do instrukcji następującej await.</span><span class="sxs-lookup"><span data-stu-id="2682d-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="2682d-137">Aby uzyskać więcej informacji, zobacz [przepływ sterowania w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="2682d-137">For more information, see  [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="2682d-138">Odczytywanie tekstu</span><span class="sxs-lookup"><span data-stu-id="2682d-138">Reading Text</span></span>  
 <span data-ttu-id="2682d-139">Poniższy przykład odczytuje tekst z pliku.</span><span class="sxs-lookup"><span data-stu-id="2682d-139">The following example reads text from a file.</span></span> <span data-ttu-id="2682d-140">Tekst buforowane i umieszczane w takim przypadku <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="2682d-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="2682d-141">Inaczej niż w poprzednim przykładzie oceny await tworzy wartość.</span><span class="sxs-lookup"><span data-stu-id="2682d-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="2682d-142"><xref:System.IO.Stream.ReadAsync%2A> Metoda zwraca <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, więc tworzy oceny await `Int32` wartość (`numRead`) po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="2682d-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="2682d-143">Aby uzyskać więcej informacji, zobacz [typy zwracać Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="2682d-143">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
```csharp  
public async void ProcessRead()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="2682d-144">Równoległe asynchroniczne We/Wy</span><span class="sxs-lookup"><span data-stu-id="2682d-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="2682d-145">W poniższym przykładzie pokazano przetwarzanie równoległe pisząc 10 plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="2682d-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="2682d-146">Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> metoda zwraca klasę task, która jest następnie dodawana do listy zadań.</span><span class="sxs-lookup"><span data-stu-id="2682d-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="2682d-147">`await Task.WhenAll(tasks);` Instrukcji opuszcza metody i wznawia w metodzie podczas przetwarzania pliku jest zakończenie wszystkich zadań.</span><span class="sxs-lookup"><span data-stu-id="2682d-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="2682d-148">Przykład zamyka wszystkie <xref:System.IO.FileStream> wystąpień w `finally` zablokować po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="2682d-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="2682d-149">Jeśli każda `FileStream` zamiast tego została utworzona w `using` instrukcji, `FileStream` może być usunięte przed ukończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="2682d-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="2682d-150">Należy pamiętać, że wszystkie wzrost wydajności prawie całkowicie z przetwarzanie równoległe i przetwarzania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="2682d-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="2682d-151">Zaletą asynchrony jest, aby nie zajmować wiele wątków i że nie blokowały wątek interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2682d-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async void ProcessWriteMult()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="2682d-152">Korzystając z <xref:System.IO.Stream.WriteAsync%2A> i <xref:System.IO.Stream.ReadAsync%2A> metod, można określić <xref:System.Threading.CancellationToken>, którego można użyć, aby anulować operację strumienia pośredniej.</span><span class="sxs-lookup"><span data-stu-id="2682d-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="2682d-153">Aby uzyskać więcej informacji, zobacz [Fine-Tuning Twoja aplikacja Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) i [anulowanie w zarządzanych wątkach](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="2682d-153">For more information, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2682d-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2682d-154">See Also</span></span>  
 [<span data-ttu-id="2682d-155">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="2682d-155">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="2682d-156">Asynchroniczne typy zwracane (C#)</span><span class="sxs-lookup"><span data-stu-id="2682d-156">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="2682d-157">Przepływ sterowania w aplikacjach asynchronicznych (C#)</span><span class="sxs-lookup"><span data-stu-id="2682d-157">Control Flow in Async Programs (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
