---
title: 'Instrukcje: Tworzenie przepływu pracy schematu blokowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 15cf94d5ea191435723f754f35e43d65632142e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773499"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="55db2-102">Instrukcje: Tworzenie przepływu pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="55db2-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="55db2-103">Przepływy pracy można skonstruować z wbudowanych działań, a także z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="55db2-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="55db2-104">Ten temat prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowanych działań, takich jak <xref:System.Activities.Statements.Flowchart> działanie i działań niestandardowych z poprzedniego [jak: Utwórz działanie](how-to-create-an-activity.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="55db2-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="55db2-105">Przepływ pracy modeli gra odgadnięcia liczb.</span><span class="sxs-lookup"><span data-stu-id="55db2-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55db2-106">Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach.</span><span class="sxs-lookup"><span data-stu-id="55db2-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="55db2-107">Aby ukończyć ten temat, najpierw musisz zakończyć [jak: Utwórz działanie](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="55db2-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55db2-108">Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="55db2-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="55db2-109">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="55db2-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="55db2-110">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="55db2-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="55db2-111">W **zainstalowane**, **wspólne elementy** węzeł **przepływu pracy**.</span><span class="sxs-lookup"><span data-stu-id="55db2-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="55db2-112">Wybierz **działania** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="55db2-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="55db2-113">Typ `FlowchartNumberGuessWorkflow` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="55db2-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="55db2-114">Przeciągnij **schemat blokowy** działanie z **schemat blokowy** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety na przepływ pracy powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="55db2-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="55db2-115">Aby utworzyć zmienne przepływu pracy i argumenty</span><span class="sxs-lookup"><span data-stu-id="55db2-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="55db2-116">Kliknij dwukrotnie **FlowchartNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania w Projektancie przepływu pracy, jeśli nie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="55db2-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="55db2-117">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="55db2-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="55db2-118">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="55db2-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="55db2-119">Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.</span><span class="sxs-lookup"><span data-stu-id="55db2-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="55db2-120">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="55db2-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="55db2-121">Typ `Turns` do **nazwa** pole, które jest pod nowo dodanym `MaxNumber` argument, wybierz opcję **się** z **kierunek** listy rozwijanej, wybierz opcję  **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="55db2-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="55db2-122">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="55db2-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="55db2-123">Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="55db2-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="55db2-124">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="55db2-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="55db2-125">Jeśli nie **Tworzenie zmiennej** zostanie wyświetlone okno, kliknij przycisk <xref:System.Activities.Statements.Flowchart> działania na powierzchni projektanta przepływu pracy, aby go zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="55db2-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="55db2-126">Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="55db2-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="55db2-127">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="55db2-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="55db2-128">Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="55db2-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="55db2-129">Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta działań, aby zamknąć **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="55db2-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="55db2-130">Aby dodać działania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="55db2-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="55db2-131">Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i zatrzymaj wskaźnik myszy nad **Start** węzła, który znajduje się w górnej części Schemat blokowy.</span><span class="sxs-lookup"><span data-stu-id="55db2-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="55db2-132">Gdy **przypisać** działań znajduje się nad **Start** węzła, trzy trójkąty wokół niego pojawią **Start** węzła.</span><span class="sxs-lookup"><span data-stu-id="55db2-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="55db2-133">Upuść **przypisać** działania na trójkąt, który jest bezpośrednio poniżej **Start** węzła.</span><span class="sxs-lookup"><span data-stu-id="55db2-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="55db2-134">To łączenie ze sobą dwa elementy, ustawiając **przypisać** działań jako pierwsze działanie w schemacie blokowym.</span><span class="sxs-lookup"><span data-stu-id="55db2-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="55db2-135">Działania mogą być wskazywane jako wyjścia działania w przepływie pracy tworząc ręcznie ich działanie węzeł początkowy.</span><span class="sxs-lookup"><span data-stu-id="55db2-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="55db2-136">Aby to zrobić, umieść kursor myszy nad **Start** węzła, kliknij jeden z prostokątami, które są wyświetlane, gdy wskaźnik myszy znajduje się nad **Start** węzeł, a następnie przeciągnij w nawiązywaniu połączenia wiersz w dół do żądanej działania i upuść je na jednym z prostokąty, które są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="55db2-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="55db2-137">Działania można wyznaczyć jako działanie początkowe, klikając prawym przyciskiem myszy it i wybierając polecenie **ustawiona jako węzeł Start**.</span><span class="sxs-lookup"><span data-stu-id="55db2-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="55db2-138">Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.</span><span class="sxs-lookup"><span data-stu-id="55db2-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="55db2-139">Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="55db2-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="55db2-140">Przeciągnij **monitu** działanie z **NumberGuessWorkflowActivities** części **przybornika**, upuść go poniżej **przypisać** działania z poprzedniego kroku, a następnie połącz **monitu** działanie **przypisać** działania.</span><span class="sxs-lookup"><span data-stu-id="55db2-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="55db2-141">Istnieją trzy sposoby, aby połączyć dwa działania.</span><span class="sxs-lookup"><span data-stu-id="55db2-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="55db2-142">Pierwszy sposób to ich połączenia, ponieważ usuniesz **monitu** działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="55db2-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="55db2-143">Podczas przeciągania **monitu** działania w przepływie pracy, jego Zatrzymaj wskaźnik myszy **przypisać** działania i upuść je na jeden z czterech trójkątów, widocznych **monitu** działanie jest nad **przypisać** działania.</span><span class="sxs-lookup"><span data-stu-id="55db2-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="55db2-144">Drugi sposób polega na upuszczanie **monitu** działanie do przepływu pracy w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="55db2-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="55db2-145">Następnie umieść kursor myszy nad **przypisać** działania i przeciągnij jeden z prostokątami, które pojawia się w dół do **monitu** działania.</span><span class="sxs-lookup"><span data-stu-id="55db2-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="55db2-146">Przeciągnij myszą, aby łączenie wierszy z **przypisać** działania nawiązanie połączenia z jednym z nich z **monitu** działania, a następnie zwolnij przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="55db2-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="55db2-147">Trzeci sposób jest bardzo podobna do pierwszej sposób, chyba że zamiast przeciągania **monitu** działanie z **przybornika**, przeciągnij ją z lokalizacji na powierzchni projektowej przepływu pracy, kursor  **Przypisz** działania i upuść je na jeden z trójkątów, które pojawia się.</span><span class="sxs-lookup"><span data-stu-id="55db2-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="55db2-148">W **okno właściwości** dla **monitu** działania, typ `"EnterGuess"` wraz z cudzysłowami do **Nazwa_zakładki** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="55db2-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="55db2-149">Typ `Guess` do **wynik** właściwości wartość pola, a następnie wpisz następujące wyrażenie w **tekstu** okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="55db2-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="55db2-150">Jeśli **okno właściwości** nie jest wyświetlany, wybierz opcję **okno właściwości** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="55db2-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="55db2-151">Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i połączyć ją przy użyciu jednej z metod opisanych w poprzednim kroku, tak aby była poniżej  **Monituj** działania.</span><span class="sxs-lookup"><span data-stu-id="55db2-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="55db2-152">Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.</span><span class="sxs-lookup"><span data-stu-id="55db2-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="55db2-153">Przeciągnij **FlowDecision** z **schemat blokowy** części **przybornika** i połączyć ją poniżej **przypisać** działania.</span><span class="sxs-lookup"><span data-stu-id="55db2-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="55db2-154">W **okno właściwości**, wpisz następujące wyrażenie do **warunek** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="55db2-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="55db2-155">Przeciągnij kolejny **FlowDecision** działanie z **przybornika** i upuść ją poniżej pierwszej.</span><span class="sxs-lookup"><span data-stu-id="55db2-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="55db2-156">Łączenie dwóch działań, przeciągając je z prostokąt, która jest oznaczona etykietą **False** u góry **FlowDecision** działania obszar przycinania na prostokąt na początku drugiej **FlowDecision**działania.</span><span class="sxs-lookup"><span data-stu-id="55db2-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="55db2-157">Jeśli nie widzisz **True** i **False** etykiet na **FlowDecision**, umieść kursor myszy nad **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="55db2-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="55db2-158">Kliknij drugą **FlowDecision** działania, aby go zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="55db2-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="55db2-159">W **okno właściwości**, wpisz następujące wyrażenie do **warunek** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="55db2-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="55db2-160">Przeciągnij dwa **WriteLine** działania z **podstawowych** części **przybornika** i upuścić je, aby były one obok siebie poniżej dwa **FlowDecision**  działań.</span><span class="sxs-lookup"><span data-stu-id="55db2-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="55db2-161">Połącz **True** akcji w dolnej części **FlowDecision** najdalej z lewej strony działania **WriteLine** działania i **False** akcji po prawej stronie **WriteLine** działania.</span><span class="sxs-lookup"><span data-stu-id="55db2-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="55db2-162">Kliknij przycisk najdalej z lewej strony **WriteLine** działanie, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** wartość właściwości pola **okno właściwości**.</span><span class="sxs-lookup"><span data-stu-id="55db2-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="55db2-163">Połącz **WriteLine** się po lewej stronie **monitu** działania stanowiący nad nim.</span><span class="sxs-lookup"><span data-stu-id="55db2-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="55db2-164">Kliknij przycisk po prawej stronie **WriteLine** działanie, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** wartość właściwości pola **okno właściwości**.</span><span class="sxs-lookup"><span data-stu-id="55db2-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="55db2-165">Połącz **WriteLine** działanie po prawej stronie **monitu** działania nad nim.</span><span class="sxs-lookup"><span data-stu-id="55db2-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="55db2-166">Poniższy przykład ilustruje ukończony przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="55db2-166">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="55db2-167">![Ukończono Windows Workflow Foundation](./media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span><span class="sxs-lookup"><span data-stu-id="55db2-167">![Completed Windows Workflow Foundation](./media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="55db2-168">Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="55db2-168">To build the workflow</span></span>  
  
1. <span data-ttu-id="55db2-169">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="55db2-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="55db2-170">Aby uzyskać instrukcje na temat sposobu uruchamiania przepływu pracy, zobacz następny temat, [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="55db2-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="55db2-171">Jeśli wykonano już [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md) kroku przy użyciu innego stylu przepływu pracy, a chcesz uruchomić go za pomocą przepływu pracy schematu blokowego, w tym kroku, przejdź do sekcji [Aby skompilować i uruchomić aplikację](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) części [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="55db2-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55db2-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55db2-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="55db2-173">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="55db2-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="55db2-174">Projektowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="55db2-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="55db2-175">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="55db2-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="55db2-176">Instrukcje: Utwórz działanie</span><span class="sxs-lookup"><span data-stu-id="55db2-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="55db2-177">Instrukcje: Uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="55db2-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
