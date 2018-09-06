---
title: Użycie Async do uzyskiwania dostępu do plików (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: bbaeb14d5c17665308932c26a0630f1e9e5dabdf
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746464"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="14395-102">Użycie Async do uzyskiwania dostępu do plików (C#)</span><span class="sxs-lookup"><span data-stu-id="14395-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="14395-103">Funkcja async dostępu do plików.</span><span class="sxs-lookup"><span data-stu-id="14395-103">You can use the async feature to access files.</span></span> <span data-ttu-id="14395-104">Za pomocą funkcji asynchronicznych, można wywoływać do metod asynchronicznych bez za pomocą wywołania zwrotne lub podział swój kod w wielu metod lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="14395-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="14395-105">Aby synchroniczny kod asynchroniczny, możesz po prostu Wywołaj metodę asynchroniczną zamiast metody synchronicznej i dodać kilka słów kluczowych w kodzie.</span><span class="sxs-lookup"><span data-stu-id="14395-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="14395-106">Należy rozważyć następujące przyczyny Dodawanie asynchroniczności do wywołania dostępu do pliku:</span><span class="sxs-lookup"><span data-stu-id="14395-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="14395-107">Asynchroniczność sprawia, że interfejsu użytkownika aplikacji zwiększyć szybkość reakcji, ponieważ wątek interfejsu użytkownika, który uruchamia operację można wykonywać inne zadania.</span><span class="sxs-lookup"><span data-stu-id="14395-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="14395-108">Jeśli kod muszą być wykonywane w wątku interfejsu użytkownika, trwa zbyt długo (np. więcej niż 50 MS), interfejs użytkownika może zawieszać się we/wy zakończenie i wątku interfejsu użytkownika jest ponownie przetwarzanie klawiatury i myszy zdarzenia wejściowe i inne.</span><span class="sxs-lookup"><span data-stu-id="14395-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="14395-109">Asynchroniczność zwiększa skalowalność platformy ASP.NET i innych aplikacji opartych na serwerze, redukując potrzebę dla wątków.</span><span class="sxs-lookup"><span data-stu-id="14395-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="14395-110">Jeśli aplikacja korzysta z dedykowanego wątku na odpowiedzi i tysiące żądań, które są aktualnie obsługiwane jednocześnie, prościej i skuteczniej niż wątki są wymagane.</span><span class="sxs-lookup"><span data-stu-id="14395-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="14395-111">Operacje asynchroniczne często trzeba użyć wątku podczas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="14395-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="14395-112">Oni korzystać z istniejącego wątku zakończenia operacji We/Wy krótko po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="14395-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="14395-113">Opóźnienie operacji dostępu do pliku może być bardzo niska, w ramach bieżących warunków, ale opóźnienie może znacznie zwiększyć w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="14395-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="14395-114">Na przykład pliku mogą być przenoszone do serwera, który jest na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="14395-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="14395-115">Dodano obciążenie związane z użyciem funkcji asynchronicznej jest mała.</span><span class="sxs-lookup"><span data-stu-id="14395-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="14395-116">Łatwo można uruchomić zadania asynchroniczne równolegle.</span><span class="sxs-lookup"><span data-stu-id="14395-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="14395-117">Uruchamianie przykładów</span><span class="sxs-lookup"><span data-stu-id="14395-117">Running the Examples</span></span>  
 <span data-ttu-id="14395-118">Aby uruchomić przykłady w tym temacie, można utworzyć **aplikacji WPF** lub **aplikacja interfejsu Windows Forms** , a następnie dodaj **przycisk**.</span><span class="sxs-lookup"><span data-stu-id="14395-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="14395-119">W przycisku `Click` zdarzeń, dodaj wywołanie do pierwszej metody w każdym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="14395-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="14395-120">W poniższych przykładach, m.in `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="14395-120">In the following examples, include the following `using` statements.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="14395-121">Użycie klasy FileStream</span><span class="sxs-lookup"><span data-stu-id="14395-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="14395-122">Przykłady w tym temacie <xref:System.IO.FileStream> klasy, która jest dostępna opcja, który powoduje, że asynchroniczne operacje We/Wy na poziomie systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="14395-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="14395-123">Za pomocą tej opcji, możesz uniknąć blokowania puli wątków w wielu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="14395-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="14395-124">Aby włączyć tę opcję, należy określić `useAsync=true` lub `options=FileOptions.Asynchronous` argument w wywołaniu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="14395-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="14395-125">Nie można użyć tej opcji z <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> Jeśli możesz otworzyć bezpośrednio, określając ścieżkę do pliku.</span><span class="sxs-lookup"><span data-stu-id="14395-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="14395-126">Jednak można użyć tej opcji, jeśli zostaną podane <xref:System.IO.Stream> , <xref:System.IO.FileStream> klasy otwarty.</span><span class="sxs-lookup"><span data-stu-id="14395-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="14395-127">Należy zauważyć, że wywołania asynchroniczne szybsza w interfejsie użytkownika aplikacji, nawet jeśli puli wątków jest zablokowany, ponieważ wątek interfejsu użytkownika nie jest blokowane podczas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="14395-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="14395-128">Pisanie tekstu</span><span class="sxs-lookup"><span data-stu-id="14395-128">Writing Text</span></span>  
 <span data-ttu-id="14395-129">Poniższy przykład zapisuje tekst do pliku.</span><span class="sxs-lookup"><span data-stu-id="14395-129">The following example writes text to a file.</span></span> <span data-ttu-id="14395-130">W każdej await instrukcji, metoda natychmiast kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="14395-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="14395-131">Po zakończeniu operacji We/Wy pliku metody wznawia działanie w instrukcji, która następuje po instrukcji czekania.</span><span class="sxs-lookup"><span data-stu-id="14395-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="14395-132">Należy zauważyć, że w definicji metody, które używają instrukcji czekania modyfikatora async.</span><span class="sxs-lookup"><span data-stu-id="14395-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="14395-133">Przykład oryginalnego zawiera instrukcję `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, który jest zmniejszenie dwie poniższe instrukcje:</span><span class="sxs-lookup"><span data-stu-id="14395-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="14395-134">Pierwsza instrukcja zwraca klasę task i powoduje, że przetwarzanie pliku rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="14395-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="14395-135">Druga instrukcja z await powoduje, że metody od razu zakończyć proces i zwraca inne zadanie.</span><span class="sxs-lookup"><span data-stu-id="14395-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="14395-136">Po zakończeniu przetwarzania w dalszej części plików, wykonywanie powraca do instrukcji następującej await.</span><span class="sxs-lookup"><span data-stu-id="14395-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="14395-137">Aby uzyskać więcej informacji, zobacz [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="14395-137">For more information, see  [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="14395-138">Odczytywanie tekstu</span><span class="sxs-lookup"><span data-stu-id="14395-138">Reading Text</span></span>  
 <span data-ttu-id="14395-139">Poniższy przykład odczytuje tekst z pliku.</span><span class="sxs-lookup"><span data-stu-id="14395-139">The following example reads text from a file.</span></span> <span data-ttu-id="14395-140">Tekst buforowane i umieszczane w tym przypadku <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="14395-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="14395-141">Inaczej niż w poprzednim przykładzie oceny await generuje wartość.</span><span class="sxs-lookup"><span data-stu-id="14395-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="14395-142"><xref:System.IO.Stream.ReadAsync%2A> Metoda zwraca <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, więc tworzy oceny await `Int32` wartość (`numRead`) po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="14395-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="14395-143">Aby uzyskać więcej informacji, zobacz [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="14395-143">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="14395-144">Równoległe asynchronicznego We/Wy</span><span class="sxs-lookup"><span data-stu-id="14395-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="14395-145">W poniższym przykładzie pokazano przetwarzania równoległego, pisząc 10 plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="14395-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="14395-146">Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> metoda zwraca klasę task, która następnie zostanie dodany do listy zadań.</span><span class="sxs-lookup"><span data-stu-id="14395-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="14395-147">`await Task.WhenAll(tasks);` Instrukcji opuszcza metody i wznawia wewnątrz metody, gdy przetwarzanie plików jest pełny dla wszystkich zadań.</span><span class="sxs-lookup"><span data-stu-id="14395-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="14395-148">Kod z przykładu zamyka wszystkie <xref:System.IO.FileStream> wystąpienia w `finally` blokować po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="14395-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="14395-149">Jeśli każda `FileStream` zamiast tego została utworzona w `using` instrukcji `FileStream` może zostać usunięte przed ukończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="14395-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="14395-150">Należy pamiętać, że wszelkie zwiększeniu wydajności prawie całkowicie z przetwarzanie równoległe i przetwarzania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="14395-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="14395-151">Zalety asynchroniczności to, czy nie blokując wiele wątków i że nie blokowały wątek interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14395-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="14395-152">Korzystając z <xref:System.IO.Stream.WriteAsync%2A> i <xref:System.IO.Stream.ReadAsync%2A> metody, można określić <xref:System.Threading.CancellationToken>, którego anulowanie strumienia środku operacji.</span><span class="sxs-lookup"><span data-stu-id="14395-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="14395-153">Aby uzyskać więcej informacji, zobacz [Fine-Tuning aplikacji asynchronicznej (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) i [anulowanie w zarządzanych wątkach](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="14395-153">For more information, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14395-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14395-154">See Also</span></span>

- [<span data-ttu-id="14395-155">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="14395-155">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
- [<span data-ttu-id="14395-156">Asynchroniczne typy zwracane (C#)</span><span class="sxs-lookup"><span data-stu-id="14395-156">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
- [<span data-ttu-id="14395-157">Przepływ sterowania w programach Async (C#)</span><span class="sxs-lookup"><span data-stu-id="14395-157">Control Flow in Async Programs (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
