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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2684473f82eb156bf8762c9797503324f318632d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584908"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="e8ff5-102">Porady: Anulowanie bloku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="e8ff5-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="e8ff5-103">Ten dokument pokazano, jak włączyć anulowania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="e8ff5-104">W tym przykładzie użyto formularzy systemu Windows do wyświetlenia, gdy elementy robocze są aktywne w potoku przepływu danych, a także skutków anulowania.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="e8ff5-105">Aby utworzyć systemu Windows w aplikacjach formularzy</span><span class="sxs-lookup"><span data-stu-id="e8ff5-105">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="e8ff5-106">Tworzenie C# lub Visual Basic **aplikacji Windows Forms** projektu.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="e8ff5-107">W poniższych krokach projektu o nazwie `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2.  <span data-ttu-id="e8ff5-108">Projektant formularzy dla tego formularza, pliku Form1.cs (Form1.vb w języku Visual Basic), Dodaj <xref:System.Windows.Forms.ToolStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="e8ff5-109">Dodaj <xref:System.Windows.Forms.ToolStripButton> formant <xref:System.Windows.Forms.ToolStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="e8ff5-110">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **dodać elementy robocze**.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4.  <span data-ttu-id="e8ff5-111">Dodaj drugi <xref:System.Windows.Forms.ToolStripButton> formant <xref:System.Windows.Forms.ToolStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="e8ff5-112">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **anulować**i <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> właściwości `False`.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="e8ff5-113">Dodaj cztery <xref:System.Windows.Forms.ToolStripProgressBar> obiekty do <xref:System.Windows.Forms.ToolStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="e8ff5-114">Tworzenie potoku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="e8ff5-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="e8ff5-115">Ta sekcja zawiera opis sposobu tworzenia potoku przepływu danych, która przetwarza elementy robocze i aktualizuje paski postępu.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="e8ff5-116">Do utworzenia potoku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="e8ff5-116">To Create the Dataflow Pipeline</span></span>  
  
1.  <span data-ttu-id="e8ff5-117">W projekcie Dodaj odwołanie do System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="e8ff5-118">Upewnij się, że pliku Form1.cs (Form1.vb w języku Visual Basic) zawiera następujące `using` instrukcje (`Imports` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e8ff5-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="e8ff5-119">Dodaj `WorkItem` klasy jako wewnętrzny typ `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="e8ff5-120">Dodaj następujące elementy członkowskie danych, aby `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="e8ff5-121">Dodaj następującą metodę `CreatePipeline`, do `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="e8ff5-122">Ponieważ `incrementProgress` i `decrementProgress` przepływu danych bloki działania w interfejsie użytkownika, ważne jest, że te zdarzenia w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="e8ff5-123">Aby to zrobić, podczas konstruowania te obiekty każdego podaj <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiektu, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> ustawioną właściwość <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e8ff5-124"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiekt, który przeprowadza pracę na bieżący kontekst synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="e8ff5-125">Ponieważ `Form1` Konstruktor jest wywoływana z wątku interfejsu użytkownika, akcje `incrementProgress` i `decrementProgress` bloków przepływu danych również uruchomić w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="e8ff5-126">W tym przykładzie <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwości, gdy tworzy on elementy członkowskie potoku.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="e8ff5-127">Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwości trwale anuluje wykonywania bloku przepływu danych, całe potoku muszą zostać ponownie utworzone po użytkownik anulował operację i chce dodać więcej elementów roboczych do potoku.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="e8ff5-128">Na przykład, który pokazuje alternatywny sposób anulowanie bloku przepływu danych, dzięki czemu inne zadania mogą być wykonywane po operacja została anulowana, zobacz [wskazówki: Korzystanie z przepływu danych w aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="e8ff5-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="e8ff5-129">Połączenie potoku przepływu danych interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e8ff5-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="e8ff5-130">W tej sekcji opisano sposób podłączania potoku przepływu danych interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="e8ff5-131">Tworzenie potoku, a także dodawanie elementów roboczych do potoku są kontrolowane przez program obsługi zdarzeń dla **dodać elementy robocze** przycisku.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="e8ff5-132">Anulowanie jest inicjowane przez **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="e8ff5-133">Gdy użytkownik kliknie jeden z tych przycisków, odpowiednie działanie jest inicjowane w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="e8ff5-134">Aby połączyć potoku przepływu danych interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e8ff5-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1.  <span data-ttu-id="e8ff5-135">W projektancie formularzy dla tego formularza należy utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla **dodać elementy robocze** przycisku.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2.  <span data-ttu-id="e8ff5-136">Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla **dodać elementy robocze** przycisku.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  <span data-ttu-id="e8ff5-137">W projektancie formularzy dla tego formularza należy utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> programu obsługi zdarzeń dla **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="e8ff5-138">Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> programu obsługi zdarzeń dla **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="e8ff5-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8ff5-139">Example</span></span>  
 <span data-ttu-id="e8ff5-140">Poniższy przykład przedstawia kompletny kod dla pliku Form1.cs (Form1.vb w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e8ff5-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="e8ff5-141">Na poniższej ilustracji przedstawiono działającej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="e8ff5-142">![Aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="e8ff5-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="e8ff5-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8ff5-143">See Also</span></span>  
 [<span data-ttu-id="e8ff5-144">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="e8ff5-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
