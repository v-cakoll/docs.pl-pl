---
title: 'Instrukcje: Tworzenie przepływu pracy automatu stanów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 84d2355a78c7d33bf712baf158f28861e59e75d1
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881937"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="31062-102">Instrukcje: Tworzenie przepływu pracy automatu stanów</span><span class="sxs-lookup"><span data-stu-id="31062-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="31062-103">Przepływy pracy można skonstruować z wbudowanych działań, a także z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="31062-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="31062-104">Ten temat prowadzi przez proces tworzenia przepływu pracy, który używa zarówno wbudowanych działań, takich jak <xref:System.Activities.Statements.StateMachine> działanie i działań niestandardowych z poprzedniego [jak: Utwórz działanie](how-to-create-an-activity.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="31062-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="31062-105">Przepływ pracy modeli gra odgadnięcia liczb.</span><span class="sxs-lookup"><span data-stu-id="31062-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31062-106">Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach.</span><span class="sxs-lookup"><span data-stu-id="31062-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="31062-107">Aby ukończyć ten temat, najpierw musisz zakończyć [jak: Utwórz działanie](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="31062-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31062-108">Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="31062-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="31062-109">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="31062-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="31062-110">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowActivities** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="31062-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="31062-111">W **zainstalowane**, **wspólne elementy** węzeł **przepływu pracy**.</span><span class="sxs-lookup"><span data-stu-id="31062-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="31062-112">Wybierz **działania** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="31062-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="31062-113">Typ `StateMachineNumberGuessWorkflow` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="31062-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="31062-114">Przeciągnij **StateMachine** działanie z **automatu stanów** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety na przepływ pracy powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="31062-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="31062-115">Aby utworzyć zmienne przepływu pracy i argumenty</span><span class="sxs-lookup"><span data-stu-id="31062-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="31062-116">Kliknij dwukrotnie **StateMachineNumberGuessWorkflow.xaml** w **Eksploratora rozwiązań** do wyświetlania w Projektancie przepływu pracy, jeśli nie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="31062-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="31062-117">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="31062-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="31062-118">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="31062-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="31062-119">Typ `MaxNumber` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **Int32** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.</span><span class="sxs-lookup"><span data-stu-id="31062-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="31062-120">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="31062-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="31062-121">Typ `Turns` do **nazwa** pole, które jest pod nowo dodanym `MaxNumber` argument, wybierz opcję **się** z **kierunek** listy rozwijanej, wybierz opcję  **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="31062-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="31062-122">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="31062-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="31062-123">Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta przepływów pracy, aby wyświetlić **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="31062-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="31062-124">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="31062-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="31062-125">Jeśli nie **Tworzenie zmiennej** zostanie wyświetlone okno, kliknij przycisk <xref:System.Activities.Statements.StateMachine> działania na powierzchni projektanta przepływu pracy, aby go zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="31062-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="31062-126">Typ `Guess` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="31062-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="31062-127">Kliknij przycisk **utworzyć zmienną**.</span><span class="sxs-lookup"><span data-stu-id="31062-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="31062-128">Typ `Target` do **nazwa** wybierz opcję **Int32** z **typ zmiennej** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="31062-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="31062-129">Kliknij przycisk **zmienne** w lewym dolnym rogu projektanta działań, aby zamknąć **zmienne** okienka.</span><span class="sxs-lookup"><span data-stu-id="31062-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="31062-130">Aby dodać działania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="31062-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="31062-131">Kliknij przycisk **stan1** aby go zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="31062-131">Click **State1** to select it.</span></span> <span data-ttu-id="31062-132">W **okno właściwości**, zmień **DisplayName** do `Initialize Target`.</span><span class="sxs-lookup"><span data-stu-id="31062-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="31062-133">Jeśli **okno właściwości** nie jest wyświetlany, wybierz opcję **okno właściwości** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="31062-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="31062-134">Kliknij dwukrotnie nowo zmienionej nazwie **zainicjować docelowej** stanu w Projektancie przepływu pracy, aby ją rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="31062-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3. <span data-ttu-id="31062-135">Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i upuść je na **wpis** sekcja stanu.</span><span class="sxs-lookup"><span data-stu-id="31062-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="31062-136">Typ `Target` do **do** pole i następującego wyrażenia do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.</span><span class="sxs-lookup"><span data-stu-id="31062-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="31062-137">Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="31062-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4. <span data-ttu-id="31062-138">Wróć do ogólnych stanu widoku maszyny w Projektancie przepływu pracy, klikając **StateMachine** w obszarze nawigacji wyświetlane w górnej części projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="31062-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5. <span data-ttu-id="31062-139">Przeciągnij **stanu** działanie z **automatu stanów** części **przybornika** w Projektancie przepływu pracy i zatrzymaj wskaźnik myszy nad **zainicjować docelowej** stanu.</span><span class="sxs-lookup"><span data-stu-id="31062-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="31062-140">Należy pamiętać, że cztery trójkąty pojawi się wokół **zainicjować docelowej** stan, gdy nowy stan to nad nim.</span><span class="sxs-lookup"><span data-stu-id="31062-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="31062-141">Upuść nowy stan na trójkąt, który znajduje się bezpośrednio pod **zainicjować docelowej** stanu.</span><span class="sxs-lookup"><span data-stu-id="31062-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="31062-142">To umieszcza nowy stan do przepływu pracy i tworzy przejście z **zainicjować docelowej** stanu do nowego stanu.</span><span class="sxs-lookup"><span data-stu-id="31062-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6. <span data-ttu-id="31062-143">Kliknij przycisk **stan1** aby ją wybrać, zmienić **DisplayName** do `Enter Guess`, a następnie kliknij dwukrotnie ikonę stanu w Projektancie przepływu pracy, aby ją rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="31062-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7. <span data-ttu-id="31062-144">Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je na **wpis** sekcja stanu.</span><span class="sxs-lookup"><span data-stu-id="31062-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8. <span data-ttu-id="31062-145">Wpisz następujące wyrażenie do **tekstu** okno właściwości z **WriteLine**.</span><span class="sxs-lookup"><span data-stu-id="31062-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="31062-146">Przeciągnij **przypisać** działanie z **podstawowych** części **przybornika** i upuścić **zakończenia** sekcja stanu.</span><span class="sxs-lookup"><span data-stu-id="31062-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="31062-147">Typ `Turns` do **do** pole i `Turns + 1` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole.</span><span class="sxs-lookup"><span data-stu-id="31062-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="31062-148">Wróć do ogólnych stanu widoku maszyny w Projektancie przepływu pracy, klikając **StateMachine** w obszarze nawigacji wyświetlane w górnej części projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="31062-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="31062-149">Przeciągnij **FinalState** działanie z **automatu stanów** części **przybornika**, Zatrzymaj wskaźnik myszy nad **wprowadź odgadnięcia** stanu i upuść go na trójkąt, który pojawia się po prawej stronie **wprowadź odgadnięcia** stanu, tak aby tworzone przejścia między **wprowadź odgadnięcia** i **FinalState**.</span><span class="sxs-lookup"><span data-stu-id="31062-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="31062-150">Domyślna nazwa przejścia to **T2**.</span><span class="sxs-lookup"><span data-stu-id="31062-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="31062-151">Kliknij przycisk przejścia w Projektancie przepływu pracy, aby go zaznaczyć, a następnie ustaw jego **DisplayName** do **odgadnięcia poprawne**.</span><span class="sxs-lookup"><span data-stu-id="31062-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="31062-152">Następnie kliknij i zaznacz **FinalState**i przeciągnij go do prawej strony, aby miejsca dla nazwy pełne przejście do wyświetlenia bez nałożenie jedną z dwóch stanów.</span><span class="sxs-lookup"><span data-stu-id="31062-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="31062-153">Spowoduje to ułatwić wykonaj pozostałe kroki w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="31062-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="31062-154">Kliknij dwukrotnie nowo zmienionej nazwie **odgadnięcia poprawne** przejścia w Projektancie przepływu pracy, aby ją rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="31062-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="31062-155">Przeciągnij **readint —** działanie z **NumberGuessWorkflowActivities** części **przybornika** i upuść je **wyzwalacza** sekcji przejścia.</span><span class="sxs-lookup"><span data-stu-id="31062-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="31062-156">W **okno właściwości** dla **readint —** działania, typ `"EnterGuess"` wraz z cudzysłowami do **Nazwa_zakładki** pole wartości właściwości i typ `Guess`do **wynik** pole wartości właściwości</span><span class="sxs-lookup"><span data-stu-id="31062-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="31062-157">Wpisz następujące wyrażenie do **odgadnięcia poprawne** firmy przejścia **warunek** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="31062-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="31062-158">Wróć do ogólnych stanu widoku maszyny w Projektancie przepływu pracy, klikając **StateMachine** w obszarze nawigacji wyświetlane w górnej części projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="31062-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31062-159">Przejście występuje po odebraniu zdarzenia wyzwalacza i <xref:System.Activities.Statements.Transition.Condition%2A>, jeśli jest obecny, daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="31062-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="31062-160">Dla tego przejścia Jeśli użytkownika `Guess` odpowiada losowo generowany `Target`, kontrola przechodzi do, a następnie **FinalState** i ukończeniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="31062-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="31062-161">W zależności od tego, czy wynik jest poprawny, przepływu pracy należy przejść do **FinalState** lub z powrotem do **wprowadź odgadnięcia** stanu dla innej próby.</span><span class="sxs-lookup"><span data-stu-id="31062-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="31062-162">Zarówno przejścia udostępnianie tego samego wyzwalacza oczekiwania przez dopasowanie użytkownika do odebrania za pośrednictwem **readint —** działania.</span><span class="sxs-lookup"><span data-stu-id="31062-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="31062-163">Jest to udostępniony przejścia.</span><span class="sxs-lookup"><span data-stu-id="31062-163">This is called a shared transition.</span></span> <span data-ttu-id="31062-164">Do tworzenia udostępnionych przejść, kliknij przycisk koła, który wskazuje początek **odgadnięcia poprawne** przejścia i przeciągnij go do żądanego stanu.</span><span class="sxs-lookup"><span data-stu-id="31062-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="31062-165">W tym przypadku przejście jest samodzielnej przejścia, więc przeciągnij punkt początkowy **odgadnięcia poprawne** przejścia i upuść go z powrotem na dolnej części **wprowadź odgadnięcia** stanu.</span><span class="sxs-lookup"><span data-stu-id="31062-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="31062-166">Po utworzeniu przejścia, wybierz ją w Projektancie przepływów pracy i ustaw jego **DisplayName** właściwości **odgadnięcia niepoprawne**.</span><span class="sxs-lookup"><span data-stu-id="31062-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31062-167">Udostępnione przejścia można również utworzyć z w Projektancie przejścia, klikając **Dodaj udostępnionych przejść wyzwalaczy** w dolnej części projektanta przejścia, a następnie wybierając stanu wybraną docelową z  **Stany połączyć** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="31062-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31062-168">Należy pamiętać, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> przejścia daje w wyniku `false` (lub zwrócić wszystkie warunki przejścia udostępnionego wyzwalacza `false`), nie nastąpi przejście, i będą wszystkie wyzwalacze dla wszystkich przejść ze stanu zaplanowane ponownie.</span><span class="sxs-lookup"><span data-stu-id="31062-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="31062-169">W tym samouczku ta sytuacja nie może się zdarzyć, ze względu na sposób warunki są skonfigurowane (mamy określonych akcji dla tego, czy wynik jest prawidłowy lub nieprawidłowy).</span><span class="sxs-lookup"><span data-stu-id="31062-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="31062-170">Kliknij dwukrotnie **odgadnięcia niepoprawne** przejścia w Projektancie przepływu pracy, aby ją rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="31062-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="31062-171">Należy pamiętać, że **wyzwalacza** jest już ustawione w taki sam **readint —** działania, który został użyty przez **odgadnięcia poprawne** przejścia.</span><span class="sxs-lookup"><span data-stu-id="31062-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="31062-172">Wpisz następujące wyrażenie do **warunek** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="31062-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="31062-173">Przeciągnij **Jeśli** działanie z **przepływ sterowania** części **przybornika** i upuść je **akcji** sekcji przejścia.</span><span class="sxs-lookup"><span data-stu-id="31062-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="31062-174">Wpisz następujące wyrażenie do **Jeśli** działania **warunek** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="31062-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="31062-175">Przeciągnij dwa **WriteLine** działania z **podstawowych** części **przybornika** i upuścić je tak, aby jeden **następnie** sekcji **Jeśli** działania i jeden znajduje się w **Else** sekcji.</span><span class="sxs-lookup"><span data-stu-id="31062-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="31062-176">Kliknij przycisk **WriteLine** działania w **następnie** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="31062-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="31062-177">Kliknij przycisk **WriteLine** działania w **Else** sekcji, aby go zaznaczyć, a następnie wpisz następujące wyrażenie do **tekstu** pole wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="31062-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="31062-178">Wróć do ogólnych stanu widoku maszyny w Projektancie przepływu pracy, klikając **StateMachine** w obszarze nawigacji wyświetlane w górnej części projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="31062-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="31062-179">Poniższy przykład ilustruje ukończony przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="31062-179">The following example illustrates the completed workflow.</span></span>  
  
     ![Ilustracja przedstawiająca przepływ pracy automatu stanu ukończenia.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="31062-181">Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="31062-181">To build the workflow</span></span>  
  
1. <span data-ttu-id="31062-182">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="31062-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="31062-183">Aby uzyskać instrukcje na temat sposobu uruchamiania przepływu pracy, zobacz następny temat, [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="31062-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="31062-184">Jeśli wykonano już [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md) kroku przy użyciu innego stylu przepływu pracy, a chcesz uruchomić go za pomocą przepływu pracy stanu komputera z tego kroku, przejdź do sekcji [Aby skompilować i uruchomić aplikację](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) części [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="31062-184">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31062-185">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31062-185">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="31062-186">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="31062-186">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="31062-187">Projektowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="31062-187">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="31062-188">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="31062-188">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="31062-189">Instrukcje: Utwórz działanie</span><span class="sxs-lookup"><span data-stu-id="31062-189">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="31062-190">Instrukcje: Uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="31062-190">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
