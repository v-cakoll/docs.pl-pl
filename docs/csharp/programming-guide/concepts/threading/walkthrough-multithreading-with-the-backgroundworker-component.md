---
title: "Wskazówki: Wielowątkowość ze składnikiem BackgroundWorker (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 72d6e9ab42ca270ebe0691be23ebe181b973620d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a>Wskazówki: Wielowątkowość ze składnikiem BackgroundWorker (C#)
Ten przewodnik przedstawia sposób tworzenia aplikacji wielowątkowych formularzy systemu Windows, która wyszukuje plik tekstowy dla wystąpień słowa. Przedstawia on:  
  
-   Definiowanie klas z metody, która może być wywoływany przez <xref:System.ComponentModel.BackgroundWorker> składnika.  
  
-   Obsługa zdarzeń zgłaszanych przez <xref:System.ComponentModel.BackgroundWorker> składnika.  
  
-   Uruchamianie <xref:System.ComponentModel.BackgroundWorker> składnik do uruchomienia metody.  
  
-   Implementowanie `Cancel` przycisku, który zatrzymuje <xref:System.ComponentModel.BackgroundWorker> składnika.  
  
### <a name="to-create-the-user-interface"></a>Aby utworzyć interfejs użytkownika  
  
1.  Otwórz nowy projekt aplikacji formularzy systemu Windows C# i utworzenie formularza o nazwie `Form1`.  
  
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
  
2.  Ustaw następujące właściwości dla obiektu backgroundWorker1.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|Wartość true|  
    |`WorkerSupportsCancellation`|Wartość true|  
  
3.  Subskrybowanie zdarzeń obiektu backgroundWorker1. W górnej części **właściwości** okna, kliknij przycisk **zdarzenia** ikony. Kliknij dwukrotnie `RunWorkerCompleted` zdarzeń, aby utworzyć metoda obsługi zdarzeń. Tym samym `ProgressChanged` i `DoWork` zdarzenia.  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>Aby zdefiniować metody, które zostanie uruchomione w oddzielnym wątku  
  
1.  Z **projektu** menu, wybierz **Dodaj klasę** Aby dodać klasę do projektu. **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz **klasy** z okna Szablony, a następnie wprowadź `Words.cs` w polu Nazwa.  
  
3.  Kliknij przycisk **Dodaj**. `Words` Wyświetlana klasy.  
  
4.  Dodaj następujący kod do `Words` klasy:  
  
    ```csharp  
    public class Words  
    {  
        // Object to store the current state, for passing to the caller.  
        public class CurrentState  
        {  
            public int LinesCounted;  
            public int WordsMatched;  
        }  
  
        public string SourceFile;  
        public string CompareString;  
        private int WordCount;  
        private int LinesCounted;  
  
        public void CountWords(  
            System.ComponentModel.BackgroundWorker worker,  
            System.ComponentModel.DoWorkEventArgs e)  
        {  
            // Initialize the variables.  
            CurrentState state = new CurrentState();  
            string line = "";  
            int elapsedTime = 20;  
            DateTime lastReportDateTime = DateTime.Now;  
  
            if (CompareString == null ||  
                CompareString == System.String.Empty)  
            {  
                throw new Exception("CompareString not specified.");  
            }  
  
            // Open a new stream.  
            using (System.IO.StreamReader myStream = new System.IO.StreamReader(SourceFile))  
            {  
                // Process lines while there are lines remaining in the file.  
                while (!myStream.EndOfStream)  
                {  
                    if (worker.CancellationPending)  
                    {  
                        e.Cancel = true;  
                        break;  
                    }  
                    else  
                    {  
                        line = myStream.ReadLine();  
                        WordCount += CountInString(line, CompareString);  
                        LinesCounted += 1;  
  
                        // Raise an event so the form can monitor progress.  
                        int compare = DateTime.Compare(  
                            DateTime.Now, lastReportDateTime.AddMilliseconds(elapsedTime));  
                        if (compare > 0)  
                        {  
                            state.LinesCounted = LinesCounted;  
                            state.WordsMatched = WordCount;  
                            worker.ReportProgress(0, state);  
                            lastReportDateTime = DateTime.Now;  
                        }  
                    }  
                    // Uncomment for testing.  
                    //System.Threading.Thread.Sleep(5);  
                }  
  
                // Report the final count values.  
                state.LinesCounted = LinesCounted;  
                state.WordsMatched = WordCount;  
                worker.ReportProgress(0, state);  
            }  
        }  
  
        private int CountInString(  
            string SourceString,  
            string CompareString)  
        {  
            // This function counts the number of times  
            // a word is found in a line.  
            if (SourceString == null)  
            {  
                return 0;  
            }  
  
            string EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString);  
  
            System.Text.RegularExpressions.Regex regex;  
            regex = new System.Text.RegularExpressions.Regex(   
                // To count all occurrences of the string, even within words, remove  
                // both instances of @"\b" from the following line.  
                @"\b" + EscapedCompareString + @"\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase);  
  
            System.Text.RegularExpressions.MatchCollection matches;  
            matches = regex.Matches(SourceString);  
            return matches.Count;  
        }  
  
    }  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a>Do obsługi zdarzeń z wątku  
  
-   Dodaj następujące programy obsługi zdarzeń do głównego formularza:  
  
    ```csharp  
    private void backgroundWorker1_RunWorkerCompleted(object sender, RunWorkerCompletedEventArgs e)  
    {  
    // This event handler is called when the background thread finishes.  
    // This method runs on the main thread.  
    if (e.Error != null)  
        MessageBox.Show("Error: " + e.Error.Message);  
    else if (e.Cancelled)  
        MessageBox.Show("Word counting canceled.");  
    else  
        MessageBox.Show("Finished counting words.");  
    }  
  
    private void backgroundWorker1_ProgressChanged(object sender, ProgressChangedEventArgs e)  
    {  
        // This method runs on the main thread.  
        Words.CurrentState state =  
            (Words.CurrentState)e.UserState;  
        this.LinesCounted.Text = state.LinesCounted.ToString();  
        this.WordsCounted.Text = state.WordsMatched.ToString();  
    }  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>Aby uruchomić i wywołać nowego wątku, który uruchamia metody WordCount  
  
1.  Dodaj poniższe procedury służą do programu:  
  
    ```csharp  
    private void backgroundWorker1_DoWork(object sender, DoWorkEventArgs e)  
    {  
        // This event handler is where the actual work is done.  
        // This method runs on the background thread.  
  
        // Get the BackgroundWorker object that raised this event.  
        System.ComponentModel.BackgroundWorker worker;  
        worker = (System.ComponentModel.BackgroundWorker)sender;  
  
        // Get the Words object and call the main method.  
        Words WC = (Words)e.Argument;  
        WC.CountWords(worker, e);  
    }  
  
    private void StartThread()  
    {  
        // This method runs on the main thread.  
        this.WordsCounted.Text = "0";  
  
        // Initialize the object that the background worker calls.  
        Words WC = new Words();  
        WC.CompareString = this.CompareString.Text;  
        WC.SourceFile = this.SourceFile.Text;  
  
        // Start the asynchronous operation.  
        backgroundWorker1.RunWorkerAsync(WC);  
    }  
    ```  
  
2.  Wywołanie `StartThread` metody z `Start` przycisk w formularzu:  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>Aby zaimplementować przycisk Anuluj, która kończy się wątek  
  
    -   Wywołanie `StopThread` procedury z `Click` programu obsługi zdarzeń dla `Cancel` przycisku.  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
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
 [Wątkowość (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [Porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
