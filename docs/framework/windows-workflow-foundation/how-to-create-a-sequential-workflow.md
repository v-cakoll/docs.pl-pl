---
title: "Porady: tworzenie sekwencyjnego przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6888d13c982f282b0d3d939c1396bfaddd673efc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="70baf-102">Porady: tworzenie sekwencyjnego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="70baf-102">How to: Create a Sequential Workflow</span></span>
<span data-ttu-id="70baf-103">Przepływy pracy można skonstruować z działań wbudowanych oraz z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="70baf-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="70baf-104">W tym temacie prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowane działania, takie jak <xref:System.Activities.Statements.Sequence> działania i działań niestandardowych z poprzedniej [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="70baf-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="70baf-105">Przepływ pracy modele numer guessing gier.</span><span class="sxs-lookup"><span data-stu-id="70baf-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70baf-106">Każdego tematu w samouczku wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="70baf-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="70baf-107">Aby ukończyć w tym temacie, najpierw musisz zakończyć [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="70baf-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70baf-108">Aby pobrać ukończoną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="70baf-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="70baf-109">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="70baf-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="70baf-110">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="70baf-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="70baf-111">W **zainstalowana**, **wspólne elementy** węzła, wybierz opcję **przepływu pracy**.</span><span class="sxs-lookup"><span data-stu-id="70baf-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="70baf-112">Wybierz **działania** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="70baf-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="70baf-113">Typ `SequentialNumberGuessWorkflow` do **nazwa** polu i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="70baf-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="70baf-114">Przeciągnij **sekwencji** działania z **przepływ sterowania** sekcji **przybornika** i upuść ją na **Upuść tutaj działanie** etykiety na powierzchni projektu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="70baf-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="70baf-115">Aby utworzyć zmienne przepływu pracy i argumenty</span><span class="sxs-lookup"><span data-stu-id="70baf-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="70baf-116">Kliknij dwukrotnie **SequentialNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania przepływu pracy w projektancie, jeśli nie jest już wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="70baf-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="70baf-117">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="70baf-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="70baf-118">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="70baf-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="70baf-119">Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argument.</span><span class="sxs-lookup"><span data-stu-id="70baf-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="70baf-120">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="70baf-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="70baf-121">Typ `Turns` do **nazwa** pole poniżej nowo dodanego `MaxNumber` argumentu, wybierz opcję **limit** z **kierunek** listy rozwijanej wybierz pozycję  **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="70baf-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="70baf-122">Kliknij przycisk **argumenty** w lewym dolnym rogu Projektant działań, aby zamknąć **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="70baf-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="70baf-123">Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="70baf-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="70baf-124">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="70baf-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="70baf-125">Jeśli nie **tworzenia zmiennej** zostanie wyświetlone okno, kliknij przycisk **sekwencji** działania na powierzchni projektanta przepływu pracy, aby go wybrać.</span><span class="sxs-lookup"><span data-stu-id="70baf-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="70baf-126">Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="70baf-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="70baf-127">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="70baf-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="70baf-128">Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="70baf-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="70baf-129">Kliknij przycisk **zmienne** w lewym dolnym rogu Projektant działań, aby zamknąć **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="70baf-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="70baf-130">Aby dodać działania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="70baf-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="70baf-131">Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i upuść ją na **sekwencji** działania.</span><span class="sxs-lookup"><span data-stu-id="70baf-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="70baf-132">Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="70baf-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="70baf-133">Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="70baf-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="70baf-134">Przeciągnij **DoWhile** działania z **przepływ sterowania** sekcji **przybornika** i upuść ją na przepływu pracy, aby była ona poniżej **przypisać** działanie.</span><span class="sxs-lookup"><span data-stu-id="70baf-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>  
  
3.  <span data-ttu-id="70baf-135">Wpisz następujące wyrażenie w **DoWhile** działania **warunku** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="70baf-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <span data-ttu-id="70baf-136">A <xref:System.Activities.Statements.DoWhile> działania wykonuje działania podrzędne, a następnie oblicza jego <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span><span class="sxs-lookup"><span data-stu-id="70baf-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="70baf-137">Jeśli <xref:System.Activities.Statements.DoWhile.Condition%2A> daje w wyniku `True`, następnie działań w <xref:System.Activities.Statements.DoWhile> wykonać ponownie.</span><span class="sxs-lookup"><span data-stu-id="70baf-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="70baf-138">W tym przykładzie wynik użytkownika jest obliczane i <xref:System.Activities.Statements.DoWhile> będzie wykonywany do momentu wynik jest poprawna.</span><span class="sxs-lookup"><span data-stu-id="70baf-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>  
  
4.  <span data-ttu-id="70baf-139">Przeciągnij **monitu** działania z **NumberGuessWorkflowActivities** sekcji **przybornika** i upuść je w **DoWhile** działania w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="70baf-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>  
  
5.  <span data-ttu-id="70baf-140">W **okna właściwości**, typ `"EnterGuess"` z cudzysłowami do **Nazwa zakładki** pole wartości właściwości dla **monitu** działania.</span><span class="sxs-lookup"><span data-stu-id="70baf-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="70baf-141">Typ `Guess` do **wynik** właściwości wartość pola, a następnie wpisz następujące wyrażenie w **tekst** pole właściwości.</span><span class="sxs-lookup"><span data-stu-id="70baf-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="70baf-142">Jeśli **okna właściwości** nie jest wyświetlane, wybierz pozycję **okna właściwości** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="70baf-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
6.  <span data-ttu-id="70baf-143">Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i upuść je w **DoWhile** działania, którego nie jest zgodny **Monitu** działania.</span><span class="sxs-lookup"><span data-stu-id="70baf-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70baf-144">Po upuszczeniu **przypisać** działanie, należy pamiętać, jak automatycznie dodaje projektanta przepływów pracy **sekwencji** działania zawiera zarówno **monitu** działania i nowo dodany **Przypisać** działania.</span><span class="sxs-lookup"><span data-stu-id="70baf-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>  
  
7.  <span data-ttu-id="70baf-145">Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="70baf-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
8.  <span data-ttu-id="70baf-146">Przeciągnij **Jeśli** działania z **przepływ sterowania** sekcji **przybornika** i upuść je w **sekwencji** działania, którego nie jest zgodny nowo dodana **przypisać** działania.</span><span class="sxs-lookup"><span data-stu-id="70baf-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>  
  
9. <span data-ttu-id="70baf-147">Wpisz następujące wyrażenie w **Jeśli** działania **warunku** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="70baf-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. <span data-ttu-id="70baf-148">Przeciągnij kolejny **Jeśli** działania z **przepływ sterowania** sekcji **przybornika** i upuść je w **następnie** sekcji pierwszego **Jeśli** działania.</span><span class="sxs-lookup"><span data-stu-id="70baf-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>  
  
11. <span data-ttu-id="70baf-149">Wpisz poniższe wyrażenie w nowo dodanym **Jeśli** działania **warunku** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="70baf-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
12. <span data-ttu-id="70baf-150">Przeciągnij dwa **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść je, tak aby jedna jest **następnie** sekcji nowo dodany **Jeśli** działania, a druga jest **Else** sekcji.</span><span class="sxs-lookup"><span data-stu-id="70baf-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>  
  
13. <span data-ttu-id="70baf-151">Kliknij przycisk **WriteLine** działania w **następnie** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="70baf-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. <span data-ttu-id="70baf-152">Kliknij przycisk **WriteLine** działania w **Else** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="70baf-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     <span data-ttu-id="70baf-153">Poniższy przykład przedstawia ukończonych przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="70baf-153">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="70baf-154">![Ukończono sekwencyjnego przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="70baf-154">![Completed Sequential Workflow](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="70baf-155">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="70baf-155">To build the workflow</span></span>  
  
1.  <span data-ttu-id="70baf-156">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="70baf-156">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="70baf-157">Dla instrukcje na temat uruchamiania przepływu pracy, zobacz temat dalej [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="70baf-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="70baf-158">Jeśli wykonano już [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) kroku z innego stylu przepływu pracy i uruchomić go za pomocą sekwencyjnego przepływu pracy z tym kroku, przejdź do [Aby skompilować i uruchomić aplikację](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)części [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="70baf-158">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70baf-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70baf-159">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="70baf-160">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="70baf-160">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="70baf-161">Projektowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="70baf-161">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="70baf-162">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="70baf-162">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="70baf-163">Instrukcje: Tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="70baf-163">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="70baf-164">Instrukcje: Uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="70baf-164">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
