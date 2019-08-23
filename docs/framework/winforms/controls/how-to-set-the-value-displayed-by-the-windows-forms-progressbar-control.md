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
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="34b05-102">Instrukcje: ustawianie wartości wyświetlanej przez kontrolkę ProgressBar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="34b05-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
> <span data-ttu-id="34b05-103">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.ProgressBar> do <xref:System.Windows.Forms.ProgressBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStripProgressBar></span><span class="sxs-lookup"><span data-stu-id="34b05-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="34b05-104">.NET Framework oferuje kilka różnych sposobów wyświetlania danej wartości w <xref:System.Windows.Forms.ProgressBar> formancie.</span><span class="sxs-lookup"><span data-stu-id="34b05-104">The .NET Framework gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="34b05-105">Wybrana metoda będzie zależeć od zadania w ręku lub podczas rozwiązywania problemu.</span><span class="sxs-lookup"><span data-stu-id="34b05-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="34b05-106">W poniższej tabeli przedstawiono podejścia, które można wybrać.</span><span class="sxs-lookup"><span data-stu-id="34b05-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="34b05-107">Podejście</span><span class="sxs-lookup"><span data-stu-id="34b05-107">Approach</span></span>|<span data-ttu-id="34b05-108">Opis</span><span class="sxs-lookup"><span data-stu-id="34b05-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="34b05-109">Ustaw wartość <xref:System.Windows.Forms.ProgressBar> formantu bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="34b05-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="34b05-110">Takie podejście jest przydatne w przypadku zadań, w których wiadomo, ile elementów jest mierzonych, takich jak odczytywanie rekordów ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="34b05-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="34b05-111">Ponadto, jeśli trzeba ustawić wartość tylko raz lub dwa razy, jest to prosty sposób.</span><span class="sxs-lookup"><span data-stu-id="34b05-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="34b05-112">Na koniec Użyj tego procesu, jeśli chcesz zmniejszyć wartość wyświetlaną na pasku postępu.</span><span class="sxs-lookup"><span data-stu-id="34b05-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="34b05-113">Zwiększ poziom <xref:System.Windows.Forms.ProgressBar> wyświetlania o ustalonej wartości.</span><span class="sxs-lookup"><span data-stu-id="34b05-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="34b05-114">Takie podejście jest przydatne, gdy wyświetlasz prostą liczbę z przedziału od minimum do maksimum, na przykład czas, który upłynął, lub liczbę plików, które zostały przetworzone z znanego podsumowania.</span><span class="sxs-lookup"><span data-stu-id="34b05-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="34b05-115"><xref:System.Windows.Forms.ProgressBar> Zwiększenie wyświetlania przez wartość, która różni się.</span><span class="sxs-lookup"><span data-stu-id="34b05-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="34b05-116">Takie podejście jest przydatne, gdy trzeba zmienić wyświetlaną wartość na liczbę razy w różnych kwotach.</span><span class="sxs-lookup"><span data-stu-id="34b05-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="34b05-117">Przykład pokazuje ilość miejsca na dysku twardym zużywanego podczas zapisywania serii plików na dysku.</span><span class="sxs-lookup"><span data-stu-id="34b05-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="34b05-118">Najbardziej bezpośrednim sposobem ustawienia wartości wyświetlanej przez pasek postępu jest ustawienie <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="34b05-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="34b05-119">Można to zrobić w czasie projektowania lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="34b05-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="34b05-120">Aby ustawić wartość ProgressBar bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="34b05-120">To set the ProgressBar value directly</span></span>  
  
1. <span data-ttu-id="34b05-121"><xref:System.Windows.Forms.ProgressBar> Ustaw kontrolkę<xref:System.Windows.Forms.ProgressBar.Maximum%2A>iwartości. <xref:System.Windows.Forms.ProgressBar.Minimum%2A></span><span class="sxs-lookup"><span data-stu-id="34b05-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="34b05-122">W kodzie, należy ustawić <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość kontrolki na wartość całkowitą z zakresu od ustalonej wartości minimalnej i maksymalnej.</span><span class="sxs-lookup"><span data-stu-id="34b05-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="34b05-123">Jeśli <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość zostanie ustawiona poza granicami ustanowionymi <xref:System.Windows.Forms.ProgressBar.Minimum%2A> przez właściwości i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> , formant zgłosi <xref:System.ArgumentException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="34b05-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="34b05-124">Poniższy przykład kodu ilustruje sposób bezpośredniego ustawiania <xref:System.Windows.Forms.ProgressBar> wartości.</span><span class="sxs-lookup"><span data-stu-id="34b05-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="34b05-125">Kod odczytuje rekordy ze źródła danych i aktualizuje pasek postępu oraz etykietę za każdym razem, gdy rekord danych zostanie odczytany.</span><span class="sxs-lookup"><span data-stu-id="34b05-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="34b05-126">Ten przykład wymaga, aby formularz miał <xref:System.Windows.Forms.Label> kontrolkę <xref:System.Windows.Forms.ProgressBar> , kontrolkę i tabelę danych z wierszem o nazwie `CustomerRow` z `FirstName` i `LastName` polami.</span><span class="sxs-lookup"><span data-stu-id="34b05-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
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
  
     Jeśli jest wyświetlany postęp, który przechodzi przez stały interwał, można ustawić wartość, a następnie wywołać metodę, która zwiększa <xref:System.Windows.Forms.ProgressBar> wartość kontrolki według tego interwału. <span data-ttu-id="34b05-128">Jest to przydatne w przypadku czasomierzy i innych scenariuszy, w których postępy nie są mierzone jako procent całości.</span><span class="sxs-lookup"><span data-stu-id="34b05-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="34b05-129">Aby zwiększyć pasek postępu o ustalonej wartości</span><span class="sxs-lookup"><span data-stu-id="34b05-129">To increase the progress bar by a fixed value</span></span>  
  
1. <span data-ttu-id="34b05-130"><xref:System.Windows.Forms.ProgressBar> Ustaw kontrolkę<xref:System.Windows.Forms.ProgressBar.Maximum%2A>iwartości. <xref:System.Windows.Forms.ProgressBar.Minimum%2A></span><span class="sxs-lookup"><span data-stu-id="34b05-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="34b05-131">Ustaw <xref:System.Windows.Forms.ProgressBar.Step%2A> właściwość kontrolki na liczbę całkowitą reprezentującą kwotę, aby zwiększyć wartość wyświetlaną na pasku postępu.</span><span class="sxs-lookup"><span data-stu-id="34b05-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3. <span data-ttu-id="34b05-132">Wywołaj <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metodę, aby zmienić wartość wyświetlaną przez kwotę ustawioną <xref:System.Windows.Forms.ProgressBar.Step%2A> we właściwości.</span><span class="sxs-lookup"><span data-stu-id="34b05-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="34b05-133">Poniższy przykład kodu ilustruje, jak pasek postępu może zachować liczbę plików w operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="34b05-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="34b05-134">W poniższym przykładzie, ponieważ każdy plik jest odczytywany do pamięci, pasek postępu i etykieta są aktualizowane w celu odzwierciedlenia łącznej liczby odczytywanych plików.</span><span class="sxs-lookup"><span data-stu-id="34b05-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="34b05-135">Ten przykład wymaga, aby formularz miał <xref:System.Windows.Forms.Label> formant <xref:System.Windows.Forms.ProgressBar> i formant.</span><span class="sxs-lookup"><span data-stu-id="34b05-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
     Na koniec można zwiększyć wartość wyświetlaną przez pasek postępu, aby każdy wzrost był unikatowy. <span data-ttu-id="34b05-137">Jest to przydatne, gdy śledzisz szereg unikatowych operacji, takich jak zapisywanie plików o różnych rozmiarach na dysku twardym, lub pomiar postępu jako procent całości.</span><span class="sxs-lookup"><span data-stu-id="34b05-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="34b05-138">Aby zwiększyć pasek postępu przez wartość dynamiczną</span><span class="sxs-lookup"><span data-stu-id="34b05-138">To increase the progress bar by a dynamic value</span></span>  
  
1. <span data-ttu-id="34b05-139"><xref:System.Windows.Forms.ProgressBar> Ustaw kontrolkę<xref:System.Windows.Forms.ProgressBar.Maximum%2A>iwartości. <xref:System.Windows.Forms.ProgressBar.Minimum%2A></span><span class="sxs-lookup"><span data-stu-id="34b05-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="34b05-140">Wywołaj <xref:System.Windows.Forms.ProgressBar.Increment%2A> metodę, aby zmienić wartość wyświetlaną przez określoną liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="34b05-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="34b05-141">Poniższy przykład kodu ilustruje, jak pasek postępu może obliczyć ilość miejsca na dysku, która została użyta podczas operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="34b05-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="34b05-142">W poniższym przykładzie, ponieważ każdy plik jest zapisywana na dysku twardym, pasek postępu i etykieta są aktualizowane w celu odzwierciedlenia ilości dostępnego miejsca na dysku twardym.</span><span class="sxs-lookup"><span data-stu-id="34b05-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="34b05-143">Ten przykład wymaga, aby formularz miał <xref:System.Windows.Forms.Label> formant <xref:System.Windows.Forms.ProgressBar> i formant.</span><span class="sxs-lookup"><span data-stu-id="34b05-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34b05-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34b05-144">See also</span></span>

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [<span data-ttu-id="34b05-145">ProgressBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="34b05-145">ProgressBar Control Overview</span></span>](progressbar-control-overview-windows-forms.md)
- [<span data-ttu-id="34b05-146">ProgressBar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="34b05-146">ProgressBar Control</span></span>](progressbar-control-windows-forms.md)
