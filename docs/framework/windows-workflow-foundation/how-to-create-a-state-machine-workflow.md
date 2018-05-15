---
title: 'Porady: Tworzenie przepływu pracy automatu stanów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 00f764421d3caf44d853d26d76c6b6d872ab1e3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="d1570-102">Porady: Tworzenie przepływu pracy automatu stanów</span><span class="sxs-lookup"><span data-stu-id="d1570-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="d1570-103">Przepływy pracy można skonstruować z działań wbudowanych oraz z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d1570-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="d1570-104">W tym temacie prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowane działania, takie jak <xref:System.Activities.Statements.StateMachine> działania i działań niestandardowych z poprzedniej [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="d1570-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="d1570-105">Przepływ pracy modele numer guessing gier.</span><span class="sxs-lookup"><span data-stu-id="d1570-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1570-106">Każdego tematu w samouczku wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="d1570-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="d1570-107">Aby ukończyć w tym temacie, najpierw musisz zakończyć [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="d1570-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1570-108">Aby pobrać ukończoną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="d1570-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="d1570-109">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="d1570-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="d1570-110">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d1570-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="d1570-111">W **zainstalowana**, **wspólne elementy** węzła, wybierz opcję **przepływu pracy**.</span><span class="sxs-lookup"><span data-stu-id="d1570-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="d1570-112">Wybierz **działania** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="d1570-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="d1570-113">Typ `StateMachineNumberGuessWorkflow` do **nazwa** polu i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="d1570-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="d1570-114">Przeciągnij **StateMachine** działania z **automatu stanów** sekcji **przybornika** i upuść ją na **Upuść tutaj działanie** etykiety na powierzchnię projektu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d1570-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="d1570-115">Aby utworzyć zmienne przepływu pracy i argumenty</span><span class="sxs-lookup"><span data-stu-id="d1570-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="d1570-116">Kliknij dwukrotnie **StateMachineNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania przepływu pracy w projektancie, jeśli nie jest już wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="d1570-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="d1570-117">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="d1570-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="d1570-118">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="d1570-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="d1570-119">Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argument.</span><span class="sxs-lookup"><span data-stu-id="d1570-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="d1570-120">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="d1570-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="d1570-121">Typ `Turns` do **nazwa** pole poniżej nowo dodanego `MaxNumber` argumentu, wybierz opcję **limit** z **kierunek** listy rozwijanej wybierz pozycję  **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="d1570-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="d1570-122">Kliknij przycisk **argumenty** w lewym dolnym rogu Projektant działań, aby zamknąć **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="d1570-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="d1570-123">Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="d1570-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="d1570-124">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="d1570-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d1570-125">Jeśli nie **tworzenia zmiennej** zostanie wyświetlone okno, kliknij przycisk <xref:System.Activities.Statements.StateMachine> działania na powierzchni projektanta przepływu pracy, aby go wybrać.</span><span class="sxs-lookup"><span data-stu-id="d1570-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="d1570-126">Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="d1570-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="d1570-127">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="d1570-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="d1570-128">Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="d1570-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="d1570-129">Kliknij przycisk **zmienne** w lewym dolnym rogu Projektant działań, aby zamknąć **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="d1570-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="d1570-130">Aby dodać działania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d1570-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="d1570-131">Kliknij przycisk **stan1** aby go wybrać.</span><span class="sxs-lookup"><span data-stu-id="d1570-131">Click **State1** to select it.</span></span> <span data-ttu-id="d1570-132">W **okna właściwości**, zmień **DisplayName** do `Initialize Target`.</span><span class="sxs-lookup"><span data-stu-id="d1570-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d1570-133">Jeśli **okna właściwości** nie jest wyświetlane, wybierz pozycję **okna właściwości** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="d1570-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="d1570-134">Kliknij dwukrotnie nowo zmieniono **zainicjować docelowej** stanu w Projektancie przepływów pracy, aby go rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="d1570-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3.  <span data-ttu-id="d1570-135">Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i upuść ją na **wpis** sekcji stanu.</span><span class="sxs-lookup"><span data-stu-id="d1570-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="d1570-136">Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="d1570-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="d1570-137">Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="d1570-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4.  <span data-ttu-id="d1570-138">Wróć do ogólnych stanu widoku maszyny w Projektancie przepływów pracy, klikając **StateMachine** w łączach wyświetlanej w górnej części projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="d1570-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5.  <span data-ttu-id="d1570-139">Przeciągnij **stanu** działania z **automatu stanów** sekcji **przybornika** do projektanta przepływów pracy i umieść kursor myszy nad **zainicjować docelowej** stanu.</span><span class="sxs-lookup"><span data-stu-id="d1570-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="d1570-140">Należy pamiętać, że cztery trójkąty pojawi się wokół **zainicjować docelowej** stan, gdy nowy stan to nad nim.</span><span class="sxs-lookup"><span data-stu-id="d1570-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="d1570-141">Upuść nowy stan na trójkąt, który znajduje się bezpośrednio pod **zainicjować docelowej** stanu.</span><span class="sxs-lookup"><span data-stu-id="d1570-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="d1570-142">To umieszcza nowy stan na przepływie pracy i tworzy przejście z **zainicjować docelowej** stanu do nowego stanu.</span><span class="sxs-lookup"><span data-stu-id="d1570-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6.  <span data-ttu-id="d1570-143">Kliknij przycisk **stan1** wybierz ją, zmień **DisplayName** do `Enter Guess`, a następnie kliknij dwukrotnie ikonę stanu w Projektancie przepływów pracy, aby go rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="d1570-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7.  <span data-ttu-id="d1570-144">Przeciągnij **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść ją na **wpis** sekcji stanu.</span><span class="sxs-lookup"><span data-stu-id="d1570-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8.  <span data-ttu-id="d1570-145">Wpisz następujące wyrażenie w **tekst** właściwość **WriteLine**.</span><span class="sxs-lookup"><span data-stu-id="d1570-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="d1570-146">Przeciągnij **przypisać** działania z **podstawowych** sekcji **przybornika** i upuścić **zakończenia** sekcji stanu.</span><span class="sxs-lookup"><span data-stu-id="d1570-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="d1570-147">Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole.</span><span class="sxs-lookup"><span data-stu-id="d1570-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="d1570-148">Wróć do ogólnych stanu widoku maszyny w Projektancie przepływów pracy, klikając **StateMachine** w łączach wyświetlanej w górnej części projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="d1570-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="d1570-149">Przeciągnij **stan końcowy** działania z **automatu stanów** sekcji **przybornika**, umieść kursor myszy nad **wprowadź odgadnąć** stanu i upuść na trójkąt, który pojawia się po prawej stronie **wprowadź odgadnąć** stanu, dzięki czemu tworzone przejścia między **wprowadź odgadnąć** i **stan końcowy**.</span><span class="sxs-lookup"><span data-stu-id="d1570-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="d1570-150">Domyślna nazwa przejścia to **T2**.</span><span class="sxs-lookup"><span data-stu-id="d1570-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="d1570-151">Kliknij przycisk przechodzenia w Projektancie przepływów pracy, aby go zaznaczyć, a następnie ustaw jego **DisplayName** do **odgadnąć poprawne**.</span><span class="sxs-lookup"><span data-stu-id="d1570-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="d1570-152">Następnie kliknij i zaznacz **stan końcowy**i przeciągnij go do prawej, dzięki czemu jest miejsce na nazwę pełne przejście do wyświetlania bez nakładanie albo dwa stany.</span><span class="sxs-lookup"><span data-stu-id="d1570-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="d1570-153">Spowoduje to ułatwić wykonaj pozostałe kroki samouczka.</span><span class="sxs-lookup"><span data-stu-id="d1570-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="d1570-154">Kliknij dwukrotnie nowo zmieniono **odgadnąć poprawne** przejścia w Projektancie przepływów pracy, aby go rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="d1570-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="d1570-155">Przeciągnij **ReadInt** działania z **NumberGuessWorkflowActivities** sekcji **przybornika** i upuść je w **wyzwalacza** sekcji przejścia.</span><span class="sxs-lookup"><span data-stu-id="d1570-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="d1570-156">W **okna właściwości** dla **ReadInt** działania, typ `"EnterGuess"` z cudzysłowami do **Nazwa zakładki** pole wartości właściwości, a typ `Guess`do **wynik** wartości właściwości — okno</span><span class="sxs-lookup"><span data-stu-id="d1570-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="d1570-157">Wpisz następujące wyrażenie w **odgadnąć poprawne** przejścia w **warunku** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="d1570-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="d1570-158">Wróć do ogólnych stanu widoku maszyny w Projektancie przepływów pracy, klikając **StateMachine** w łączach wyświetlanej w górnej części projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="d1570-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1570-159">Przejście występuje po odebraniu zdarzenia wyzwalacza i <xref:System.Activities.Statements.Transition.Condition%2A>, jeśli jest obecny, daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="d1570-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="d1570-160">Dla tego przejścia Jeśli użytkownika `Guess` odpowiada losowo generowany `Target`, następnie kontrola przechodzi do **stan końcowy** i zakończeniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d1570-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="d1570-161">W zależności od tego, czy wynik jest poprawny, przepływu pracy należy przejść do **stan końcowy** lub z powrotem do **Wprowadź wynik** stanu do innego elementu try.</span><span class="sxs-lookup"><span data-stu-id="d1570-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="d1570-162">Zarówno przejścia udostępnianie tego samego wyzwalacza czekać na dopasowanie użytkownika do odebrania przez **ReadInt** działania.</span><span class="sxs-lookup"><span data-stu-id="d1570-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="d1570-163">Jest to udostępniony przejścia.</span><span class="sxs-lookup"><span data-stu-id="d1570-163">This is called a shared transition.</span></span> <span data-ttu-id="d1570-164">Aby utworzyć przejście udostępniony, kliknij koło, która wskazuje początek **odgadnąć poprawne** przejścia i przeciągnij go do pożądanego stanu.</span><span class="sxs-lookup"><span data-stu-id="d1570-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="d1570-165">W takim przypadku przejście jest przejście zwrotne, więc przeciągnij punkt początkowy **odgadnąć poprawne** przejście i upuść go z powrotem na dole **wprowadź odgadnąć** stanu.</span><span class="sxs-lookup"><span data-stu-id="d1570-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="d1570-166">Po utworzeniu przejścia, wybierz je w Projektancie przepływów pracy i ustawić jej **DisplayName** właściwości **odgadnąć niepoprawne**.</span><span class="sxs-lookup"><span data-stu-id="d1570-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1570-167">Udostępniony przejścia można również tworzyć od w Projektancie przejścia, klikając **Dodaj udostępnione przejście z wyzwalaczem** w dolnej części projektanta przejścia, a następnie wybierając stan docelowy z  **Dostępne stany do połączenia** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="d1570-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1570-168">Należy pamiętać, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> przejścia daje w wyniku `false` (lub wszystkie warunki przejście z wyzwalaczem udostępnionym obliczać `false`), nie nastąpi przejście i będzie wszystkich wyzwalaczy dla wszystkich przejścia ze stanu zaplanowane ponownie.</span><span class="sxs-lookup"><span data-stu-id="d1570-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="d1570-169">W tym samouczku tej sytuacji niemożliwe ze względu na sposób warunki są skonfigurowane (mamy określonych akcji dla tego, czy wynik jest prawidłowy lub nieprawidłowy).</span><span class="sxs-lookup"><span data-stu-id="d1570-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="d1570-170">Kliknij dwukrotnie **odgadnąć niepoprawne** przejścia w Projektancie przepływów pracy, aby go rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="d1570-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="d1570-171">Należy pamiętać, że **wyzwalacza** jest już ustawione w taki sam **ReadInt** działania, który był używany przez **odgadnąć poprawne** przejścia.</span><span class="sxs-lookup"><span data-stu-id="d1570-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="d1570-172">Wpisz następujące wyrażenie w **warunku** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="d1570-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="d1570-173">Przeciągnij **Jeśli** działania z **przepływ sterowania** sekcji **przybornika** i upuść je w **akcji** sekcji przejścia.</span><span class="sxs-lookup"><span data-stu-id="d1570-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="d1570-174">Wpisz następujące wyrażenie w **Jeśli** działania **warunku** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="d1570-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="d1570-175">Przeciągnij dwa **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść je, tak aby jedna jest **następnie** sekcji **Jeśli** działania, a druga jest **Else** sekcji.</span><span class="sxs-lookup"><span data-stu-id="d1570-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="d1570-176">Kliknij przycisk **WriteLine** działania w **następnie** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="d1570-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="d1570-177">Kliknij przycisk **WriteLine** działania w **Else** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie w **tekst** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="d1570-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="d1570-178">Wróć do ogólnych stanu widoku maszyny w Projektancie przepływów pracy, klikając **StateMachine** w łączach wyświetlanej w górnej części projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="d1570-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="d1570-179">Poniższy przykład przedstawia ukończonych przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="d1570-179">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="d1570-180">![Ukończono przepływ pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="d1570-180">![Completed State Machine Workflow](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="d1570-181">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="d1570-181">To build the workflow</span></span>  
  
1.  <span data-ttu-id="d1570-182">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d1570-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="d1570-183">Dla instrukcje na temat uruchamiania przepływu pracy, zobacz temat dalej [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d1570-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="d1570-184">Jeśli wykonano już [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) kroku z innego stylu przepływu pracy i uruchomić go za pomocą przepływ pracy automatu stanów z tego kroku, przejdź do [Aby skompilować i uruchomić aplikację](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) sekcji [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d1570-184">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1570-185">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1570-185">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="d1570-186">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="d1570-186">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="d1570-187">Projektowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="d1570-187">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="d1570-188">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="d1570-188">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="d1570-189">Instrukcje: Tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="d1570-189">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="d1570-190">Instrukcje: Uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d1570-190">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
