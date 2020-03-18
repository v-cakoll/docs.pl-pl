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
# <a name="using-async-for-file-access-c"></a>Korzystanie z asynchronii dostępu do plików (C#)
Aby uzyskać dostęp do plików, można użyć funkcji asynchronicznej. Za pomocą funkcji asynchronicznej, można wywołać w metodach asynchronicznych bez używania wywołania wstecznego lub dzielenia kodu na wiele metod lub wyrażeń lambda. Aby kod synchroniczny asynchroniczny, po prostu wywołać metodę asynchroniczną zamiast metody synchronicznej i dodać kilka słów kluczowych do kodu.  
  
 Można rozważyć następujące przyczyny dodawania asynchrony do wywołań dostępu do plików:  
  
- Asynchrony sprawia, że aplikacje interfejsu użytkownika bardziej elastyczne, ponieważ wątek interfejsu użytkownika, który uruchamia operację można wykonać inną pracę. Jeśli wątek interfejsu użytkownika musi wykonać kod, który zajmuje dużo czasu (na przykład więcej niż 50 milisekund), interfejsu użytkownika może zamrozić, dopóki we/wy jest kompletna i wątku interfejsu użytkownika można ponownie przetwarzać klawiatury i myszy wprowadzania i innych zdarzeń.  
  
- Asynchrony zwiększa skalowalność ASP.NET i innych aplikacji opartych na serwerze, zmniejszając zapotrzebowanie na wątki. Jeśli aplikacja używa dedykowanego wątku na odpowiedź i tysiąc żądań są obsługiwane jednocześnie, potrzebny chłosta jest potrzebna tysiąc wątków. Operacje asynchroniczne często nie trzeba używać wątku podczas oczekiwania. Używają istniejącego wątku zakończenia we/wy krótko na końcu.  
  
- Opóźnienie operacji dostępu do plików może być bardzo niska w obecnych warunkach, ale opóźnienie może znacznie zwiększyć w przyszłości. Na przykład plik może zostać przeniesiony na serwer, który jest na całym świecie.  
  
- Dodatkowe obciążenie przy użyciu funkcji Async jest niewielkie.  
  
- Zadania asynchroniczne można łatwo uruchamiać równolegle.  
  
## <a name="running-the-examples"></a>Uruchamianie przykładów  
 Aby uruchomić przykłady w tym temacie, można utworzyć **aplikację WPF** lub **aplikację formularzy systemu Windows,** a następnie dodać **przycisk**. W `Click` przypadku przycisku dodaj wywołanie do pierwszej metody w każdym przykładzie.  
  
 W poniższych przykładach dołącz `using` następujące instrukcje.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a>Korzystanie z klasy FileStream  
 Przykłady w tym temacie <xref:System.IO.FileStream> użyć klasy, która ma opcję, która powoduje asynchroniczne we/wy występuje na poziomie systemu operacyjnego. Za pomocą tej opcji można uniknąć blokowania wątku puli wątków w wielu przypadkach. Aby włączyć tę opcję, `useAsync=true` `options=FileOptions.Asynchronous` należy określić lub argument w wywołaniu konstruktora.  
  
 Nie można użyć tej <xref:System.IO.StreamReader> opcji <xref:System.IO.StreamWriter> z i jeśli otworzysz je bezpośrednio, określając ścieżkę pliku. Jednak można użyć tej opcji, jeśli <xref:System.IO.Stream> podasz im, że <xref:System.IO.FileStream> klasa została otwarta. Należy zauważyć, że wywołania asynchroniczne są szybsze w aplikacjach interfejsu użytkownika, nawet jeśli wątek puli wątków jest zablokowany, ponieważ wątek interfejsu użytkownika nie jest blokowany podczas oczekiwania.  
  
## <a name="writing-text"></a>Pisanie tekstu  
 Poniższy przykład zapisuje tekst do pliku. Przy każdej instrukcji await metoda natychmiast kończy działanie. Po zakończeniu we/wy pliku, metoda wznawia w instrukcji, która następuje await instrukcji. Należy zauważyć, że modyfikator asynchronii znajduje się w definicji metod, które używają await instrukcji.  
  
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
  
 Oryginalny przykład ma `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`instrukcję , która jest skurcz emanuje następującymi dwoma stwierdzeniami:  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 Pierwsza instrukcja zwraca zadanie i powoduje rozpoczęcie przetwarzania plików. Druga instrukcja z await powoduje, że metoda natychmiast zakończyć i zwrócić inne zadanie. Po zakończeniu przetwarzania pliku później, wykonanie powraca do instrukcji, która następuje await. Aby uzyskać więcej informacji, zobacz [Przepływ sterowania w programach asynchronicznych (C#)](./control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Czytanie tekstu  
 Poniższy przykład odczytuje tekst z pliku. Tekst jest buforowany i w tym przypadku <xref:System.Text.StringBuilder>umieszczany w pliku . W przeciwieństwie do poprzedniego przykładu oceny await daje wartość. Metoda <xref:System.IO.Stream.ReadAsync%2A> <xref:System.Threading.Tasks.Task> \< <xref:System.Int32> zwraca>, więc ocena await tworzy `Int32` wartość`numRead`( ) po zakończeniu operacji. Aby uzyskać więcej informacji, zobacz [Async Return Types (C#)](./async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Równoległe asynchroniczne we/wy  
 Poniższy przykład pokazuje przetwarzanie równoległe przez zapis 10 plików tekstowych. Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> metoda zwraca zadanie, które jest następnie dodawane do listy zadań. Instrukcja `await Task.WhenAll(tasks);` kończy działanie metody i wznawia pracę w ramach metody po zakończeniu przetwarzania pliku dla wszystkich zadań.  
  
 W przykładzie zamyka <xref:System.IO.FileStream> wszystkie wystąpienia `finally` w bloku po zakończeniu zadań. Jeśli `FileStream` każdy został utworzony `using` w instrukcji, `FileStream` może być usunięte przed zakończeniem zadania.  
  
 Należy zauważyć, że każdy wzrost wydajności jest prawie całkowicie z przetwarzania równoległego, a nie przetwarzania asynchronicznego. Zalety asynchrony są takie, że nie wiąże się z wieloma wątkami i że nie wiąże wątku interfejsu użytkownika.  
  
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
  
 Korzystając z <xref:System.IO.Stream.WriteAsync%2A> <xref:System.IO.Stream.ReadAsync%2A> i metod, można <xref:System.Threading.CancellationToken>określić , które można użyć do anulowania operacji mid-stream. Aby uzyskać więcej informacji, zobacz [Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md) i [anulowanie w wątkach zarządzanych](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne z async i await (C#)](./index.md)
- [Typy zwrotu asynchronicznego (C#)](./async-return-types.md)
- [Przepływ sterowania w programach asynchroniczny (C#)](./control-flow-in-async-programs.md)
