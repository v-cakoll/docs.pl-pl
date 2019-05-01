---
title: 'Instrukcje: pobieranie pliku w tle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
ms.openlocfilehash: af5a607b4800635d096e83b55a5bd5a912c8538d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941505"
---
# <a name="how-to-download-a-file-in-the-background"></a><span data-ttu-id="c4a51-102">Instrukcje: pobieranie pliku w tle</span><span class="sxs-lookup"><span data-stu-id="c4a51-102">How to: Download a File in the Background</span></span>
<span data-ttu-id="c4a51-103">Pobieranie pliku jest typowym zadaniem i jest często przydatne do wykonania tej operacji potencjalnie czasochłonne w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="c4a51-103">Downloading a file is a common task, and it is often useful to run this potentially time-consuming operation on a separate thread.</span></span> <span data-ttu-id="c4a51-104">Użyj <xref:System.ComponentModel.BackgroundWorker> składnika, aby wykonać to zadanie za pomocą bardzo niewielkiej ilości kodu.</span><span class="sxs-lookup"><span data-stu-id="c4a51-104">Use the <xref:System.ComponentModel.BackgroundWorker> component to accomplish this task with very little code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4a51-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4a51-105">Example</span></span>  
 <span data-ttu-id="c4a51-106">Poniższy przykład kodu demonstruje sposób używania <xref:System.ComponentModel.BackgroundWorker> składnika można załadować pliku XML z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="c4a51-106">The following code example demonstrates how to use a <xref:System.ComponentModel.BackgroundWorker> component to load an XML file from a URL.</span></span> <span data-ttu-id="c4a51-107">Kiedy użytkownik kliknie **Pobierz** przycisku <xref:System.Windows.Forms.Control.Click> wywołań obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody <xref:System.ComponentModel.BackgroundWorker> składnika, aby uruchomić operację pobierania.</span><span class="sxs-lookup"><span data-stu-id="c4a51-107">When the user clicks the **Download** button, the <xref:System.Windows.Forms.Control.Click> event handler calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of a <xref:System.ComponentModel.BackgroundWorker> component to start the download operation.</span></span> <span data-ttu-id="c4a51-108">Ten przycisk jest wyłączone na czas trwania pobierania i włączone po zakończeniu pobierania.</span><span class="sxs-lookup"><span data-stu-id="c4a51-108">The button is disabled for the duration of the download, and then enabled when the download is complete.</span></span> <span data-ttu-id="c4a51-109">A <xref:System.Windows.Forms.MessageBox> Wyświetla zawartość pliku.</span><span class="sxs-lookup"><span data-stu-id="c4a51-109">A <xref:System.Windows.Forms.MessageBox> displays the contents of the file.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 <span data-ttu-id="c4a51-110">**Pobieranie pliku**</span><span class="sxs-lookup"><span data-stu-id="c4a51-110">**Downloading the file**</span></span>  
  
 <span data-ttu-id="c4a51-111">Plik jest pobierany na <xref:System.ComponentModel.BackgroundWorker> wątku roboczego składnika, który jest uruchamiany <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c4a51-111">The file is downloaded on the <xref:System.ComponentModel.BackgroundWorker> component's worker thread, which runs the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="c4a51-112">Ten wątek rozpoczyna się, gdy kod wywołuje <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c4a51-112">This thread starts when your code calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 <span data-ttu-id="c4a51-113">**BackgroundWorker zakończyć oczekiwanie**</span><span class="sxs-lookup"><span data-stu-id="c4a51-113">**Waiting for a BackgroundWorker to finish**</span></span>  
  
 <span data-ttu-id="c4a51-114">`downloadButton_Click` Programu obsługi zdarzeń pokazuje, jak czekać na <xref:System.ComponentModel.BackgroundWorker> składnika, aby zakończyć jego zadanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="c4a51-114">The `downloadButton_Click` event handler demonstrates how to wait for a <xref:System.ComponentModel.BackgroundWorker> component to finish its asynchronous task.</span></span>  
  
 <span data-ttu-id="c4a51-115">Jeśli tylko aplikacja ma reagować na zdarzenia, a nie chcesz wykonać pracę w wątku głównym, podczas oczekiwania na ukończenie wątku tła, po prostu zamknąć program obsługi.</span><span class="sxs-lookup"><span data-stu-id="c4a51-115">If you only want the application to respond to events and do not want to do any work in the main thread while you wait for the background thread to complete, just exit the handler.</span></span>  
  
 <span data-ttu-id="c4a51-116">Jeśli chcesz to kontynuować pracę w wątku głównym, użyj <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> właściwości, aby określić, czy <xref:System.ComponentModel.BackgroundWorker> wątek jest nadal uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="c4a51-116">If you want to continue doing work in the main thread, use the <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> property to determine whether the <xref:System.ComponentModel.BackgroundWorker> thread is still running.</span></span> <span data-ttu-id="c4a51-117">W tym przykładzie paska postępu jest aktualizowana podczas przetwarzania pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="c4a51-117">In the example, a progress bar is updated while the download is processing.</span></span> <span data-ttu-id="c4a51-118">Pamiętaj wywołać <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metodę, aby zachować dynamicznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c4a51-118">Be sure to call the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method to keep the UI responsive.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 <span data-ttu-id="c4a51-119">**Wyświetlanie wyników**</span><span class="sxs-lookup"><span data-stu-id="c4a51-119">**Displaying the result**</span></span>  
  
 <span data-ttu-id="c4a51-120">`backgroundWorker1_RunWorkerCompleted` Metodę uchwytów <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzenie i jest wywoływana po zakończeniu operacji w tle.</span><span class="sxs-lookup"><span data-stu-id="c4a51-120">The `backgroundWorker1_RunWorkerCompleted` method handles the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event and is called when the background operation is completed.</span></span> <span data-ttu-id="c4a51-121">Metoda ta najpierw sprawdza <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c4a51-121">This method first checks the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="c4a51-122">Jeśli <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> jest `null`, wówczas ta metoda Wy Wyświetla zawartość pliku.</span><span class="sxs-lookup"><span data-stu-id="c4a51-122">If <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> is `null`, then this method displays the contents of the file.</span></span> <span data-ttu-id="c4a51-123">Umożliwia ona następnie przycisk pobierania, który został wyłączony w momencie rozpoczęcia pobierania, i resetuje pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="c4a51-123">It then enables the download button, which was disabled when the download began, and it resets the progress bar.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c4a51-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c4a51-124">Compiling the Code</span></span>  
 <span data-ttu-id="c4a51-125">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c4a51-125">This example requires:</span></span>  
  
- <span data-ttu-id="c4a51-126">Odwołania do zestawów System.Xml, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="c4a51-126">References to the System.Drawing, System.Windows.Forms, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="c4a51-127">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c4a51-127">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c4a51-128">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="c4a51-128">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c4a51-129">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="c4a51-129">Robust Programming</span></span>  
 <span data-ttu-id="c4a51-130">Zawsze sprawdzaj <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> właściwości w swojej <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> programu obsługi zdarzeń przed podjęciem próby uzyskania dostępu <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> właściwości lub inny obiekt, który może mieć wpływ <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c4a51-130">Always check the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property in your <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler before attempting to access the <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> property or any other object that may have been affected by the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a51-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4a51-131">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="c4a51-132">Instrukcje: Uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="c4a51-132">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="c4a51-133">Instrukcje: Implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="c4a51-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
