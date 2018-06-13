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
# <a name="using-async-for-file-access-c"></a>Użycie Async do uzyskiwania dostępu do plików (C#)
Funkcja async dostęp do plików. Korzystając z funkcji asynchronicznych, należy wywołać do metod asynchronicznych bez przy użyciu wywołania zwrotne i dzielenia kodu wielu metod lub wyrażenia lambda. Aby wprowadzić kod synchroniczne asynchroniczne, możesz tylko wywołania metody asynchronicznej zamiast metoda synchroniczna i dodać kilka słów kluczowych w kodzie.  
  
 Należy rozważyć następujące przyczyny dodawania asynchrony do wywołania dostępu do pliku:  
  
-   Asynchrony sprawia, że aplikacje interfejsu użytkownika usprawnia ponieważ wątku interfejsu użytkownika, który uruchamia operację można wykonywać inne zadania. Jeśli kod musi być wykonywany w wątku interfejsu użytkownika który zajmuje dużo czasu (na przykład więcej niż 50 w milisekundach), interfejsu użytkownika może zawieszać się dopiero po zakończeniu operacji We/Wy i wątku interfejsu użytkownika można ponownie przetworzyć klawiatury i myszy zdarzenia wejściowe i inne.  
  
-   Asynchrony poprawia skalowalność programu ASP.NET i innych aplikacji serwerowych, zmniejszając potrzebę wątków. Jeśli aplikacja używa dedykowanego wątku na odpowiedzi i żądania tysięcy są obsługiwane jednocześnie, potrzebne są tysiące wątków. Operacje asynchroniczne często nie trzeba używać wątku podczas oczekiwania. Istniejące wątku zakończenia We/Wy będzie używać krótko po zakończeniu.  
  
-   Opóźnienie operacji dostępu do pliku może być bardzo niskich warunkach bieżący, ale opóźnienie może znacznie zwiększyć w przyszłości. Na przykład plik może przenieść do serwera, który jest na całym świecie.  
  
-   Dodany korzystać z funkcji asynchronicznych jest mała.  
  
-   Zadania asynchronicznego łatwo mogą być uruchamiane równolegle.  
  
## <a name="running-the-examples"></a>Uruchamianie przykładów  
 Aby uruchomić przykłady w tym temacie, można utworzyć **aplikacji WPF** lub **aplikacji Windows Forms** , a następnie dodaj **przycisk**. Przycisk `Click` zdarzeń, dodaj wywołanie do metody pierwszy w każdym przykładzie.  
  
 W poniższych przykładach są następujące `using` instrukcje.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>Użyj klasy FileStream  
 Przykłady w tym temacie <xref:System.IO.FileStream> klasy, która jest dostępna opcja, która powoduje występowanie asynchroniczne We/Wy na poziomie systemu operacyjnego. Przy użyciu tej opcji, można uniknąć, blokuje puli wątków w wielu przypadkach. Aby włączyć tę opcję, należy określić `useAsync=true` lub `options=FileOptions.Asynchronous` argument w wywołaniu konstruktora.  
  
 Nie można użyć tej opcji z <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> otwarcia bezpośrednio, określając ścieżkę pliku. Jednak można użyć tej opcji, jeśli zostaną podane <xref:System.IO.Stream> który <xref:System.IO.FileStream> klasy otwarty. Należy zauważyć, że wywołania asynchroniczne szybsze w aplikacjach interfejsu użytkownika, nawet jeśli puli wątków jest zablokowana, ponieważ wątku interfejsu użytkownika nie jest blokowane podczas oczekiwania.  
  
## <a name="writing-text"></a>Pisanie tekstu  
 Poniższy przykład zapisuje tekst w pliku. W każdej await instrukcji, metoda natychmiast kończy pracę. Po zakończeniu operacji We/Wy pliku metody wznawia działanie w instrukcji, która wykonuje instrukcję await. Należy zauważyć, że w definicji metody, które używają instrukcja await modyfikatora async.  
  
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
  
 Przykład oryginalnego ma instrukcji `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, która jest zmniejszenie następujące dwie instrukcje:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 Pierwsza instrukcja zwraca klasę task i powoduje, że przetwarzanie pliku rozpocząć. Drugi instrukcji z await powoduje, że metoda natychmiast wyjść i wrócić inne zadanie. Po zakończeniu przetwarzania później plików, wykonanie zwraca do instrukcji następującej await. Aby uzyskać więcej informacji, zobacz [przepływ sterowania w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Odczytywanie tekstu  
 Poniższy przykład odczytuje tekst z pliku. Tekst buforowane i umieszczane w takim przypadku <xref:System.Text.StringBuilder>. Inaczej niż w poprzednim przykładzie oceny await tworzy wartość. <xref:System.IO.Stream.ReadAsync%2A> Metoda zwraca <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, więc tworzy oceny await `Int32` wartość (`numRead`) po zakończeniu operacji. Aby uzyskać więcej informacji, zobacz [typy zwracać Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Równoległe asynchroniczne We/Wy  
 W poniższym przykładzie pokazano przetwarzanie równoległe pisząc 10 plików tekstowych. Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> metoda zwraca klasę task, która jest następnie dodawana do listy zadań. `await Task.WhenAll(tasks);` Instrukcji opuszcza metody i wznawia w metodzie podczas przetwarzania pliku jest zakończenie wszystkich zadań.  
  
 Przykład zamyka wszystkie <xref:System.IO.FileStream> wystąpień w `finally` zablokować po zakończeniu zadania. Jeśli każda `FileStream` zamiast tego została utworzona w `using` instrukcji, `FileStream` może być usunięte przed ukończeniem zadania.  
  
 Należy pamiętać, że wszystkie wzrost wydajności prawie całkowicie z przetwarzanie równoległe i przetwarzania asynchronicznego. Zaletą asynchrony jest, aby nie zajmować wiele wątków i że nie blokowały wątek interfejsu użytkownika.  
  
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
  
 Korzystając z <xref:System.IO.Stream.WriteAsync%2A> i <xref:System.IO.Stream.ReadAsync%2A> metod, można określić <xref:System.Threading.CancellationToken>, którego można użyć, aby anulować operację strumienia pośredniej. Aby uzyskać więcej informacji, zobacz [Fine-Tuning Twoja aplikacja Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) i [anulowanie w zarządzanych wątkach](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Asynchroniczne typy zwracane (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [Przepływ sterowania w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
