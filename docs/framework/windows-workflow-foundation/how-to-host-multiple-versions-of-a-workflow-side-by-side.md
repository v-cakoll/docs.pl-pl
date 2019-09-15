---
title: 'Instrukcje: Równoczesne hostowanie wielu wersji przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 820ed324c8095e2f9f2823513a37965099f42c48
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989649"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="bcc7c-102">Instrukcje: Równoczesne hostowanie wielu wersji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bcc7c-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>

<span data-ttu-id="bcc7c-103">`WorkflowIdentity`umożliwia deweloperom aplikacji przepływu pracy kojarzenie nazwy i wersji z definicją przepływu pracy oraz dla tych informacji do skojarzenia z utrwalonym wystąpieniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="bcc7c-104">Te informacje o tożsamości mogą być używane przez deweloperów aplikacji przepływu pracy do włączania scenariuszy, takich jak wykonywanie równoczesne wielu wersji definicji przepływu pracy i udostępniają one podstawę do innych funkcji, takich jak aktualizacja dynamiczna.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="bcc7c-105">Ten krok w samouczku pokazuje, jak używać `WorkflowIdentity` do hostowania wielu wersji przepływu pracy w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="bcc7c-106">Aby pobrać kompletną wersję lub wyświetlić przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="bcc7c-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="bcc7c-107">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="bcc7c-107">In this topic</span></span>

<span data-ttu-id="bcc7c-108">W tym kroku samouczka `WriteLine` działania w przepływie pracy są modyfikowane w celu zapewnienia dodatkowych informacji i dodawane jest nowe `WriteLine` działanie.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="bcc7c-109">Kopia oryginalnego zestawu przepływu pracy jest przechowywana, a aplikacja hosta zostanie zaktualizowana tak, aby mogła jednocześnie uruchamiać zarówno oryginalny, jak i zaktualizowany przepływy pracy.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>

- [<span data-ttu-id="bcc7c-110">Aby utworzyć kopię projektu NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="bcc7c-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [<span data-ttu-id="bcc7c-111">Aby zaktualizować przepływy pracy</span><span class="sxs-lookup"><span data-stu-id="bcc7c-111">To update the workflows</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

  - [<span data-ttu-id="bcc7c-112">Aby zaktualizować przepływ pracy StateMachine</span><span class="sxs-lookup"><span data-stu-id="bcc7c-112">To update the StateMachine workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

  - [<span data-ttu-id="bcc7c-113">Aby zaktualizować przepływ pracy Flowchart</span><span class="sxs-lookup"><span data-stu-id="bcc7c-113">To update the Flowchart workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

  - [<span data-ttu-id="bcc7c-114">Aby zaktualizować sekwencyjny przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="bcc7c-114">To update the Sequential workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [<span data-ttu-id="bcc7c-115">Aby zaktualizować WorkflowVersionMap w celu uwzględnienia poprzednich wersji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bcc7c-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="bcc7c-116">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="bcc7c-116">To build and run the application</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> <span data-ttu-id="bcc7c-117">Przed wykonaniem kroków opisanych w tym temacie należy uruchomić aplikację, uruchomić kilka przepływów pracy każdego typu i wprowadzić jedną lub dwie wartości dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="bcc7c-118">Te utrwalone przepływy pracy są używane w tym kroku i w [następujących krokach: Zaktualizuj definicję uruchomionego wystąpienia](how-to-update-the-definition-of-a-running-workflow-instance.md)przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

> [!NOTE]
> <span data-ttu-id="bcc7c-119">Każdy krok w samouczku Wprowadzenie zależy od poprzednich kroków.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="bcc7c-120">Jeśli poprzednie kroki nie zostały wykonane, możesz pobrać ukończoną wersję samouczka z [Windows Workflow Foundation (WF45) — wprowadzenie samouczka](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="bcc7c-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

### <a name="BKMK_BackupCopy"></a><span data-ttu-id="bcc7c-121">Aby utworzyć kopię projektu NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="bcc7c-121">To make a copy of the NumberGuessWorkflowActivities project</span></span>

1. <span data-ttu-id="bcc7c-122">Otwórz rozwiązanie **WF45GettingStartedTutorial** w programie Visual Studio 2012, jeśli nie jest otwarte.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-122">Open the **WF45GettingStartedTutorial** solution in Visual Studio 2012 if it is not open.</span></span>

2. <span data-ttu-id="bcc7c-123">Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-123">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="bcc7c-124">Zamknij rozwiązanie **WF45GettingStartedTutorial** .</span><span class="sxs-lookup"><span data-stu-id="bcc7c-124">Close the **WF45GettingStartedTutorial** solution.</span></span>

4. <span data-ttu-id="bcc7c-125">Otwórz Eksploratora Windows i przejdź do folderu, w którym znajdują się pliki rozwiązania samouczka i foldery projektu.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>

5. <span data-ttu-id="bcc7c-126">Utwórz nowy folder o nazwie **PreviousVersions** w tym samym folderze, co **NumberGuessWorkflowHost** i **NumberGuessWorkflowActivities**.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="bcc7c-127">Ten folder służy do przechowywania zestawów zawierających różne wersje przepływów pracy używanych w kolejnych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>

6. <span data-ttu-id="bcc7c-128">Przejdź do folderu **NumberGuessWorkflowActivities\bin\debug** (lub **bin\Release** w zależności od ustawień projektu).</span><span class="sxs-lookup"><span data-stu-id="bcc7c-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="bcc7c-129">Skopiuj plik **NumberGuessWorkflowActivities. dll** i wklej go do folderu **PreviousVersions** .</span><span class="sxs-lookup"><span data-stu-id="bcc7c-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>

7. <span data-ttu-id="bcc7c-130">Zmień nazwę **NumberGuessWorkflowActivities. dll** w folderze **PreviousVersions** na **NumberGuessWorkflowActivities_v1. dll**.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bcc7c-131">Kroki przedstawione w tym temacie przedstawiają jeden ze sposobów zarządzania zestawami używanymi do przechowywania wielu wersji przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="bcc7c-132">Można również użyć innych metod, takich jak silne nazewnictwo zestawów i rejestrowanie ich w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>

8. <span data-ttu-id="bcc7c-133">Utwórz nowy folder o nazwie **NumberGuessWorkflowActivities_du** w tym samym folderze, co **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**i nowo dodany folder **PreviousVersions** , a następnie skopiuj wszystkie pliki i podfoldery z folderu **NumberGuessWorkflowActivities** do nowego folderu **NumberGuessWorkflowActivities_du** .</span><span class="sxs-lookup"><span data-stu-id="bcc7c-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="bcc7c-134">Ta kopia zapasowa projektu dla początkowej wersji działań jest używana w [następujący sposób: Zaktualizuj definicję uruchomionego wystąpienia](how-to-update-the-definition-of-a-running-workflow-instance.md)przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

9. <span data-ttu-id="bcc7c-135">Otwórz ponownie rozwiązanie **WF45GettingStartedTutorial** w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-135">Re-open the **WF45GettingStartedTutorial** solution in Visual Studio 2012.</span></span>

### <a name="BKMK_UpdateWorkflows"></a><span data-ttu-id="bcc7c-136">Aby zaktualizować przepływy pracy</span><span class="sxs-lookup"><span data-stu-id="bcc7c-136">To update the workflows</span></span>

<span data-ttu-id="bcc7c-137">W tej sekcji definicje przepływów pracy zostaną zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="bcc7c-138">Dwa `WriteLine` działania, które dają opinię na temat odgadnięcia użytkownika, są aktualizowane i dodawane jest `WriteLine` nowe działanie, które zapewnia dodatkowe informacje o grze, gdy nastąpi odpuszczenie liczby.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>

#### <a name="BKMK_UpdateStateMachine"></a><span data-ttu-id="bcc7c-139">Aby zaktualizować przepływ pracy StateMachine</span><span class="sxs-lookup"><span data-stu-id="bcc7c-139">To update the StateMachine workflow</span></span>

1. <span data-ttu-id="bcc7c-140">W **Eksplorator rozwiązań**w projekcie **NumberGuessWorkflowActivities** kliknij dwukrotnie **StateMachineNumberGuessWorkflow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="bcc7c-141">Kliknij dwukrotnie **nieprawidłowe** przejście na komputerze stanu.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>

3. <span data-ttu-id="bcc7c-142">Zaktualizuj część z lewej strony `WriteLine` `If` działania. `Text`</span><span class="sxs-lookup"><span data-stu-id="bcc7c-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. <span data-ttu-id="bcc7c-143">Zaktualizuj część z prawej strony `WriteLine` `If` działania. `Text`</span><span class="sxs-lookup"><span data-stu-id="bcc7c-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. <span data-ttu-id="bcc7c-144">Wróć do widoku ogólnego automatu stanów w Projektancie przepływów pracy, klikając pozycję **StateMachine** w obszarze odsyłanie w górnej części projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>

6. <span data-ttu-id="bcc7c-145">Kliknij dwukrotnie **odpowiednie przejście na** komputerze stanu.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-145">Double-click the **Guess Correct** transition on the state machine.</span></span>

7. <span data-ttu-id="bcc7c-146">Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je w **działaniu akcji upuść tutaj** etykieta przejścia.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>

8. <span data-ttu-id="bcc7c-147">Wpisz następujące wyrażenie w `Text` polu właściwości.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-147">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a><span data-ttu-id="bcc7c-148">Aby zaktualizować przepływ pracy Flowchart</span><span class="sxs-lookup"><span data-stu-id="bcc7c-148">To update the Flowchart workflow</span></span>

1. <span data-ttu-id="bcc7c-149">W **Eksplorator rozwiązań**w projekcie **NumberGuessWorkflowActivities** kliknij dwukrotnie **FlowchartNumberGuessWorkflow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="bcc7c-150">Zaktualizuj wartość `Text` `WriteLine` działania z lewej strony.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="bcc7c-151">`Text` Zaktualizuj część `WriteLine` działania z prawej strony.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="bcc7c-152">Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je w punkcie `True` upuszczania akcji najwyższego `FlowDecision`poziomu.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="bcc7c-153">Działanie jest dodawane do schematu blokowego i połączone `True` z akcją `FlowDecision`. `WriteLine`</span><span class="sxs-lookup"><span data-stu-id="bcc7c-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>

5. <span data-ttu-id="bcc7c-154">Wpisz następujące wyrażenie w `Text` polu właściwości.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-154">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a><span data-ttu-id="bcc7c-155">Aby zaktualizować sekwencyjny przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="bcc7c-155">To update the Sequential workflow</span></span>

1. <span data-ttu-id="bcc7c-156">W **Eksplorator rozwiązań**w projekcie **NumberGuessWorkflowActivities** kliknij dwukrotnie **SequentialNumberGuessWorkflow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="bcc7c-157">Zaktualizuj część z lewej strony `WriteLine` `If` działania. `Text`</span><span class="sxs-lookup"><span data-stu-id="bcc7c-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="bcc7c-158">`WriteLine` Zaktualizuj działanie `If` z prawej strony `Text` w działaniu.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="bcc7c-159">Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je po działaniu **DoWhile** , tak aby Metoda **WriteLine** była ostatnim działaniem w działaniu `Sequence` głównym.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>

5. <span data-ttu-id="bcc7c-160">Wpisz następujące wyrażenie w `Text` polu właściwości.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-160">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a><span data-ttu-id="bcc7c-161">Aby zaktualizować WorkflowVersionMap w celu uwzględnienia poprzednich wersji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bcc7c-161">To update WorkflowVersionMap to include the previous workflow versions</span></span>

1. <span data-ttu-id="bcc7c-162">Kliknij dwukrotnie pozycję **WorkflowVersionMap.cs** (lub **WorkflowVersionMap. vb**) w projekcie **NumberGuessWorkflowHost** , aby go otworzyć.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

2. <span data-ttu-id="bcc7c-163">Dodaj następujące `using` instrukcje (lub `Imports`) na początku pliku z innymi `using` instrukcjami (lub `Imports`).</span><span class="sxs-lookup"><span data-stu-id="bcc7c-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. <span data-ttu-id="bcc7c-164">Dodaj trzy nowe tożsamości przepływu pracy tuż poniżej trzech istniejących deklaracji tożsamości przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="bcc7c-165">Te nowe `v1` tożsamości przepływu pracy będą używane do zapewnienia, że przepływy pracy zostały uruchomione przed wprowadzeniem aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 Identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;
    ```

4. <span data-ttu-id="bcc7c-166">W konstruktorze `Version` zaktualizuj właściwość trzech bieżących tożsamości przepływu pracy do `2.0.0.0`. `WorkflowVersionMap`</span><span class="sxs-lookup"><span data-stu-id="bcc7c-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>

    ```vb
    'Add the current workflow version identities.
    StateMachineNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    SequentialNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
    map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
    map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
    ```

    ```csharp
    // Add the current workflow version identities.
    StateMachineNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    SequentialNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
    map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
    map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
    ```

    <span data-ttu-id="bcc7c-167">Kod w programie, który dodaje bieżące wersje przepływów pracy do słownika używa bieżących wersji, do których odwołuje się projekt, więc kod inicjujący definicje przepływu pracy nie musi zostać zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>

5. <span data-ttu-id="bcc7c-168">Dodaj następujący kod w konstruktorze bezpośrednio po kodzie, który dodaje bieżące wersje do słownika.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>

    ```vb
    'Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }
    ```

    ```csharp
    // Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };
    ```

    <span data-ttu-id="bcc7c-169">Te tożsamości przepływu pracy są skojarzone z początkowymi wersjami odpowiednich definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>

6. <span data-ttu-id="bcc7c-170">Następnie Załaduj zestaw zawierający początkową wersję definicji przepływu pracy i Utwórz i Dodaj odpowiednie definicje przepływów pracy do słownika.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>

    ```vb
    'Add the previous version workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v1 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
    Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Add the previous version workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v1 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
    Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

    <span data-ttu-id="bcc7c-171">Poniższy przykład to kompletna lista dla zaktualizowanej `WorkflowVersionMap` klasy.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 Identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
        }
    }
    ```

### <a name="BKMK_BuildAndRun"></a><span data-ttu-id="bcc7c-172">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="bcc7c-172">To build and run the application</span></span>

1. <span data-ttu-id="bcc7c-173">Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować aplikację, a następnie naciśnij klawisze CTRL + F5, aby rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>

2. <span data-ttu-id="bcc7c-174">Uruchom nowy przepływ pracy, klikając pozycję **Nowa gra**.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="bcc7c-175">Wersja przepływu pracy jest wyświetlana w oknie stanu i odzwierciedla zaktualizowaną wersję ze skojarzonego `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="bcc7c-176">Zanotuj `InstanceId` , aby można było wyświetlić plik śledzenia dla przepływu pracy po jego zakończeniu, a następnie wprowadzić wartości odgadnięcia do momentu zakończenia gry.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="bcc7c-177">Zwróć uwagę, w jaki sposób odgadnięcie użytkownika jest wyświetlane w informacjach wyświetlanych w oknie stanu na podstawie aktualizacji `WriteLine` działań.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    Congratulations, you guessed the number in 4 turns.
    ```

    > [!NOTE]
    > <span data-ttu-id="bcc7c-178">Wyświetlany jest zaktualizowany tekst `WriteLine` działań, ale dane wyjściowe działania końcowego `WriteLine` , które zostało dodane w tym temacie, nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-178">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="bcc7c-179">Wynika to z faktu, że okno stanu jest `PersistableIdle` aktualizowane przez program obsługi.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-179">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="bcc7c-180">Ponieważ przepływ pracy kończy się i nie przechodzi bezczynnie po zakończeniu działania końcowego `PersistableIdle` , program obsługi nie zostanie wywołany.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-180">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="bcc7c-181">Jednak podobny komunikat jest wyświetlany w oknie stanu przez `Completed` program obsługi.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-181">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="bcc7c-182">W razie potrzeby kod można dodać do `Completed` programu obsługi, aby wyodrębnić tekst `StringWriter` z i wyświetlić go w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-182">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>

3. <span data-ttu-id="bcc7c-183">Otwórz Eksploratora Windows i przejdź do folderu **NumberGuessWorkflowHost\bin\debug** (lub **bin\Release** w zależności od ustawień projektu) i Otwórz plik śledzenia przy użyciu Notatnika odpowiadającego zakończonemu przepływowi pracy.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-183">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="bcc7c-184">Jeśli nie zanotujesz tego `InstanceId`, możesz zidentyfikować prawidłowy plik śledzenia przy użyciu informacji o **dacie modyfikacji** w Eksploratorze Windows.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-184">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    2 is correct. You guessed it in 4 turns.
    ```

    <span data-ttu-id="bcc7c-185">Zaktualizowane `WriteLine` dane wyjściowe są zawarte w pliku śledzenia, łącznie z danymi wyjściowymi `WriteLine` , które zostały dodane w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-185">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>

4. <span data-ttu-id="bcc7c-186">Przełącz się z powrotem do aplikacji umożliwiającej odgadnięcie i wybierz jeden z przepływów pracy, które zostały uruchomione przed wprowadzeniem aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-186">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="bcc7c-187">Wersję aktualnie wybranego przepływu pracy można zidentyfikować, przeglądając informacje o wersji, które są wyświetlane poniżej okna stanu.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-187">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="bcc7c-188">Wprowadź kilka prób i zwróć uwagę na to, że aktualizacje stanu `WriteLine` są zgodne z danymi wyjściowymi działania z poprzedniej wersji i nie uwzględniają odgadnięcia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-188">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="bcc7c-189">Wynika to z faktu, że te przepływy pracy używają poprzedniej definicji przepływu pracy `WriteLine` , która nie ma aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-189">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>

    <span data-ttu-id="bcc7c-190">W następnym kroku, [jak: Aktualizacja definicji uruchomionego wystąpienia](how-to-update-the-definition-of-a-running-workflow-instance.md)przepływu pracy, uruchomione `v1` wystąpienia przepływu pracy są aktualizowane, aby zawierały nowe funkcje jako `v2` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="bcc7c-190">In the next step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
