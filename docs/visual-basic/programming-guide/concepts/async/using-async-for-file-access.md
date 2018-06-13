---
title: Użycie Async do uzyskiwania dostępu do plików (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: e12eaa57d0f7186e9d281b89ec3abd26280e12ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644228"
---
# <a name="using-async-for-file-access-visual-basic"></a>Użycie Async do uzyskiwania dostępu do plików (Visual Basic)
Funkcja Async dostęp do plików. Korzystając z funkcji asynchronicznych, należy wywołać do metod asynchronicznych bez przy użyciu wywołania zwrotne i dzielenia kodu wielu metod lub wyrażenia lambda. Aby wprowadzić kod synchroniczne asynchroniczne, możesz tylko wywołania metody asynchronicznej zamiast metoda synchroniczna i dodać kilka słów kluczowych w kodzie.  
  
 Należy rozważyć następujące przyczyny dodawania asynchrony do wywołania dostępu do pliku:  
  
-   Asynchrony sprawia, że aplikacje interfejsu użytkownika usprawnia ponieważ wątku interfejsu użytkownika, który uruchamia operację można wykonywać inne zadania. Jeśli kod musi być wykonywany w wątku interfejsu użytkownika który zajmuje dużo czasu (na przykład więcej niż 50 w milisekundach), interfejsu użytkownika może zawieszać się dopiero po zakończeniu operacji We/Wy i wątku interfejsu użytkownika można ponownie przetworzyć klawiatury i myszy zdarzenia wejściowe i inne.  
  
-   Asynchrony poprawia skalowalność programu ASP.NET i innych aplikacji serwerowych, zmniejszając potrzebę wątków. Jeśli aplikacja używa dedykowanego wątku na odpowiedzi i żądania tysięcy są obsługiwane jednocześnie, potrzebne są tysiące wątków. Operacje asynchroniczne często nie trzeba używać wątku podczas oczekiwania. Istniejące wątku zakończenia We/Wy będzie używać krótko po zakończeniu.  
  
-   Opóźnienie operacji dostępu do pliku może być bardzo niskich warunkach bieżący, ale opóźnienie może znacznie zwiększyć w przyszłości. Na przykład plik może przenieść do serwera, który jest na całym świecie.  
  
-   Dodany korzystać z funkcji asynchronicznych jest mała.  
  
-   Zadania asynchronicznego łatwo mogą być uruchamiane równolegle.  
  
## <a name="running-the-examples"></a>Uruchamianie przykładów  
 Aby uruchomić przykłady w tym temacie, można utworzyć **aplikacji WPF** lub **aplikacji Windows Forms** , a następnie dodaj **przycisk**. Przycisk `Click` zdarzeń, dodaj wywołanie do metody pierwszy w każdym przykładzie.  
  
 W poniższych przykładach są następujące `Imports` instrukcje.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>Użyj klasy FileStream  
 Przykłady w tym temacie <xref:System.IO.FileStream> klasy, która jest dostępna opcja, która powoduje występowanie asynchroniczne We/Wy na poziomie systemu operacyjnego. Przy użyciu tej opcji, można uniknąć, blokuje puli wątków w wielu przypadkach. Aby włączyć tę opcję, należy określić `useAsync=true` lub `options=FileOptions.Asynchronous` argument w wywołaniu konstruktora.  
  
 Nie można użyć tej opcji z <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> otwarcia bezpośrednio, określając ścieżkę pliku. Jednak można użyć tej opcji, jeśli zostaną podane <xref:System.IO.Stream> który <xref:System.IO.FileStream> klasy otwarty. Należy zauważyć, że wywołania asynchroniczne szybsze w aplikacjach interfejsu użytkownika, nawet jeśli puli wątków jest zablokowana, ponieważ wątku interfejsu użytkownika nie jest blokowane podczas oczekiwania.  
  
## <a name="writing-text"></a>Pisanie tekstu  
 Poniższy przykład zapisuje tekst w pliku. W każdej await instrukcji, metoda natychmiast kończy pracę. Po zakończeniu operacji We/Wy pliku metody wznawia działanie w instrukcji, która wykonuje instrukcję await. Należy zauważyć, że w definicji metody, które używają instrukcja await modyfikatora async.  
  
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
  
 Przykład oryginalnego ma instrukcji `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, która jest zmniejszenie następujące dwie instrukcje:  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 Pierwsza instrukcja zwraca klasę task i powoduje, że przetwarzanie pliku rozpocząć. Drugi instrukcji z await powoduje, że metoda natychmiast wyjść i wrócić inne zadanie. Po zakończeniu przetwarzania później plików, wykonanie zwraca do instrukcji następującej await. Aby uzyskać więcej informacji, zobacz [przepływ sterowania w aplikacjach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Odczytywanie tekstu  
 Poniższy przykład odczytuje tekst z pliku. Tekst buforowane i umieszczane w takim przypadku <xref:System.Text.StringBuilder>. Inaczej niż w poprzednim przykładzie oceny await tworzy wartość. <xref:System.IO.Stream.ReadAsync%2A> Metoda zwraca <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, więc tworzy oceny await `Int32` wartość (`numRead`) po zakończeniu operacji. Aby uzyskać więcej informacji, zobacz [Async zwracać typów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Równoległe asynchroniczne We/Wy  
 W poniższym przykładzie pokazano przetwarzanie równoległe pisząc 10 plików tekstowych. Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> metoda zwraca klasę task, która jest następnie dodawana do listy zadań. `Await Task.WhenAll(tasks)` Instrukcji opuszcza metody i wznawia w metodzie podczas przetwarzania pliku jest zakończenie wszystkich zadań.  
  
 Przykład zamyka wszystkie <xref:System.IO.FileStream> wystąpień w `Finally` zablokować po zakończeniu zadania. Jeśli każda `FileStream` zamiast tego została utworzona w `Imports` instrukcji, `FileStream` może być usunięte przed ukończeniem zadania.  
  
 Należy pamiętać, że wszystkie wzrost wydajności prawie całkowicie z przetwarzanie równoległe i przetwarzania asynchronicznego. Zaletą asynchrony jest, aby nie zajmować wiele wątków i że nie blokowały wątek interfejsu użytkownika.  
  
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
  
 Korzystając z <xref:System.IO.Stream.WriteAsync%2A> i <xref:System.IO.Stream.ReadAsync%2A> metod, można określić <xref:System.Threading.CancellationToken>, którego można użyć, aby anulować operację strumienia pośredniej. Aby uzyskać więcej informacji, zobacz [Fine-Tuning Twoja aplikacja Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) i [anulowanie w zarządzanych wątkach](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [Przepływ sterowania w aplikacjach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
