---
title: 'Instrukcje: Tworzenie przepływu pracy automatu stanów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 451f9581ae997ad86fee968fa978713db2049455
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044387"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="44f93-102">Instrukcje: Tworzenie przepływu pracy automatu stanów</span><span class="sxs-lookup"><span data-stu-id="44f93-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="44f93-103">Przepływy pracy mogą być zbudowane z wbudowanych działań, a także z działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="44f93-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="44f93-104">W tym temacie przedstawiono procedurę tworzenia przepływu pracy, który używa zarówno wbudowanych działań, jak <xref:System.Activities.Statements.StateMachine> działania, jak i działań niestandardowych, z poprzednich [metod: Utwórz temat działania](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="44f93-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="44f93-105">Przepływ pracy modeluje grę z liczbą odgadnąć.</span><span class="sxs-lookup"><span data-stu-id="44f93-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44f93-106">Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="44f93-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="44f93-107">Aby ukończyć ten temat, należy najpierw wykonać [następujące czynności: Utwórz działanie](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="44f93-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44f93-108">Aby pobrać kompletną wersję samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="44f93-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="44f93-109">Aby utworzyć przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="44f93-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="44f93-110">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowActivities** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**, **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="44f93-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="44f93-111">W węźle **zainstalowane**, **wspólne elementy** wybierz pozycję **przepływ pracy**.</span><span class="sxs-lookup"><span data-stu-id="44f93-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="44f93-112">Wybierz **działanie** z listy **przepływów pracy** .</span><span class="sxs-lookup"><span data-stu-id="44f93-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="44f93-113">Wpisz `StateMachineNumberGuessWorkflow` tekst w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="44f93-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="44f93-114">Przeciągnij działanie **StateMachine** z sekcji **stan automatu** przybornika i upuść je na etykiecie **działania upuść** na powierzchni projektowej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="44f93-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="44f93-115">Aby utworzyć zmienne i argumenty przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="44f93-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="44f93-116">Kliknij dwukrotnie pozycję **StateMachineNumberGuessWorkflow. XAML** w **Eksplorator rozwiązań** , aby wyświetlić przepływ pracy w projektancie, jeśli nie jest on jeszcze wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="44f93-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="44f93-117">Kliknij pozycję **argumenty** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="44f93-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="44f93-118">Kliknij przycisk **Utwórz argument**.</span><span class="sxs-lookup"><span data-stu-id="44f93-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="44f93-119">Wpisz `MaxNumber` **w** polu **Nazwa** , wybierz z listy rozwijanej **kierunek** , wybierz **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER, aby zapisać argument.</span><span class="sxs-lookup"><span data-stu-id="44f93-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="44f93-120">Kliknij przycisk **Utwórz argument**.</span><span class="sxs-lookup"><span data-stu-id="44f93-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="44f93-121">Wpisz `Turns` w polu **Nazwa** , który znajduje się poniżej nowo dodanego `MaxNumber` argumentu , wybierz pozycję z listy rozwijanej **kierunek** , wybierz pozycję **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="44f93-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="44f93-122">Kliknij pozycję **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć okienko **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="44f93-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="44f93-123">Kliknij przycisk **zmienne** w lewej dolnej części projektanta przepływu pracy, aby wyświetlić okienko **zmienne** .</span><span class="sxs-lookup"><span data-stu-id="44f93-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="44f93-124">Kliknij pozycję **Utwórz zmienną**.</span><span class="sxs-lookup"><span data-stu-id="44f93-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="44f93-125">Jeśli nie zostanie wyświetlone pole **Utwórz zmienną** , kliknij <xref:System.Activities.Statements.StateMachine> działanie na powierzchni projektanta przepływu pracy, aby je wybrać.</span><span class="sxs-lookup"><span data-stu-id="44f93-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="44f93-126">Wpisz `Guess` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="44f93-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="44f93-127">Kliknij pozycję **Utwórz zmienną**.</span><span class="sxs-lookup"><span data-stu-id="44f93-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="44f93-128">Wpisz `Target` w polu **Nazwa** , wybierz wartość **Int32** z listy rozwijanej **Typ zmiennej** , a następnie naciśnij klawisz ENTER, aby zapisać zmienną.</span><span class="sxs-lookup"><span data-stu-id="44f93-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="44f93-129">Kliknij pozycję **zmienne** w lewej dolnej części okna projektanta działań, aby zamknąć okienko **zmienne** .</span><span class="sxs-lookup"><span data-stu-id="44f93-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="44f93-130">Aby dodać działania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="44f93-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="44f93-131">Kliknij pozycję **State1** , aby ją zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="44f93-131">Click **State1** to select it.</span></span> <span data-ttu-id="44f93-132">W **oknie właściwości**Zmień wartość parametru **DisplayName** na `Initialize Target`.</span><span class="sxs-lookup"><span data-stu-id="44f93-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="44f93-133">Jeśli **okno właściwości** nie jest wyświetlane, wybierz pozycję **okno właściwości** w menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="44f93-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="44f93-134">Kliknij dwukrotnie nowo zmieniono nazwę stanu **docelowego inicjalizacji** w Projektancie przepływu pracy, aby go rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="44f93-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3. <span data-ttu-id="44f93-135">Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w przyborniku i upuść je w sekcji **wpis** stanu.</span><span class="sxs-lookup"><span data-stu-id="44f93-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="44f93-136">Wpisz `Target` w polu **do** i poniższe wyrażenie w polu  **C# wprowadź wyrażenie** lub **wprowadź wyrażenie w języku VB** .</span><span class="sxs-lookup"><span data-stu-id="44f93-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="44f93-137">Jeśli okno **Przybornik** nie jest wyświetlane, wybierz pozycję **Przybornik** z menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="44f93-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4. <span data-ttu-id="44f93-138">Wróć do widoku ogólnego automatu stanów w Projektancie przepływów pracy, klikając pozycję **StateMachine** w obszarze odsyłanie w górnej części projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="44f93-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5. <span data-ttu-id="44f93-139">Przeciągnij działanie **stanu** z sekcji **stan komputera** przybornika do projektanta przepływów pracy i umieść je na stanie inicjalizacji **docelowej** .</span><span class="sxs-lookup"><span data-stu-id="44f93-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="44f93-140">Należy zauważyć, że cztery Trójkąty będą widoczne wokół stanu **inicjowania elementu docelowego** , gdy nowy stan jest na nim.</span><span class="sxs-lookup"><span data-stu-id="44f93-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="44f93-141">Upuść nowy stan w trójkącie, który znajduje się bezpośrednio poniżej stanu **inicjalizacji docelowej** .</span><span class="sxs-lookup"><span data-stu-id="44f93-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="44f93-142">Spowoduje to umieszczenie nowego stanu w przepływie pracy i utworzenie przejścia z stanu **inicjowania docelowego** do nowego stanu.</span><span class="sxs-lookup"><span data-stu-id="44f93-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6. <span data-ttu-id="44f93-143">Kliknij pozycję **State1** , aby ją zaznaczyć, Zmień wartość `Enter Guess`parametru **DisplayName** na, a następnie kliknij dwukrotnie stan w Projektancie przepływu pracy, aby go rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="44f93-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7. <span data-ttu-id="44f93-144">Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** w przyborniku i upuść je do sekcji **wejście** stanu.</span><span class="sxs-lookup"><span data-stu-id="44f93-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8. <span data-ttu-id="44f93-145">Wpisz następujące wyrażenie w polu właściwości **Text** **WriteLine**.</span><span class="sxs-lookup"><span data-stu-id="44f93-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="44f93-146">Przeciągnij działanie **Przypisz** z sekcji elementy **pierwotne** w przyborniku i upuść je na sekcję **wyjście** stanu.</span><span class="sxs-lookup"><span data-stu-id="44f93-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="44f93-147">Wpisz `Turns` w polu **do** i `Turns + 1` w polu **wprowadź C# wyrażenie** lub wprowadź wyrażenie w **języku VB** .</span><span class="sxs-lookup"><span data-stu-id="44f93-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="44f93-148">Wróć do widoku ogólnego automatu stanów w Projektancie przepływów pracy, klikając pozycję **StateMachine** w obszarze odsyłanie w górnej części projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="44f93-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="44f93-149">Przeciągnij działanie **FinalState** z sekcji **stan automatu** **przybornika**, umieść kursor nad odpowiednim stanem , a następnie upuść je do trójkąta, który pojawia się po prawej stronie w obszarze **wprowadzanie** stanu odgadnięcia, aby przejść utworzono między argumentami **Enter** i **FinalState**.</span><span class="sxs-lookup"><span data-stu-id="44f93-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="44f93-150">Domyślną nazwą przejścia jest **T2**.</span><span class="sxs-lookup"><span data-stu-id="44f93-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="44f93-151">Kliknij przejście w Projektancie przepływu pracy, aby je zaznaczyć, a następnie ustaw jego **Właściwość DisplayName** na wartość **odgadnięcia poprawne**.</span><span class="sxs-lookup"><span data-stu-id="44f93-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="44f93-152">Następnie kliknij i wybierz **FinalState**i przeciągnij go w prawo, aby zapewnić, że istnieje pomieszczenie dla nazwy pełnego przejścia, które ma być wyświetlane bez nakładania jednego z tych dwóch stanów.</span><span class="sxs-lookup"><span data-stu-id="44f93-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="44f93-153">Ułatwi to ukończenie pozostałych kroków samouczka.</span><span class="sxs-lookup"><span data-stu-id="44f93-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="44f93-154">Kliknij dwukrotnie nowo zmieniono nazwę **odgadnięcia odpowiednie** przejście w Projektancie przepływu pracy, aby je rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="44f93-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="44f93-155">Przeciągnij działanie **ReadInt** z sekcji **NumberGuessWorkflowActivities** w przyborniku i upuść je w sekcji **wyzwalacz** przejścia.</span><span class="sxs-lookup"><span data-stu-id="44f93-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="44f93-156">W **oknie właściwości** działania **ReadInt** `"EnterGuess"` , wpisz w tym cudzysłowy w polu wartość właściwości **zakładkaname** , a następnie wpisz `Guess` w polu wartość właściwości **wynik** .</span><span class="sxs-lookup"><span data-stu-id="44f93-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="44f93-157">Wpisz następujące wyrażenie w polu wartość właściwości **warunek** poprawnego przejścia.</span><span class="sxs-lookup"><span data-stu-id="44f93-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="44f93-158">Wróć do widoku ogólnego automatu stanów w Projektancie przepływów pracy, klikając pozycję **StateMachine** w obszarze odsyłanie w górnej części projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="44f93-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="44f93-159">Przejście następuje po odebraniu zdarzenia wyzwalacza i <xref:System.Activities.Statements.Transition.Condition%2A>, jeśli jest obecny, ma `True`wartość.</span><span class="sxs-lookup"><span data-stu-id="44f93-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="44f93-160">W przypadku tego przejścia, jeśli użytkownik jest `Guess` zgodny z losowo generowanym `Target`, wówczas kontrola przeszedł do **FinalState** i zakończy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="44f93-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="44f93-161">W zależności od tego, czy wartość odgadnięcia jest poprawna, przepływ pracy powinien przejść do **FinalState** lub z powrotem do stanu **wprowadzenia** dla innej próby.</span><span class="sxs-lookup"><span data-stu-id="44f93-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="44f93-162">Oba przejścia mają ten sam wyzwalacz, który oczekuje na odebranie użytkownika za pośrednictwem działania **ReadInt** .</span><span class="sxs-lookup"><span data-stu-id="44f93-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="44f93-163">Jest to nazywane przechodzeniem udostępnionym.</span><span class="sxs-lookup"><span data-stu-id="44f93-163">This is called a shared transition.</span></span> <span data-ttu-id="44f93-164">Aby utworzyć wspólne przejście, kliknij okrąg, który wskazuje początek poprawnego przejścia i przeciągnij go do żądanego stanu.</span><span class="sxs-lookup"><span data-stu-id="44f93-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="44f93-165">W takim przypadku przejście jest przechodzeniem samodzielnym, dlatego przeciągnij punkt początkowy przypuszczalnie i upuść go ponownie w dolnej części zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="44f93-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="44f93-166">Po utworzeniu przejścia wybierz je w Projektancie przepływów pracy i ustaw właściwość **DisplayName** na **nieprawidłowe**.</span><span class="sxs-lookup"><span data-stu-id="44f93-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="44f93-167">Współużytkowane przejścia można także utworzyć z poziomu projektanta przejścia, klikając pozycję **Dodaj przechodzenie wyzwalacza udostępnionego** u dołu projektanta przejścia, a następnie wybierając żądany stan docelowy z **dostępnych Stanów do połączenia** Lista rozwijana.</span><span class="sxs-lookup"><span data-stu-id="44f93-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="44f93-168">Należy zauważyć, że <xref:System.Activities.Statements.Transition.Condition%2A> Jeśli przechodzenie jest szacowane do `false` (lub wszystkie warunki przejścia wyzwalacza udostępnionego jest oceniane do `false`), przejście nie zostanie wykonane, a wszystkie wyzwalacze dla wszystkich przejść ze stanu będą zmienił.</span><span class="sxs-lookup"><span data-stu-id="44f93-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="44f93-169">W tym samouczku ta sytuacja nie może wystąpić ze względu na sposób skonfigurowania warunków (istnieją określone akcje dotyczące tego, czy wartość dopuszczalna jest poprawna czy niepoprawna).</span><span class="sxs-lookup"><span data-stu-id="44f93-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="44f93-170">Kliknij dwukrotnie **nieprawidłowe** przejście w Projektancie przepływu pracy, aby je rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="44f93-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="44f93-171">Należy zauważyć, że **wyzwalacz** jest już ustawiony na to samo działanie **ReadInt** , które było używane przez odpowiednie przechodzenie.</span><span class="sxs-lookup"><span data-stu-id="44f93-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="44f93-172">Wpisz następujące wyrażenie w polu wartość właściwości **warunek** .</span><span class="sxs-lookup"><span data-stu-id="44f93-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="44f93-173">Przeciągnij działanie **if** z sekcji **przepływ sterowania** w przyborniku i upuść je w sekcji **akcji** przejścia.</span><span class="sxs-lookup"><span data-stu-id="44f93-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="44f93-174">Wpisz następujące wyrażenie w polu wartość właściwości **warunek** działania **if** .</span><span class="sxs-lookup"><span data-stu-id="44f93-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="44f93-175">Przeciągnij dwie działania **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je tak, aby były w sekcji **then** działania **if** , a jeden z nich znajduje się w sekcji **else** .</span><span class="sxs-lookup"><span data-stu-id="44f93-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="44f93-176">Kliknij działanie **WriteLine** w sekcji Then, aby je zaznaczyć, a **następnie** wpisz następujące wyrażenie w polu wartość właściwości **Text** .</span><span class="sxs-lookup"><span data-stu-id="44f93-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="44f93-177">Kliknij działanie **WriteLine** w sekcji **else** , aby je zaznaczyć, a następnie wpisz następujące wyrażenie w polu wartość właściwości **Text** .</span><span class="sxs-lookup"><span data-stu-id="44f93-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="44f93-178">Wróć do widoku ogólnego automatu stanów w Projektancie przepływów pracy, klikając pozycję **StateMachine** w obszarze odsyłanie w górnej części projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="44f93-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="44f93-179">Poniższy przykład ilustruje ukończony przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="44f93-179">The following example illustrates the completed workflow.</span></span>  
  
     ![Ilustracja przedstawiająca ukończony przepływ pracy automatu Stanów.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="44f93-181">Aby skompilować przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="44f93-181">To build the workflow</span></span>  
  
1. <span data-ttu-id="44f93-182">Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="44f93-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="44f93-183">Instrukcje dotyczące sposobu uruchamiania przepływu pracy można znaleźć w następnym temacie, [jak: Uruchom przepływ pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="44f93-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="44f93-184">Jeśli zostały już wykonane [następujące instrukcje: Uruchom krok przepływu](how-to-run-a-workflow.md) pracy z innym stylem przepływu pracy i chcę uruchomić go za pomocą przepływu pracy automatu Stanów z tego kroku, przejdź do tematu, [ [Aby skompilować i uruchomić aplikację](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) w temacie How to: Uruchom przepływ pracy](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="44f93-184">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f93-185">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44f93-185">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="44f93-186">Programowanie w programie Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="44f93-186">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="44f93-187">Projektowanie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="44f93-187">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="44f93-188">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="44f93-188">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="44f93-189">Instrukcje: Tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="44f93-189">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="44f93-190">Instrukcje: Uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="44f93-190">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
