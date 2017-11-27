---
title: "Porady: Anulowanie bloku przepływu danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d6fbde31cd4b4b5d0c6404b8baf23230f2bda77
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="0f1df-102">Porady: Anulowanie bloku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="0f1df-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="0f1df-103">Ten dokument pokazano, jak włączyć anulowania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f1df-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="0f1df-104">W tym przykładzie użyto formularzy systemu Windows do wyświetlenia, gdy elementy robocze są aktywne w potoku przepływu danych, a także skutków anulowania.</span><span class="sxs-lookup"><span data-stu-id="0f1df-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="0f1df-105">Biblioteka przepływu danych tpl (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> przestrzeni nazw) nie jest rozpowszechniana z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f1df-105">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="0f1df-106">Aby zainstalować <xref:System.Threading.Tasks.Dataflow> przestrzeni nazw, otwórz projekt w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], wybierz **Zarządzaj pakietami NuGet** z menu projektu i wyszukaj w trybie online `Microsoft.Tpl.Dataflow` pakietu.</span><span class="sxs-lookup"><span data-stu-id="0f1df-106">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="0f1df-107">Aby utworzyć systemu Windows w aplikacjach formularzy</span><span class="sxs-lookup"><span data-stu-id="0f1df-107">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="0f1df-108">Tworzenie C# lub Visual Basic **aplikacji Windows Forms** projektu.</span><span class="sxs-lookup"><span data-stu-id="0f1df-108">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="0f1df-109">W poniższych krokach projektu o nazwie `CancellationWinForms`.</span><span class="sxs-lookup"><span data-stu-id="0f1df-109">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2.  <span data-ttu-id="0f1df-110">W formularzu projektanta dla tego formularza, pliku Form1.cs (Form1.vb dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), Dodaj <xref:System.Windows.Forms.ToolStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="0f1df-110">On the form designer for the main form, Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="0f1df-111">Dodaj <xref:System.Windows.Forms.ToolStripButton> formant <xref:System.Windows.Forms.ToolStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="0f1df-111">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="0f1df-112">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **dodać elementy robocze**.</span><span class="sxs-lookup"><span data-stu-id="0f1df-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4.  <span data-ttu-id="0f1df-113">Dodaj drugi <xref:System.Windows.Forms.ToolStripButton> formant <xref:System.Windows.Forms.ToolStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="0f1df-113">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="0f1df-114">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **anulować**i <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> właściwości `False`.</span><span class="sxs-lookup"><span data-stu-id="0f1df-114">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="0f1df-115">Dodaj cztery <xref:System.Windows.Forms.ToolStripProgressBar> obiekty do <xref:System.Windows.Forms.ToolStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="0f1df-115">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="0f1df-116">Tworzenie potoku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="0f1df-116">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="0f1df-117">Ta sekcja zawiera opis sposobu tworzenia potoku przepływu danych, która przetwarza elementy robocze i aktualizuje paski postępu.</span><span class="sxs-lookup"><span data-stu-id="0f1df-117">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
#### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="0f1df-118">Do utworzenia potoku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="0f1df-118">To Create the Dataflow Pipeline</span></span>  
  
1.  <span data-ttu-id="0f1df-119">W projekcie Dodaj odwołanie do System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="0f1df-119">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="0f1df-120">Upewnij się, że pliku Form1.cs (Form1.vb dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) zawiera następujące `using` instrukcje (`Imports` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="0f1df-120">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` statements (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="0f1df-121">Dodaj `WorkItem` klasy jako wewnętrzny typ `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="0f1df-121">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="0f1df-122">Dodaj następujące elementy członkowskie danych, aby `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="0f1df-122">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="0f1df-123">Dodaj następującą metodę `CreatePipeline`, do `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="0f1df-123">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="0f1df-124">Ponieważ `incrementProgress` i `decrementProgress` przepływu danych bloki działania w interfejsie użytkownika, ważne jest, że te zdarzenia w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0f1df-124">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="0f1df-125">Aby to zrobić, podczas konstruowania te obiekty każdego podaj <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiektu, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> ustawioną właściwość <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0f1df-125">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0f1df-126"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiekt, który przeprowadza pracę na bieżący kontekst synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="0f1df-126">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="0f1df-127">Ponieważ `Form1` Konstruktor jest wywoływana z wątku interfejsu użytkownika, akcje `incrementProgress` i `decrementProgress` bloków przepływu danych również uruchomić w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0f1df-127">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="0f1df-128">W tym przykładzie <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwości, gdy tworzy on elementy członkowskie potoku.</span><span class="sxs-lookup"><span data-stu-id="0f1df-128">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="0f1df-129">Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwości trwale anuluje wykonywania bloku przepływu danych, całe potoku muszą zostać ponownie utworzone po użytkownik anulował operację i chce dodać więcej elementów roboczych do potoku.</span><span class="sxs-lookup"><span data-stu-id="0f1df-129">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="0f1df-130">Na przykład, który pokazuje alternatywny sposób anulowanie bloku przepływu danych, dzięki czemu inne zadania mogą być wykonywane po operacja została anulowana, zobacz [wskazówki: Korzystanie z przepływu danych w aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="0f1df-130">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="0f1df-131">Połączenie potoku przepływu danych interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0f1df-131">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="0f1df-132">W tej sekcji opisano sposób podłączania potoku przepływu danych interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0f1df-132">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="0f1df-133">Tworzenie potoku, a także dodawanie elementów roboczych do potoku są kontrolowane przez program obsługi zdarzeń dla **dodać elementy robocze** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0f1df-133">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="0f1df-134">Anulowanie jest inicjowane przez **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0f1df-134">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="0f1df-135">Gdy użytkownik kliknie jeden z tych przycisków, odpowiednie działanie jest inicjowane w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="0f1df-135">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
#### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="0f1df-136">Aby połączyć potoku przepływu danych interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0f1df-136">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1.  <span data-ttu-id="0f1df-137">W projektancie formularzy dla tego formularza należy utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla **dodać elementy robocze** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0f1df-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2.  <span data-ttu-id="0f1df-138">Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla **dodać elementy robocze** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0f1df-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  <span data-ttu-id="0f1df-139">W projektancie formularzy dla tego formularza należy utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> programu obsługi zdarzeń dla **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0f1df-139">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="0f1df-140">Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> programu obsługi zdarzeń dla **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0f1df-140">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="0f1df-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f1df-141">Example</span></span>  
 <span data-ttu-id="0f1df-142">Poniższy przykład przedstawia kompletny kod dla pliku Form1.cs (Form1.vb dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="0f1df-142">The following example shows the complete code for Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="0f1df-143">Na poniższej ilustracji przedstawiono działającej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f1df-143">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="0f1df-144">![Aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="0f1df-144">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0f1df-145">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="0f1df-145">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f1df-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f1df-146">See Also</span></span>  
 [<span data-ttu-id="0f1df-147">Biblioteka przepływu danych</span><span class="sxs-lookup"><span data-stu-id="0f1df-147">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
