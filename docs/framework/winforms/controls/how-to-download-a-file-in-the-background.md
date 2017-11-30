---
title: 'Porady: pobieranie pliku w tle'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b83f5ae935ed9ba6c5351d48175ee7747e7b01b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-download-a-file-in-the-background"></a><span data-ttu-id="354fc-102">Porady: pobieranie pliku w tle</span><span class="sxs-lookup"><span data-stu-id="354fc-102">How to: Download a File in the Background</span></span>
<span data-ttu-id="354fc-103">Pobieranie pliku jest typowych zadań i często jest przydatne do przeprowadzenia tej operacji potencjalnie czasochłonne w oddzielnym wątku.</span><span class="sxs-lookup"><span data-stu-id="354fc-103">Downloading a file is a common task, and it is often useful to run this potentially time-consuming operation on a separate thread.</span></span> <span data-ttu-id="354fc-104">Użyj <xref:System.ComponentModel.BackgroundWorker> składnika, aby wykonać to zadanie wymaga bardzo mało kodu.</span><span class="sxs-lookup"><span data-stu-id="354fc-104">Use the <xref:System.ComponentModel.BackgroundWorker> component to accomplish this task with very little code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="354fc-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="354fc-105">Example</span></span>  
 <span data-ttu-id="354fc-106">Poniższy przykład kodu pokazuje sposób użycia <xref:System.ComponentModel.BackgroundWorker> składnika można załadować pliku XML z adresu URL.</span><span class="sxs-lookup"><span data-stu-id="354fc-106">The following code example demonstrates how to use a <xref:System.ComponentModel.BackgroundWorker> component to load an XML file from a URL.</span></span> <span data-ttu-id="354fc-107">Po kliknięciu przez użytkownika **Pobierz** przycisku <xref:System.Windows.Forms.Control.Click> wywołań obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody <xref:System.ComponentModel.BackgroundWorker> składnik, aby uruchomić operację pobierania.</span><span class="sxs-lookup"><span data-stu-id="354fc-107">When the user clicks the **Download** button, the <xref:System.Windows.Forms.Control.Click> event handler calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of a <xref:System.ComponentModel.BackgroundWorker> component to start the download operation.</span></span> <span data-ttu-id="354fc-108">Przycisk jest wyłączone na czas trwania pobierania, a następnie włączona po ukończeniu pobierania.</span><span class="sxs-lookup"><span data-stu-id="354fc-108">The button is disabled for the duration of the download, and then enabled when the download is complete.</span></span> <span data-ttu-id="354fc-109">A <xref:System.Windows.Forms.MessageBox> Wyświetla zawartość pliku.</span><span class="sxs-lookup"><span data-stu-id="354fc-109">A <xref:System.Windows.Forms.MessageBox> displays the contents of the file.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 <span data-ttu-id="354fc-110">**Trwa pobieranie pliku**</span><span class="sxs-lookup"><span data-stu-id="354fc-110">**Downloading the file**</span></span>  
  
 <span data-ttu-id="354fc-111">Plik jest pobierany na <xref:System.ComponentModel.BackgroundWorker> wątku roboczego składnika, w którym jest uruchomiona <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="354fc-111">The file is downloaded on the <xref:System.ComponentModel.BackgroundWorker> component's worker thread, which runs the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="354fc-112">Ten wątek rozpoczyna się, gdy kod wywołuje <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="354fc-112">This thread starts when your code calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 <span data-ttu-id="354fc-113">**Oczekiwanie na BackgroundWorker do zakończenia**</span><span class="sxs-lookup"><span data-stu-id="354fc-113">**Waiting for a BackgroundWorker to finish**</span></span>  
  
 <span data-ttu-id="354fc-114">`downloadButton_Click` Obsługi zdarzeń pokazuje, jak oczekiwania <xref:System.ComponentModel.BackgroundWorker> składnika na zakończenie swojego zadania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="354fc-114">The `downloadButton_Click` event handler demonstrates how to wait for a <xref:System.ComponentModel.BackgroundWorker> component to finish its asynchronous task.</span></span>  
  
 <span data-ttu-id="354fc-115">Jeśli tylko aplikacja ma odpowiadanie na zdarzenia i nie chcesz wykonać pracę w głównym wątku podczas oczekiwania na zakończenie wątku tła, po prostu Wyjdź. program obsługi.</span><span class="sxs-lookup"><span data-stu-id="354fc-115">If you only want the application to respond to events and do not want to do any work in the main thread while you wait for the background thread to complete, just exit the handler.</span></span>  
  
 <span data-ttu-id="354fc-116">Jeśli chcesz kontynuować pracę w głównym wątku, użyj <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> umożliwia określenie, czy <xref:System.ComponentModel.BackgroundWorker> wątku jest nadal uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="354fc-116">If you want to continue doing work in the main thread, use the <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> property to determine whether the <xref:System.ComponentModel.BackgroundWorker> thread is still running.</span></span> <span data-ttu-id="354fc-117">W tym przykładzie paska postępu jest aktualizowany podczas przetwarzania pobierania.</span><span class="sxs-lookup"><span data-stu-id="354fc-117">In the example, a progress bar is updated while the download is processing.</span></span> <span data-ttu-id="354fc-118">Pamiętaj wywołać <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> Metoda aktualizowania reakcji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="354fc-118">Be sure to call the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method to keep the UI responsive.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 <span data-ttu-id="354fc-119">**Wyświetlanie wyników**</span><span class="sxs-lookup"><span data-stu-id="354fc-119">**Displaying the result**</span></span>  
  
 <span data-ttu-id="354fc-120">`backgroundWorker1_RunWorkerCompleted` Dojścia metody <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń i jest wywoływana po wykonaniu operacji w tle.</span><span class="sxs-lookup"><span data-stu-id="354fc-120">The `backgroundWorker1_RunWorkerCompleted` method handles the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event and is called when the background operation is completed.</span></span> <span data-ttu-id="354fc-121">Ta metoda sprawdza najpierw <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="354fc-121">This method first checks the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="354fc-122">Jeśli <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> jest `null`, a następnie ta metoda Wyświetla zawartość pliku.</span><span class="sxs-lookup"><span data-stu-id="354fc-122">If <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> is `null`, then this method displays the contents of the file.</span></span> <span data-ttu-id="354fc-123">Następnie włącza przycisk pobierania, który został wyłączony w momencie rozpoczęcia pobierania, oraz resetuje pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="354fc-123">It then enables the download button, which was disabled when the download began, and it resets the progress bar.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="354fc-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="354fc-124">Compiling the Code</span></span>  
 <span data-ttu-id="354fc-125">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="354fc-125">This example requires:</span></span>  
  
-   <span data-ttu-id="354fc-126">Odwołania do zestawów System.Xml, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="354fc-126">References to the System.Drawing, System.Windows.Forms, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="354fc-127">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="354fc-127">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="354fc-128">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="354fc-128">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="354fc-129">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="354fc-129">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="354fc-130">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="354fc-130">Robust Programming</span></span>  
 <span data-ttu-id="354fc-131">Zawsze sprawdzaj <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> właściwości w Twojej <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obsługi zdarzeń przed podjęciem próby uzyskania dostępu <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> właściwości lub inny obiekt, który może mieć wpływ <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="354fc-131">Always check the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property in your <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler before attempting to access the <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> property or any other object that may have been affected by the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="354fc-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="354fc-132">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [<span data-ttu-id="354fc-133">Porady: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="354fc-133">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="354fc-134">Porady: Implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="354fc-134">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
