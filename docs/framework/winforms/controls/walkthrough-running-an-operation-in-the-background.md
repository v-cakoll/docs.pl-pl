---
title: "Wskazówki: przeprowadzanie operacji w tle"
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
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9be47fd57e49973c0f77a069c4f3371e4f63194
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-running-an-operation-in-the-background"></a><span data-ttu-id="17457-102">Wskazówki: przeprowadzanie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="17457-102">Walkthrough: Running an Operation in the Background</span></span>
<span data-ttu-id="17457-103">Jeśli masz operacji potrwa długo, i nie chcesz powodować opóźnienia w interfejsie użytkownika, można użyć <xref:System.ComponentModel.BackgroundWorker> klasę, aby uruchomić operację w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="17457-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="17457-104">Aby uzyskać pełną listę kod używany w tym przykładzie, zobacz [porady: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="17457-104">For a complete listing of the code used in this example, see [How to: Run an Operation in the Background](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17457-105">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="17457-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="17457-106">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="17457-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="17457-107">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="17457-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-run-an-operation-in-the-background"></a><span data-ttu-id="17457-108">Uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="17457-108">To run an operation in the background</span></span>  
  
1.  <span data-ttu-id="17457-109">Formularz aktywne w narzędziu Projektant dla formularzy systemu Windows, przeciągnij dwa <xref:System.Windows.Forms.Button> formantów **przybornika** do formularza, a następnie ustawić `Name` i <xref:System.Windows.Forms.Control.Text%2A> właściwości przycisków zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="17457-109">With your form active in the Windows Forms Designer, drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to the form, and then set the `Name` and <xref:System.Windows.Forms.Control.Text%2A> properties of the buttons according to the following table.</span></span>  
  
    |<span data-ttu-id="17457-110">Przycisk</span><span class="sxs-lookup"><span data-stu-id="17457-110">Button</span></span>|<span data-ttu-id="17457-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="17457-111">Name</span></span>|<span data-ttu-id="17457-112">Tekst</span><span class="sxs-lookup"><span data-stu-id="17457-112">Text</span></span>|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|<span data-ttu-id="17457-113">**Start**</span><span class="sxs-lookup"><span data-stu-id="17457-113">**Start**</span></span>|  
    |`button2`|`cancelBtn`|<span data-ttu-id="17457-114">**Anuluj**</span><span class="sxs-lookup"><span data-stu-id="17457-114">**Cancel**</span></span>|  
  
2.  <span data-ttu-id="17457-115">Otwórz **przybornika**, kliknij przycisk **składniki** karcie, a następnie przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="17457-115">Open the **Toolbox**, click the **Components** tab, and then drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span>  
  
     <span data-ttu-id="17457-116">`backgroundWorker1` Składnika jest wyświetlana w **zasobnik składnika**.</span><span class="sxs-lookup"><span data-stu-id="17457-116">The `backgroundWorker1` component appears in the **Component Tray**.</span></span>  
  
3.  <span data-ttu-id="17457-117">W **właściwości** ustaw <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="17457-117">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> property to `true`.</span></span>  
  
4.  <span data-ttu-id="17457-118">W **właściwości** kliknij na **zdarzenia** przycisk, a następnie kliknij dwukrotnie <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzenia można utworzyć procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17457-118">In the **Properties** window, click on the **Events** button, and then double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span>  
  
5.  <span data-ttu-id="17457-119">Wstaw kod czasochłonne do <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17457-119">Insert your time-consuming code into the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
6.  <span data-ttu-id="17457-120">Wyodrębnij wszystkie parametry wymagane przez operację z <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs> parametru.</span><span class="sxs-lookup"><span data-stu-id="17457-120">Extract any parameters required by the operation from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs> parameter.</span></span>  
  
7.  <span data-ttu-id="17457-121">Przypisz wynik do obliczenia <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="17457-121">Assign the result of the computation to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span>  
  
     <span data-ttu-id="17457-122">Jest to będzie dostępna do <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17457-122">This is will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  <span data-ttu-id="17457-123">Wstawianie kodu do pobierania wyników operacji w <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17457-123">Insert code for retrieving the result of your operation in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. <span data-ttu-id="17457-124">Implementowanie `TimeConsumingOperation` metody.</span><span class="sxs-lookup"><span data-stu-id="17457-124">Implement the `TimeConsumingOperation` method.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="17457-125">W narzędziu Projektant dla formularzy systemu Windows, kliknij dwukrotnie `startButton` utworzyć <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17457-125">In the Windows Forms Designer, double-click `startButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
11. <span data-ttu-id="17457-126">Wywołanie <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody w <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `startButton`.</span><span class="sxs-lookup"><span data-stu-id="17457-126">Call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `startButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. <span data-ttu-id="17457-127">W narzędziu Projektant dla formularzy systemu Windows, kliknij dwukrotnie `cancelButton` utworzyć <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17457-127">In the Windows Forms Designer, double-click `cancelButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
13. <span data-ttu-id="17457-128">Wywołanie <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody w <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="17457-128">Call the <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `cancelButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. <span data-ttu-id="17457-129">W górnej części pliku należy zaimportować System.ComponentModel i System.Threading przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="17457-129">At the top of the file, import the System.ComponentModel and System.Threading namespaces.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. <span data-ttu-id="17457-130">Naciśnij klawisz F6 w celu skompilowania rozwiązania, a następnie naciśnij klawisz CTRL-F5, aby uruchomić aplikację poza debugerem.</span><span class="sxs-lookup"><span data-stu-id="17457-130">Press F6 to build the solution, and then press CTRL-F5 to run the application outside the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17457-131">Jeśli użytkownik naciśnie klawisz F5, aby uruchomić aplikację w debugerze, wyjątek w `TimeConsumingOperation` metoda przechwycony i wyświetlane przez debuger.</span><span class="sxs-lookup"><span data-stu-id="17457-131">If you press F5 to run the application under the debugger, the exception raised in the `TimeConsumingOperation` method is caught and displayed by the debugger.</span></span> <span data-ttu-id="17457-132">Po uruchomieniu aplikacji poza debugerem, <xref:System.ComponentModel.BackgroundWorker> obsługuje wyjątek i buforuje ją w <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwość <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="17457-132">When you run the application outside the debugger, the <xref:System.ComponentModel.BackgroundWorker> handles the exception and caches it in the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> property of the <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span></span>  
  
1.  <span data-ttu-id="17457-133">Kliknij przycisk **Start** przycisk, aby uruchomić operację asynchroniczną, a następnie kliknij przycisk **anulować** przycisk, aby zatrzymać operację uruchomiona asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="17457-133">Click the **Start** button to run an asynchronous operation, and then click the **Cancel** button to stop a running asynchronous operation.</span></span>  
  
     <span data-ttu-id="17457-134">Wynik każdej operacji jest wyświetlany w <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="17457-134">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="17457-135">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="17457-135">Next Steps</span></span>  
  
-   <span data-ttu-id="17457-136">Implementowanie formularza, który zgłasza postęp w trakcie wykonywania operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="17457-136">Implement a form that reports progress as an asynchronous operation proceeds.</span></span> <span data-ttu-id="17457-137">Aby uzyskać więcej informacji, zobacz [porady: Implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="17457-137">For more information, see [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
-   <span data-ttu-id="17457-138">Implementuje klasę, która obsługuje wzorca asynchronicznego dla składników.</span><span class="sxs-lookup"><span data-stu-id="17457-138">Implement a class that supports the Asynchronous Pattern for Components.</span></span> <span data-ttu-id="17457-139">Aby uzyskać więcej informacji, zobacz [implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="17457-139">For more information, see [Implementing the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17457-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17457-140">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="17457-141">Instrukcje: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="17457-141">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="17457-142">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="17457-142">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="17457-143">BackgroundWorker, składnik</span><span class="sxs-lookup"><span data-stu-id="17457-143">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
