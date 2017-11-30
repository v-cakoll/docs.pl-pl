---
title: "Porady: tworzenie przepływów pracy schematu blokowego"
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
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 570e51c3b9c8ee227a9c5688fc7caa1b4a0d9c6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="02c82-102">Porady: tworzenie przepływów pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="02c82-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="02c82-103">Przepływy pracy można skonstruować z działań wbudowanych oraz z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="02c82-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="02c82-104">W tym temacie prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowane działania, takie jak <xref:System.Activities.Statements.Flowchart> działania i działań niestandardowych z poprzedniej [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="02c82-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="02c82-105">Przepływ pracy modele numer guessing gier.</span><span class="sxs-lookup"><span data-stu-id="02c82-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02c82-106">Każdego tematu w samouczku wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="02c82-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="02c82-107">Aby ukończyć w tym temacie, najpierw musisz zakończyć [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="02c82-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02c82-108">Aby pobrać ukończoną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="02c82-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="02c82-109">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="02c82-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="02c82-110">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="02c82-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="02c82-111">W **zainstalowana**, **wspólne elementy** węzła, wybierz opcję **przepływu pracy**.</span><span class="sxs-lookup"><span data-stu-id="02c82-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="02c82-112">Wybierz **działania** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="02c82-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="02c82-113">Typ `FlowchartNumberGuessWorkflow` do **nazwa** polu i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="02c82-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="02c82-114">Przeciągnij **schemat blokowy** działania z **schemat blokowy** sekcji **przybornika** i upuść ją na **Upuść tutaj działanie** etykiety na powierzchni projektu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="02c82-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="02c82-115">Aby utworzyć zmienne przepływu pracy i argumenty</span><span class="sxs-lookup"><span data-stu-id="02c82-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="02c82-116">Kliknij dwukrotnie **FlowchartNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania przepływu pracy w projektancie, jeśli nie jest już wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="02c82-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="02c82-117">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="02c82-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="02c82-118">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="02c82-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="02c82-119">Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argument.</span><span class="sxs-lookup"><span data-stu-id="02c82-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="02c82-120">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="02c82-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="02c82-121">Typ `Turns` do **nazwa** pole poniżej nowo dodanego `MaxNumber` argumentu, wybierz opcję **limit** z **kierunek** listy rozwijanej wybierz pozycję  **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="02c82-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="02c82-122">Kliknij przycisk **argumenty** w lewym dolnym rogu Projektant działań, aby zamknąć **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="02c82-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="02c82-123">Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="02c82-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="02c82-124">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="02c82-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="02c82-125">Jeśli nie **tworzenia zmiennej** zostanie wyświetlone okno, kliknij przycisk <xref:System.Activities.Statements.Flowchart> działania na powierzchni projektanta przepływu pracy, aby go wybrać.</span><span class="sxs-lookup"><span data-stu-id="02c82-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="02c82-126">Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="02c82-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="02c82-127">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="02c82-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="02c82-128">Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="02c82-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="02c82-129">Kliknij przycisk **zmienne** w lewym dolnym rogu Projektant działań, aby zamknąć **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="02c82-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="02c82-130">Aby dodać działania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="02c82-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="02c82-131">Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i umieść kursor myszy nad **Start** węzła, który znajduje się na początku Schemat blokowy.</span><span class="sxs-lookup"><span data-stu-id="02c82-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="02c82-132">Gdy **przypisać** działanie znajduje się nad **Start** węzła, trzy trójkąty pojawi się wokół **Start** węzła.</span><span class="sxs-lookup"><span data-stu-id="02c82-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="02c82-133">Upuść **przypisać** działania na trójkąt, która jest bezpośrednio poniżej **Start** węzła.</span><span class="sxs-lookup"><span data-stu-id="02c82-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="02c82-134">To będzie połączyć dwóch elementów i wyznacza **przypisać** działania jako pierwsze działanie w schemacie blokowym.</span><span class="sxs-lookup"><span data-stu-id="02c82-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="02c82-135">Działania mogą być wskazywane jako rozpoczęcia działania w przepływie pracy przez ręcznie łączenie ich działania z węzła początkowego.</span><span class="sxs-lookup"><span data-stu-id="02c82-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="02c82-136">Aby to zrobić, umieść kursor myszy nad **Start** węzła, kliknij jeden z prostokąty, które są wyświetlane, gdy wskaźnik myszy znajduje się nad **Start** węzeł, a następnie przeciągnij połączenie wiersz w dół, aby odpowiednie działanie i upuść ją na jednym z prostokąty, które są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="02c82-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="02c82-137">Możesz też określić i działania jako działanie początkowe prawym przyciskiem myszy it i wybierając pozycję **ustawić jako węzeł Start**.</span><span class="sxs-lookup"><span data-stu-id="02c82-137">You can also designate and activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2.  <span data-ttu-id="02c82-138">Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="02c82-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="02c82-139">Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="02c82-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="02c82-140">Przeciągnij **monitu** działania z **NumberGuessWorkflowActivities** sekcji **przybornika**, upuść ją poniżej **przypisać** działania od poprzedniego kroku, a następnie połącz **monitu** działanie **przypisać** działania.</span><span class="sxs-lookup"><span data-stu-id="02c82-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="02c82-141">Istnieją trzy sposoby podłączenia dwóch działań.</span><span class="sxs-lookup"><span data-stu-id="02c82-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="02c82-142">Pierwszym sposobem jest ich połączenia, ponieważ musisz porzucić **monitu** działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="02c82-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="02c82-143">Podczas przeciągania **monitu** działania w przepływie pracy, umieść ją nad **przypisać** działania i upuść ją na jeden z czterech trójkątów widocznych **monitu** działanie znajduje się nad **przypisać** działania.</span><span class="sxs-lookup"><span data-stu-id="02c82-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="02c82-144">Drugi sposób polega na porzucić **monitu** działania do przepływu pracy w wybranej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="02c82-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="02c82-145">Następnie, umieść kursor myszy nad **przypisać** działania i przeciągnij jedną prostokątów występujące w dół do **monitu** działania.</span><span class="sxs-lookup"><span data-stu-id="02c82-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="02c82-146">Przeciągnij mysz, aby połączyć wiersz z **przypisać** działania połączy się z jednym z prostokątów z **monitu** działania, a następnie zwolnij przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="02c82-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="02c82-147">Trzeci sposób jest bardzo podobny do pierwszy sposób, z wyjątkiem przeciąganie **monitu** działania z **przybornika**, przeciągnij ją z lokalizacji na powierzchni projektu przepływu pracy, Aktywuj  **Przypisz** działania i upuść ją na jedną trójkąty, które zostanie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="02c82-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4.  <span data-ttu-id="02c82-148">W **okna właściwości** dla **monitu** działania, typ `"EnterGuess"` z cudzysłowami do **Nazwa zakładki** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="02c82-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="02c82-149">Typ `Guess` do **wynik** właściwości wartość pola, a następnie wpisz następujące wyrażenie w **tekst** pole właściwości.</span><span class="sxs-lookup"><span data-stu-id="02c82-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="02c82-150">Jeśli **okna właściwości** nie jest wyświetlane, wybierz pozycję **okna właściwości** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="02c82-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="02c82-151">Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i podłącz go przy użyciu jednej z metod opisanych w poprzednim kroku, aby była poniżej  **Monituj** działania.</span><span class="sxs-lookup"><span data-stu-id="02c82-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6.  <span data-ttu-id="02c82-152">Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="02c82-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7.  <span data-ttu-id="02c82-153">Przeciągnij **elementu FlowDecision** z **schemat blokowy** sekcji **przybornika** i podłącz go poniżej **przypisać** działania.</span><span class="sxs-lookup"><span data-stu-id="02c82-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="02c82-154">W **okna właściwości**, wpisz następujące wyrażenie w **warunku** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="02c82-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  <span data-ttu-id="02c82-155">Przeciągnij kolejny **elementu FlowDecision** działania z **przybornika** i upuść ją poniżej pierwsza z nich.</span><span class="sxs-lookup"><span data-stu-id="02c82-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="02c82-156">Połącz dwa działania przez przeciąganie z okna o nazwie **False** u góry **elementu FlowDecision** działanie prostokąt na początku drugiej **elementu FlowDecision**działania.</span><span class="sxs-lookup"><span data-stu-id="02c82-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="02c82-157">Jeśli nie widzisz **True** i **False** etykiet na **elementu FlowDecision**, umieść kursor myszy nad **elementu FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="02c82-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="02c82-158">Kliknij pozycję drugiego **elementu FlowDecision** działania, aby go wybrać.</span><span class="sxs-lookup"><span data-stu-id="02c82-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="02c82-159">W **okna właściwości**, wpisz następujące wyrażenie w **warunku** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="02c82-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="02c82-160">Przeciągnij dwa **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść je, aby były one obok siebie poniżej dwa **elementu FlowDecision**  działań.</span><span class="sxs-lookup"><span data-stu-id="02c82-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="02c82-161">Połączyć **True** akcji dolnego **elementu FlowDecision** działania do lewej **WriteLine** działania i **False** akcji po prawej stronie **WriteLine** działania.</span><span class="sxs-lookup"><span data-stu-id="02c82-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="02c82-162">Kliknij przycisk lewej **WriteLine** działanie, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** wartość właściwości pola w **okna właściwości**.</span><span class="sxs-lookup"><span data-stu-id="02c82-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="02c82-163">Połącz **WriteLine** do lewej strony **monitu** działanie, które jest nad nim.</span><span class="sxs-lookup"><span data-stu-id="02c82-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="02c82-164">Kliknij przycisk skrajnej **WriteLine** działanie, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** wartość właściwości pola w **okna właściwości**.</span><span class="sxs-lookup"><span data-stu-id="02c82-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="02c82-165">Połącz **WriteLine** do prawej strony działania **monitu** działania powyżej.</span><span class="sxs-lookup"><span data-stu-id="02c82-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="02c82-166">Poniższy przykład przedstawia ukończonych przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="02c82-166">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="02c82-167">![Ukończono Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span><span class="sxs-lookup"><span data-stu-id="02c82-167">![Completed Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="02c82-168">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="02c82-168">To build the workflow</span></span>  
  
1.  <span data-ttu-id="02c82-169">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="02c82-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="02c82-170">Dla instrukcje na temat uruchamiania przepływu pracy, zobacz temat dalej [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="02c82-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="02c82-171">Jeśli wykonano już [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) kroku z innego stylu przepływu pracy i uruchomić go za pomocą schematu blokowego przepływu pracy z tym kroku, przejdź do [Aby skompilować i uruchomić aplikację](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)części [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="02c82-171">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02c82-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02c82-172">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="02c82-173">Windows Workflow Foundation programowania</span><span class="sxs-lookup"><span data-stu-id="02c82-173">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="02c82-174">Projektowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="02c82-174">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="02c82-175">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="02c82-175">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="02c82-176">Porady: tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="02c82-176">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="02c82-177">Porady: uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="02c82-177">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
