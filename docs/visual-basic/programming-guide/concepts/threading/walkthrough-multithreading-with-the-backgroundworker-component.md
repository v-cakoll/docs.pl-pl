---
title: Wielowątkowość ze składnikiem BackgroundWorker (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
ms.openlocfilehash: 07700aa526866729f1ba1a8d846f22ce333c356d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654294"
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a>Wskazówki: Wielowątkowość ze składnikiem BackgroundWorker (Visual Basic)
Ten przewodnik przedstawia sposób tworzenia aplikacji wielowątkowych formularzy systemu Windows, która wyszukuje plik tekstowy dla wystąpień słowa. Przedstawia on:  
  
-   Definiowanie klas z metody, która może być wywoływany przez <xref:System.ComponentModel.BackgroundWorker> składnika.  
  
-   Obsługa zdarzeń zgłaszanych przez <xref:System.ComponentModel.BackgroundWorker> składnika.  
  
-   Uruchamianie <xref:System.ComponentModel.BackgroundWorker> składnik do uruchomienia metody.  
  
-   Implementowanie `Cancel` przycisku, który zatrzymuje <xref:System.ComponentModel.BackgroundWorker> składnika.  
  
### <a name="to-create-the-user-interface"></a>Aby utworzyć interfejs użytkownika  
  
1.  Otwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic i tworzenia formularza o nazwie `Form1`.  
  
2.  Dodawanie dwóch przycisków i cztery pola tekstowe do `Form1`.  
  
3.  Nazwy obiektów, jak pokazano w poniższej tabeli.  
  
    |Obiekt|Właściwość|Ustawienie|  
    |------------|--------------|-------------|  
    |Pierwszy przycisk|`Name`, `Text`|Start, uruchamia|  
    |Drugi przycisk|`Name`, `Text`|Anuluj, Anuluj|  
    |Pierwsze pole tekstowe|`Name`, `Text`|SourceFile, ""|  
    |Drugie pole tekstowe|`Name`, `Text`|CompareString, ""|  
    |Trzecie pole tekstowe|`Name`, `Text`|WordsCounted "0"|  
    |Czwarte pole tekstowe|`Name`, `Text`|LinesCounted "0"|  
  
4.  Dodaj etykietę obok każdego pola tekstowego. Ustaw `Text` właściwości dla każdej etykiety, jak pokazano w poniższej tabeli.  
  
    |Obiekt|Właściwość|Ustawienie|  
    |------------|--------------|-------------|  
    |Pierwsza etykieta|`Text`|Plik źródłowy|  
    |Drugi etykiety|`Text`|Porównanie ciągów|  
    |Trzeci etykiety|`Text`|Dopasowanie słów|  
    |Czwarty etykiety|`Text`|Wiersze zliczane|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>Aby utworzyć składnika BackgroundWorker i subskrybowanie zdarzeń jego  
  
1.  Dodaj <xref:System.ComponentModel.BackgroundWorker> składnika z **składniki** sekcji **przybornika** do formularza. Pojawi się w części formularza na pasku zadań.  
  
2.  Ustaw następujące właściwości dla obiektu BackgroundWorker1.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|True|  
    |`WorkerSupportsCancellation`|True|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>Aby zdefiniować metody, które zostanie uruchomione w oddzielnym wątku  
  
1.  Z **projektu** menu, wybierz **Dodaj klasę** Aby dodać klasę do projektu. **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz **klasy** z okna Szablony, a następnie wprowadź `Words.vb` w polu Nazwa.  
  
3.  Kliknij przycisk **Dodaj**. `Words` Wyświetlana klasy.  
  
4.  Dodaj następujący kod do `Words` klasy:  
  
    ```vb  
    Public Class Words  
        ' Object to store the current state, for passing to the caller.  
        Public Class CurrentState  
            Public LinesCounted As Integer  
            Public WordsMatched As Integer  
        End Class  
  
        Public SourceFile As String  
        Public CompareString As String  
        Private WordCount As Integer = 0  
        Private LinesCounted As Integer = 0  
  
        Public Sub CountWords(  
            ByVal worker As System.ComponentModel.BackgroundWorker,  
            ByVal e As System.ComponentModel.DoWorkEventArgs  
        )  
            ' Initialize the variables.  
            Dim state As New CurrentState  
            Dim line = ""  
            Dim elapsedTime = 20  
            Dim lastReportDateTime = Now  
  
            If CompareString Is Nothing OrElse  
               CompareString = System.String.Empty Then  
  
               Throw New Exception("CompareString not specified.")  
            End If  
  
            Using myStream As New System.IO.StreamReader(SourceFile)  
  
                ' Process lines while there are lines remaining in the file.  
                Do While Not myStream.EndOfStream  
                    If worker.CancellationPending Then  
                        e.Cancel = True  
                        Exit Do  
                    Else  
                        line = myStream.ReadLine  
                        WordCount += CountInString(line, CompareString)  
                        LinesCounted += 1  
  
                        ' Raise an event so the form can monitor progress.  
                        If Now > lastReportDateTime.AddMilliseconds(elapsedTime) Then  
                            state.LinesCounted = LinesCounted  
                            state.WordsMatched = WordCount  
                            worker.ReportProgress(0, state)  
                            lastReportDateTime = Now  
                        End If  
  
                        ' Uncomment for testing.  
                        'System.Threading.Thread.Sleep(5)  
                    End If  
                Loop  
  
                ' Report the final count values.  
                state.LinesCounted = LinesCounted  
                state.WordsMatched = WordCount  
                worker.ReportProgress(0, state)  
            End Using  
        End Sub  
  
        Private Function CountInString(  
            ByVal SourceString As String,  
            ByVal CompareString As String  
        ) As Integer  
            ' This function counts the number of times  
            ' a word is found in a line.  
            If SourceString Is Nothing Then  
                Return 0  
            End If  
  
            Dim EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString)  
  
            ' To count all occurrences of the string, even within words, remove  
            ' both instances of "\b".  
            Dim regex As New System.Text.RegularExpressions.Regex(  
                "\b" + EscapedCompareString + "\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase)  
  
            Dim matches As System.Text.RegularExpressions.MatchCollection  
            matches = regex.Matches(SourceString)  
            Return matches.Count  
        End Function  
    End Class  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a>Do obsługi zdarzeń z wątku  
  
-   Dodaj następujące programy obsługi zdarzeń do głównego formularza:  
  
    ```vb  
    Private Sub BackgroundWorker1_RunWorkerCompleted(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
      ) Handles BackgroundWorker1.RunWorkerCompleted  
  
        ' This event handler is called when the background thread finishes.  
        ' This method runs on the main thread.  
        If e.Error IsNot Nothing Then  
            MessageBox.Show("Error: " & e.Error.Message)  
        ElseIf e.Cancelled Then  
            MessageBox.Show("Word counting canceled.")  
        Else  
            MessageBox.Show("Finished counting words.")  
        End If  
    End Sub  
  
    Private Sub BackgroundWorker1_ProgressChanged(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.ProgressChangedEventArgs  
      ) Handles BackgroundWorker1.ProgressChanged  
  
        ' This method runs on the main thread.  
        Dim state As Words.CurrentState =   
            CType(e.UserState, Words.CurrentState)  
        Me.LinesCounted.Text = state.LinesCounted.ToString  
        Me.WordsCounted.Text = state.WordsMatched.ToString  
    End Sub  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>Aby uruchomić i wywołać nowego wątku, który uruchamia metody WordCount  
  
1.  Dodaj poniższe procedury służą do programu:  
  
    ```vb  
    Private Sub BackgroundWorker1_DoWork(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.DoWorkEventArgs  
      ) Handles BackgroundWorker1.DoWork  
  
        ' This event handler is where the actual work is done.  
        ' This method runs on the background thread.  
  
        ' Get the BackgroundWorker object that raised this event.  
        Dim worker As System.ComponentModel.BackgroundWorker  
        worker = CType(sender, System.ComponentModel.BackgroundWorker)  
  
        ' Get the Words object and call the main method.  
        Dim WC As Words = CType(e.Argument, Words)  
        WC.CountWords(worker, e)  
    End Sub  
  
    Sub StartThread()  
        ' This method runs on the main thread.  
        Me.WordsCounted.Text = "0"  
  
        ' Initialize the object that the background worker calls.  
        Dim WC As New Words  
        WC.CompareString = Me.CompareString.Text  
        WC.SourceFile = Me.SourceFile.Text  
  
        ' Start the asynchronous operation.  
        BackgroundWorker1.RunWorkerAsync(WC)  
    End Sub  
    ```  
  
2.  Wywołanie `StartThread` metody z `Start` przycisk w formularzu:  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>Aby zaimplementować przycisk Anuluj, która kończy się wątek  
  
-   Wywołanie `StopThread` procedury z `Click` programu obsługi zdarzeń dla `Cancel` przycisku.  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a>Testowanie  
 Teraz możesz przetestować aplikację, aby upewnić się, że działa on prawidłowo.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Naciśnij klawisz F5, aby uruchomić aplikację.  
  
2.  Gdy formularz jest wyświetlany, podaj ścieżkę do pliku dla pliku, który chcesz przetestować w `sourceFile` pole. Na przykład przy założeniu, że plik testu nosi nazwę Test.txt, wprowadź C:\Test.txt.  
  
3.  W drugim polu tekstowym wprowadź słowo lub frazę dla aplikacji, aby wyszukać w pliku tekstowym.  
  
4.  Kliknij przycisk `Start` przycisku. `LinesCounted` Przycisk powinien rozpocząć zwiększanie natychmiast. Aplikacja wyświetla komunikat "Zakończono zliczania" po jej zakończeniu.  
  
#### <a name="to-test-the-cancel-button"></a>Aby przetestować przycisku Anuluj  
  
1.  Naciśnij klawisz F5, aby uruchomić aplikację, a następnie wprowadź plik nazwę i wyszukaj słowo zgodnie z opisem w poprzedniej procedurze. Upewnij się, że wybrany plik jest wystarczająco duże, aby upewnić się, że będzie czasu, aby anulować procedury przed zakończeniem.  
  
2.  Kliknij przycisk `Start` przycisk, aby uruchomić aplikację.  
  
3.  Kliknij przycisk `Cancel` przycisku. Aplikacja ma zostać zatrzymana, licząc od razu.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zawiera niektóre obsługi podstawowych błędów. Ta funkcja wykrywa ciągów wyszukiwania puste. Możesz wprowadzić ten program bardziej niezawodne dzięki obsłudze inne błędy, takich jak przekroczenie maksymalnej liczby słów lub wierszy, które mogą być traktowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Wątkowość (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [Wskazówki: Tworzenie prostego składnika wielowątkowości za pomocą Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)  
 [Instrukcje: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
