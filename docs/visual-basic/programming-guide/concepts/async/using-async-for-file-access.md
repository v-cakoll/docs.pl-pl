---
title: Użycie Async do uzyskiwania dostępu do plików
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: 2ee1efa69f4b13224be65fe802ebf5f834c941aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400774"
---
# <a name="using-async-for-file-access-visual-basic"></a>Używanie Async na potrzeby dostępu do plików (Visual Basic)
Do uzyskiwania dostępu do plików można użyć funkcji asynchronicznej. Za pomocą funkcji asynchronicznej można wywołać metody asynchroniczne bez używania wywołań zwrotnych lub dzieląc kod w wielu metodach lub wyrażeniach lambda. Aby przeprowadzić synchroniczne asynchroniczne kod, wystarczy wywołać metodę asynchroniczną zamiast metody synchronicznej i dodać kilka słów kluczowych do kodu.  
  
 Aby dodać asynchroniczności do wywołań dostępu do plików, należy wziąć pod uwagę następujące przyczyny:  
  
- Asynchroniczności sprawia, że aplikacje interfejsu użytkownika działają szybciej, ponieważ wątek interfejsu użytkownika uruchamiający operację może wykonać inne czynności. Jeśli wątek interfejsu użytkownika musi wykonać kod, który zajmuje dużo czasu (na przykład więcej niż 50 milisekund), interfejs użytkownika może się zamrozić do momentu zakończenia operacji we/wy, a wątek interfejsu użytkownika może ponownie przetwarzać dane wejściowe klawiatury i myszy oraz inne zdarzenia.  
  
- Asynchroniczności poprawia skalowalność ASP.NET i innych aplikacji opartych na serwerze, zmniejszając potrzebę wątków. Jeśli aplikacja korzysta z dedykowanego wątku na odpowiedź i jednocześnie są obsługiwane tysiące żądań, są zbędne tysiące wątków. Operacje asynchroniczne często nie muszą używać wątku podczas oczekiwania. Z chwilą korzystają z istniejącego wątku zakończenia operacji we/wy.  
  
- Opóźnienie operacji dostępu do pliku może być bardzo niskie w bieżących warunkach, ale opóźnienie może znacznie wzrosnąć w przyszłości. Na przykład plik można przenieść na serwer, na którym znajduje się na całym świecie.  
  
- Dodatkowe obciążenie związane z korzystaniem z funkcji asynchronicznej jest małe.  
  
- Zadania asynchroniczne można łatwo uruchomić równolegle.  
  
## <a name="running-the-examples"></a>Uruchamianie przykładów  
 Aby uruchomić przykłady w tym temacie, można utworzyć **aplikację WPF** lub **aplikację Windows Forms** , a następnie dodać **przycisk**. W `Click` zdarzeniu przycisku Dodaj wywołanie do pierwszej metody w każdym przykładzie.  
  
 W poniższych przykładach Uwzględnij poniższe `Imports` instrukcje.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>Użycie klasy FileStream  
 Przykłady w tym temacie używają <xref:System.IO.FileStream> klasy, która powoduje wystąpienie asynchroniczne we/wy na poziomie systemu operacyjnego. Korzystając z tej opcji, można uniknąć zablokowania wątku puli wątków w wielu przypadkach. Aby włączyć tę opcję, należy określić `useAsync=true` argument or `options=FileOptions.Asynchronous` w wywołaniu konstruktora.  
  
 Nie można użyć tej opcji razem z <xref:System.IO.StreamReader> i, <xref:System.IO.StreamWriter> Jeśli otworzysz je bezpośrednio, określając ścieżkę pliku. Można jednak użyć tej opcji, jeśli podajesz im <xref:System.IO.Stream> , że została <xref:System.IO.FileStream> otwarta Klasa. Należy zauważyć, że wywołania asynchroniczne są szybsze w aplikacjach interfejsu użytkownika, nawet jeśli wątek puli wątków jest zablokowany, ponieważ wątek interfejsu użytkownika nie jest blokowany podczas oczekiwania.  
  
## <a name="writing-text"></a>Pisanie tekstu  
 Poniższy przykład zapisuje tekst do pliku. W każdej instrukcji Await Metoda natychmiast opuszcza. Po zakończeniu operacji we/wy pliku Metoda zostaje wznowiona przy użyciu instrukcji, która następuje po instrukcji Await. Należy zauważyć, że modyfikator Async jest w definicji metod, które używają instrukcji Await.  
  
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
  
 Oryginalny przykład zawiera instrukcję `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)` , która jest umową obejmującą następujące dwie instrukcje:  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 Pierwsza instrukcja zwraca zadanie i powoduje uruchomienie przetwarzania plików. Druga instrukcja z Await powoduje, że metoda natychmiast zakończy działanie i zwróci inne zadanie. Po późniejszym zakończeniu przetwarzania plików wykonanie powraca do instrukcji, która następuje po oczekiwania. Aby uzyskać więcej informacji, zobacz [sterowanie przepływem w programach asynchronicznych (Visual Basic)](control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Odczytywanie tekstu  
 Poniższy przykład odczytuje tekst z pliku. Tekst jest buforowany i, w tym przypadku, umieszczony w <xref:System.Text.StringBuilder> . W przeciwieństwie do poprzedniego przykładu, obliczanie oczekiwania powoduje utworzenie wartości. <xref:System.IO.Stream.ReadAsync%2A>Metoda zwraca <xref:System.Threading.Tasks.Task> \<<xref:System.Int32>>, więc Ocena await generuje `Int32` wartość ( `numRead` ) po zakończeniu operacji. Aby uzyskać więcej informacji, zobacz [asynchroniczne typy zwracane (Visual Basic)](async-return-types.md).  
  
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
  
## <a name="parallel-asynchronous-io"></a>Równoległe asynchroniczne operacje we/wy  
 Poniższy przykład ilustruje przetwarzanie równoległe, pisząc 10 plików tekstowych. Dla każdego pliku <xref:System.IO.Stream.WriteAsync%2A> Metoda zwraca zadanie, które jest następnie dodawane do listy zadań. `Await Task.WhenAll(tasks)`Instrukcja kończy metodę i wznawia działanie w ramach metody po zakończeniu przetwarzania plików dla wszystkich zadań.  
  
 Przykład zamyka wszystkie <xref:System.IO.FileStream> wystąpienia w `Finally` bloku po zakończeniu zadań. Jeśli każdy z `FileStream` nich został utworzony w `Imports` instrukcji, `FileStream` może zostać usunięty przed ukończeniem zadania.  
  
 Należy pamiętać, że zwiększenie wydajności jest niemal całkowicie wynikiem przetwarzania równoległego, a nie przetwarzania asynchronicznego. Zalety asynchroniczności są takie same, że nie wiążą się z wieloma wątkami i nie wiążą się z wątkiem interfejsu użytkownika.  
  
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
  
 W przypadku korzystania <xref:System.IO.Stream.WriteAsync%2A> z <xref:System.IO.Stream.ReadAsync%2A> metod i można określić <xref:System.Threading.CancellationToken> , której można użyć do anulowania strumienia średniej operacji. Aby uzyskać więcej informacji, zobacz [dostrajanie aplikacji asynchronicznej (Visual Basic)](fine-tuning-your-async-application.md) i [Anulowanie w zarządzanych wątkach](../../../../standard/threading/cancellation-in-managed-threads.md).  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne z Async i Await (Visual Basic)](index.md)
- [Asynchroniczne typy zwracane (Visual Basic)](async-return-types.md)
- [Przepływ sterowania w programach asynchronicznych (Visual Basic)](control-flow-in-async-programs.md)
