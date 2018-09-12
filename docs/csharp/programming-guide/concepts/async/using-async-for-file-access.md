---
title: Użycie Async do uzyskiwania dostępu do plików (C#)
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: bbaeb14d5c17665308932c26a0630f1e9e5dabdf
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511451"
---
# <a name="using-async-for-file-access-c"></a>Użycie Async do uzyskiwania dostępu do plików (C#)
Funkcja async dostępu do plików. Za pomocą funkcji asynchronicznych, można wywoływać do metod asynchronicznych bez za pomocą wywołania zwrotne lub podział swój kod w wielu metod lub wyrażenia lambda. Aby synchroniczny kod asynchroniczny, możesz po prostu Wywołaj metodę asynchroniczną zamiast metody synchronicznej i dodać kilka słów kluczowych w kodzie.  
  
 Należy rozważyć następujące przyczyny Dodawanie asynchroniczności do wywołania dostępu do pliku:  
  
-   Asynchroniczność sprawia, że interfejsu użytkownika aplikacji zwiększyć szybkość reakcji, ponieważ wątek interfejsu użytkownika, który uruchamia operację można wykonywać inne zadania. Jeśli kod muszą być wykonywane w wątku interfejsu użytkownika, trwa zbyt długo (np. więcej niż 50 MS), interfejs użytkownika może zawieszać się we/wy zakończenie i wątku interfejsu użytkownika jest ponownie przetwarzanie klawiatury i myszy zdarzenia wejściowe i inne.  
  
-   Asynchroniczność zwiększa skalowalność platformy ASP.NET i innych aplikacji opartych na serwerze, redukując potrzebę dla wątków. Jeśli aplikacja korzysta z dedykowanego wątku na odpowiedzi i tysiące żądań, które są aktualnie obsługiwane jednocześnie, prościej i skuteczniej niż wątki są wymagane. Operacje asynchroniczne często trzeba użyć wątku podczas oczekiwania. Oni korzystać z istniejącego wątku zakończenia operacji We/Wy krótko po zakończeniu.  
  
-   Opóźnienie operacji dostępu do pliku może być bardzo niska, w ramach bieżących warunków, ale opóźnienie może znacznie zwiększyć w przyszłości. Na przykład pliku mogą być przenoszone do serwera, który jest na całym świecie.  
  
-   Dodano obciążenie związane z użyciem funkcji asynchronicznej jest mała.  
  
-   Łatwo można uruchomić zadania asynchroniczne równolegle.  
  
## <a name="running-the-examples"></a>Uruchamianie przykładów  
 Aby uruchomić przykłady w tym temacie, można utworzyć **aplikacji WPF** lub **aplikacja interfejsu Windows Forms** , a następnie dodaj **przycisk**. W przycisku `Click` zdarzeń, dodaj wywołanie do pierwszej metody w każdym przykładzie.  
  
 W poniższych przykładach, m.in `using` instrukcji.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>Użycie klasy FileStream  
 Przykłady w tym temacie <xref:System.IO.FileStream> klasy, która jest dostępna opcja, który powoduje, że asynchroniczne operacje We/Wy na poziomie systemu operacyjnego. Za pomocą tej opcji, możesz uniknąć blokowania puli wątków w wielu przypadkach. Aby włączyć tę opcję, należy określić `useAsync=true` lub `options=FileOptions.Asynchronous` argument w wywołaniu konstruktora.  
  
 Nie można użyć tej opcji z <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> Jeśli możesz otworzyć bezpośrednio, określając ścieżkę do pliku. Jednak można użyć tej opcji, jeśli zostaną podane <xref:System.IO.Stream> , <xref:System.IO.FileStream> klasy otwarty. Należy zauważyć, że wywołania asynchroniczne szybsza w interfejsie użytkownika aplikacji, nawet jeśli puli wątków jest zablokowany, ponieważ wątek interfejsu użytkownika nie jest blokowane podczas oczekiwania.  
  
## <a name="writing-text"></a>Pisanie tekstu  
 Poniższy przykład zapisuje tekst do pliku. W każdej await instrukcji, metoda natychmiast kończy pracę. Po zakończeniu operacji We/Wy pliku metody wznawia działanie w instrukcji, która następuje po instrukcji czekania. Należy zauważyć, że w definicji metody, które używają instrukcji czekania modyfikatora async.  
  
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
  
 Przykład oryginalnego zawiera instrukcję `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, który jest zmniejszenie dwie poniższe instrukcje:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 Pierwsza instrukcja zwraca klasę task i powoduje, że przetwarzanie pliku rozpocząć. Druga instrukcja z await powoduje, że metody od razu zakończyć proces i zwraca inne zadanie. Po zakończeniu przetwarzania w dalszej części plików, wykonywanie powraca do instrukcji następującej await. Aby uzyskać więcej informacji, zobacz [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Odczytywanie tekstu  
 Poniższy przykład odczytuje tekst z pliku. Tekst buforowane i umieszczane w tym przypadku <xref:System.Text.StringBuilder>. Inaczej niż w poprzednim przykładzie oceny await generuje wartość. <xref:System.IO.Stream.ReadAsync%2A> Metoda zwraca <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, więc tworzy oceny await `Int32` wartość (`numRead`) po zakończeniu operacji. Aby uzyskać więcej informacji, zobacz [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Równoległe asynchronicznego We/Wy  
 W poniższym przykładzie pokazano przetwarzania równoległego, pisząc 10 plików tekstowych. Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> metoda zwraca klasę task, która następnie zostanie dodany do listy zadań. `await Task.WhenAll(tasks);` Instrukcji opuszcza metody i wznawia wewnątrz metody, gdy przetwarzanie plików jest pełny dla wszystkich zadań.  
  
 Kod z przykładu zamyka wszystkie <xref:System.IO.FileStream> wystąpienia w `finally` blokować po zakończeniu zadania. Jeśli każda `FileStream` zamiast tego została utworzona w `using` instrukcji `FileStream` może zostać usunięte przed ukończeniem zadania.  
  
 Należy pamiętać, że wszelkie zwiększeniu wydajności prawie całkowicie z przetwarzanie równoległe i przetwarzania asynchronicznego. Zalety asynchroniczności to, czy nie blokując wiele wątków i że nie blokowały wątek interfejsu użytkownika.  
  
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
  
 Korzystając z <xref:System.IO.Stream.WriteAsync%2A> i <xref:System.IO.Stream.ReadAsync%2A> metody, można określić <xref:System.Threading.CancellationToken>, którego anulowanie strumienia środku operacji. Aby uzyskać więcej informacji, zobacz [Fine-Tuning aplikacji asynchronicznej (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) i [anulowanie w zarządzanych wątkach](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
- [Asynchroniczne typy zwracane (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
- [Przepływ sterowania w programach Async (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
