---
title: Użycie Async do uzyskiwania dostępu do plików (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: 0b2b95f1e4f9bc120acdad606b0f15503285057a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61829533"
---
# <a name="using-async-for-file-access-visual-basic"></a>Użycie Async do uzyskiwania dostępu do plików (Visual Basic)
Funkcja Async dostępu do plików. Za pomocą funkcji asynchronicznych, można wywoływać do metod asynchronicznych bez za pomocą wywołania zwrotne lub podział swój kod w wielu metod lub wyrażenia lambda. Aby synchroniczny kod asynchroniczny, możesz po prostu Wywołaj metodę asynchroniczną zamiast metody synchronicznej i dodać kilka słów kluczowych w kodzie.  
  
 Należy rozważyć następujące przyczyny Dodawanie asynchroniczności do wywołania dostępu do pliku:  
  
- Asynchroniczność sprawia, że interfejsu użytkownika aplikacji zwiększyć szybkość reakcji, ponieważ wątek interfejsu użytkownika, który uruchamia operację można wykonywać inne zadania. Jeśli kod muszą być wykonywane w wątku interfejsu użytkownika, trwa zbyt długo (np. więcej niż 50 MS), interfejs użytkownika może zawieszać się we/wy zakończenie i wątku interfejsu użytkownika jest ponownie przetwarzanie klawiatury i myszy zdarzenia wejściowe i inne.  
  
- Asynchroniczność zwiększa skalowalność platformy ASP.NET i innych aplikacji opartych na serwerze, redukując potrzebę dla wątków. Jeśli aplikacja korzysta z dedykowanego wątku na odpowiedzi i tysiące żądań, które są aktualnie obsługiwane jednocześnie, prościej i skuteczniej niż wątki są wymagane. Operacje asynchroniczne często trzeba użyć wątku podczas oczekiwania. Oni korzystać z istniejącego wątku zakończenia operacji We/Wy krótko po zakończeniu.  
  
- Opóźnienie operacji dostępu do pliku może być bardzo niska, w ramach bieżących warunków, ale opóźnienie może znacznie zwiększyć w przyszłości. Na przykład pliku mogą być przenoszone do serwera, który jest na całym świecie.  
  
- Dodano obciążenie związane z użyciem funkcji asynchronicznej jest mała.  
  
- Łatwo można uruchomić zadania asynchroniczne równolegle.  
  
## <a name="running-the-examples"></a>Uruchamianie przykładów  
 Aby uruchomić przykłady w tym temacie, można utworzyć **aplikacji WPF** lub **aplikacja interfejsu Windows Forms** , a następnie dodaj **przycisk**. W przycisku `Click` zdarzeń, dodaj wywołanie do pierwszej metody w każdym przykładzie.  
  
 W poniższych przykładach, m.in `Imports` instrukcji.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>Użycie klasy FileStream  
 Przykłady w tym temacie <xref:System.IO.FileStream> klasy, która jest dostępna opcja, który powoduje, że asynchroniczne operacje We/Wy na poziomie systemu operacyjnego. Za pomocą tej opcji, możesz uniknąć blokowania puli wątków w wielu przypadkach. Aby włączyć tę opcję, należy określić `useAsync=true` lub `options=FileOptions.Asynchronous` argument w wywołaniu konstruktora.  
  
 Nie można użyć tej opcji z <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> Jeśli możesz otworzyć bezpośrednio, określając ścieżkę do pliku. Jednak można użyć tej opcji, jeśli zostaną podane <xref:System.IO.Stream> , <xref:System.IO.FileStream> klasy otwarty. Należy zauważyć, że wywołania asynchroniczne szybsza w interfejsie użytkownika aplikacji, nawet jeśli puli wątków jest zablokowany, ponieważ wątek interfejsu użytkownika nie jest blokowane podczas oczekiwania.  
  
## <a name="writing-text"></a>Pisanie tekstu  
 Poniższy przykład zapisuje tekst do pliku. W każdej await instrukcji, metoda natychmiast kończy pracę. Po zakończeniu operacji We/Wy pliku metody wznawia działanie w instrukcji, która następuje po instrukcji czekania. Należy zauważyć, że w definicji metody, które używają instrukcji czekania modyfikatora async.  
  
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
  
 Przykład oryginalnego zawiera instrukcję `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, który jest zmniejszenie dwie poniższe instrukcje:  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 Pierwsza instrukcja zwraca klasę task i powoduje, że przetwarzanie pliku rozpocząć. Druga instrukcja z await powoduje, że metody od razu zakończyć proces i zwraca inne zadanie. Po zakończeniu przetwarzania w dalszej części plików, wykonywanie powraca do instrukcji następującej await. Aby uzyskać więcej informacji, zobacz [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Odczytywanie tekstu  
 Poniższy przykład odczytuje tekst z pliku. Tekst buforowane i umieszczane w tym przypadku <xref:System.Text.StringBuilder>. Inaczej niż w poprzednim przykładzie oceny await generuje wartość. <xref:System.IO.Stream.ReadAsync%2A> Metoda zwraca <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, więc tworzy oceny await `Int32` wartość (`numRead`) po zakończeniu operacji. Aby uzyskać więcej informacji, zobacz [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Równoległe asynchronicznego We/Wy  
 W poniższym przykładzie pokazano przetwarzania równoległego, pisząc 10 plików tekstowych. Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> metoda zwraca klasę task, która następnie zostanie dodany do listy zadań. `Await Task.WhenAll(tasks)` Instrukcji opuszcza metody i wznawia wewnątrz metody, gdy przetwarzanie plików jest pełny dla wszystkich zadań.  
  
 Kod z przykładu zamyka wszystkie <xref:System.IO.FileStream> wystąpienia w `Finally` blokować po zakończeniu zadania. Jeśli każda `FileStream` zamiast tego została utworzona w `Imports` instrukcji `FileStream` może zostać usunięte przed ukończeniem zadania.  
  
 Należy pamiętać, że wszelkie zwiększeniu wydajności prawie całkowicie z przetwarzanie równoległe i przetwarzania asynchronicznego. Zalety asynchroniczności to, czy nie blokując wiele wątków i że nie blokowały wątek interfejsu użytkownika.  
  
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
  
 Korzystając z <xref:System.IO.Stream.WriteAsync%2A> i <xref:System.IO.Stream.ReadAsync%2A> metody, można określić <xref:System.Threading.CancellationToken>, którego anulowanie strumienia środku operacji. Aby uzyskać więcej informacji, zobacz [aplikacji asynchronicznej Fine-Tuning (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) i [anulowanie w zarządzanych wątkach](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Przepływ sterowania w programach Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
