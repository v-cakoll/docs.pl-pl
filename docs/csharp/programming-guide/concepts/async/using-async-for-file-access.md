---
title: Korzystanie z asynchronii dostępu do plików (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: e6b0370049d9b9315de6a72d0e84c080aac12481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595533"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="3e840-102">Korzystanie z asynchronii dostępu do plików (C#)</span><span class="sxs-lookup"><span data-stu-id="3e840-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="3e840-103">Aby uzyskać dostęp do plików, można użyć funkcji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="3e840-103">You can use the async feature to access files.</span></span> <span data-ttu-id="3e840-104">Za pomocą funkcji asynchronicznej, można wywołać w metodach asynchronicznych bez używania wywołania wstecznego lub dzielenia kodu na wiele metod lub wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="3e840-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="3e840-105">Aby kod synchroniczny asynchroniczny, po prostu wywołać metodę asynchroniczną zamiast metody synchronicznej i dodać kilka słów kluczowych do kodu.</span><span class="sxs-lookup"><span data-stu-id="3e840-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="3e840-106">Można rozważyć następujące przyczyny dodawania asynchrony do wywołań dostępu do plików:</span><span class="sxs-lookup"><span data-stu-id="3e840-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="3e840-107">Asynchrony sprawia, że aplikacje interfejsu użytkownika bardziej elastyczne, ponieważ wątek interfejsu użytkownika, który uruchamia operację można wykonać inną pracę.</span><span class="sxs-lookup"><span data-stu-id="3e840-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="3e840-108">Jeśli wątek interfejsu użytkownika musi wykonać kod, który zajmuje dużo czasu (na przykład więcej niż 50 milisekund), interfejsu użytkownika może zamrozić, dopóki we/wy jest kompletna i wątku interfejsu użytkownika można ponownie przetwarzać klawiatury i myszy wprowadzania i innych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3e840-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="3e840-109">Asynchrony zwiększa skalowalność ASP.NET i innych aplikacji opartych na serwerze, zmniejszając zapotrzebowanie na wątki.</span><span class="sxs-lookup"><span data-stu-id="3e840-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="3e840-110">Jeśli aplikacja używa dedykowanego wątku na odpowiedź i tysiąc żądań są obsługiwane jednocześnie, potrzebny chłosta jest potrzebna tysiąc wątków.</span><span class="sxs-lookup"><span data-stu-id="3e840-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="3e840-111">Operacje asynchroniczne często nie trzeba używać wątku podczas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="3e840-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="3e840-112">Używają istniejącego wątku zakończenia we/wy krótko na końcu.</span><span class="sxs-lookup"><span data-stu-id="3e840-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="3e840-113">Opóźnienie operacji dostępu do plików może być bardzo niska w obecnych warunkach, ale opóźnienie może znacznie zwiększyć w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="3e840-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="3e840-114">Na przykład plik może zostać przeniesiony na serwer, który jest na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="3e840-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="3e840-115">Dodatkowe obciążenie przy użyciu funkcji Async jest niewielkie.</span><span class="sxs-lookup"><span data-stu-id="3e840-115">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="3e840-116">Zadania asynchroniczne można łatwo uruchamiać równolegle.</span><span class="sxs-lookup"><span data-stu-id="3e840-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="3e840-117">Uruchamianie przykładów</span><span class="sxs-lookup"><span data-stu-id="3e840-117">Running the Examples</span></span>  
 <span data-ttu-id="3e840-118">Aby uruchomić przykłady w tym temacie, można utworzyć **aplikację WPF** lub **aplikację formularzy systemu Windows,** a następnie dodać **przycisk**.</span><span class="sxs-lookup"><span data-stu-id="3e840-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="3e840-119">W `Click` przypadku przycisku dodaj wywołanie do pierwszej metody w każdym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3e840-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="3e840-120">W poniższych przykładach dołącz `using` następujące instrukcje.</span><span class="sxs-lookup"><span data-stu-id="3e840-120">In the following examples, include the following `using` statements.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="3e840-121">Korzystanie z klasy FileStream</span><span class="sxs-lookup"><span data-stu-id="3e840-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="3e840-122">Przykłady w tym temacie <xref:System.IO.FileStream> użyć klasy, która ma opcję, która powoduje asynchroniczne we/wy występuje na poziomie systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="3e840-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="3e840-123">Za pomocą tej opcji można uniknąć blokowania wątku puli wątków w wielu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="3e840-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="3e840-124">Aby włączyć tę opcję, `useAsync=true` `options=FileOptions.Asynchronous` należy określić lub argument w wywołaniu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="3e840-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="3e840-125">Nie można użyć tej <xref:System.IO.StreamReader> opcji <xref:System.IO.StreamWriter> z i jeśli otworzysz je bezpośrednio, określając ścieżkę pliku.</span><span class="sxs-lookup"><span data-stu-id="3e840-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="3e840-126">Jednak można użyć tej opcji, jeśli <xref:System.IO.Stream> podasz im, że <xref:System.IO.FileStream> klasa została otwarta.</span><span class="sxs-lookup"><span data-stu-id="3e840-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="3e840-127">Należy zauważyć, że wywołania asynchroniczne są szybsze w aplikacjach interfejsu użytkownika, nawet jeśli wątek puli wątków jest zablokowany, ponieważ wątek interfejsu użytkownika nie jest blokowany podczas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="3e840-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="3e840-128">Pisanie tekstu</span><span class="sxs-lookup"><span data-stu-id="3e840-128">Writing Text</span></span>  
 <span data-ttu-id="3e840-129">Poniższy przykład zapisuje tekst do pliku.</span><span class="sxs-lookup"><span data-stu-id="3e840-129">The following example writes text to a file.</span></span> <span data-ttu-id="3e840-130">Przy każdej instrukcji await metoda natychmiast kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="3e840-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="3e840-131">Po zakończeniu we/wy pliku, metoda wznawia w instrukcji, która następuje await instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3e840-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="3e840-132">Należy zauważyć, że modyfikator asynchronii znajduje się w definicji metod, które używają await instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3e840-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async Task ProcessWriteAsync()  
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
  
 <span data-ttu-id="3e840-133">Oryginalny przykład ma `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`instrukcję , która jest skurcz emanuje następującymi dwoma stwierdzeniami:</span><span class="sxs-lookup"><span data-stu-id="3e840-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="3e840-134">Pierwsza instrukcja zwraca zadanie i powoduje rozpoczęcie przetwarzania plików.</span><span class="sxs-lookup"><span data-stu-id="3e840-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="3e840-135">Druga instrukcja z await powoduje, że metoda natychmiast zakończyć i zwrócić inne zadanie.</span><span class="sxs-lookup"><span data-stu-id="3e840-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="3e840-136">Po zakończeniu przetwarzania pliku później, wykonanie powraca do instrukcji, która następuje await.</span><span class="sxs-lookup"><span data-stu-id="3e840-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="3e840-137">Aby uzyskać więcej informacji, zobacz [Przepływ sterowania w programach asynchronicznych (C#)](./control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="3e840-137">For more information, see  [Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="3e840-138">Czytanie tekstu</span><span class="sxs-lookup"><span data-stu-id="3e840-138">Reading Text</span></span>  
 <span data-ttu-id="3e840-139">Poniższy przykład odczytuje tekst z pliku.</span><span class="sxs-lookup"><span data-stu-id="3e840-139">The following example reads text from a file.</span></span> <span data-ttu-id="3e840-140">Tekst jest buforowany i w tym przypadku <xref:System.Text.StringBuilder>umieszczany w pliku .</span><span class="sxs-lookup"><span data-stu-id="3e840-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="3e840-141">W przeciwieństwie do poprzedniego przykładu oceny await daje wartość.</span><span class="sxs-lookup"><span data-stu-id="3e840-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="3e840-142">Metoda <xref:System.IO.Stream.ReadAsync%2A> <xref:System.Threading.Tasks.Task> \< <xref:System.Int32> zwraca>, więc ocena await tworzy `Int32` wartość`numRead`( ) po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="3e840-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="3e840-143">Aby uzyskać więcej informacji, zobacz [Async Return Types (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="3e840-143">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>  
  
```csharp  
public async Task ProcessReadAsync()  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="3e840-144">Równoległe asynchroniczne we/wy</span><span class="sxs-lookup"><span data-stu-id="3e840-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="3e840-145">Poniższy przykład pokazuje przetwarzanie równoległe przez zapis 10 plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="3e840-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="3e840-146">Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> metoda zwraca zadanie, które jest następnie dodawane do listy zadań.</span><span class="sxs-lookup"><span data-stu-id="3e840-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="3e840-147">Instrukcja `await Task.WhenAll(tasks);` kończy działanie metody i wznawia pracę w ramach metody po zakończeniu przetwarzania pliku dla wszystkich zadań.</span><span class="sxs-lookup"><span data-stu-id="3e840-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="3e840-148">W przykładzie zamyka <xref:System.IO.FileStream> wszystkie wystąpienia `finally` w bloku po zakończeniu zadań.</span><span class="sxs-lookup"><span data-stu-id="3e840-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="3e840-149">Jeśli `FileStream` każdy został utworzony `using` w instrukcji, `FileStream` może być usunięte przed zakończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="3e840-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="3e840-150">Należy zauważyć, że każdy wzrost wydajności jest prawie całkowicie z przetwarzania równoległego, a nie przetwarzania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="3e840-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="3e840-151">Zalety asynchrony są takie, że nie wiąże się z wieloma wątkami i że nie wiąże wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3e840-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async Task ProcessWriteMultAsync()  
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
  
 <span data-ttu-id="3e840-152">Korzystając z <xref:System.IO.Stream.WriteAsync%2A> <xref:System.IO.Stream.ReadAsync%2A> i metod, można <xref:System.Threading.CancellationToken>określić , które można użyć do anulowania operacji mid-stream.</span><span class="sxs-lookup"><span data-stu-id="3e840-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="3e840-153">Aby uzyskać więcej informacji, zobacz [Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md) i [anulowanie w wątkach zarządzanych](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="3e840-153">For more information, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e840-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e840-154">See also</span></span>

- [<span data-ttu-id="3e840-155">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="3e840-155">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="3e840-156">Typy zwrotu asynchronicznego (C#)</span><span class="sxs-lookup"><span data-stu-id="3e840-156">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="3e840-157">Przepływ sterowania w programach asynchroniczny (C#)</span><span class="sxs-lookup"><span data-stu-id="3e840-157">Control Flow in Async Programs (C#)</span></span>](./control-flow-in-async-programs.md)
