---
title: 'Instrukcje: Ustawianie wartości wyświetlanej przez formant ProgressBar formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: d1be2bb2c909b8074f1092d4ce138feff5c9607f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496039"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="ce127-102">Instrukcje: Ustawianie wartości wyświetlanej przez formant ProgressBar formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="ce127-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="ce127-103"><xref:System.Windows.Forms.ToolStripProgressBar> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.ProgressBar> kontrolować; jednak <xref:System.Windows.Forms.ProgressBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="ce127-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="ce127-104">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zapewnia kilka różnych sposobów, aby wyświetlić podanej wartości w <xref:System.Windows.Forms.ProgressBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ce127-104">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="ce127-105">Które rozwiązanie wybierzesz będzie zależeć od wykonywanego zadania lub są rozwiązywania problemu.</span><span class="sxs-lookup"><span data-stu-id="ce127-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="ce127-106">W poniższej tabeli przedstawiono podejścia, możesz wybrać.</span><span class="sxs-lookup"><span data-stu-id="ce127-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="ce127-107">Podejście</span><span class="sxs-lookup"><span data-stu-id="ce127-107">Approach</span></span>|<span data-ttu-id="ce127-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ce127-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ce127-109">Ustaw wartość <xref:System.Windows.Forms.ProgressBar> kontrolować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ce127-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="ce127-110">To podejście jest przydatne w przypadku zadań, gdy wiadomo, łącznie elementu mierzonych, który będzie angażowany, takich jak odczytywanie rekordy ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ce127-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="ce127-111">Ponadto jeśli wymagane jest tylko jeden lub dwa razy określoną wartość, to prosty sposób, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="ce127-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="ce127-112">Na koniec Użyj tego procesu, jeśli chcesz zmniejszyć wartości wyświetlanej przez pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="ce127-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="ce127-113">Zwiększ <xref:System.Windows.Forms.ProgressBar> wyświetlane przez wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="ce127-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="ce127-114">Takie podejście jest przydatne, wyświetlając prostą liczba między minimalną i maksymalną, takie jak czas lub liczby plików, które zostały przetworzone z całkowitej znane.</span><span class="sxs-lookup"><span data-stu-id="ce127-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="ce127-115">Zwiększ <xref:System.Windows.Forms.ProgressBar> wyświetlane według wartości, który jest różny.</span><span class="sxs-lookup"><span data-stu-id="ce127-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="ce127-116">To podejście jest przydatne, gdy zachodzi potrzeba zmiany wartości wyświetlanych kilka razy w różnych ilości.</span><span class="sxs-lookup"><span data-stu-id="ce127-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="ce127-117">Przykładem będą wyświetlane ilość miejsca na dysku twardym, które są używane podczas zapisywania szereg plików na dysku.</span><span class="sxs-lookup"><span data-stu-id="ce127-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="ce127-118">Najbardziej bezpośrednim sposobem Ustawianie wartości wyświetlanej przez pasek postępu jest ustawienie <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ce127-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="ce127-119">Można to zrobić w czasie projektowania lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ce127-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="ce127-120">Aby ustawić wartość elementu ProgressBar bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="ce127-120">To set the ProgressBar value directly</span></span>  
  
1.  <span data-ttu-id="ce127-121">Ustaw <xref:System.Windows.Forms.ProgressBar> kontrolki <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.</span><span class="sxs-lookup"><span data-stu-id="ce127-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="ce127-122">W kodzie, ustawić <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwości na wartość całkowitą między minimalne i maksymalne wartości, że ustanowiono.</span><span class="sxs-lookup"><span data-stu-id="ce127-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce127-123">Jeśli ustawisz <xref:System.Windows.Forms.ProgressBar.Value%2A> właściwość poza granicami ustanowione przez <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> właściwości kontrolki zgłasza <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ce127-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="ce127-124">Poniższy przykładowy kod przedstawia sposób ustawiania <xref:System.Windows.Forms.ProgressBar> wartość bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ce127-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="ce127-125">Kod odczytuje rekordy ze źródła danych i aktualizuje pasek postępu i etykiety, za każdym razem, gdy rekord danych jest do odczytu.</span><span class="sxs-lookup"><span data-stu-id="ce127-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="ce127-126">W tym przykładzie wymaga, że formularz ma <xref:System.Windows.Forms.Label> kontroli <xref:System.Windows.Forms.ProgressBar> kontroli i tabelę danych z wiersz o nazwie `CustomerRow` z `FirstName` i `LastName` pola.</span><span class="sxs-lookup"><span data-stu-id="ce127-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
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
  
     W przypadku wyświetlania postępu, który będzie kontynuowane przy stałym interwale można ustawiania wartości, a następnie wywołać metodę, która zwiększa <xref:System.Windows.Forms.ProgressBar> wartości kontrolki przez tego interwału. <span data-ttu-id="ce127-128">Jest to przydatne dla czasomierze i inne scenariusze, w którym nie są pomiaru postępu postaci procentu całości.</span><span class="sxs-lookup"><span data-stu-id="ce127-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="ce127-129">Aby zwiększyć pasek postępu o wartości stałej</span><span class="sxs-lookup"><span data-stu-id="ce127-129">To increase the progress bar by a fixed value</span></span>  
  
1.  <span data-ttu-id="ce127-130">Ustaw <xref:System.Windows.Forms.ProgressBar> kontrolki <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.</span><span class="sxs-lookup"><span data-stu-id="ce127-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="ce127-131">Ustaw dla formantu <xref:System.Windows.Forms.ProgressBar.Step%2A> właściwości Liczba całkowita reprezentująca wartość do zwiększenia pasek postępu jest wyświetlana wartość.</span><span class="sxs-lookup"><span data-stu-id="ce127-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3.  <span data-ttu-id="ce127-132">Wywołaj <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metodę, aby zmienić wartości wyświetlanej przez wartość ustawiona w <xref:System.Windows.Forms.ProgressBar.Step%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ce127-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="ce127-133">Poniższy przykład kodu ilustruje, jak pasek postępu może zachować liczba plików w operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="ce127-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="ce127-134">W poniższym przykładzie zgodnie z każdego pliku jest do odczytu do pamięci, aby odzwierciedlić, że całkowita liczba plików do odczytu są aktualizowane pasek postępu i etykiety.</span><span class="sxs-lookup"><span data-stu-id="ce127-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="ce127-135">W tym przykładzie wymaga, że formularz ma <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.ProgressBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ce127-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
     Na koniec można zwiększyć wartości wyświetlanej przez pasek postępu, tak aby każdy wzrost jest unikatowy. <span data-ttu-id="ce127-137">Jest to przydatne, gdy użytkownik jest rejestrowanie informacji o szereg unikatowy operacje, takie jak zapisywanie plików o różnych rozmiarach na dysku twardym lub postępów w postaci procentu całości.</span><span class="sxs-lookup"><span data-stu-id="ce127-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="ce127-138">Aby zwiększyć pasek postępu przez wartości dynamiczne</span><span class="sxs-lookup"><span data-stu-id="ce127-138">To increase the progress bar by a dynamic value</span></span>  
  
1.  <span data-ttu-id="ce127-139">Ustaw <xref:System.Windows.Forms.ProgressBar> kontrolki <xref:System.Windows.Forms.ProgressBar.Minimum%2A> i <xref:System.Windows.Forms.ProgressBar.Maximum%2A> wartości.</span><span class="sxs-lookup"><span data-stu-id="ce127-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2.  <span data-ttu-id="ce127-140">Wywołaj <xref:System.Windows.Forms.ProgressBar.Increment%2A> metodę, aby zmienić wartości wyświetlanej przez liczbę całkowitą, które określisz.</span><span class="sxs-lookup"><span data-stu-id="ce127-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="ce127-141">Poniższy przykład kodu ilustruje, jak pasek postępu może obliczyć ilość miejsca na dysku został użyty podczas operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="ce127-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="ce127-142">W poniższym przykładzie ponieważ każdy plik jest zapisywany na dysku twardym, pasek postępu i etykiety zostały zaktualizowane pod odzwierciedla ilość dostępnego miejsca na dysku twardym.</span><span class="sxs-lookup"><span data-stu-id="ce127-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="ce127-143">W tym przykładzie wymaga, że formularz ma <xref:System.Windows.Forms.Label> kontroli i <xref:System.Windows.Forms.ProgressBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ce127-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ce127-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce127-144">See also</span></span>
- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [<span data-ttu-id="ce127-145">ProgressBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="ce127-145">ProgressBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)
- [<span data-ttu-id="ce127-146">ProgressBar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="ce127-146">ProgressBar Control</span></span>](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
