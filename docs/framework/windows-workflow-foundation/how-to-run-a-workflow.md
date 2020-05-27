---
title: 'Instrukcje: Uruchamianie przepływu pracy'
description: W tym artykule opisano sposób tworzenia hosta przepływu pracy i uruchamiania przepływu pracy zdefiniowanego w poprzednim artykule w tej Windows Workflow Foundation serii samouczków.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 86062dd5147e6e354833928fd98bd1f6b5de9114
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421504"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="84475-103">Instrukcje: Uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="84475-103">How to: Run a Workflow</span></span>
<span data-ttu-id="84475-104">Ten temat jest kontynuacją samouczka Windows Workflow Foundation Wprowadzenie i zawiera opis sposobu tworzenia hosta przepływu pracy i uruchamiania przepływu pracy zdefiniowanego w poprzednich tematach [: tworzenie przepływu](how-to-create-a-workflow.md) pracy.</span><span class="sxs-lookup"><span data-stu-id="84475-104">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="84475-105">Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="84475-105">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="84475-106">Aby ukończyć ten temat, należy najpierw wykonać [instrukcje: tworzenie działania](how-to-create-an-activity.md) i [instrukcje: tworzenie przepływu pracy](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="84475-106">To complete this topic you must first complete [How to: Create an Activity](how-to-create-an-activity.md) and [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

> [!NOTE]
> <span data-ttu-id="84475-107">Aby pobrać kompletną wersję samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="84475-107">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="84475-108">Aby utworzyć projekt hosta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="84475-108">To create the workflow host project</span></span>  
  
1. <span data-ttu-id="84475-109">Otwórz rozwiązanie z poprzedniej procedury [: Tworzenie tematu działania](how-to-create-an-activity.md) przy użyciu programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="84475-109">Open the solution from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic by using Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="84475-110">Kliknij prawym przyciskiem myszy rozwiązanie **WF45GettingStartedTutorial** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**, **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="84475-110">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="84475-111">Jeśli okno **Eksplorator rozwiązań** nie jest wyświetlane, wybierz pozycję **Eksplorator rozwiązań** z menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="84475-111">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="84475-112">W **zainstalowanym** węźle wybierz pozycję **Visual C#**, **przepływ pracy** (lub **Visual Basic**, **przepływ pracy**).</span><span class="sxs-lookup"><span data-stu-id="84475-112">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="84475-113">W zależności od tego, który język programowania jest skonfigurowany jako język podstawowy w programie Visual Studio, węzeł **Visual C#** lub **Visual Basic** może znajdować się w węźle **inne języki** w **zainstalowanym** węźle.</span><span class="sxs-lookup"><span data-stu-id="84475-113">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="84475-114">Upewnij się, że na liście rozwijanej wersja .NET Framework została wybrana **.NET Framework 4,5** .</span><span class="sxs-lookup"><span data-stu-id="84475-114">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="84475-115">Wybierz pozycję **aplikacja konsoli przepływu pracy** z listy **przepływów pracy** .</span><span class="sxs-lookup"><span data-stu-id="84475-115">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="84475-116">Wpisz tekst `NumberGuessWorkflowHost` w polu **Nazwa** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="84475-116">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="84475-117">Spowoduje to utworzenie aplikacji typu "Start Workflow" z obsługą podstawowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="84475-117">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="84475-118">Ten podstawowy kod hostingu jest modyfikowany i używany do uruchamiania aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="84475-118">This basic hosting code is modified and used to run the workflow application.</span></span>

4. <span data-ttu-id="84475-119">Kliknij prawym przyciskiem myszy nowo dodany projekt **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="84475-119">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="84475-120">Wybierz **rozwiązanie** z listy **Dodaj odwołanie** , zaznacz pole wyboru obok **NumberGuessWorkflowActivities**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="84475-120">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>

5. <span data-ttu-id="84475-121">Kliknij prawym przyciskiem myszy **Workflow1. XAML** w **Eksplorator rozwiązań** i wybierz polecenie **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="84475-121">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="84475-122">Kliknij przycisk **OK** , aby potwierdzić.</span><span class="sxs-lookup"><span data-stu-id="84475-122">Click **OK** to confirm.</span></span>

### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="84475-123">Aby zmodyfikować kod hostingu przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="84475-123">To modify the workflow hosting code</span></span>

1. <span data-ttu-id="84475-124">Kliknij dwukrotnie pozycję **program.cs** lub **Module1. vb** w **Eksplorator rozwiązań** , aby wyświetlić kod.</span><span class="sxs-lookup"><span data-stu-id="84475-124">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>

    > [!TIP]
    > <span data-ttu-id="84475-125">Jeśli okno **Eksplorator rozwiązań** nie jest wyświetlane, wybierz pozycję **Eksplorator rozwiązań** z menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="84475-125">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

     <span data-ttu-id="84475-126">Ponieważ ten projekt został utworzony przy użyciu szablonu **aplikacji konsoli przepływu pracy** , **program.cs** lub **Module1. vb** zawiera następujący podstawowy kod hostingu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="84475-126">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>

    ```vb
    ' Create and cache the workflow definition.
    Dim workflow1 As Activity = New Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition.
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     <span data-ttu-id="84475-127">Ten wygenerowany kod hostingu używa <xref:System.Activities.WorkflowInvoker> .</span><span class="sxs-lookup"><span data-stu-id="84475-127">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="84475-128"><xref:System.Activities.WorkflowInvoker>zapewnia prostą metodę wywoływania przepływu pracy tak, jakby była wywołaniem metody i może być używana tylko dla przepływów pracy, które nie używają trwałości.</span><span class="sxs-lookup"><span data-stu-id="84475-128"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="84475-129"><xref:System.Activities.WorkflowApplication>zapewnia bogatszy model służący do wykonywania przepływów pracy, które obejmują powiadomienia o zdarzeniach cyklu życia, kontroli wykonywania, wznawianiu zakładek i trwałości.</span><span class="sxs-lookup"><span data-stu-id="84475-129"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="84475-130">W tym przykładzie użyto zakładek i <xref:System.Activities.WorkflowApplication> jest on używany do hostowania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="84475-130">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="84475-131">Dodaj następującą `using` instrukcję lub **Imports** w górnej części **program.cs** lub **Module1. vb** poniżej istniejących instrukcji **using** lub **Imports** .</span><span class="sxs-lookup"><span data-stu-id="84475-131">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <span data-ttu-id="84475-132">Zastąp wiersze kodu, który <xref:System.Activities.WorkflowInvoker> jest używany z następującym podstawowym <xref:System.Activities.WorkflowApplication> kodem hostingu.</span><span class="sxs-lookup"><span data-stu-id="84475-132">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="84475-133">Ten przykładowy kod hostingu pokazuje podstawowe kroki hostingu i wywoływania przepływu pracy, ale nie zawiera jeszcze funkcji, aby pomyślnie uruchomić przepływ pracy z tego tematu.</span><span class="sxs-lookup"><span data-stu-id="84475-133">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="84475-134">W poniższych krokach ten kod podstawowy jest modyfikowany, a dodatkowe funkcje są dodawane do momentu ukończenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="84475-134">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="84475-135">Zastąp `Workflow1` w tych przykładach z `FlowchartNumberGuessWorkflow` , `SequentialNumberGuessWorkflow` lub `StateMachineNumberGuessWorkflow` , w zależności od przepływu pracy, który został ukończony w poprzednich krokach [: Tworzenie kroku przepływu pracy](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="84475-135">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="84475-136">Jeśli nie zastąpisz, podczas `Workflow1` próby utworzenia lub uruchomienia przepływu pracy zostaną wyświetlone błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="84475-136">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     <span data-ttu-id="84475-137">Ten kod tworzy <xref:System.Activities.WorkflowApplication> , subskrybuje trzy zdarzenia cyklu życia przepływu pracy, uruchamia przepływ pracy z wywołaniem <xref:System.Activities.WorkflowApplication.Run%2A> , a następnie czeka na zakończenie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="84475-137">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="84475-138">Po zakończeniu przepływu pracy <xref:System.Threading.AutoResetEvent> jest ustawiony i aplikacja hosta zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="84475-138">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>

### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="84475-139">Aby ustawić argumenty wejściowe przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="84475-139">To set input arguments of a workflow</span></span>

1. <span data-ttu-id="84475-140">Dodaj następującą instrukcję w górnej części **program.cs** lub **Module1. vb** poniżej istniejących `using` `Imports` instrukcji lub.</span><span class="sxs-lookup"><span data-stu-id="84475-140">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. <span data-ttu-id="84475-141">Zastąp wiersz kodu, który tworzy nowy, <xref:System.Activities.WorkflowApplication> przy użyciu następującego kodu, który tworzy i przekazuje słownik parametrów do przepływu pracy podczas jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="84475-141">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="84475-142">Zastąp `Workflow1` w tych przykładach z `FlowchartNumberGuessWorkflow` , `SequentialNumberGuessWorkflow` lub `StateMachineNumberGuessWorkflow` , w zależności od przepływu pracy, który został ukończony w poprzednich krokach [: Tworzenie kroku przepływu pracy](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="84475-142">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="84475-143">Jeśli nie zastąpisz, podczas `Workflow1` próby utworzenia lub uruchomienia przepływu pracy zostaną wyświetlone błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="84475-143">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="84475-144">Ten słownik zawiera jeden element z kluczem `MaxNumber` .</span><span class="sxs-lookup"><span data-stu-id="84475-144">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="84475-145">Klucze w słowniku wejściowym odnoszą się do argumentów wejściowych w głównym działaniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="84475-145">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="84475-146">`MaxNumber`jest używany przez przepływ pracy do określenia górnej granicy dla losowo wygenerowanego numeru.</span><span class="sxs-lookup"><span data-stu-id="84475-146">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>

### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="84475-147">Aby pobrać argumenty wyjściowe przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="84475-147">To retrieve output arguments of a workflow</span></span>

1. <span data-ttu-id="84475-148">Zmodyfikuj <xref:System.Activities.WorkflowApplication.Completed%2A> procedurę obsługi, aby pobrać i wyświetlić liczbę zmian używanych przez przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="84475-148">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a><span data-ttu-id="84475-149">Aby wznowić zakładkę</span><span class="sxs-lookup"><span data-stu-id="84475-149">To resume a bookmark</span></span>

1. <span data-ttu-id="84475-150">Dodaj poniższy kod w górnej części `Main` metody tuż po istniejącej <xref:System.Threading.AutoResetEvent> deklaracji.</span><span class="sxs-lookup"><span data-stu-id="84475-150">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. <span data-ttu-id="84475-151">Dodaj poniższy <xref:System.Activities.WorkflowApplication.Idle%2A> program obsługi tuż poniżej istniejących trzech programów obsługi cyklu życia przepływu pracy w programie `Main` .</span><span class="sxs-lookup"><span data-stu-id="84475-151">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     <span data-ttu-id="84475-152">Za każdym razem, gdy przepływ pracy przechodzi w stan bezczynności, czeka na kolejne odpuszczenie, ta procedura obsługi jest wywoływana i `idleAction` <xref:System.Threading.AutoResetEvent> jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="84475-152">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="84475-153">Kod w poniższym kroku używa `idleEvent` i `syncEvent` do określenia, czy przepływ pracy oczekuje na następne odgadnięcie lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="84475-153">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="84475-154">W tym przykładzie aplikacja hosta używa zdarzeń autoresetowania w programach i, <xref:System.Activities.WorkflowApplication.Completed%2A> <xref:System.Activities.WorkflowApplication.Idle%2A> Aby zsynchronizować aplikację hosta z postępem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="84475-154">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="84475-155">Nie jest konieczne zablokowanie i zaczekanie, aż przepływ pracy przestanie być bezczynny przed wznowieniem zakładki, ale w tym przykładzie są wymagane zdarzenia synchronizacji, aby Host wiedział, czy przepływ pracy został ukończony, czy też czeka na więcej danych wejściowych użytkownika przy użyciu <xref:System.Activities.Bookmark> .</span><span class="sxs-lookup"><span data-stu-id="84475-155">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="84475-156">Aby uzyskać więcej informacji, zobacz [zakładki](bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="84475-156">For more information, see [Bookmarks](bookmarks.md).</span></span>

3. <span data-ttu-id="84475-157">Usuń wywołanie do `WaitOne` i zastąp je kodem, aby zebrać dane wejściowe od użytkownika i wznowić <xref:System.Activities.Bookmark> .</span><span class="sxs-lookup"><span data-stu-id="84475-157">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>

     <span data-ttu-id="84475-158">Usuń następujący wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="84475-158">Remove the following line of code.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     <span data-ttu-id="84475-159">Zastąp go następującym przykładem.</span><span class="sxs-lookup"><span data-stu-id="84475-159">Replace it with the following example.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="to-build-and-run-the-application"></a><a name="BKMK_ToRunTheApplication"></a><span data-ttu-id="84475-160">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="84475-160">To build and run the application</span></span>

1. <span data-ttu-id="84475-161">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="84475-161">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="84475-162">Naciśnij kombinację klawiszy CTRL + F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="84475-162">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="84475-163">Spróbuj złamać liczbę w możliwie najmniejszej liczbie.</span><span class="sxs-lookup"><span data-stu-id="84475-163">Try to guess the number in as few turns as possible.</span></span>

     <span data-ttu-id="84475-164">Aby wypróbować aplikację przy użyciu jednego z innych stylów przepływu pracy, Zastąp `Workflow1` kod, który tworzy <xref:System.Activities.WorkflowApplication> za pomocą `FlowchartNumberGuessWorkflow` , `SequentialNumberGuessWorkflow` lub `StateMachineNumberGuessWorkflow` , w zależności od tego, który styl przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="84475-164">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="84475-165">Aby uzyskać instrukcje dotyczące sposobu dodawania trwałości do aplikacji przepływu pracy, zobacz następny temat [: Tworzenie i uruchamianie długotrwałego przepływu pracy](how-to-create-and-run-a-long-running-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="84475-165">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md).</span></span>

## <a name="example"></a><span data-ttu-id="84475-166">Przykład</span><span class="sxs-lookup"><span data-stu-id="84475-166">Example</span></span>
 <span data-ttu-id="84475-167">Poniższy przykład to kompletna lista kodu dla `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="84475-167">The following example is the complete code listing for the `Main` method.</span></span>

> [!NOTE]
> <span data-ttu-id="84475-168">Zastąp `Workflow1` w tych przykładach z `FlowchartNumberGuessWorkflow` , `SequentialNumberGuessWorkflow` lub `StateMachineNumberGuessWorkflow` , w zależności od przepływu pracy, który został ukończony w poprzednich krokach [: Tworzenie kroku przepływu pracy](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="84475-168">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="84475-169">Jeśli nie zastąpisz, podczas `Workflow1` próby utworzenia lub uruchomienia przepływu pracy zostaną wyświetlone błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="84475-169">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a><span data-ttu-id="84475-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84475-170">See also</span></span>

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [<span data-ttu-id="84475-171">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="84475-171">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="84475-172">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="84475-172">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="84475-173">Instrukcje: Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="84475-173">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="84475-174">Instrukcje: Tworzenie i uruchamianie długotrwałego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="84475-174">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)
- [<span data-ttu-id="84475-175">Oczekiwanie na dane wejściowe w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="84475-175">Waiting for Input in a Workflow</span></span>](waiting-for-input-in-a-workflow.md)
- [<span data-ttu-id="84475-176">Hostowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="84475-176">Hosting Workflows</span></span>](hosting-workflows.md)
