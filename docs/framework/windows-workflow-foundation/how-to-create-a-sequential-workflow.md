---
title: 'Instrukcje: Tworzenie sekwencyjnego przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 61e3f01b1259536ff15d71526e91aef42069722e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989704"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="62a97-102">Instrukcje: Tworzenie sekwencyjnego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="62a97-102">How to: Create a Sequential Workflow</span></span>

<span data-ttu-id="62a97-103">Przepływy pracy mogą być zbudowane z wbudowanych działań, a także z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="62a97-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="62a97-104">W tym temacie przedstawiono procedurę tworzenia przepływu pracy, który używa zarówno wbudowanych działań, jak <xref:System.Activities.Statements.Sequence> działania, jak i działań niestandardowych, z poprzednich [metod: Utwórz temat działania](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="62a97-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="62a97-105">Przepływ pracy modeluje grę z liczbą odgadnąć.</span><span class="sxs-lookup"><span data-stu-id="62a97-105">The workflow models a number guessing game.</span></span>

> [!NOTE]
> <span data-ttu-id="62a97-106">Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="62a97-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="62a97-107">Aby ukończyć ten temat, należy najpierw wykonać [następujące czynności: Utwórz działanie](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="62a97-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="62a97-108">Aby pobrać kompletną wersję samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="62a97-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-workflow"></a><span data-ttu-id="62a97-109">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="62a97-109">To create the workflow</span></span>

1. <span data-ttu-id="62a97-110">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowActivities** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="62a97-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>

2. <span data-ttu-id="62a97-111">W węźle **zainstalowane**, **wspólne elementy** wybierz pozycję **przepływ pracy**.</span><span class="sxs-lookup"><span data-stu-id="62a97-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="62a97-112">Wybierz **działanie** z listy **przepływów pracy** .</span><span class="sxs-lookup"><span data-stu-id="62a97-112">Select **Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="62a97-113">Wpisz `SequentialNumberGuessWorkflow` tekst w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="62a97-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>

4. <span data-ttu-id="62a97-114">Przeciągnij działanie **sekwencji** z sekcji **przepływ sterowania** w **przyborniku** i upuść je na etykiecie **działania upuść** na powierzchni projektowej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="62a97-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>

## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="62a97-115">Aby utworzyć zmienne i argumenty przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="62a97-115">To create the workflow variables and arguments</span></span>

1. <span data-ttu-id="62a97-116">Kliknij dwukrotnie pozycję **SequentialNumberGuessWorkflow. XAML** w **Eksplorator rozwiązań** , aby wyświetlić przepływ pracy w projektancie, jeśli nie jest on jeszcze wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="62a97-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>

2. <span data-ttu-id="62a97-117">Kliknij pozycję **argumenty** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="62a97-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>

3. <span data-ttu-id="62a97-118">Kliknij przycisk **Utwórz argument**.</span><span class="sxs-lookup"><span data-stu-id="62a97-118">Click **Create Argument**.</span></span>

4. <span data-ttu-id="62a97-119">Wpisz `MaxNumber` **w** polu **Nazwa** , wybierz z listy rozwijanej **kierunek** , wybierz **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER, aby zapisać argument.</span><span class="sxs-lookup"><span data-stu-id="62a97-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>

5. <span data-ttu-id="62a97-120">Kliknij przycisk **Utwórz argument**.</span><span class="sxs-lookup"><span data-stu-id="62a97-120">Click **Create Argument**.</span></span>

6. <span data-ttu-id="62a97-121">Wpisz `Turns` w polu **Nazwa** , który znajduje się poniżej nowo dodanego `MaxNumber` argumentu, wybierz **pozycję z listy** rozwijanej **kierunek** , wybierz pozycję **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="62a97-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>

7. <span data-ttu-id="62a97-122">Kliknij pozycję **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć okienko **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="62a97-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

8. <span data-ttu-id="62a97-123">Kliknij przycisk **zmienne** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **zmienne** .</span><span class="sxs-lookup"><span data-stu-id="62a97-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>

9. <span data-ttu-id="62a97-124">Kliknij pozycję **Utwórz zmienną**.</span><span class="sxs-lookup"><span data-stu-id="62a97-124">Click **Create Variable**.</span></span>

    > [!TIP]
    > <span data-ttu-id="62a97-125">Jeśli nie zostanie wyświetlone pole **Utwórz zmienną** , kliknij działanie **sekwencji** na powierzchni projektanta przepływu pracy, aby je wybrać.</span><span class="sxs-lookup"><span data-stu-id="62a97-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>

10. <span data-ttu-id="62a97-126">Wpisz `Guess` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="62a97-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

11. <span data-ttu-id="62a97-127">Kliknij pozycję **Utwórz zmienną**.</span><span class="sxs-lookup"><span data-stu-id="62a97-127">Click **Create Variable**.</span></span>

12. <span data-ttu-id="62a97-128">Wpisz `Target` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="62a97-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

13. <span data-ttu-id="62a97-129">Kliknij pozycję **zmienne** w lewej dolnej części okna projektanta działań, aby zamknąć okienko **zmienne** .</span><span class="sxs-lookup"><span data-stu-id="62a97-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>

## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="62a97-130">Aby dodać działania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="62a97-130">To add the workflow activities</span></span>

1. <span data-ttu-id="62a97-131">Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w **przyborniku** i upuść je na działanie **sekwencji** .</span><span class="sxs-lookup"><span data-stu-id="62a97-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="62a97-132">Wpisz `Target` w polu **do** i poniższe wyrażenie w polu  **C# wprowadź wyrażenie** lub **wprowadź wyrażenie w języku VB** .</span><span class="sxs-lookup"><span data-stu-id="62a97-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > <span data-ttu-id="62a97-133">Jeśli okno **Przybornik** nie jest wyświetlane, wybierz pozycję **Przybornik** z menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="62a97-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

2. <span data-ttu-id="62a97-134">Przeciągnij działanie **DoWhile** z sekcji **przepływ sterowania** w **przyborniku** i upuść je w przepływie pracy, tak aby była niższa od akcji **przypisywania** .</span><span class="sxs-lookup"><span data-stu-id="62a97-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>

3. <span data-ttu-id="62a97-135">Wpisz następujące wyrażenie w polu wartość właściwości **warunek** działania **DoWhile** .</span><span class="sxs-lookup"><span data-stu-id="62a97-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <span data-ttu-id="62a97-136">Działanie wykonuje działania podrzędne, a następnie szacuje <xref:System.Activities.Statements.DoWhile.Condition%2A>je. <xref:System.Activities.Statements.DoWhile></span><span class="sxs-lookup"><span data-stu-id="62a97-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="62a97-137">Jeśli zostanie <xref:System.Activities.Statements.DoWhile.Condition%2A> obliczona `True`wartość, działania <xref:System.Activities.Statements.DoWhile> wykonywane ponownie.</span><span class="sxs-lookup"><span data-stu-id="62a97-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="62a97-138">W tym przykładzie oszacowanie użytkownika jest oceniane i <xref:System.Activities.Statements.DoWhile> kontynuuje do momentu poprawienia wartości.</span><span class="sxs-lookup"><span data-stu-id="62a97-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>

4. <span data-ttu-id="62a97-139">Przeciągnij działanie **monitu** z sekcji **NumberGuessWorkflowActivities** w **przyborniku** i upuść je w działaniu **DoWhile** z poprzedniego kroku.</span><span class="sxs-lookup"><span data-stu-id="62a97-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>

5. <span data-ttu-id="62a97-140">W **oknie właściwości**, w polu `"EnterGuess"` wartość właściwości **zakładkiname** dla działania **monitu** wpisz cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="62a97-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="62a97-141">Wpisz `Guess` w polu wartość właściwości **wynik** i wpisz następujące wyrażenie w polu właściwości **Text** .</span><span class="sxs-lookup"><span data-stu-id="62a97-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > <span data-ttu-id="62a97-142">Jeśli **okno właściwości** nie jest wyświetlane, wybierz pozycję **okno właściwości** w menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="62a97-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

6. <span data-ttu-id="62a97-143">Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w **przyborniku** i upuść je w działaniu **DoWhile** , tak aby była zgodna z działaniem **monitu** .</span><span class="sxs-lookup"><span data-stu-id="62a97-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>

    > [!NOTE]
    > <span data-ttu-id="62a97-144">Po porzucenia działania **Przypisz** należy zwrócić uwagę, jak Projektant przepływu pracy automatycznie dodaje działanie **sekwencji** , aby zawierało zarówno działanie **monitu** , jak i nowo dodane działanie **przypisywania** .</span><span class="sxs-lookup"><span data-stu-id="62a97-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>

7. <span data-ttu-id="62a97-145">Wpisz `Turns` w polu **do** i `Turns + 1` w polu **wprowadź C# wyrażenie** lub wprowadź wyrażenie w **języku VB** .</span><span class="sxs-lookup"><span data-stu-id="62a97-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

8. <span data-ttu-id="62a97-146">Przeciągnij działanie **if** z sekcji **przepływ sterowania** w **przyborniku** i upuść je w działaniu **sekwencji** , tak aby była zgodna z nowo dodanym działaniem **przypisywania** .</span><span class="sxs-lookup"><span data-stu-id="62a97-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>

9. <span data-ttu-id="62a97-147">Wpisz następujące wyrażenie w polu wartość właściwości **warunek** działania **if** .</span><span class="sxs-lookup"><span data-stu-id="62a97-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. <span data-ttu-id="62a97-148">Przeciągnij inną aktywność w **przypadku** działania z sekcji **przepływ sterowania** w **przyborniku** i upuść ją w **sekcji po** pierwszej aktywności **if** .</span><span class="sxs-lookup"><span data-stu-id="62a97-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>

11. <span data-ttu-id="62a97-149">Wpisz następujące wyrażenie w polu wartość właściwości **warunek** dla nowo dodanego działania **if** .</span><span class="sxs-lookup"><span data-stu-id="62a97-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>

    ```text
    Guess < Target
    ```

12. <span data-ttu-id="62a97-150">Przeciągnij dwie **działania WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je tak, aby były widoczne w **sekcji nowo** dodanego działania **if** , a jeden z nich znajduje się w sekcji **else** .</span><span class="sxs-lookup"><span data-stu-id="62a97-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>

13. <span data-ttu-id="62a97-151">Kliknij działanie **WriteLine** w sekcji Then, aby je zaznaczyć, a **następnie** wpisz następujące wyrażenie w polu wartość właściwości **Text** .</span><span class="sxs-lookup"><span data-stu-id="62a97-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too low."
    ```

14. <span data-ttu-id="62a97-152">Kliknij działanie **WriteLine** w sekcji **else** , aby je zaznaczyć, a następnie wpisz następujące wyrażenie w polu wartość właściwości **Text** .</span><span class="sxs-lookup"><span data-stu-id="62a97-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too high."
    ```

     <span data-ttu-id="62a97-153">Poniższy przykład ilustruje ukończony przepływ pracy:</span><span class="sxs-lookup"><span data-stu-id="62a97-153">The following example illustrates the completed workflow:</span></span>

     ![Zrzut ekranu przedstawiający ukończony sekwencyjny przepływ pracy.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a><span data-ttu-id="62a97-155">Aby skompilować przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="62a97-155">To build the workflow</span></span>

1. <span data-ttu-id="62a97-156">Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="62a97-156">Press CTRL+SHIFT+B to build the solution.</span></span>

     <span data-ttu-id="62a97-157">Instrukcje dotyczące sposobu uruchamiania przepływu pracy można znaleźć w następnym temacie, [jak: Uruchom przepływ pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="62a97-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="62a97-158">Jeśli zostały już wykonane [następujące instrukcje: Uruchom krok przepływu](how-to-run-a-workflow.md) pracy z innym stylem przepływu pracy i chcesz uruchomić go przy użyciu sekwencyjnego przepływu pracy z tego kroku, przejdź do sekcji [Aby skompilować i uruchomić](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [aplikację w temacie How to: Uruchom przepływ pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="62a97-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62a97-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62a97-159">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="62a97-160">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="62a97-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="62a97-161">Projektowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="62a97-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="62a97-162">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="62a97-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="62a97-163">Instrukcje: Tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="62a97-163">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="62a97-164">Instrukcje: Uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="62a97-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
