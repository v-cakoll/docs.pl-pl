---
title: 'Porady: ustawianie wartości wyświetlanej przez formant ProgressBar formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 66093cacea4f76ab65af40658f03c03ce7560f0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="7afb7-102">Porady: ustawianie wartości wyświetlanej przez formant ProgressBar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7afb7-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="7afb7-103"><xref:System.Windows.Forms.ToolStripProgressBar> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.ProgressBar> kontrolować; jednak <xref:System.Windows.Forms.ProgressBar> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="7afb7-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="7afb7-104">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zapewnia kilka różnych sposobów, aby wyświetlić w danej wartości <xref:System.Windows.Forms.ProgressBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="7afb7-104">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="7afb7-105">Które rozwiązanie możesz wybrać będzie zależeć od wykonywanego zadania lub są rozwiązywania tego problemu.</span><span class="sxs-lookup"><span data-stu-id="7afb7-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="7afb7-106">W poniższej tabeli przedstawiono metodami, czy są dostępne.</span><span class="sxs-lookup"><span data-stu-id="7afb7-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="7afb7-107">Podejście</span><span class="sxs-lookup"><span data-stu-id="7afb7-107">Approach</span></span>|<span data-ttu-id="7afb7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="7afb7-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7afb7-109">Ustaw wartość <xref:System.Windows.Forms.ProgressBar> kontrolować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="7afb7-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="7afb7-110">Ta metoda jest przydatne w przypadku zadania, w którym wiadomo łącznie elementu mierzonych, które będą objęte, takich jak odczytywanie rekordy ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7afb7-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="7afb7-111">Ponadto jeśli wymagane jest tylko jeden lub dwa razy wartości, to prosty sposób, aby wykonać to zadanie.</span><span class="sxs-lookup"><span data-stu-id="7afb7-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="7afb7-112">Na koniec Użyj tego procesu, jeśli musisz zmniejszyć wartości wyświetlane na pasku postępu.</span><span class="sxs-lookup"><span data-stu-id="7afb7-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="7afb7-113">Zwiększ <xref:System.Windows.Forms.ProgressBar> wyświetlane przez wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="7afb7-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="7afb7-114">Takie rozwiązanie jest przydatne, wyświetlając proste liczba między minimalną i maksymalną, takie jak czas lub liczbę plików, które zostały przetworzone liczba znane.</span><span class="sxs-lookup"><span data-stu-id="7afb7-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="7afb7-115">Zwiększ <xref:System.Windows.Forms.ProgressBar> wyświetlić wartość, która może być różna.</span><span class="sxs-lookup"><span data-stu-id="7afb7-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="7afb7-116">Takie rozwiązanie jest przydatne, gdy trzeba będzie zmienić wartości wyświetlanych kilka razy w różnych ilości.</span><span class="sxs-lookup"><span data-stu-id="7afb7-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="7afb7-117">Przykład będzie wyświetlana ilość miejsca na dysku twardym są używane podczas zapisywania serię plików na dysku.</span><span class="sxs-lookup"><span data-stu-id="7afb7-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="7afb7-118">Najbardziej bezpośrednim sposobem Ustawianie wartości wyświetlanej przez paska postępu jest ustawienie <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7afb7-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="7afb7-119">Można to zrobić w czasie projektowania lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7afb7-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="7afb7-120">Aby ustawić wartość elementu ProgressBar bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="7afb7-120">To set the ProgressBar value directly</span></span>  
  
1.  <span data-ttu-id="7afb7-121">Ustaw <xref:System.Windows.Forms.ProgressBar> formantu <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.</span><span class="sxs-lookup"><span data-stu-id="7afb7-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="7afb7-122">W kodzie, ustaw dla formantu <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości na wartość całkowitą między minimalną i maksymalną wartość zostało ustanowione.</span><span class="sxs-lookup"><span data-stu-id="7afb7-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7afb7-123">Jeśli ustawisz <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości poza granicami ustala <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> właściwości formantu zgłasza <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7afb7-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="7afb7-124">Poniższy przykładowy kod przedstawia sposób ustawiania <xref:System.Windows.Forms.ProgressBar> wartość bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="7afb7-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="7afb7-125">Ten kod odczytuje rekordy ze źródła danych i aktualizuje pasek postępu i etykiety, za każdym razem, gdy rekord danych jest do odczytu.</span><span class="sxs-lookup"><span data-stu-id="7afb7-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="7afb7-126">W tym przykładzie wymaga, aby miało formularza <xref:System.Windows.Forms.Label> kontroli, <xref:System.Windows.Forms.ProgressBar> kontroli i tabelę danych z wierszem o nazwie `CustomerRow` z `FirstName` i `LastName` pól.</span><span class="sxs-lookup"><span data-stu-id="7afb7-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
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
  
     W przypadku wyświetlania postępu, który będzie kontynuowana przy stałym interwale można ustawiania wartości, a następnie wywołaj metodę, która zwiększa <xref:System.Windows.Forms.ProgressBar> wartość formantu w tym interwał. <span data-ttu-id="7afb7-128">Jest to przydatne dla czasomierze i innych scenariuszy, w którym nie są pomiaru postępu jako procent całości.</span><span class="sxs-lookup"><span data-stu-id="7afb7-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="7afb7-129">Aby zwiększyć pasek postępu przez wartość stałą</span><span class="sxs-lookup"><span data-stu-id="7afb7-129">To increase the progress bar by a fixed value</span></span>  
  
1.  <span data-ttu-id="7afb7-130">Ustaw <xref:System.Windows.Forms.ProgressBar> formantu <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.</span><span class="sxs-lookup"><span data-stu-id="7afb7-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="7afb7-131">Ustawianie formantu <xref:System.Windows.Forms.ProgressBar.Step%2A> wartości wyświetlane właściwości na liczbę całkowitą reprezentującą wielkość zwiększające pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="7afb7-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3.  <span data-ttu-id="7afb7-132">Wywołanie <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metodę, aby zmienić wartość wyświetlana wartość ustawiona w <xref:System.Windows.Forms.ProgressBar.Step%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7afb7-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="7afb7-133">Poniższy przykład kodu pokazuje, jak pasek postępu można zachować liczba plików w operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="7afb7-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="7afb7-134">W poniższym przykładzie każdy plik jest w trybie odczytu do pamięci, aby odzwierciedlał całkowita liczba plików do odczytu są aktualizowane pasek postępu i etykiety.</span><span class="sxs-lookup"><span data-stu-id="7afb7-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="7afb7-135">W tym przykładzie wymaga, aby miało formularza <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.ProgressBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="7afb7-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
     Na koniec można zwiększyć wartości wyświetlanej przez pasek postępu, dzięki czemu każdy wzrost jest unikatowy. <span data-ttu-id="7afb7-137">Jest to przydatne, gdy użytkownik są rejestrowanie informacji o szereg unikatowy operacje, takie jak zapisywanie plików o różnych rozmiarach na dysk twardy lub postępów w procentach całego.</span><span class="sxs-lookup"><span data-stu-id="7afb7-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="7afb7-138">Aby zwiększyć pasek postępu przez wartość dynamiczną</span><span class="sxs-lookup"><span data-stu-id="7afb7-138">To increase the progress bar by a dynamic value</span></span>  
  
1.  <span data-ttu-id="7afb7-139">Ustaw <xref:System.Windows.Forms.ProgressBar> formantu <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.</span><span class="sxs-lookup"><span data-stu-id="7afb7-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="7afb7-140">Wywołanie <xref:System.Windows.Forms.ProgressBar.Increment%2A> metodę, aby zmienić wartość wyświetlana przez całkowitą określisz.</span><span class="sxs-lookup"><span data-stu-id="7afb7-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="7afb7-141">Poniższy przykład kodu pokazuje, jak pasek postępu obliczyć ilość miejsca na dysku został użyty podczas operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="7afb7-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="7afb7-142">W poniższym przykładzie ponieważ każdy plik jest zapisywany na dysku twardym pasek postępu i etykiety są aktualizowane odzwierciedlają ilość dostępnego miejsca na dysku twardym.</span><span class="sxs-lookup"><span data-stu-id="7afb7-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="7afb7-143">W tym przykładzie wymaga, aby miało formularza <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.ProgressBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="7afb7-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7afb7-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7afb7-144">See Also</span></span>  
 <xref:System.Windows.Forms.ProgressBar>  
 <xref:System.Windows.Forms.ToolStripProgressBar>  
 [<span data-ttu-id="7afb7-145">ProgressBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="7afb7-145">ProgressBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)  
 [<span data-ttu-id="7afb7-146">ProgressBar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7afb7-146">ProgressBar Control</span></span>](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
