---
title: 'Instrukcje: Anulowanie bloku przepływu danych'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b95f0a3535716c4a01dae52abe38eb850f080cf0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345199"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="84012-102">Instrukcje: Anulowanie bloku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="84012-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="84012-103">W tym dokumencie pokazano, jak włączyć anulowania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="84012-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="84012-104">W tym przykładzie użyto Windows Forms, aby pokazać, gdzie elementy robocze są aktywne w potoku przepływu danych, a także skutki anulowania.</span><span class="sxs-lookup"><span data-stu-id="84012-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="84012-105">Aby utworzyć Windows Forms aplikacji</span><span class="sxs-lookup"><span data-stu-id="84012-105">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="84012-106">Tworzenie języka C# lub Visual Basic **aplikacja interfejsu Windows Forms** projektu.</span><span class="sxs-lookup"><span data-stu-id="84012-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="84012-107">W poniższych krokach projekt nazwano `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="84012-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2. <span data-ttu-id="84012-108">Projektant formularzy dla tego formularza Form1.cs (Form1.vb dla języka Visual Basic), Dodaj <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="84012-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="84012-109">Dodaj <xref:System.Windows.Forms.ToolStripButton> kontrolę <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="84012-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="84012-110">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **dodać elementy robocze**.</span><span class="sxs-lookup"><span data-stu-id="84012-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4. <span data-ttu-id="84012-111">Dodaj drugą <xref:System.Windows.Forms.ToolStripButton> kontrolę <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="84012-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="84012-112">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **anulować**i <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> właściwość `False`.</span><span class="sxs-lookup"><span data-stu-id="84012-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="84012-113">Dodaj cztery <xref:System.Windows.Forms.ToolStripProgressBar> obiekty do <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="84012-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="84012-114">Tworzenie potoku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="84012-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="84012-115">W tej sekcji opisano tworzenie potoku przepływu danych, która przetwarza elementy robocze i aktualizuje paski postępu.</span><span class="sxs-lookup"><span data-stu-id="84012-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="84012-116">Tworzenie potoku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="84012-116">To Create the Dataflow Pipeline</span></span>  
  
1. <span data-ttu-id="84012-117">W projekcie należy dodać odwołanie do System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="84012-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="84012-118">Upewnij się, że Form1.cs (Form1.vb dla języka Visual Basic) zawiera następujące `using` instrukcji (`Imports` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="84012-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. <span data-ttu-id="84012-119">Dodaj `WorkItem` klasy jako wewnętrzny typ `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="84012-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. <span data-ttu-id="84012-120">Dodaj następujące elementy członkowskie danych do `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="84012-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. <span data-ttu-id="84012-121">Dodaj następującą metodę `CreatePipeline`, `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="84012-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="84012-122">Ponieważ `incrementProgress` i `decrementProgress` przepływu danych blokuje działanie w interfejsie użytkownika, ważne jest, czy w wątku interfejsu użytkownika są wykonywane następujące akcje.</span><span class="sxs-lookup"><span data-stu-id="84012-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="84012-123">Aby to osiągnąć, podczas konstruowania tych obiektów, każda oferuje <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> właściwością <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84012-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="84012-124"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiektu, który wykonuje pracę w bieżącym kontekście synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="84012-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="84012-125">Ponieważ `Form1` Konstruktor jest wywoływana z wątku interfejsu użytkownika, akcje w przypadku `incrementProgress` i `decrementProgress` bloków przepływu danych również działać w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="84012-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="84012-126">W tym przykładzie <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwość podczas jego tworzy elementy członkowskie w potoku.</span><span class="sxs-lookup"><span data-stu-id="84012-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="84012-127">Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwość trwale anuluje wykonanie bloku przepływu danych, cały potok musi zostać ponownie utworzona po użytkownik anuluje operację i chce dodać więcej elementów roboczych do potoku.</span><span class="sxs-lookup"><span data-stu-id="84012-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="84012-128">Aby uzyskać przykład demonstrujący alternatywny sposób anulowanie bloku przepływu danych, dzięki czemu mogą być wykonywane inne prace, po operacji zostało anulowane, zobacz [instruktażu: Korzystanie z przepływu danych w Windows Forms aplikacji](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="84012-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="84012-129">Łączenie potoku przepływu danych z interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="84012-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="84012-130">W tej sekcji opisano sposób podłączania potoku przepływu danych do interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="84012-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="84012-131">Tworzenie potoku i dodawanie elementów roboczych do potoku, które są kontrolowane przez program obsługi zdarzeń dla **dodać elementy robocze** przycisku.</span><span class="sxs-lookup"><span data-stu-id="84012-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="84012-132">Anulowanie jest inicjowane przez **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="84012-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="84012-133">Gdy użytkownik kliknie jeden z tych przycisków, odpowiednie działanie jest inicjowane w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="84012-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="84012-134">Aby połączyć potoku przepływu danych do interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="84012-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1. <span data-ttu-id="84012-135">W Projektancie formularza dla tego formularza, należy utworzyć program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie **dodać elementy robocze** przycisku.</span><span class="sxs-lookup"><span data-stu-id="84012-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2. <span data-ttu-id="84012-136">Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie **dodać elementy robocze** przycisku.</span><span class="sxs-lookup"><span data-stu-id="84012-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. <span data-ttu-id="84012-137">W Projektancie formularza dla tego formularza, należy utworzyć program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> program obsługi zdarzeń dla **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="84012-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="84012-138">Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> program obsługi zdarzeń dla **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="84012-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="84012-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="84012-139">Example</span></span>  
 <span data-ttu-id="84012-140">Poniższy przykład pokazuje kompletny kod dla Form1.cs (Form1.vb dla języka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="84012-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="84012-141">Na poniższej ilustracji przedstawiono uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="84012-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="84012-142">![Windows Forms aplikacji](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="84012-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="84012-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84012-143">See also</span></span>

- [<span data-ttu-id="84012-144">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="84012-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
