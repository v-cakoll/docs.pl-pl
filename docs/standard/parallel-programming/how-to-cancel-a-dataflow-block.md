---
title: 'Porady: Anulowanie bloku przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
ms.openlocfilehash: aa175d95f27fcbf28c3f3da3eaa7b8f7988681e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140094"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="70ec8-102">Porady: Anulowanie bloku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="70ec8-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="70ec8-103">W tym dokumencie pokazano, jak włączyć anulowanie w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70ec8-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="70ec8-104">W tym przykładzie użyto formularzy systemu Windows, aby pokazać, gdzie elementy robocze są aktywne w potoku przepływu danych, a także skutki anulowania.</span><span class="sxs-lookup"><span data-stu-id="70ec8-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="70ec8-105">Aby utworzyć aplikację formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="70ec8-105">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="70ec8-106">Utwórz projekt aplikacji **formularzy systemu** Windows w języku C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="70ec8-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="70ec8-107">W poniższych krokach projekt `CancellationWinForms`nosi nazwę .</span><span class="sxs-lookup"><span data-stu-id="70ec8-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2. <span data-ttu-id="70ec8-108">W projektancie formularza dla formularza głównego Form1.cs (Form1.vb <xref:System.Windows.Forms.ToolStrip> dla języka Visual Basic) dodaj formant.</span><span class="sxs-lookup"><span data-stu-id="70ec8-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="70ec8-109">Dodaj <xref:System.Windows.Forms.ToolStripButton> formant do <xref:System.Windows.Forms.ToolStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="70ec8-110">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwość <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwość, aby **dodać elementy robocze**.</span><span class="sxs-lookup"><span data-stu-id="70ec8-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4. <span data-ttu-id="70ec8-111">Dodaj drugi <xref:System.Windows.Forms.ToolStripButton> formant <xref:System.Windows.Forms.ToolStrip> do formantu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="70ec8-112">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwość <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>na <xref:System.Windows.Forms.ToolStripItem.Text%2A> , właściwość **Anuluj**, a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> właściwość na `False`.</span><span class="sxs-lookup"><span data-stu-id="70ec8-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="70ec8-113">Dodaj <xref:System.Windows.Forms.ToolStripProgressBar> cztery obiekty <xref:System.Windows.Forms.ToolStrip> do formantu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="70ec8-114">Tworzenie potoku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="70ec8-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="70ec8-115">W tej sekcji opisano sposób tworzenia potoku przepływu danych, który przetwarza elementy robocze i aktualizuje paski postępu.</span><span class="sxs-lookup"><span data-stu-id="70ec8-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="70ec8-116">Aby utworzyć potok przepływu danych</span><span class="sxs-lookup"><span data-stu-id="70ec8-116">To Create the Dataflow Pipeline</span></span>  
  
1. <span data-ttu-id="70ec8-117">W projekcie dodaj odwołanie do pliku System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="70ec8-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="70ec8-118">Upewnij się, że Form1.cs (Form1.vb `using` dla`Imports` języka Visual Basic) zawiera następujące instrukcje (w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="70ec8-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. <span data-ttu-id="70ec8-119">Dodaj `WorkItem` klasę jako wewnętrzny typ `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="70ec8-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. <span data-ttu-id="70ec8-120">Dodaj następujące elementy członkowskie `Form1` danych do klasy.</span><span class="sxs-lookup"><span data-stu-id="70ec8-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. <span data-ttu-id="70ec8-121">Dodaj następującą `CreatePipeline`metodę, `Form1` , do klasy.</span><span class="sxs-lookup"><span data-stu-id="70ec8-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="70ec8-122">Ponieważ `incrementProgress` bloki przepływu `decrementProgress` danych działają na interfejsie użytkownika, ważne jest, aby te akcje wystąpiły w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="70ec8-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="70ec8-123">Aby to osiągnąć, podczas budowy <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> te obiekty <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> każdy podać <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>obiekt, który ma właściwość ustawioną na .</span><span class="sxs-lookup"><span data-stu-id="70ec8-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="70ec8-124">Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> tworzy <xref:System.Threading.Tasks.TaskScheduler> obiekt, który wykonuje pracę na bieżącym kontekście synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="70ec8-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="70ec8-125">Ponieważ `Form1` konstruktor jest wywoływana z wątku `incrementProgress` interfejsu `decrementProgress` użytkownika, akcje dla bloków i przepływu danych również uruchomić w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="70ec8-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="70ec8-126">W tym <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> przykładzie ustawia właściwość, gdy konstruuje elementy członkowskie potoku.</span><span class="sxs-lookup"><span data-stu-id="70ec8-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="70ec8-127">Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwość trwale anuluje wykonanie bloku przepływu danych, cały potok musi zostać utworzony ponownie po użytkownik anuluje operację, a następnie chce dodać więcej elementów roboczych do potoku.</span><span class="sxs-lookup"><span data-stu-id="70ec8-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="70ec8-128">Na przykład, który pokazuje alternatywny sposób anulowania bloku przepływu danych, dzięki czemu można wykonać inną pracę po anulowaniu operacji, zobacz [Instruktaż: Korzystanie z przepływu danych w aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="70ec8-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="70ec8-129">Podłączanie potoku przepływu danych do interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="70ec8-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="70ec8-130">W tej sekcji opisano sposób łączenia potoku przepływu danych z interfejsem użytkownika.</span><span class="sxs-lookup"><span data-stu-id="70ec8-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="70ec8-131">Zarówno tworzenie potoku, jak i dodawanie elementów roboczych do potoku są kontrolowane przez program obsługi zdarzeń dla przycisku **Dodaj elementy robocze.**</span><span class="sxs-lookup"><span data-stu-id="70ec8-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="70ec8-132">Anulowanie jest inicjowane przez przycisk **Anuluj.**</span><span class="sxs-lookup"><span data-stu-id="70ec8-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="70ec8-133">Gdy użytkownik kliknie jeden z tych przycisków, odpowiednia akcja jest inicjowana w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="70ec8-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="70ec8-134">Aby połączyć potok przepływu danych z interfejsem użytkownika</span><span class="sxs-lookup"><span data-stu-id="70ec8-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1. <span data-ttu-id="70ec8-135">W projektancie formularza dla formularza głównego utwórz program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla przycisku Dodaj elementy **robocze.**</span><span class="sxs-lookup"><span data-stu-id="70ec8-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2. <span data-ttu-id="70ec8-136">Zaimplementuj <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie dla przycisku **Dodaj elementy robocze.**</span><span class="sxs-lookup"><span data-stu-id="70ec8-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. <span data-ttu-id="70ec8-137">W projektancie formularza dla formularza głównego utwórz program obsługi zdarzeń dla programu obsługi <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń dla przycisku **Anuluj.**</span><span class="sxs-lookup"><span data-stu-id="70ec8-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="70ec8-138">Zaimplementuj program <xref:System.Windows.Forms.ToolStripItem.Click> obsługi zdarzeń dla przycisku **Anuluj.**</span><span class="sxs-lookup"><span data-stu-id="70ec8-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="70ec8-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="70ec8-139">Example</span></span>  
 <span data-ttu-id="70ec8-140">W poniższym przykładzie przedstawiono kompletny kod Form1.cs (Form1.vb dla języka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="70ec8-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="70ec8-141">Na poniższej ilustracji przedstawiono uruchomioną aplikację.</span><span class="sxs-lookup"><span data-stu-id="70ec8-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="70ec8-142">![Aplikacja formularzy systemu Windows](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="70ec8-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="70ec8-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70ec8-143">See also</span></span>

- [<span data-ttu-id="70ec8-144">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="70ec8-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
