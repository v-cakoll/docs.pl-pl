---
title: 'Porady: uruchamianie przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 47227bdd23efc9648da25bc879c7946dadee4594
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527946"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="8ad63-102">Porady: uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8ad63-102">How to: Run a Workflow</span></span>
<span data-ttu-id="8ad63-103">W tym temacie jest kontynuacją samouczka Windows Workflow Foundation wprowadzenie i w tym artykule omówiono sposób tworzenia hosta przepływu pracy i uruchomić przepływ pracy zdefiniowane w poprzednim [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="8ad63-103">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ad63-104">Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach.</span><span class="sxs-lookup"><span data-stu-id="8ad63-104">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="8ad63-105">Aby zakończyć w tym temacie, najpierw musisz zakończyć [instrukcje: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) i [jak: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8ad63-105">To complete this topic you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) and [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ad63-106">Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="8ad63-106">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="8ad63-107">Aby utworzyć projekt hosta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8ad63-107">To create the workflow host project</span></span>  
  
1.  <span data-ttu-id="8ad63-108">Otwórz rozwiązanie z poprzedniego [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu przy użyciu [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8ad63-108">Open the solution from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic by using [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="8ad63-109">Kliknij prawym przyciskiem myszy **WF45GettingStartedTutorial** rozwiązania **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="8ad63-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="8ad63-110">Jeśli **Eksploratora rozwiązań** nie zostanie wyświetlone okno, wybierz **Eksploratora rozwiązań** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="8ad63-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="8ad63-111">W **zainstalowane** węzeł **Visual C#**, **przepływu pracy** (lub **języka Visual Basic**, **przepływu pracy**).</span><span class="sxs-lookup"><span data-stu-id="8ad63-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ad63-112">Zależności od tego, jaki język programowania jest skonfigurowany jako podstawowy język w programie Visual Studio, **Visual C#** lub **języka Visual Basic** węzła może znajdować się w **inne języki** w węźle **zainstalowane** węzła.</span><span class="sxs-lookup"><span data-stu-id="8ad63-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="8ad63-113">Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ad63-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="8ad63-114">Wybierz **Aplikacja konsoli przepływu pracy** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="8ad63-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="8ad63-115">Typ `NumberGuessWorkflowHost` do **nazwa** pole, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ad63-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="8ad63-116">Spowoduje to utworzenie aplikacji przepływu pracy starter z podstawowym przepływem pracy, obsługa hostingu.</span><span class="sxs-lookup"><span data-stu-id="8ad63-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="8ad63-117">Ten podstawowy kod hostingu zostanie zmodyfikowana i używane do uruchamiania aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8ad63-117">This basic hosting code is modified and used to run the workflow application.</span></span>  
  
4.  <span data-ttu-id="8ad63-118">Kliknij prawym przyciskiem myszy nowo dodanych **NumberGuessWorkflowHost** projektu w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="8ad63-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="8ad63-119">Wybierz **rozwiązania** z **Dodaj odwołanie** listy, zaznacz pole wyboru obok pozycji **NumberGuessWorkflowActivities**, a następnie kliknij przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="8ad63-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="8ad63-120">Kliknij prawym przyciskiem myszy **Workflow1.xaml** w **Eksploratora rozwiązań** i wybierz polecenie **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="8ad63-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="8ad63-121">Kliknij przycisk **OK** o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="8ad63-121">Click **OK** to confirm.</span></span>  
  
### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="8ad63-122">Aby zmodyfikować przepływ pracy, kod hostingu</span><span class="sxs-lookup"><span data-stu-id="8ad63-122">To modify the workflow hosting code</span></span>  
  
1.  <span data-ttu-id="8ad63-123">Kliknij dwukrotnie **Program.cs** lub **Module1.vb** w **Eksploratora rozwiązań** Aby wyświetlić kod.</span><span class="sxs-lookup"><span data-stu-id="8ad63-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="8ad63-124">Jeśli **Eksploratora rozwiązań** nie zostanie wyświetlone okno, wybierz **Eksploratora rozwiązań** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="8ad63-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
     <span data-ttu-id="8ad63-125">Ponieważ ten projekt został utworzony przy użyciu **Aplikacja konsoli przepływu pracy** szablonu, **Program.cs** lub **Module1.vb** zawiera następujące hostingu podstawowy przepływ pracy Kod.</span><span class="sxs-lookup"><span data-stu-id="8ad63-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>  
  
    ```vb  
    ' Create and cache the workflow definition  
    Activity workflow1 = new Workflow1()  
    WorkflowInvoker.Invoke(workflow1)  
    ```  
  
    ```csharp  
    // Create and cache the workflow definition  
    Activity workflow1 = new Workflow1();  
    WorkflowInvoker.Invoke(workflow1);  
    ```  
  
     <span data-ttu-id="8ad63-126">Ten wygenerowany kod hostingu, używa <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="8ad63-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="8ad63-127"><xref:System.Activities.WorkflowInvoker> zapewnia prostą metodę do wywołania przepływu pracy tak, jakby były wywołania metody i mogą służyć tylko w przypadku przepływów pracy, które nie korzystają z trwałości.</span><span class="sxs-lookup"><span data-stu-id="8ad63-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="8ad63-128"><xref:System.Activities.WorkflowApplication> udostępnia bogatszy model do wykonywania przepływów pracy, które zawierają powiadomienie o zdarzenia cyklu życia, kontrola wykonywania, wznowienie zakładki i trwałości.</span><span class="sxs-lookup"><span data-stu-id="8ad63-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="8ad63-129">W tym przykładzie użyto zakładek i <xref:System.Activities.WorkflowApplication> jest używany do hostowania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8ad63-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="8ad63-130">Dodaj następujący kod `using` lub **Importy** instrukcji na górze **Program.cs** lub **Module1.vb** poniżej istniejącego **przy użyciu** lub **Importy** instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8ad63-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Threading  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Threading;  
    ```  
  
     <span data-ttu-id="8ad63-131">Zamień wiersze kodu, które używają <xref:System.Activities.WorkflowInvoker> za pomocą następujących basic <xref:System.Activities.WorkflowApplication> kod hostingu.</span><span class="sxs-lookup"><span data-stu-id="8ad63-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="8ad63-132">Ten przykładowy kod hostingu przedstawiono podstawowe kroki obsługi i wywoływania przepływu pracy, ale nie zawiera jeszcze funkcji do pomyślnego uruchomienia przepływu pracy z tego tematu.</span><span class="sxs-lookup"><span data-stu-id="8ad63-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="8ad63-133">W poniższych krokach ten podstawowy kod jest modyfikowany, a dodatkowe funkcje zostaną dodane do czasu zakończenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ad63-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ad63-134">Zastąp `Workflow1` w tych przykładach za pomocą `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy ukończone w ciągu poprzednich [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku.</span><span class="sxs-lookup"><span data-stu-id="8ad63-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="8ad63-135">Jeśli nie zastąpisz `Workflow1` , a następnie otrzymasz błędy kompilacji podczas spróbuj i kompilacji lub uruchamiania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8ad63-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]  
  
     <span data-ttu-id="8ad63-136">Ten kod tworzy <xref:System.Activities.WorkflowApplication>, subskrybuje trzy zdarzenia cyklu życia przepływu pracy, przepływ pracy zaczyna się od wywołania <xref:System.Activities.WorkflowApplication.Run%2A>, a następnie czeka na przepływ pracy zakończy się.</span><span class="sxs-lookup"><span data-stu-id="8ad63-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="8ad63-137">Po ukończeniu przepływu pracy <xref:System.Threading.AutoResetEvent> jest ustawiony, host zakończeniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ad63-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>  
  
### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="8ad63-138">Aby ustawić argumentów wejściowych przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8ad63-138">To set input arguments of a workflow</span></span>  
  
1.  <span data-ttu-id="8ad63-139">Dodaj następującą instrukcję w górnej części **Program.cs** lub **Module1.vb** poniżej istniejącego `using` lub `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8ad63-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]  
  
2.  <span data-ttu-id="8ad63-140">Zastąp wiersz kodu, który tworzy nowy <xref:System.Activities.WorkflowApplication> następującym kodem, które tworzy i przekazuje słownik parametrów do przepływu pracy, podczas jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="8ad63-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ad63-141">Zastąp `Workflow1` w tych przykładach za pomocą `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy ukończone w ciągu poprzednich [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku.</span><span class="sxs-lookup"><span data-stu-id="8ad63-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="8ad63-142">Jeśli nie zastąpisz `Workflow1` , a następnie otrzymasz błędy kompilacji podczas spróbuj i kompilacji lub uruchamiania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8ad63-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     <span data-ttu-id="8ad63-143">Ten słownik zawiera jeden element z kluczem `MaxNumber`.</span><span class="sxs-lookup"><span data-stu-id="8ad63-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="8ad63-144">Klucze w słowniku wejściowe odpowiadają wprowadzanie argumentów działania głównego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8ad63-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="8ad63-145">`MaxNumber` jest używany przez przepływ pracy do określenia górną granicę losowo generowany numer.</span><span class="sxs-lookup"><span data-stu-id="8ad63-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>  
  
### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="8ad63-146">Aby pobrać argumenty danych wyjściowych przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8ad63-146">To retrieve output arguments of a workflow</span></span>  
  
1.  <span data-ttu-id="8ad63-147">Modyfikowanie <xref:System.Activities.WorkflowApplication.Completed%2A> program obsługi, aby pobrać i wyświetlić liczbę włącza używane przez przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="8ad63-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#7](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]  
  
### <a name="to-resume-a-bookmark"></a><span data-ttu-id="8ad63-148">Wznowienie zakładki</span><span class="sxs-lookup"><span data-stu-id="8ad63-148">To resume a bookmark</span></span>  
  
1.  <span data-ttu-id="8ad63-149">Dodaj następujący kod w górnej części `Main` metoda zaraz po istniejącej <xref:System.Threading.AutoResetEvent> deklaracji.</span><span class="sxs-lookup"><span data-stu-id="8ad63-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#8](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]  
  
2.  <span data-ttu-id="8ad63-150">Dodaj następujący kod <xref:System.Activities.WorkflowApplication.Idle%2A> obsługi tuż poniżej istniejącego trzy przepływu pracy cyklu życia obsługi w `Main`.</span><span class="sxs-lookup"><span data-stu-id="8ad63-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#9](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]  
  
     <span data-ttu-id="8ad63-151">Każdorazowo przepływu pracy staje się nieaktywna, oczekiwanie na następnym razem ten program obsługi jest wywoływany i `idleAction` <xref:System.Threading.AutoResetEvent> jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="8ad63-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="8ad63-152">Kod w następnym kroku używa `idleEvent` i `syncEvent` czy czeka na następny wynik przepływu pracy, czy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="8ad63-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ad63-153">W tym przykładzie korzysta z resetowaniem automatycznym zdarzenia w aplikacji hosta <xref:System.Activities.WorkflowApplication.Completed%2A> i <xref:System.Activities.WorkflowApplication.Idle%2A> programów obsługi, aby zapewnić synchronizację aplikacji hosta z postęp przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8ad63-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="8ad63-154">Nie jest konieczne do blokowania i poczekać na przepływ pracy przejdzie w stan bezczynności przed wznowieniem zakładki, ale w tym przykładzie zdarzenia synchronizacji są wymagane tak przyjmującym wie, czy przepływu pracy zostało ukończone lub czy oczekuje na więcej danych wejściowych użytkownika za pomocą <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="8ad63-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="8ad63-155">Aby uzyskać więcej informacji, zobacz [zakładki](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="8ad63-155">For more information, see [Bookmarks](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>  
  
3.  <span data-ttu-id="8ad63-156">Usuń wywołanie funkcji `WaitOne`i Zastąp kod w celu zbierania danych wejściowych od użytkownika i Wznów <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="8ad63-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>  
  
     <span data-ttu-id="8ad63-157">Usuń następujący wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="8ad63-157">Remove the following line of code.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#10](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]  
  
     <span data-ttu-id="8ad63-158">Zastąp go poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ad63-158">Replace it with the following example.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#11](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]  
  
##  <a name="BKMK_ToRunTheApplication"></a> <span data-ttu-id="8ad63-159">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="8ad63-159">To build and run the application</span></span>  
  
1.  <span data-ttu-id="8ad63-160">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="8ad63-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
2.  <span data-ttu-id="8ad63-161">Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8ad63-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="8ad63-162">Próby odgadnięcia numer w tak małą włącza, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="8ad63-162">Try to guess the number in as few turns as possible.</span></span>  
  
     <span data-ttu-id="8ad63-163">Aby wypróbować aplikację przy użyciu jednego z innymi stylami przepływu pracy, należy zastąpić `Workflow1` w kodzie, który tworzy <xref:System.Activities.WorkflowApplication> z `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, w zależności od stylu przepływu pracy użytkowników.</span><span class="sxs-lookup"><span data-stu-id="8ad63-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     <span data-ttu-id="8ad63-164">Instrukcje dotyczące sposobu dodawania trwałości do poziomu aplikacji przepływu pracy, zobacz następny temat [porady: tworzenie i uruchamianie długiego uruchamiania przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8ad63-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ad63-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ad63-165">Example</span></span>  
 <span data-ttu-id="8ad63-166">Poniższy przykład przedstawia kompletny kod dla `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="8ad63-166">The following example is the complete code listing for the `Main` method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ad63-167">Zastąp `Workflow1` w tych przykładach za pomocą `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy ukończone w ciągu poprzednich [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku.</span><span class="sxs-lookup"><span data-stu-id="8ad63-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="8ad63-168">Jeśli nie zastąpisz `Workflow1` , a następnie otrzymasz błędy kompilacji podczas spróbuj i kompilacji lub uruchamiania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8ad63-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
 [!code-csharp[CFX_WF_GettingStarted#12](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="8ad63-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ad63-169">See Also</span></span>  
 <xref:System.Activities.WorkflowApplication>  
 <xref:System.Activities.Bookmark>  
 [<span data-ttu-id="8ad63-170">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="8ad63-170">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="8ad63-171">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="8ad63-171">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="8ad63-172">Instrukcje: Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8ad63-172">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="8ad63-173">Instrukcje: Tworzenie i uruchamianie długotrwałego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8ad63-173">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 [<span data-ttu-id="8ad63-174">Oczekiwanie na dane wejściowe w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="8ad63-174">Waiting for Input in a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/waiting-for-input-in-a-workflow.md)  
 [<span data-ttu-id="8ad63-175">Hostowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="8ad63-175">Hosting Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/hosting-workflows.md)
