---
title: 'Wskazówki: przeprowadzanie operacji w tle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
ms.openlocfilehash: 09019f24248985c0a1057873f0226ee69a30ca9d
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254757"
---
# <a name="walkthrough-running-an-operation-in-the-background"></a><span data-ttu-id="ccda2-102">Wskazówki: przeprowadzanie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="ccda2-102">Walkthrough: Running an Operation in the Background</span></span>
<span data-ttu-id="ccda2-103">Jeśli operacja, która będzie zająć dużo czasu, i nie chcesz powodować opóźnienia w interfejsie użytkownika, możesz użyć <xref:System.ComponentModel.BackgroundWorker> klasy, aby uruchomić operację na inny wątek.</span><span class="sxs-lookup"><span data-stu-id="ccda2-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="ccda2-104">Aby uzyskać pełną listę kod używany w tym przykładzie, zobacz [porady: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="ccda2-104">For a complete listing of the code used in this example, see [How to: Run an Operation in the Background](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ccda2-105">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="ccda2-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ccda2-106">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="ccda2-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ccda2-107">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="ccda2-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-run-an-operation-in-the-background"></a><span data-ttu-id="ccda2-108">Uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="ccda2-108">To run an operation in the background</span></span>  
  
1.  <span data-ttu-id="ccda2-109">Za pomocą formularza aktywny w Windows Forms Designer, przeciągnij dwa <xref:System.Windows.Forms.Button> kontrolki z **przybornika** do formularza, a następnie ustaw `Name` i <xref:System.Windows.Forms.Control.Text%2A> właściwości przycisków zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="ccda2-109">With your form active in the Windows Forms Designer, drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to the form, and then set the `Name` and <xref:System.Windows.Forms.Control.Text%2A> properties of the buttons according to the following table.</span></span>  
  
    |<span data-ttu-id="ccda2-110">Przycisk</span><span class="sxs-lookup"><span data-stu-id="ccda2-110">Button</span></span>|<span data-ttu-id="ccda2-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ccda2-111">Name</span></span>|<span data-ttu-id="ccda2-112">Tekst</span><span class="sxs-lookup"><span data-stu-id="ccda2-112">Text</span></span>|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|<span data-ttu-id="ccda2-113">**Start**</span><span class="sxs-lookup"><span data-stu-id="ccda2-113">**Start**</span></span>|  
    |`button2`|`cancelBtn`|<span data-ttu-id="ccda2-114">**Anulowanie**</span><span class="sxs-lookup"><span data-stu-id="ccda2-114">**Cancel**</span></span>|  
  
2.  <span data-ttu-id="ccda2-115">Otwórz **przybornika**, kliknij przycisk **składniki** kartę, a następnie przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="ccda2-115">Open the **Toolbox**, click the **Components** tab, and then drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span>  
  
     <span data-ttu-id="ccda2-116">`backgroundWorker1` Składnika, który pojawia się w **zasobniku składnika**.</span><span class="sxs-lookup"><span data-stu-id="ccda2-116">The `backgroundWorker1` component appears in the **Component Tray**.</span></span>  
  
3.  <span data-ttu-id="ccda2-117">W **właściwości** oknie <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="ccda2-117">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> property to `true`.</span></span>  
  
4.  <span data-ttu-id="ccda2-118">W **właściwości** okna, kliknij pozycję **zdarzenia** przycisk, a następnie kliknij dwukrotnie <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń, aby utworzyć procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ccda2-118">In the **Properties** window, click on the **Events** button, and then double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span>  
  
5.  <span data-ttu-id="ccda2-119">Wstaw kod czasochłonne do <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ccda2-119">Insert your time-consuming code into the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
6.  <span data-ttu-id="ccda2-120">Wyodrębnij wszystkie parametry wymagane przez operację z <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs> parametru.</span><span class="sxs-lookup"><span data-stu-id="ccda2-120">Extract any parameters required by the operation from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs> parameter.</span></span>  
  
7.  <span data-ttu-id="ccda2-121">Przypisz wynik obliczeń, aby <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="ccda2-121">Assign the result of the computation to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span>  
  
     <span data-ttu-id="ccda2-122">To jest dostępne <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ccda2-122">This is will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  <span data-ttu-id="ccda2-123">Wstawianie kodu do pobierania wyników operacji w <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ccda2-123">Insert code for retrieving the result of your operation in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. <span data-ttu-id="ccda2-124">Implementowanie `TimeConsumingOperation` metody.</span><span class="sxs-lookup"><span data-stu-id="ccda2-124">Implement the `TimeConsumingOperation` method.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="ccda2-125">W Windows Forms Designer, kliknij dwukrotnie `startButton` utworzyć <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ccda2-125">In the Windows Forms Designer, double-click `startButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
11. <span data-ttu-id="ccda2-126">Wywołaj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in Class metoda <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla `startButton`.</span><span class="sxs-lookup"><span data-stu-id="ccda2-126">Call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `startButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. <span data-ttu-id="ccda2-127">W Windows Forms Designer, kliknij dwukrotnie `cancelButton` utworzyć <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ccda2-127">In the Windows Forms Designer, double-click `cancelButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
13. <span data-ttu-id="ccda2-128">Wywołaj <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in Class metoda <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="ccda2-128">Call the <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `cancelButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. <span data-ttu-id="ccda2-129">W górnej części pliku zaimportuj przestrzenie nazw System.ComponentModel i System.Threading.</span><span class="sxs-lookup"><span data-stu-id="ccda2-129">At the top of the file, import the System.ComponentModel and System.Threading namespaces.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. <span data-ttu-id="ccda2-130">Naciśnij klawisz F6, aby skompilować rozwiązanie, a następnie naciśnij kombinację klawiszy CTRL-F5, aby uruchomić aplikację poza debugerem.</span><span class="sxs-lookup"><span data-stu-id="ccda2-130">Press F6 to build the solution, and then press CTRL-F5 to run the application outside the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ccda2-131">Jeśli użytkownik naciśnie klawisz F5, aby uruchomić aplikację w debugerze, wyjątek zgłoszony w `TimeConsumingOperation` metoda jest przechwycony i wyświetlane przez debuger.</span><span class="sxs-lookup"><span data-stu-id="ccda2-131">If you press F5 to run the application under the debugger, the exception raised in the `TimeConsumingOperation` method is caught and displayed by the debugger.</span></span> <span data-ttu-id="ccda2-132">Po uruchomieniu aplikacji poza debugerem, <xref:System.ComponentModel.BackgroundWorker> obsługuje wyjątek i zapisuje go w pamięci podręcznej <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwość <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="ccda2-132">When you run the application outside the debugger, the <xref:System.ComponentModel.BackgroundWorker> handles the exception and caches it in the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> property of the <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span></span>  
  
1.  <span data-ttu-id="ccda2-133">Kliknij przycisk **Start** przycisk, aby uruchomić operację asynchroniczną, a następnie kliknij przycisk **anulować** przycisk, aby zatrzymać operację pracę asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="ccda2-133">Click the **Start** button to run an asynchronous operation, and then click the **Cancel** button to stop a running asynchronous operation.</span></span>  
  
     <span data-ttu-id="ccda2-134">Wynikiem operacji jest wyświetlana w <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="ccda2-134">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ccda2-135">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ccda2-135">Next Steps</span></span>  
  
-   <span data-ttu-id="ccda2-136">Implementowanie formularza, który zgłasza postępy pracy w trakcie wykonywania operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ccda2-136">Implement a form that reports progress as an asynchronous operation proceeds.</span></span> <span data-ttu-id="ccda2-137">Aby uzyskać więcej informacji, zobacz [porady: Implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="ccda2-137">For more information, see [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
-   <span data-ttu-id="ccda2-138">Implementuje klasę, która obsługuje wzorca asynchronicznego dla składników.</span><span class="sxs-lookup"><span data-stu-id="ccda2-138">Implement a class that supports the Asynchronous Pattern for Components.</span></span> <span data-ttu-id="ccda2-139">Aby uzyskać więcej informacji, zobacz [implementacja wzorca asynchronicznego opartego na zdarzeniach](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="ccda2-139">For more information, see [Implementing the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccda2-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccda2-140">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="ccda2-141">Instrukcje: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="ccda2-141">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="ccda2-142">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="ccda2-142">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="ccda2-143">BackgroundWorker, składnik</span><span class="sxs-lookup"><span data-stu-id="ccda2-143">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
