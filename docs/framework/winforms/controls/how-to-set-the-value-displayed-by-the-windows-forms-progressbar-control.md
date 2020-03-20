---
title: Ustawianie wartości wyświetlanej przez formant paska postępu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: d295079a96ca19a4e4c98e113a3f3051c6403182
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141814"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Porady: ustawianie wartości wyświetlanej przez formant ProgressBar formularzy systemu Windows
> [!IMPORTANT]
> Formant <xref:System.Windows.Forms.ToolStripProgressBar> zastępuje i dodaje funkcjonalność <xref:System.Windows.Forms.ProgressBar> do formantu; jednak <xref:System.Windows.Forms.ProgressBar> formant jest zachowywany zarówno dla zgodności z powrotem i przyszłego użycia, jeśli wybierzesz.  
  
 .NET Framework oferuje kilka różnych sposobów wyświetlania <xref:System.Windows.Forms.ProgressBar> danej wartości w formancie. To, które podejście wybierzesz, będzie zależało od wykonywanego zadania lub rozwiązania problemu. W poniższej tabeli przedstawiono podejścia, które można wybrać.  
  
|Podejście|Opis|  
|--------------|-----------------|  
|Ustaw wartość <xref:System.Windows.Forms.ProgressBar> formantu bezpośrednio.|Takie podejście jest przydatne w przypadku zadań, w których znasz sumę mierzonego elementu, który będzie zaangażowany, na przykład odczytywanie rekordów ze źródła danych. Ponadto jeśli wystarczy ustawić wartość raz lub dwa razy, jest to łatwy sposób, aby to zrobić. Na koniec użyj tego procesu, jeśli chcesz zmniejszyć wartość wyświetlaną przez pasek postępu.|  
|Zwiększ <xref:System.Windows.Forms.ProgressBar> wyświetlanie o stałą wartość.|Takie podejście jest przydatne podczas wyświetlania prostej liczby między minimalną i maksymalną, taką jak czas, który upłynął lub liczba plików, które zostały przetworzone ze znanej sumy.|  
|Zwiększ <xref:System.Windows.Forms.ProgressBar> wyświetlanie o wartość, która się zmienia.|Takie podejście jest przydatne, gdy trzeba zmienić wyświetlaną wartość kilka razy w różnych kwotach. Przykładem może być pokazanie ilości miejsca na dysku twardym zużywanego podczas zapisywania serii plików na dysku.|  
  
 Najbardziej bezpośrednim sposobem ustawienia wartości wyświetlanej przez pasek postępu <xref:System.Windows.Forms.ProgressBar.Value%2A> jest ustawienie właściwości. Można to zrobić w czasie projektowania lub w czasie wykonywania.  
  
### <a name="to-set-the-progressbar-value-directly"></a>Aby bezpośrednio ustawić wartość ProgressBar  
  
1. Ustaw <xref:System.Windows.Forms.ProgressBar> formant <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.  
  
2. W kodzie ustaw <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość formantu na wartość całkowitą między wartościami minimalnymi i maksymalnymi, które zostały ustalone.  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.ProgressBar.Value%2A> Jeśli ustawisz właściwość poza granicami <xref:System.Windows.Forms.ProgressBar.Minimum%2A> <xref:System.Windows.Forms.ProgressBar.Maximum%2A> ustanowionymi przez i właściwości, formant zgłasza wyjątek. <xref:System.ArgumentException>  
  
     Poniższy przykład kodu ilustruje <xref:System.Windows.Forms.ProgressBar> sposób bezpośredniego ustawiania wartości. Kod odczytuje rekordy ze źródła danych i aktualizuje pasek postępu i etykietę za każdym razem, gdy rekord danych jest odczytywany. W tym przykładzie wymaga, że formularz ma <xref:System.Windows.Forms.Label> formant, <xref:System.Windows.Forms.ProgressBar> formant i tabelę danych z wierszem wywoływanym `CustomerRow` z `FirstName` i `LastName` polami.  
  
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
  
     Jeśli są wyświetlane postępu, który przebiega przez stały interwał, można ustawić wartość, a następnie wywołać metodę, która zwiększa wartość <xref:System.Windows.Forms.ProgressBar> formantu przez ten interwał. Jest to przydatne w przypadku czasomierzy i innych scenariuszy, w których nie mierzysz postępu jako procentu całości.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Aby zwiększyć pasek postępu o stałą wartość  
  
1. Ustaw <xref:System.Windows.Forms.ProgressBar> formant <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.  
  
2. Ustaw <xref:System.Windows.Forms.ProgressBar.Step%2A> właściwość formantu na liczbę całkowitą reprezentującą kwotę, aby zwiększyć wyświetlaną wartość paska postępu.  
  
3. Wywołanie <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metody, aby zmienić wartość wyświetlaną <xref:System.Windows.Forms.ProgressBar.Step%2A> przez kwotę ustawioną we właściwości.  
  
     Poniższy przykład kodu ilustruje, jak pasek postępu może obsługiwać liczbę plików w operacji kopiowania.  
  
     W poniższym przykładzie, jak każdy plik jest odczytywany do pamięci, pasek postępu i etykieta są aktualizowane w celu odzwierciedlenia całkowitej liczby odczytanych plików. W tym przykładzie wymaga, aby formularz miał <xref:System.Windows.Forms.Label> formant i formant. <xref:System.Windows.Forms.ProgressBar>  
  
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
  
     Na koniec można zwiększyć wartość wyświetlaną przez pasek postępu, tak aby każdy wzrost był kwotą unikatową. Jest to przydatne, gdy śledzisz serię unikatowych operacji, takich jak zapisywanie plików o różnych rozmiarach na dysku twardym lub mierzenie postępu jako procent całości.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Aby zwiększyć pasek postępu o wartość dynamiczną  
  
1. Ustaw <xref:System.Windows.Forms.ProgressBar> formant <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.  
  
2. Wywołanie <xref:System.Windows.Forms.ProgressBar.Increment%2A> metody, aby zmienić wartość wyświetlaną przez określoną ć całkowitą.  
  
     Poniższy przykład kodu ilustruje, jak pasek postępu można obliczyć, ile miejsca na dysku zostało użyte podczas operacji kopiowania.  
  
     W poniższym przykładzie, gdy każdy plik jest zapisywany na dysku twardym, pasek postępu i etykieta są aktualizowane w celu odzwierciedlenia ilości dostępnego miejsca na dysku twardym. W tym przykładzie wymaga, aby formularz miał <xref:System.Windows.Forms.Label> formant i formant. <xref:System.Windows.Forms.ProgressBar>  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [ProgressBar — Informacje o formancie](progressbar-control-overview-windows-forms.md)
- [ProgressBar, kontrolka](progressbar-control-windows-forms.md)
