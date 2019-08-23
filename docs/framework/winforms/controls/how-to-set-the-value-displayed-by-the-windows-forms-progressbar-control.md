---
title: 'Instrukcje: ustawianie wartości wyświetlanej przez kontrolkę ProgressBar formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 2e0134206ba3ebdce35f5374cbad575e34483d58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956084"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Instrukcje: ustawianie wartości wyświetlanej przez kontrolkę ProgressBar formularzy systemu Windows
> [!IMPORTANT]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.ProgressBar> do <xref:System.Windows.Forms.ProgressBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStripProgressBar>  
  
 .NET Framework oferuje kilka różnych sposobów wyświetlania danej wartości w <xref:System.Windows.Forms.ProgressBar> formancie. Wybrana metoda będzie zależeć od zadania w ręku lub podczas rozwiązywania problemu. W poniższej tabeli przedstawiono podejścia, które można wybrać.  
  
|Podejście|Opis|  
|--------------|-----------------|  
|Ustaw wartość <xref:System.Windows.Forms.ProgressBar> formantu bezpośrednio.|Takie podejście jest przydatne w przypadku zadań, w których wiadomo, ile elementów jest mierzonych, takich jak odczytywanie rekordów ze źródła danych. Ponadto, jeśli trzeba ustawić wartość tylko raz lub dwa razy, jest to prosty sposób. Na koniec Użyj tego procesu, jeśli chcesz zmniejszyć wartość wyświetlaną na pasku postępu.|  
|Zwiększ poziom <xref:System.Windows.Forms.ProgressBar> wyświetlania o ustalonej wartości.|Takie podejście jest przydatne, gdy wyświetlasz prostą liczbę z przedziału od minimum do maksimum, na przykład czas, który upłynął, lub liczbę plików, które zostały przetworzone z znanego podsumowania.|  
|<xref:System.Windows.Forms.ProgressBar> Zwiększenie wyświetlania przez wartość, która różni się.|Takie podejście jest przydatne, gdy trzeba zmienić wyświetlaną wartość na liczbę razy w różnych kwotach. Przykład pokazuje ilość miejsca na dysku twardym zużywanego podczas zapisywania serii plików na dysku.|  
  
 Najbardziej bezpośrednim sposobem ustawienia wartości wyświetlanej przez pasek postępu jest ustawienie <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości. Można to zrobić w czasie projektowania lub w czasie wykonywania.  
  
### <a name="to-set-the-progressbar-value-directly"></a>Aby ustawić wartość ProgressBar bezpośrednio  
  
1. <xref:System.Windows.Forms.ProgressBar> Ustaw kontrolkę<xref:System.Windows.Forms.ProgressBar.Maximum%2A>iwartości. <xref:System.Windows.Forms.ProgressBar.Minimum%2A>  
  
2. W kodzie, należy ustawić <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość kontrolki na wartość całkowitą z zakresu od ustalonej wartości minimalnej i maksymalnej.  
  
    > [!NOTE]
    > Jeśli <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość zostanie ustawiona poza granicami ustanowionymi <xref:System.Windows.Forms.ProgressBar.Minimum%2A> przez właściwości i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> , formant zgłosi <xref:System.ArgumentException> wyjątek.  
  
     Poniższy przykład kodu ilustruje sposób bezpośredniego ustawiania <xref:System.Windows.Forms.ProgressBar> wartości. Kod odczytuje rekordy ze źródła danych i aktualizuje pasek postępu oraz etykietę za każdym razem, gdy rekord danych zostanie odczytany. Ten przykład wymaga, aby formularz miał <xref:System.Windows.Forms.Label> kontrolkę <xref:System.Windows.Forms.ProgressBar> , kontrolkę i tabelę danych z wierszem o nazwie `CustomerRow` z `FirstName` i `LastName` polami.  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     Jeśli jest wyświetlany postęp, który przechodzi przez stały interwał, można ustawić wartość, a następnie wywołać metodę, która zwiększa <xref:System.Windows.Forms.ProgressBar> wartość kontrolki według tego interwału. Jest to przydatne w przypadku czasomierzy i innych scenariuszy, w których postępy nie są mierzone jako procent całości.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Aby zwiększyć pasek postępu o ustalonej wartości  
  
1. <xref:System.Windows.Forms.ProgressBar> Ustaw kontrolkę<xref:System.Windows.Forms.ProgressBar.Maximum%2A>iwartości. <xref:System.Windows.Forms.ProgressBar.Minimum%2A>  
  
2. Ustaw <xref:System.Windows.Forms.ProgressBar.Step%2A> właściwość kontrolki na liczbę całkowitą reprezentującą kwotę, aby zwiększyć wartość wyświetlaną na pasku postępu.  
  
3. Wywołaj <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metodę, aby zmienić wartość wyświetlaną przez kwotę ustawioną <xref:System.Windows.Forms.ProgressBar.Step%2A> we właściwości.  
  
     Poniższy przykład kodu ilustruje, jak pasek postępu może zachować liczbę plików w operacji kopiowania.  
  
     W poniższym przykładzie, ponieważ każdy plik jest odczytywany do pamięci, pasek postępu i etykieta są aktualizowane w celu odzwierciedlenia łącznej liczby odczytywanych plików. Ten przykład wymaga, aby formularz miał <xref:System.Windows.Forms.Label> formant <xref:System.Windows.Forms.ProgressBar> i formant.  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     Na koniec można zwiększyć wartość wyświetlaną przez pasek postępu, aby każdy wzrost był unikatowy. Jest to przydatne, gdy śledzisz szereg unikatowych operacji, takich jak zapisywanie plików o różnych rozmiarach na dysku twardym, lub pomiar postępu jako procent całości.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Aby zwiększyć pasek postępu przez wartość dynamiczną  
  
1. <xref:System.Windows.Forms.ProgressBar> Ustaw kontrolkę<xref:System.Windows.Forms.ProgressBar.Maximum%2A>iwartości. <xref:System.Windows.Forms.ProgressBar.Minimum%2A>  
  
2. Wywołaj <xref:System.Windows.Forms.ProgressBar.Increment%2A> metodę, aby zmienić wartość wyświetlaną przez określoną liczbę całkowitą.  
  
     Poniższy przykład kodu ilustruje, jak pasek postępu może obliczyć ilość miejsca na dysku, która została użyta podczas operacji kopiowania.  
  
     W poniższym przykładzie, ponieważ każdy plik jest zapisywana na dysku twardym, pasek postępu i etykieta są aktualizowane w celu odzwierciedlenia ilości dostępnego miejsca na dysku twardym. Ten przykład wymaga, aby formularz miał <xref:System.Windows.Forms.Label> formant <xref:System.Windows.Forms.ProgressBar> i formant.  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number   
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number   
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example   
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of   
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_   
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number   
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and   
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number   
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example   
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of   
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [ProgressBar, kontrolka — omówienie](progressbar-control-overview-windows-forms.md)
- [ProgressBar, kontrolka](progressbar-control-windows-forms.md)
