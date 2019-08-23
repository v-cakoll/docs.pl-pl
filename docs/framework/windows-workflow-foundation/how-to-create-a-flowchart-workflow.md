---
title: 'Instrukcje: Tworzenie przepływu pracy schematu blokowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 6d67629503d5acfeff7e14e1889a047444a8d399
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962394"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="6d108-102">Instrukcje: Tworzenie przepływu pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="6d108-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="6d108-103">Przepływy pracy mogą być zbudowane z wbudowanych działań, a także z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6d108-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="6d108-104">W tym temacie przedstawiono procedurę tworzenia przepływu pracy, który używa zarówno wbudowanych działań, jak <xref:System.Activities.Statements.Flowchart> działania, jak i działań niestandardowych, z poprzednich [metod: Utwórz temat działania](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="6d108-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="6d108-105">Przepływ pracy modeluje grę z liczbą odgadnąć.</span><span class="sxs-lookup"><span data-stu-id="6d108-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d108-106">Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="6d108-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="6d108-107">Aby ukończyć ten temat, należy najpierw wykonać [następujące czynności: Utwórz działanie](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="6d108-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d108-108">Aby pobrać kompletną wersję samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="6d108-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="6d108-109">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="6d108-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="6d108-110">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowActivities** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="6d108-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="6d108-111">W węźle **zainstalowane**, **wspólne elementy** wybierz pozycję **przepływ pracy**.</span><span class="sxs-lookup"><span data-stu-id="6d108-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="6d108-112">Wybierz **działanie** z listy **przepływów pracy** .</span><span class="sxs-lookup"><span data-stu-id="6d108-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="6d108-113">Wpisz `FlowchartNumberGuessWorkflow` tekst w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="6d108-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="6d108-114">Przeciągnij działanie **Flowchart** z sekcji **Flowchart** w przyborniku i upuść je do **działania Drop tutaj** etykieta na powierzchni projektowej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6d108-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="6d108-115">Aby utworzyć zmienne i argumenty przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6d108-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="6d108-116">Kliknij dwukrotnie pozycję **FlowchartNumberGuessWorkflow. XAML** w **Eksplorator rozwiązań** , aby wyświetlić przepływ pracy w projektancie, jeśli nie jest on jeszcze wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="6d108-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="6d108-117">Kliknij pozycję **argumenty** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="6d108-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="6d108-118">Kliknij przycisk **Utwórz argument**.</span><span class="sxs-lookup"><span data-stu-id="6d108-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="6d108-119">Wpisz `MaxNumber` **w** polu **Nazwa** , wybierz z listy rozwijanej **kierunek** , wybierz **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER, aby zapisać argument.</span><span class="sxs-lookup"><span data-stu-id="6d108-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="6d108-120">Kliknij przycisk **Utwórz argument**.</span><span class="sxs-lookup"><span data-stu-id="6d108-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="6d108-121">Wpisz `Turns` w polu **Nazwa** , który znajduje się poniżej nowo dodanego `MaxNumber` argumentu , wybierz pozycję z listy rozwijanej **kierunek** , wybierz pozycję **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="6d108-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="6d108-122">Kliknij pozycję **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć okienko **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="6d108-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="6d108-123">Kliknij przycisk **zmienne** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **zmienne** .</span><span class="sxs-lookup"><span data-stu-id="6d108-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="6d108-124">Kliknij pozycję **Utwórz zmienną**.</span><span class="sxs-lookup"><span data-stu-id="6d108-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="6d108-125">Jeśli nie zostanie wyświetlone pole **Utwórz zmienną** , kliknij <xref:System.Activities.Statements.Flowchart> działanie na powierzchni projektanta przepływu pracy, aby je wybrać.</span><span class="sxs-lookup"><span data-stu-id="6d108-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="6d108-126">Wpisz `Guess` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="6d108-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="6d108-127">Kliknij pozycję **Utwórz zmienną**.</span><span class="sxs-lookup"><span data-stu-id="6d108-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="6d108-128">Wpisz `Target` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="6d108-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="6d108-129">Kliknij pozycję **zmienne** w lewej dolnej części okna projektanta działań, aby zamknąć okienko **zmienne** .</span><span class="sxs-lookup"><span data-stu-id="6d108-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="6d108-130">Aby dodać działania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6d108-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="6d108-131">Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w przyborniku i umieść je nad węzłem **początkowym** znajdującym się w górnej części schematu blokowego.</span><span class="sxs-lookup"><span data-stu-id="6d108-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="6d108-132">Gdy działanie **Assign** znajduje się nad węzłem **startowym** , zostaną wyświetlone trzy trójkąty wokół węzła **Start** .</span><span class="sxs-lookup"><span data-stu-id="6d108-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="6d108-133">Upuść działanie **Assign** na trójkącie, które znajduje się bezpośrednio pod węzłem **początkowym** .</span><span class="sxs-lookup"><span data-stu-id="6d108-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="6d108-134">Spowoduje to połączenie dwóch elementów i wyznaczenie działania **przypisania** jako pierwszego działania w schemacie blokowym.</span><span class="sxs-lookup"><span data-stu-id="6d108-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6d108-135">Działania mogą być również wskazywane jako działanie uruchamiania w przepływie pracy przez ręczne łączenie z tym działaniem z węzłem początkowym.</span><span class="sxs-lookup"><span data-stu-id="6d108-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="6d108-136">Aby to zrobić, umieść kursor myszy nad węzłem **startowym** , kliknij jeden z prostokątów, który pojawia się, gdy wskaźnik myszy znajduje się nad węzłem **startowym** , i przeciągnij linię łączącą w dół do żądanego działania i upuść ją na jednym z prostokątów, które są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="6d108-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="6d108-137">Możesz również wyznaczyć działanie jako działanie uruchamiania, klikając je prawym przyciskiem myszy i wybierając pozycję **Ustaw jako węzeł startowy**.</span><span class="sxs-lookup"><span data-stu-id="6d108-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="6d108-138">Wpisz `Target` w polu **do** i poniższe wyrażenie w polu  **C# wprowadź wyrażenie** lub **wprowadź wyrażenie w języku VB** .</span><span class="sxs-lookup"><span data-stu-id="6d108-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="6d108-139">Jeśli okno **Przybornik** nie jest wyświetlane, wybierz pozycję **Przybornik** z menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="6d108-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="6d108-140">Przeciągnij działanie **monitu** z sekcji **NumberGuessWorkflowActivities** w przyborniku, upuść je poniżej akcji **Przypisz** z poprzedniego kroku, a następnie połącz działanie monitu z przypisaniem działania.</span><span class="sxs-lookup"><span data-stu-id="6d108-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="6d108-141">Istnieją trzy sposoby łączenia tych dwóch działań.</span><span class="sxs-lookup"><span data-stu-id="6d108-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="6d108-142">Pierwszy sposób polega na nawiązaniu połączenia w trakcie upuszczania działania **monitu** w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="6d108-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="6d108-143">Przeciągając działanie monitu do przepływu pracy, umieść je nad przydziałem **Assign** i upuść je na jednym z czterech trójkątów, które pojawiają się, gdy działanie **monitu** znajduje się nad przypisaniem.</span><span class="sxs-lookup"><span data-stu-id="6d108-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="6d108-144">Drugi sposób polega na porzucenia działania **monitu** na przepływ pracy w odpowiedniej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="6d108-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="6d108-145">Następnie przesuń wskaźnik myszy nad działanie przypisywania i przeciągnij jeden z prostokątów, które pojawiają się w dół do działania **monitu** .</span><span class="sxs-lookup"><span data-stu-id="6d108-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="6d108-146">Przeciągnij myszą tak, aby linia łącząca z działania **Assign** łączyła się z jednym z prostokątów działania **monitu** , a następnie zwolnij przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="6d108-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="6d108-147">Trzeci sposób jest bardzo podobny do pierwszego, z tą różnicą, że zamiast przeciągać działanie **monitu** z **przybornika**, przeciągasz go z jego lokalizacji na powierzchni projektowej przepływu pracy, przesuwaj go na działanie przypisywania i upuść je na jedną z widoczne trójkąty.</span><span class="sxs-lookup"><span data-stu-id="6d108-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="6d108-148">W **oknie właściwości** działania monitu wpisz `"EnterGuess"` , w tym cudzysłowy w polu wartość właściwości **zakładkaname** .</span><span class="sxs-lookup"><span data-stu-id="6d108-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="6d108-149">Wpisz `Guess` w polu wartość właściwości **wynik** i wpisz następujące wyrażenie w polu właściwości **Text** .</span><span class="sxs-lookup"><span data-stu-id="6d108-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="6d108-150">Jeśli **okno właściwości** nie jest wyświetlane, wybierz pozycję **okno właściwości** w menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="6d108-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="6d108-151">Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w przyborniku i połącz je przy użyciu jednej z metod opisanych w poprzednim kroku, tak aby była niższa od działania **monitu** .</span><span class="sxs-lookup"><span data-stu-id="6d108-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="6d108-152">Wpisz `Turns` w polu **do** i `Turns + 1` w polu **wprowadź C# wyrażenie** lub wprowadź wyrażenie w **języku VB** .</span><span class="sxs-lookup"><span data-stu-id="6d108-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="6d108-153">Przeciągnij element **FlowDecision** z sekcji **Flowchart** w przyborniku i połącz go pod działaniem **Assign** .</span><span class="sxs-lookup"><span data-stu-id="6d108-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="6d108-154">W **oknie właściwości**wpisz następujące wyrażenie w polu wartość właściwości **warunek** .</span><span class="sxs-lookup"><span data-stu-id="6d108-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="6d108-155">Przeciągnij kolejną aktywność **FlowDecision** z **przybornika** i upuść ją poniżej pierwszego.</span><span class="sxs-lookup"><span data-stu-id="6d108-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="6d108-156">Połącz dwa działania, przeciągając od prostokąta, który jest oznaczony jako **false** w górnym działaniu **FlowDecision** do prostokąta w górnej części drugiego działania **FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="6d108-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="6d108-157">Jeśli nie widzisz etykiet **prawda** i **Fałsz** w **FlowDecision**, umieść wskaźnik myszy nad **FlowDecisionem**.</span><span class="sxs-lookup"><span data-stu-id="6d108-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="6d108-158">Kliknij drugie działanie **FlowDecision** , aby je wybrać.</span><span class="sxs-lookup"><span data-stu-id="6d108-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="6d108-159">W **oknie właściwości**wpisz następujące wyrażenie w polu wartość właściwości **warunek** .</span><span class="sxs-lookup"><span data-stu-id="6d108-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="6d108-160">Przeciągnij dwie działania **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je tak, aby znajdowały się obok dwóch działań **FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="6d108-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="6d108-161">Połącz **rzeczywistą** akcję dolnego działania **FlowDecision** do lewego działania **WriteLine** i **wartość false** dla działania **WriteLine** z prawej strony.</span><span class="sxs-lookup"><span data-stu-id="6d108-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="6d108-162">Kliknij z lewej strony działanie **WriteLine** , aby je zaznaczyć, a następnie wpisz następujące wyrażenie w polu wartość właściwości **tekst** w **oknie właściwości**.</span><span class="sxs-lookup"><span data-stu-id="6d108-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="6d108-163">Połącz metodę **WriteLine** z lewą stroną działania monitu o powyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="6d108-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="6d108-164">Kliknij prawym przyciskiem, aby go zaznaczyć, i wpisz następujące wyrażenie w polu wartość właściwości **tekst** w **oknie właściwości**.</span><span class="sxs-lookup"><span data-stu-id="6d108-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="6d108-165">Połącz działanie **WriteLine** z prawą stroną działania monitu.</span><span class="sxs-lookup"><span data-stu-id="6d108-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="6d108-166">Poniższy przykład ilustruje ukończony przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="6d108-166">The following example illustrates the completed workflow.</span></span>  
  
     ![Diagram przedstawiający ukończony schemat blokowy Windows Workflow Foundation.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="6d108-168">Aby skompilować przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="6d108-168">To build the workflow</span></span>  
  
1. <span data-ttu-id="6d108-169">Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6d108-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="6d108-170">Instrukcje dotyczące sposobu uruchamiania przepływu pracy można znaleźć w następnym temacie, [jak: Uruchom przepływ pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6d108-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="6d108-171">Jeśli zostały już wykonane [następujące instrukcje: Uruchom krok przepływu](how-to-run-a-workflow.md) pracy z innym stylem przepływu pracy i chcę uruchomić go za pomocą przepływu pracy Flowchart z tego kroku, przejdź do tematu [ [w celu skompilowania i uruchomienia aplikacji](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) w temacie How to: Uruchom przepływ pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6d108-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d108-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d108-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="6d108-173">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="6d108-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="6d108-174">Projektowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="6d108-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="6d108-175">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="6d108-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="6d108-176">Instrukcje: Tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="6d108-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="6d108-177">Instrukcje: Uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6d108-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
