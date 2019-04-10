---
title: 'Instrukcje: Tworzenie sekwencyjnego przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: c8a16dc0269fbd768a73e99f15f53e38c207a8d4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326843"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="48823-102">Instrukcje: Tworzenie sekwencyjnego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="48823-102">How to: Create a Sequential Workflow</span></span>
<span data-ttu-id="48823-103">Przepływy pracy można skonstruować z wbudowanych działań, a także z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="48823-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="48823-104">Ten temat prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowanych działań, takich jak <xref:System.Activities.Statements.Sequence> działanie i działań niestandardowych z poprzedniego [jak: Utwórz działanie](how-to-create-an-activity.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="48823-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="48823-105">Przepływ pracy modeli gra odgadnięcia liczb.</span><span class="sxs-lookup"><span data-stu-id="48823-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48823-106">Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach.</span><span class="sxs-lookup"><span data-stu-id="48823-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="48823-107">Aby ukończyć ten temat, najpierw musisz zakończyć [jak: Utwórz działanie](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="48823-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48823-108">Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="48823-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-workflow"></a><span data-ttu-id="48823-109">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="48823-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="48823-110">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="48823-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="48823-111">W **zainstalowane**, **wspólne elementy** węzeł **przepływu pracy**.</span><span class="sxs-lookup"><span data-stu-id="48823-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="48823-112">Wybierz **działania** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="48823-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="48823-113">Typ `SequentialNumberGuessWorkflow` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="48823-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="48823-114">Przeciągnij **sekwencji** działanie z **przepływ sterowania** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety na przepływ pracy powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="48823-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="48823-115">Aby utworzyć zmienne przepływu pracy i argumenty</span><span class="sxs-lookup"><span data-stu-id="48823-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="48823-116">Kliknij dwukrotnie **SequentialNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania w Projektancie przepływu pracy, jeśli nie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="48823-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="48823-117">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="48823-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="48823-118">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="48823-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="48823-119">Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.</span><span class="sxs-lookup"><span data-stu-id="48823-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="48823-120">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="48823-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="48823-121">Typ `Turns` do **nazwa** pole, które jest pod nowo dodanym `MaxNumber` argument, wybierz opcję **się** z **kierunek** listy rozwijanej, wybierz opcję  **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="48823-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="48823-122">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="48823-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="48823-123">Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="48823-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="48823-124">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="48823-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="48823-125">Jeśli nie **Tworzenie zmiennej** zostanie wyświetlone okno, kliknij przycisk **sekwencji** działania na powierzchni projektanta przepływu pracy, aby go zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="48823-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="48823-126">Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="48823-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="48823-127">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="48823-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="48823-128">Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="48823-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="48823-129">Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta działań, aby zamknąć **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="48823-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="48823-130">Aby dodać działania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="48823-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="48823-131">Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i upuść je na **sekwencji** działania.</span><span class="sxs-lookup"><span data-stu-id="48823-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="48823-132">Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.</span><span class="sxs-lookup"><span data-stu-id="48823-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="48823-133">Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="48823-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="48823-134">Przeciągnij **DoWhile** działanie z **przepływ sterowania** części **przybornika** i upuść je na przepływ pracy, tak aby była poniżej **przypisać** działanie.</span><span class="sxs-lookup"><span data-stu-id="48823-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>  
  
3. <span data-ttu-id="48823-135">Wpisz następujące wyrażenie do **DoWhile** działania **warunek** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="48823-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <span data-ttu-id="48823-136">A <xref:System.Activities.Statements.DoWhile> wykonuje działania podrzędne działania, a następnie oblicza jego <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span><span class="sxs-lookup"><span data-stu-id="48823-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="48823-137">Jeśli <xref:System.Activities.Statements.DoWhile.Condition%2A> daje w wyniku `True`, następnie działań w <xref:System.Activities.Statements.DoWhile> wykonywania ponownie.</span><span class="sxs-lookup"><span data-stu-id="48823-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="48823-138">W tym przykładzie jest szacowana wynik użytkownika i <xref:System.Activities.Statements.DoWhile> kontynuowany do momentu odgadnięcia jest poprawna.</span><span class="sxs-lookup"><span data-stu-id="48823-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>  
  
4. <span data-ttu-id="48823-139">Przeciągnij **monitu** działanie z **NumberGuessWorkflowActivities** części **przybornika** i upuść je **DoWhile** działania w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="48823-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>  
  
5. <span data-ttu-id="48823-140">W **okno właściwości**, typ `"EnterGuess"` wraz z cudzysłowami do **Nazwa_zakładki** pole wartości właściwości dla **monitu** działania.</span><span class="sxs-lookup"><span data-stu-id="48823-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="48823-141">Typ `Guess` do **wynik** właściwości wartość pola, a następnie wpisz następujące wyrażenie w **tekstu** okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="48823-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="48823-142">Jeśli **okno właściwości** nie jest wyświetlany, wybierz opcję **okno właściwości** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="48823-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
6. <span data-ttu-id="48823-143">Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i upuść je **DoWhile** działania, tak że następuje po **Monitu** działania.</span><span class="sxs-lookup"><span data-stu-id="48823-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48823-144">Po umieszczeniu **przypisać** aktywności, należy pamiętać, jak automatycznie dodaje projektanta przepływów pracy **sekwencji** działania, które zawierają zarówno **monitu** działanie i nowo dodane **Przypisać** działania.</span><span class="sxs-lookup"><span data-stu-id="48823-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>  
  
7. <span data-ttu-id="48823-145">Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.</span><span class="sxs-lookup"><span data-stu-id="48823-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
8. <span data-ttu-id="48823-146">Przeciągnij **Jeśli** działanie z **przepływ sterowania** części **przybornika** i upuść je **sekwencji** działania, tak że następuje po nowo dodane **przypisać** działania.</span><span class="sxs-lookup"><span data-stu-id="48823-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>  
  
9. <span data-ttu-id="48823-147">Wpisz następujące wyrażenie do **Jeśli** działania **warunek** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="48823-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. <span data-ttu-id="48823-148">Przeciągnij kolejny **Jeśli** działanie z **przepływ sterowania** części **przybornika** i upuść je **następnie** części pierwszego **Jeśli** działania.</span><span class="sxs-lookup"><span data-stu-id="48823-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>  
  
11. <span data-ttu-id="48823-149">Wprowadź następujące wyrażenie w nowo dodanym **Jeśli** działania **warunek** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="48823-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
12. <span data-ttu-id="48823-150">Przeciągnij dwa **WriteLine** działania z **podstawowych** części **przybornika** i upuścić je tak, aby jeden **następnie** sekcji nowo dodane **Jeśli** działania i jeden znajduje się w **Else** sekcji.</span><span class="sxs-lookup"><span data-stu-id="48823-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>  
  
13. <span data-ttu-id="48823-151">Kliknij przycisk **WriteLine** działania w **następnie** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="48823-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
14. <span data-ttu-id="48823-152">Kliknij przycisk **WriteLine** działania w **Else** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="48823-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
     <span data-ttu-id="48823-153">Poniższy przykład ilustruje ukończony przepływ pracy:</span><span class="sxs-lookup"><span data-stu-id="48823-153">The following example illustrates the completed workflow:</span></span>  
  
     ![Zrzut ekranu pokazujący ukończone sekwencyjnego przepływu pracy.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)  
  
## <a name="to-build-the-workflow"></a><span data-ttu-id="48823-155">Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="48823-155">To build the workflow</span></span>  
  
1. <span data-ttu-id="48823-156">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="48823-156">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="48823-157">Aby uzyskać instrukcje na temat sposobu uruchamiania przepływu pracy, zobacz następny temat, [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="48823-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="48823-158">Jeśli wykonano już [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md) kroku przy użyciu innego stylu przepływu pracy, a chcesz uruchomić go za pomocą sekwencyjnego przepływu pracy, w tym kroku, przejdź do sekcji [Aby skompilować i uruchomić aplikację](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) części [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="48823-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48823-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48823-159">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="48823-160">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="48823-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="48823-161">Projektowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="48823-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="48823-162">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="48823-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="48823-163">Instrukcje: Tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="48823-163">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="48823-164">Instrukcje: Uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="48823-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
