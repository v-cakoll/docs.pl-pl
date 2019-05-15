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
ms.openlocfilehash: 10e864ccfeb22113e5704a4063f903d7a91fedcd
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591581"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Instrukcje: ustawianie wartości wyświetlanej przez kontrolkę ProgressBar formularzy systemu Windows
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.ProgressBar> kontrolować; jednak <xref:System.Windows.Forms.ProgressBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.  
  
 .NET Framework zapewnia kilka różnych sposobów, aby wyświetlić podanej wartości w <xref:System.Windows.Forms.ProgressBar> kontroli. Które rozwiązanie wybierzesz będzie zależeć od wykonywanego zadania lub są rozwiązywania problemu. W poniższej tabeli przedstawiono podejścia, możesz wybrać.  
  
|Podejście|Opis|  
|--------------|-----------------|  
|Ustaw wartość <xref:System.Windows.Forms.ProgressBar> kontrolować bezpośrednio.|To podejście jest przydatne w przypadku zadań, gdy wiadomo, łącznie elementu mierzonych, który będzie angażowany, takich jak odczytywanie rekordy ze źródła danych. Ponadto jeśli wymagane jest tylko jeden lub dwa razy określoną wartość, to prosty sposób, aby to zrobić. Na koniec Użyj tego procesu, jeśli chcesz zmniejszyć wartości wyświetlanej przez pasek postępu.|  
|Zwiększ <xref:System.Windows.Forms.ProgressBar> wyświetlane przez wartość stałą.|Takie podejście jest przydatne, wyświetlając prostą liczba między minimalną i maksymalną, takie jak czas lub liczby plików, które zostały przetworzone z całkowitej znane.|  
|Zwiększ <xref:System.Windows.Forms.ProgressBar> wyświetlane według wartości, który jest różny.|To podejście jest przydatne, gdy zachodzi potrzeba zmiany wartości wyświetlanych kilka razy w różnych ilości. Przykładem będą wyświetlane ilość miejsca na dysku twardym, które są używane podczas zapisywania szereg plików na dysku.|  
  
 Najbardziej bezpośrednim sposobem Ustawianie wartości wyświetlanej przez pasek postępu jest ustawienie <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości. Można to zrobić w czasie projektowania lub w czasie wykonywania.  
  
### <a name="to-set-the-progressbar-value-directly"></a>Aby ustawić wartość elementu ProgressBar bezpośrednio  
  
1. Ustaw <xref:System.Windows.Forms.ProgressBar> kontrolki <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.  
  
2. W kodzie, ustawić <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości na wartość całkowitą między minimalne i maksymalne wartości, że ustanowiono.  
  
    > [!NOTE]
    >  Jeśli ustawisz <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość poza granicami ustanowione przez <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> właściwości kontrolki zgłasza <xref:System.ArgumentException> wyjątku.  
  
     Poniższy przykładowy kod przedstawia sposób ustawiania <xref:System.Windows.Forms.ProgressBar> wartość bezpośrednio. Kod odczytuje rekordy ze źródła danych i aktualizuje pasek postępu i etykiety, za każdym razem, gdy rekord danych jest do odczytu. W tym przykładzie wymaga, że formularz ma <xref:System.Windows.Forms.Label> kontroli <xref:System.Windows.Forms.ProgressBar> kontroli i tabelę danych z wiersz o nazwie `CustomerRow` z `FirstName` i `LastName` pola.  
  
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
  
     W przypadku wyświetlania postępu, który będzie kontynuowane przy stałym interwale można ustawiania wartości, a następnie wywołać metodę, która zwiększa <xref:System.Windows.Forms.ProgressBar> wartości kontrolki przez tego interwału. Jest to przydatne dla czasomierze i inne scenariusze, w którym nie są pomiaru postępu postaci procentu całości.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Aby zwiększyć pasek postępu o wartości stałej  
  
1. Ustaw <xref:System.Windows.Forms.ProgressBar> kontrolki <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.  
  
2. Ustaw dla formantu <xref:System.Windows.Forms.ProgressBar.Step%2A> właściwości Liczba całkowita reprezentująca wartość do zwiększenia pasek postępu jest wyświetlana wartość.  
  
3. Wywołaj <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metodę, aby zmienić wartości wyświetlanej przez wartość ustawiona w <xref:System.Windows.Forms.ProgressBar.Step%2A> właściwości.  
  
     Poniższy przykład kodu ilustruje, jak pasek postępu może zachować liczba plików w operacji kopiowania.  
  
     W poniższym przykładzie zgodnie z każdego pliku jest do odczytu do pamięci, aby odzwierciedlić, że całkowita liczba plików do odczytu są aktualizowane pasek postępu i etykiety. W tym przykładzie wymaga, że formularz ma <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.ProgressBar> kontroli.  
  
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
  
     Na koniec można zwiększyć wartości wyświetlanej przez pasek postępu, tak aby każdy wzrost jest unikatowy. Jest to przydatne, gdy użytkownik jest rejestrowanie informacji o szereg unikatowy operacje, takie jak zapisywanie plików o różnych rozmiarach na dysku twardym lub postępów w postaci procentu całości.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Aby zwiększyć pasek postępu przez wartości dynamiczne  
  
1. Ustaw <xref:System.Windows.Forms.ProgressBar> kontrolki <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.  
  
2. Wywołaj <xref:System.Windows.Forms.ProgressBar.Increment%2A> metodę, aby zmienić wartości wyświetlanej przez liczbę całkowitą, które określisz.  
  
     Poniższy przykład kodu ilustruje, jak pasek postępu może obliczyć ilość miejsca na dysku został użyty podczas operacji kopiowania.  
  
     W poniższym przykładzie ponieważ każdy plik jest zapisywany na dysku twardym, pasek postępu i etykiety zostały zaktualizowane pod odzwierciedla ilość dostępnego miejsca na dysku twardym. W tym przykładzie wymaga, że formularz ma <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.ProgressBar> kontroli.  
  
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
