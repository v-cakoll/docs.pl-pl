---
title: 'Instrukcje: Określanie harmonogramu zadań w bloku przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 681c0f1f918c8991ed2544189488d1ea25547834
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345849"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="edd73-102">Instrukcje: Określanie harmonogramu zadań w bloku przepływu danych</span><span class="sxs-lookup"><span data-stu-id="edd73-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>
<span data-ttu-id="edd73-103">W tym dokumencie pokazano, jak skojarzyć harmonogram zadań szczególnych, korzystając z przepływu danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="edd73-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="edd73-104">W przykładzie użyto <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> klasy w aplikacji Windows Forms do wyświetlenia, gdy czytnik zadania są aktywne i podczas zadania zapisywania jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="edd73-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="edd73-105">Korzysta również <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> metodę umożliwiającą włączenie bloku przepływu danych do uruchamiania w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="edd73-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="edd73-106">Aby utworzyć Windows Forms aplikacji</span><span class="sxs-lookup"><span data-stu-id="edd73-106">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="edd73-107">Tworzenie języka Visual C# lub Visual Basic **aplikacja interfejsu Windows Forms** projektu.</span><span class="sxs-lookup"><span data-stu-id="edd73-107">Create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="edd73-108">W poniższych krokach projekt nazwano `WriterReadersWinForms`.</span><span class="sxs-lookup"><span data-stu-id="edd73-108">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2. <span data-ttu-id="edd73-109">W Projektancie formularza dla tego formularza Form1.cs (Form1.vb dla języka Visual Basic), dodaj cztery <xref:System.Windows.Forms.CheckBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="edd73-109">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="edd73-110">Ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości **1 czytnika** dla `checkBox1`, **Reader 2** dla `checkBox2`, **3 czytnika** dla `checkBox3`, i  **Moduł zapisujący** dla `checkBox4`.</span><span class="sxs-lookup"><span data-stu-id="edd73-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="edd73-111">Ustaw <xref:System.Windows.Forms.Control.Enabled%2A> właściwości dla każdego formantu do `False`.</span><span class="sxs-lookup"><span data-stu-id="edd73-111">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3. <span data-ttu-id="edd73-112">Dodaj <xref:System.Windows.Forms.Timer> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="edd73-112">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="edd73-113">Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwość `2500`.</span><span class="sxs-lookup"><span data-stu-id="edd73-113">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="edd73-114">Dodawanie funkcjonalności przepływu danych</span><span class="sxs-lookup"><span data-stu-id="edd73-114">Adding Dataflow Functionality</span></span>  
 <span data-ttu-id="edd73-115">W tej sekcji opisano sposób tworzenia bloków przepływu danych, które uczestniczą w aplikacji oraz jak skojarzyć każdy z nich za pomocą harmonogramu zadań.</span><span class="sxs-lookup"><span data-stu-id="edd73-115">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="edd73-116">Aby dodać funkcje przepływu danych do aplikacji</span><span class="sxs-lookup"><span data-stu-id="edd73-116">To Add Dataflow Functionality to the Application</span></span>  
  
1. <span data-ttu-id="edd73-117">W projekcie należy dodać odwołanie do System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="edd73-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="edd73-118">Upewnij się, że Form1.cs (Form1.vb dla języka Visual Basic) zawiera następujące `using` instrukcji (`Imports` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="edd73-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. <span data-ttu-id="edd73-119">Dodaj <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> element członkowski danych do `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="edd73-119">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. <span data-ttu-id="edd73-120">W `Form1` konstruktora, po wywołaniu `InitializeComponent`, Utwórz <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt, który włącza/wyłącza stan <xref:System.Windows.Forms.CheckBox> obiektów.</span><span class="sxs-lookup"><span data-stu-id="edd73-120">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. <span data-ttu-id="edd73-121">W `Form1` konstruktora, Utwórz <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> obiektu i cztery <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektów, po jednym <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt dla każdego <xref:System.Windows.Forms.CheckBox> obiektu.</span><span class="sxs-lookup"><span data-stu-id="edd73-121">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="edd73-122">Dla każdego <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektów, określ <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> właściwością <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> właściwości dla czytników zawartości i <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> właściwości dla edytora.</span><span class="sxs-lookup"><span data-stu-id="edd73-122">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. <span data-ttu-id="edd73-123">W `Form1` konstruktora, start <xref:System.Windows.Forms.Timer> obiektu.</span><span class="sxs-lookup"><span data-stu-id="edd73-123">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. <span data-ttu-id="edd73-124">W Projektancie formularza dla tego formularza, należy utworzyć program obsługi zdarzeń dla <xref:System.Windows.Forms.Timer.Tick> zdarzenie czasomierza.</span><span class="sxs-lookup"><span data-stu-id="edd73-124">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8. <span data-ttu-id="edd73-125">Implementowanie <xref:System.Windows.Forms.Timer.Tick> zdarzenie czasomierza.</span><span class="sxs-lookup"><span data-stu-id="edd73-125">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="edd73-126">Ponieważ `toggleCheckBox` działa bloku przepływu danych w interfejsie użytkownika, ważne jest, że ta akcja wystąpić w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="edd73-126">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="edd73-127">Aby to osiągnąć, podczas konstruowania ten obiekt zawiera <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> właściwością <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="edd73-127">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="edd73-128"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiektu, który wykonuje pracę w bieżącym kontekście synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="edd73-128">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="edd73-129">Ponieważ `Form1` Konstruktor jest wywoływana z wątku interfejsu użytkownika w akcji dla `toggleCheckBox` bloku przepływu danych jest również uruchamiane w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="edd73-129">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="edd73-130">W tym przykładzie również użyto <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> klasy w celu włączenia pewnych bloków przepływu danych, która będzie działać jednocześnie, a inny blok przepływu danych do działania na wyłączność w odniesieniu do wszystkich innych bloków przepływu danych, które są uruchamiane na tym samym <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> obiektu.</span><span class="sxs-lookup"><span data-stu-id="edd73-130">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="edd73-131">Ta technika jest przydatna, gdy wiele bloków przepływu danych dzielą jakiś zasób, a niektóre wymagają wyłącznego dostępu do tego zasobu, ponieważ eliminuje wymóg, aby ręcznie zsynchronizować dostęp do tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="edd73-131">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="edd73-132">Eliminacja ręcznej synchronizacji może uczynić kod bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="edd73-132">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edd73-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="edd73-133">Example</span></span>  
 <span data-ttu-id="edd73-134">Poniższy przykład pokazuje kompletny kod dla Form1.cs (Form1.vb dla języka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="edd73-134">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="edd73-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edd73-135">See also</span></span>

- [<span data-ttu-id="edd73-136">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="edd73-136">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
