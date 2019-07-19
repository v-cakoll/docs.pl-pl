---
title: Używanie Async na potrzeby dostępu doC#plików ()
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 6ca47157575ef4569a43f334dae4f99a1986a7ce
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68330935"
---
# <a name="using-async-for-file-access-c"></a>Używanie Async na potrzeby dostępu doC#plików ()
Do uzyskiwania dostępu do plików można użyć funkcji asynchronicznej. Za pomocą funkcji asynchronicznej można wywołać metody asynchroniczne bez używania wywołań zwrotnych lub dzieląc kod w wielu metodach lub wyrażeniach lambda. Aby przeprowadzić synchroniczne asynchroniczne kod, wystarczy wywołać metodę asynchroniczną zamiast metody synchronicznej i dodać kilka słów kluczowych do kodu.  
  
 Aby dodać asynchroniczności do wywołań dostępu do plików, należy wziąć pod uwagę następujące przyczyny:  
  
- Asynchroniczności sprawia, że aplikacje interfejsu użytkownika działają szybciej, ponieważ wątek interfejsu użytkownika uruchamiający operację może wykonać inne czynności. Jeśli wątek interfejsu użytkownika musi wykonać kod, który zajmuje dużo czasu (na przykład więcej niż 50 milisekund), interfejs użytkownika może się zamrozić do momentu zakończenia operacji we/wy, a wątek interfejsu użytkownika może ponownie przetwarzać dane wejściowe klawiatury i myszy oraz inne zdarzenia.  
  
- Asynchroniczności poprawia skalowalność ASP.NET i innych aplikacji opartych na serwerze, zmniejszając potrzebę wątków. Jeśli aplikacja korzysta z dedykowanego wątku na odpowiedź i jednocześnie są obsługiwane tysiące żądań, są zbędne tysiące wątków. Operacje asynchroniczne często nie muszą używać wątku podczas oczekiwania. Z chwilą korzystają z istniejącego wątku zakończenia operacji we/wy.  
  
- Opóźnienie operacji dostępu do pliku może być bardzo niskie w bieżących warunkach, ale opóźnienie może znacznie wzrosnąć w przyszłości. Na przykład plik można przenieść na serwer, na którym znajduje się na całym świecie.  
  
- Dodatkowe obciążenie związane z korzystaniem z funkcji asynchronicznej jest małe.  
  
- Zadania asynchroniczne można łatwo uruchomić równolegle.  
  
## <a name="running-the-examples"></a>Uruchamianie przykładów  
 Aby uruchomić przykłady w tym temacie, można utworzyć **aplikację WPF** lub **aplikację Windows Forms** , a następnie dodać **przycisk**. W `Click` zdarzeniu przycisku Dodaj wywołanie do pierwszej metody w każdym przykładzie.  
  
 W poniższych przykładach Uwzględnij poniższe `using` instrukcje.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>Użycie klasy FileStream  
 Przykłady w tym temacie używają <xref:System.IO.FileStream> klasy, która powoduje wystąpienie asynchroniczne we/wy na poziomie systemu operacyjnego. Korzystając z tej opcji, można uniknąć zablokowania wątku puli wątków w wielu przypadkach. Aby włączyć tę opcję, należy określić `useAsync=true` argument or `options=FileOptions.Asynchronous` w wywołaniu konstruktora.  
  
 Nie można użyć tej opcji razem <xref:System.IO.StreamReader> z <xref:System.IO.StreamWriter> i, jeśli otworzysz je bezpośrednio, określając ścieżkę pliku. Można jednak użyć tej opcji, jeśli podajesz im <xref:System.IO.Stream> <xref:System.IO.FileStream> , że została otwarta Klasa. Należy zauważyć, że wywołania asynchroniczne są szybsze w aplikacjach interfejsu użytkownika, nawet jeśli wątek puli wątków jest zablokowany, ponieważ wątek interfejsu użytkownika nie jest blokowany podczas oczekiwania.  
  
## <a name="writing-text"></a>Pisanie tekstu  
 Poniższy przykład zapisuje tekst do pliku. W każdej instrukcji Await Metoda natychmiast opuszcza. Po zakończeniu operacji we/wy pliku Metoda zostaje wznowiona przy użyciu instrukcji, która następuje po instrukcji Await. Należy zauważyć, że modyfikator Async jest w definicji metod, które używają instrukcji Await.  
  
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
  
 Oryginalny przykład zawiera instrukcję `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, która jest umową obejmującą następujące dwie instrukcje:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 Pierwsza instrukcja zwraca zadanie i powoduje uruchomienie przetwarzania plików. Druga instrukcja z Await powoduje, że metoda natychmiast zakończy działanie i zwróci inne zadanie. Po późniejszym zakończeniu przetwarzania plików wykonanie powraca do instrukcji, która następuje po oczekiwania. Aby uzyskać więcej informacji, zobacz [sterowanie przepływem w programachC#asynchronicznych ()](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Odczytywanie tekstu  
 Poniższy przykład odczytuje tekst z pliku. Tekst jest buforowany i, w tym przypadku, umieszczony w <xref:System.Text.StringBuilder>. W przeciwieństwie do poprzedniego przykładu, obliczanie oczekiwania powoduje utworzenie wartości. <xref:System.IO.Stream.ReadAsync%2A> Metoda <xref:System.Threading.Tasks.Task> `Int32` zwraca >, więc Ocena await generuje wartość(`numRead`) po zakończeniu operacji. \< <xref:System.Int32> Aby uzyskać więcej informacji, zobacz [asynchroniczne typy zwracaneC#()](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Równoległe asynchroniczne operacje we/wy  
 Poniższy przykład ilustruje przetwarzanie równoległe, pisząc 10 plików tekstowych. Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> Metoda zwraca zadanie, które jest następnie dodawane do listy zadań. `await Task.WhenAll(tasks);` Instrukcja kończy metodę i wznawia działanie w ramach metody po zakończeniu przetwarzania plików dla wszystkich zadań.  
  
 Przykład zamyka wszystkie <xref:System.IO.FileStream> wystąpienia `finally` w bloku po zakończeniu zadań. Jeśli każdy `FileStream` z nich został utworzony `using` w instrukcji, `FileStream` może zostać usunięty przed ukończeniem zadania.  
  
 Należy pamiętać, że zwiększenie wydajności jest niemal całkowicie wynikiem przetwarzania równoległego, a nie przetwarzania asynchronicznego. Zalety asynchroniczności są takie same, że nie wiążą się z wieloma wątkami i nie wiążą się z wątkiem interfejsu użytkownika.  
  
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
  
 W przypadku korzystania <xref:System.IO.Stream.WriteAsync%2A> z <xref:System.IO.Stream.ReadAsync%2A> metod i można określić <xref:System.Threading.CancellationToken>, której można użyć do anulowania strumienia średniej operacji. Aby uzyskać więcej informacji, zobacz [dostrajanie aplikacji asynchronicznej (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) i [Anulowanie w zarządzanych wątkach](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z Async i Await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Asynchroniczne typy zwracane (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [Przepływ sterowania w programach asynchronicznychC#()](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
