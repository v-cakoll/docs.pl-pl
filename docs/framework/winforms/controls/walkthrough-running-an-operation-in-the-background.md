---
title: 'Przewodnik: uruchamianie operacji w tle'
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
ms.openlocfilehash: 6c705c6d6ff9bbd233bbddc3a73acf8aca13a547
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211525"
---
# <a name="walkthrough-running-an-operation-in-the-background"></a><span data-ttu-id="a3d2f-102">Przewodnik: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="a3d2f-102">Walkthrough: Running an Operation in the Background</span></span>

<span data-ttu-id="a3d2f-103">Jeśli operacja, która będzie zająć dużo czasu, i nie chcesz powodować opóźnienia w interfejsie użytkownika, możesz użyć <xref:System.ComponentModel.BackgroundWorker> klasy, aby uruchomić operację na inny wątek.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>

<span data-ttu-id="a3d2f-104">Aby uzyskać pełną listę kod używany w tym przykładzie, zobacz [jak: Uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="a3d2f-104">For a complete listing of the code used in this example, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>

## <a name="run-an-operation-in-the-background"></a><span data-ttu-id="a3d2f-105">Uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="a3d2f-105">Run an operation in the background</span></span>

1. <span data-ttu-id="a3d2f-106">Za pomocą formularza aktywny w Windows Forms Designer w programie Visual Studio, przeciągnij dwa <xref:System.Windows.Forms.Button> kontrolki z **przybornika** do formularza, a następnie ustaw `Name` i <xref:System.Windows.Forms.Control.Text%2A> właściwości przycisków zgodnie z opisem w Poniższa tabela.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-106">With your form active in the Windows Forms Designer in Visual Studio, drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to the form, and then set the `Name` and <xref:System.Windows.Forms.Control.Text%2A> properties of the buttons according to the following table.</span></span>

    |<span data-ttu-id="a3d2f-107">Przycisk</span><span class="sxs-lookup"><span data-stu-id="a3d2f-107">Button</span></span>|<span data-ttu-id="a3d2f-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a3d2f-108">Name</span></span>|<span data-ttu-id="a3d2f-109">Tekst</span><span class="sxs-lookup"><span data-stu-id="a3d2f-109">Text</span></span>|
    |------------|----------|----------|
    |`button1`|`startBtn`|<span data-ttu-id="a3d2f-110">**Start**</span><span class="sxs-lookup"><span data-stu-id="a3d2f-110">**Start**</span></span>|
    |`button2`|`cancelBtn`|<span data-ttu-id="a3d2f-111">**Anulowanie**</span><span class="sxs-lookup"><span data-stu-id="a3d2f-111">**Cancel**</span></span>|

2. <span data-ttu-id="a3d2f-112">Otwórz **przybornika**, kliknij przycisk **składniki** kartę, a następnie przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-112">Open the **Toolbox**, click the **Components** tab, and then drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span>

     <span data-ttu-id="a3d2f-113">`backgroundWorker1` Składnika, który pojawia się w **zasobniku składnika**.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-113">The `backgroundWorker1` component appears in the **Component Tray**.</span></span>

3. <span data-ttu-id="a3d2f-114">W oknie **Właściwości** ustaw właściwość <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> na `true`. </span><span class="sxs-lookup"><span data-stu-id="a3d2f-114">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> property to `true`.</span></span>

4. <span data-ttu-id="a3d2f-115">W **właściwości** okna, kliknij pozycję **zdarzenia** przycisk, a następnie kliknij dwukrotnie <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń, aby utworzyć procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-115">In the **Properties** window, click on the **Events** button, and then double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span>

5. <span data-ttu-id="a3d2f-116">Wstaw kod czasochłonne do <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-116">Insert your time-consuming code into the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>

6. <span data-ttu-id="a3d2f-117">Wyodrębnij wszystkie parametry wymagane przez operację z <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs> parametru.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-117">Extract any parameters required by the operation from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs> parameter.</span></span>

7. <span data-ttu-id="a3d2f-118">Przypisz wynik obliczeń, aby <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-118">Assign the result of the computation to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span>

     <span data-ttu-id="a3d2f-119">To jest dostępne <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-119">This is will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]

8. <span data-ttu-id="a3d2f-120">Wstawianie kodu do pobierania wyników operacji w <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-120">Insert code for retrieving the result of your operation in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]

9. <span data-ttu-id="a3d2f-121">Implementowanie `TimeConsumingOperation` metody.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-121">Implement the `TimeConsumingOperation` method.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]

10. <span data-ttu-id="a3d2f-122">W Windows Forms Designer, kliknij dwukrotnie `startButton` utworzyć <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-122">In the Windows Forms Designer, double-click `startButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>

11. <span data-ttu-id="a3d2f-123">Wywołaj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in Class metoda <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla `startButton`.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-123">Call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `startButton`.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]

12. <span data-ttu-id="a3d2f-124">W Windows Forms Designer, kliknij dwukrotnie `cancelButton` utworzyć <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-124">In the Windows Forms Designer, double-click `cancelButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>

13. <span data-ttu-id="a3d2f-125">Wywołaj <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in Class metoda <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-125">Call the <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `cancelButton`.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]

14. <span data-ttu-id="a3d2f-126">W górnej części pliku zaimportuj przestrzenie nazw System.ComponentModel i System.Threading.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-126">At the top of the file, import the System.ComponentModel and System.Threading namespaces.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]

15. <span data-ttu-id="a3d2f-127">Naciśnij klawisz **F6** Skompiluj rozwiązanie, a następnie naciśnij klawisz **Ctrl**+**F5** do uruchamiania aplikacji poza debugerem.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-127">Press **F6** to build the solution, and then press **Ctrl**+**F5** to run the application outside the debugger.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a3d2f-128">Jeśli użytkownik naciśnie klawisz **F5** do uruchamiania aplikacji w debugerze, wyjątek zgłoszony w `TimeConsumingOperation` metoda jest przechwycony i wyświetlane przez debuger.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-128">If you press **F5** to run the application under the debugger, the exception raised in the `TimeConsumingOperation` method is caught and displayed by the debugger.</span></span> <span data-ttu-id="a3d2f-129">Po uruchomieniu aplikacji poza debugerem, <xref:System.ComponentModel.BackgroundWorker> obsługuje wyjątek i zapisuje go w pamięci podręcznej <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwość <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-129">When you run the application outside the debugger, the <xref:System.ComponentModel.BackgroundWorker> handles the exception and caches it in the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> property of the <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span></span>

16. <span data-ttu-id="a3d2f-130">Kliknij przycisk **Start** przycisk, aby uruchomić operację asynchroniczną, a następnie kliknij przycisk **anulować** przycisk, aby zatrzymać operację pracę asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-130">Click the **Start** button to run an asynchronous operation, and then click the **Cancel** button to stop a running asynchronous operation.</span></span>

     <span data-ttu-id="a3d2f-131">Wynikiem operacji jest wyświetlana w <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-131">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a3d2f-132">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a3d2f-132">Next steps</span></span>

- <span data-ttu-id="a3d2f-133">Implementowanie formularza, który zgłasza postępy pracy w trakcie wykonywania operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-133">Implement a form that reports progress as an asynchronous operation proceeds.</span></span> <span data-ttu-id="a3d2f-134">Aby uzyskać więcej informacji, zobacz [jak: Implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="a3d2f-134">For more information, see [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>

- <span data-ttu-id="a3d2f-135">Implementuje klasę, która obsługuje wzorca asynchronicznego dla składników.</span><span class="sxs-lookup"><span data-stu-id="a3d2f-135">Implement a class that supports the Asynchronous Pattern for Components.</span></span> <span data-ttu-id="a3d2f-136">Aby uzyskać więcej informacji, zobacz [implementacja wzorca asynchronicznego opartego na zdarzeniach](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="a3d2f-136">For more information, see [Implementing the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a3d2f-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3d2f-137">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="a3d2f-138">Instrukcje: Implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="a3d2f-138">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="a3d2f-139">Instrukcje: Uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="a3d2f-139">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="a3d2f-140">BackgroundWorker, składnik</span><span class="sxs-lookup"><span data-stu-id="a3d2f-140">BackgroundWorker Component</span></span>](backgroundworker-component.md)
