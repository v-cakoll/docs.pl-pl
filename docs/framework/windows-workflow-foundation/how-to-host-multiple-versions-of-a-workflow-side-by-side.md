---
title: 'Instrukcje: hostowanie wielu wersji przepływu pracy Side-by-Side'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 525aeab7ff08da95735e9c9df7f6f040e8b9e215
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856364"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="24f2c-102">Instrukcje: hostowanie wielu wersji przepływu pracy Side-by-Side</span><span class="sxs-lookup"><span data-stu-id="24f2c-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>
<span data-ttu-id="24f2c-103">`WorkflowIdentity` Umożliwia deweloperom aplikacji przepływu pracy skojarzyć nazwę i wersję z definicji przepływu pracy i te informacje, które ma zostać skojarzony z istniejącym wystąpieniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="24f2c-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="24f2c-104">Informacje o tożsamości może służyć przez deweloperów aplikacji przepływu pracy można obsługiwać scenariusze takie jak side-by-side wykonywanie wielu wersji definicji przepływu pracy i zapewnia podstawę dla innych funkcji, takich jak aktualizacja dynamiczna.</span><span class="sxs-lookup"><span data-stu-id="24f2c-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="24f2c-105">Ten krok, w tym samouczku przedstawiono sposób użycia `WorkflowIdentity` do hostowania wielu wersji przepływu pracy w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="24f2c-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24f2c-106">Aby pobrać wersję inną ukończone lub wyświetlić Przewodnik wideo tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="24f2c-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="24f2c-107">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="24f2c-107">In this topic</span></span>  
 <span data-ttu-id="24f2c-108">W tym kroku samouczka `WriteLine` działań w przepływie pracy są modyfikowane w celu dodatkowe informacje i nową `WriteLine` dodanym działaniem.</span><span class="sxs-lookup"><span data-stu-id="24f2c-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="24f2c-109">Kopia oryginalnego zestawu przepływu pracy jest przechowywana, a aplikacja hosta zostanie zaktualizowana, dzięki czemu można uruchamiać zarówno oryginał, jak i zaktualizowano przepływów pracy w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="24f2c-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>  
  
-   [<span data-ttu-id="24f2c-110">Aby utworzyć kopię projektu NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="24f2c-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [<span data-ttu-id="24f2c-111">Aby zaktualizować przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="24f2c-111">To update the workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [<span data-ttu-id="24f2c-112">Aktualizacja Automat stanów przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="24f2c-112">To update the StateMachine workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [<span data-ttu-id="24f2c-113">Aktualizacja przepływu pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="24f2c-113">To update the Flowchart workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [<span data-ttu-id="24f2c-114">Aby zaktualizować sekwencyjnego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="24f2c-114">To update the Sequential workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [<span data-ttu-id="24f2c-115">Aby zaktualizować WorkflowVersionMap obejmujący poprzednich wersji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="24f2c-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="24f2c-116">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="24f2c-116">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  <span data-ttu-id="24f2c-117">Przed wykonaniem kroków w tym temacie, uruchom aplikację, uruchom wiele przepływów pracy dla każdego typu, a dzięki jednej lub dwóch prób dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="24f2c-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="24f2c-118">Tych utrwalonych przepływów pracy są używane w tym kroku i następny krok [porady: aktualizowanie definicji uruchomione wystąpienie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="24f2c-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24f2c-119">Poszczególne kroki samouczka Wprowadzenie zależy od poprzednich kroków.</span><span class="sxs-lookup"><span data-stu-id="24f2c-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="24f2c-120">Jeśli nie została ukończona poprzednich kroków możesz pobrać pełną wersję z samouczka w [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="24f2c-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
###  <a name="BKMK_BackupCopy"></a> <span data-ttu-id="24f2c-121">Aby utworzyć kopię projektu NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="24f2c-121">To make a copy of the NumberGuessWorkflowActivities project</span></span>  
  
1.  <span data-ttu-id="24f2c-122">Otwórz **WF45GettingStartedTutorial** rozwiązania [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] Jeśli nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="24f2c-122">Open the **WF45GettingStartedTutorial** solution in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] if it is not open.</span></span>  
  
2.  <span data-ttu-id="24f2c-123">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="24f2c-123">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="24f2c-124">Zamknij **WF45GettingStartedTutorial** rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="24f2c-124">Close the **WF45GettingStartedTutorial** solution.</span></span>  
  
4.  <span data-ttu-id="24f2c-125">Otwórz Eksploratora Windows i przejdź do folderu, w którym znajdują się w pliku rozwiązania samouczka i folderów projektu.</span><span class="sxs-lookup"><span data-stu-id="24f2c-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>  
  
5.  <span data-ttu-id="24f2c-126">Utwórz nowy folder o nazwie **PreviousVersions** w tym samym folderze co **NumberGuessWorkflowHost** i **NumberGuessWorkflowActivities**.</span><span class="sxs-lookup"><span data-stu-id="24f2c-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="24f2c-127">Ten folder jest używany do zawierają zestawy, które zawierają różne wersje przepływy pracy, wykorzystywane w kolejnych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="24f2c-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>  
  
6.  <span data-ttu-id="24f2c-128">Przejdź do **NumberGuessWorkflowActivities\bin\debug** folder (lub **bin\release** w zależności od ustawień projektu).</span><span class="sxs-lookup"><span data-stu-id="24f2c-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="24f2c-129">Kopiuj **NumberGuessWorkflowActivities.dll** i wklej go w **PreviousVersions** folderu.</span><span class="sxs-lookup"><span data-stu-id="24f2c-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>  
  
7.  <span data-ttu-id="24f2c-130">Zmień nazwę **NumberGuessWorkflowActivities.dll** w **PreviousVersions** folder **NumberGuessWorkflowActivities_v1.dll**.</span><span class="sxs-lookup"><span data-stu-id="24f2c-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="24f2c-131">Kroki opisane w tym temacie pokazują jeden sposób zarządzania zestawów zawiera wiele wersji przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="24f2c-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="24f2c-132">Można również zmienić innych metod, takich jak silnych nazw zestawów i rejestrowania ich w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="24f2c-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>  
  
8.  <span data-ttu-id="24f2c-133">Utwórz nowy folder o nazwie **NumberGuessWorkflowActivities_du** w tym samym folderze co **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, a nowo dodano **PreviousVersions** folder, a następnie skopiuj wszystkie pliki i podfoldery z **NumberGuessWorkflowActivities** do nowego folderu  **NumberGuessWorkflowActivities_du** folderu.</span><span class="sxs-lookup"><span data-stu-id="24f2c-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="24f2c-134">Ta kopia zapasowa projektu dla początkowej wersji działania jest używana w [porady: aktualizowanie definicji uruchomione wystąpienie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="24f2c-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>  
  
9. <span data-ttu-id="24f2c-135">Otwórz ponownie **WF45GettingStartedTutorial** rozwiązania [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24f2c-135">Re-open the **WF45GettingStartedTutorial** solution in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
###  <a name="BKMK_UpdateWorkflows"></a> <span data-ttu-id="24f2c-136">Aby zaktualizować przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="24f2c-136">To update the workflows</span></span>  
 <span data-ttu-id="24f2c-137">W tej sekcji definicji przepływu pracy są aktualizowane.</span><span class="sxs-lookup"><span data-stu-id="24f2c-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="24f2c-138">Dwa `WriteLine` działań, które Prześlij opinię na temat odgadnięcia użytkownika są aktualizowane i nowej `WriteLine` dodanym działaniem, zawiera dodatkowe informacje o gry, gdy liczba jest złamać.</span><span class="sxs-lookup"><span data-stu-id="24f2c-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>  
  
####  <a name="BKMK_UpdateStateMachine"></a> <span data-ttu-id="24f2c-139">Aktualizacja Automat stanów przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="24f2c-139">To update the StateMachine workflow</span></span>  
  
1.  <span data-ttu-id="24f2c-140">W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **StateMachineNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="24f2c-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="24f2c-141">Kliknij dwukrotnie **odgadnięcia niepoprawne** przejście maszyny stanu.</span><span class="sxs-lookup"><span data-stu-id="24f2c-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>  
  
3.  <span data-ttu-id="24f2c-142">Aktualizacja `Text` z lewym skrajnym `WriteLine` w `If` działania.</span><span class="sxs-lookup"><span data-stu-id="24f2c-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
4.  <span data-ttu-id="24f2c-143">Aktualizacja `Text` z najbardziej po prawej stronie `WriteLine` w `If` działania.</span><span class="sxs-lookup"><span data-stu-id="24f2c-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
5.  <span data-ttu-id="24f2c-144">Wróć do ogólnych stanu widoku maszyny w Projektancie przepływu pracy, klikając **StateMachine** w obszarze nawigacji wyświetlane w górnej części projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="24f2c-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
6.  <span data-ttu-id="24f2c-145">Kliknij dwukrotnie **odgadnięcia poprawne** przejście maszyny stanu.</span><span class="sxs-lookup"><span data-stu-id="24f2c-145">Double-click the **Guess Correct** transition on the state machine.</span></span>  
  
7.  <span data-ttu-id="24f2c-146">Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je na **działania Upuść działanie tutaj** etykiety przejście.</span><span class="sxs-lookup"><span data-stu-id="24f2c-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>  
  
8.  <span data-ttu-id="24f2c-147">Wpisz następujące wyrażenie do `Text` okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="24f2c-147">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateFlowchart"></a> <span data-ttu-id="24f2c-148">Aktualizacja przepływu pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="24f2c-148">To update the Flowchart workflow</span></span>  
  
1.  <span data-ttu-id="24f2c-149">W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **FlowchartNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="24f2c-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="24f2c-150">Aktualizacja `Text` z lewym skrajnym `WriteLine` działania.</span><span class="sxs-lookup"><span data-stu-id="24f2c-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  <span data-ttu-id="24f2c-151">Aktualizacja `Text` z najbardziej po prawej stronie `WriteLine` działania.</span><span class="sxs-lookup"><span data-stu-id="24f2c-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  <span data-ttu-id="24f2c-152">Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je w punkcie listy `True` akcji najwyższy `FlowDecision` .</span><span class="sxs-lookup"><span data-stu-id="24f2c-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="24f2c-153">`WriteLine` Działania zostaną dodane do schematu blokowego i połączone z `True` akcji `FlowDecision`.</span><span class="sxs-lookup"><span data-stu-id="24f2c-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>  
  
5.  <span data-ttu-id="24f2c-154">Wpisz następujące wyrażenie do `Text` okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="24f2c-154">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateSequential"></a> <span data-ttu-id="24f2c-155">Aby zaktualizować sekwencyjnego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="24f2c-155">To update the Sequential workflow</span></span>  
  
1.  <span data-ttu-id="24f2c-156">W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **SequentialNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="24f2c-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="24f2c-157">Aktualizacja `Text` z lewym skrajnym `WriteLine` w `If` działania.</span><span class="sxs-lookup"><span data-stu-id="24f2c-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  <span data-ttu-id="24f2c-158">Aktualizacja `Text` z najbardziej po prawej stronie `WriteLine` działania w `If` działania.</span><span class="sxs-lookup"><span data-stu-id="24f2c-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  <span data-ttu-id="24f2c-159">Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je po **DoWhile** działanie tak, aby  **WriteLine** jest ostatnie działanie w katalogu głównym `Sequence` działania.</span><span class="sxs-lookup"><span data-stu-id="24f2c-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>  
  
5.  <span data-ttu-id="24f2c-160">Wpisz następujące wyrażenie do `Text` okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="24f2c-160">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="24f2c-161">Aby zaktualizować WorkflowVersionMap obejmujący poprzednich wersji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="24f2c-161">To update WorkflowVersionMap to include the previous workflow versions</span></span>  
  
1.  <span data-ttu-id="24f2c-162">Kliknij dwukrotnie **WorkflowVersionMap.cs** (lub **WorkflowVersionMap.vb**) w obszarze **NumberGuessWorkflowHost** projektu, aby go otworzyć.</span><span class="sxs-lookup"><span data-stu-id="24f2c-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>  
  
2.  <span data-ttu-id="24f2c-163">Dodaj następujący kod `using` (lub `Imports`) instrukcji na górze pliku razem z innymi `using` (lub `Imports`) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="24f2c-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Reflection  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Reflection;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="24f2c-164">Dodaj trzy nowe tożsamości przepływu pracy po prostu poniższe trzy deklaracje tożsamość istniejącego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="24f2c-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="24f2c-165">Te nowe `v1` przepływu pracy będą używane tożsamości udostępniają definicje poprawne przepływu pracy do przepływów pracy uruchomionych przed aktualizacje zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="24f2c-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>  
  
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
  
4.  <span data-ttu-id="24f2c-166">W `WorkflowVersionMap` Konstruktor, aktualizacja `Version` właściwość trzy bieżącej tożsamości przepływu pracy do `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="24f2c-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>  
  
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
  
     <span data-ttu-id="24f2c-167">Kod, który dodaje aktualne wersje przepływy pracy do słownika używa bieżące wersje, które są określone w projekcie, więc kod, który inicjuje definicji przepływu pracy nie musi zostać zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="24f2c-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>  
  
5.  <span data-ttu-id="24f2c-168">Dodaj następujący kod w Konstruktorze zaraz po kod, który dodaje bieżące wersje do słownika.</span><span class="sxs-lookup"><span data-stu-id="24f2c-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>  
  
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
  
     <span data-ttu-id="24f2c-169">Te tożsamości przepływu pracy są skojarzone z odpowiedniej definicji przepływu pracy w wersji początkowej.</span><span class="sxs-lookup"><span data-stu-id="24f2c-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>  
  
6.  <span data-ttu-id="24f2c-170">Następnie Załaduj zestaw, który zawiera wstępną wersję definicji przepływu pracy i tworzenie i dodawanie odpowiedniej definicji przepływu pracy do słownika.</span><span class="sxs-lookup"><span data-stu-id="24f2c-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>  
  
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
  
     <span data-ttu-id="24f2c-171">Poniższy przykład przedstawia pełną listę, aby uzyskać zaktualizowany `WorkflowVersionMap` klasy.</span><span class="sxs-lookup"><span data-stu-id="24f2c-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>  
  
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
  
###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="24f2c-172">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="24f2c-172">To build and run the application</span></span>  
  
1.  <span data-ttu-id="24f2c-173">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować aplikację i CTRL + F5, aby rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="24f2c-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>  
  
2.  <span data-ttu-id="24f2c-174">Rozpocznij nowy przepływ pracy, klikając **nową grę**.</span><span class="sxs-lookup"><span data-stu-id="24f2c-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="24f2c-175">Wersja przepływu pracy jest wyświetlany w oknie stanu i uwzględnia zaktualizowaną wersję z powiązanego `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="24f2c-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="24f2c-176">Zwróć uwagę na `InstanceId` , można wyświetlić pliku śledzenia dla przepływu pracy po jego ukończeniu, a następnie wprowadź liczbę prób, aż do zakończenia gry.</span><span class="sxs-lookup"><span data-stu-id="24f2c-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="24f2c-177">Należy zauważyć, jak odgadnięcia użytkownika jest wyświetlany w informacjach wyświetlanych w oknie stanu na podstawie aktualizacji do `WriteLine` działań.</span><span class="sxs-lookup"><span data-stu-id="24f2c-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>  
  
 <span data-ttu-id="24f2c-178">**Wprowadź liczbę między 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="24f2c-178">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="24f2c-179">**5 jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="24f2c-179">**5 is too high.** </span></span>  
<span data-ttu-id="24f2c-180">**Wprowadź liczbę między 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="24f2c-180">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="24f2c-181">**3 jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="24f2c-181">**3 is too high.** </span></span>  
<span data-ttu-id="24f2c-182">**Wprowadź liczbę między 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="24f2c-182">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="24f2c-183">**1 jest zbyt mała.** </span><span class="sxs-lookup"><span data-stu-id="24f2c-183">**1 is too low.** </span></span>  
<span data-ttu-id="24f2c-184">**Wprowadź liczbę między 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="24f2c-184">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="24f2c-185">**Gratulacje, złamać numer w włącza 4.**</span><span class="sxs-lookup"><span data-stu-id="24f2c-185">**Congratulations, you guessed the number in 4 turns.**</span></span>    
    > [!NOTE]
    >  <span data-ttu-id="24f2c-186">Zaktualizowany tekst z `WriteLine` działania jest wyświetlane, ale dane wyjściowe końcowe `WriteLine` braku aktywności, który został dodany w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="24f2c-186">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="24f2c-187">Wynika to z okna stanu jest aktualizowana przez `PersistableIdle` programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="24f2c-187">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="24f2c-188">Ponieważ przepływ pracy zakończy i nie przechodzi bezczynności po ostatnim działaniu `PersistableIdle` nie zostanie wywołana procedura obsługi.</span><span class="sxs-lookup"><span data-stu-id="24f2c-188">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="24f2c-189">Jednak podobny komunikat jest wyświetlany w oknie stanu przez `Completed` programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="24f2c-189">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="24f2c-190">Jeśli to konieczne, kod może zostać dodany do `Completed` obsługi do wyodrębniania tekstu z `StringWriter` i wyświetl ją w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="24f2c-190">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>  
  
3.  <span data-ttu-id="24f2c-191">Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowHost\bin\debug** folder (lub **bin\release** w zależności od ustawień projektu), a następnie otwórz plik śledzenia za pomocą Notatnika, który odpowiada Aby ukończony przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="24f2c-191">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="24f2c-192">Jeśli nie została wprowadzona Zanotuj `InstanceId`, plik śledzenia poprawne można zidentyfikować za pomocą **Data modyfikacji** informacji w Eksploratorze Windows.</span><span class="sxs-lookup"><span data-stu-id="24f2c-192">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>  
  
 <span data-ttu-id="24f2c-193">**Wprowadź liczbę między 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="24f2c-193">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="24f2c-194">**5 jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="24f2c-194">**5 is too high.** </span></span>  
<span data-ttu-id="24f2c-195">**Wprowadź liczbę między 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="24f2c-195">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="24f2c-196">**3 jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="24f2c-196">**3 is too high.** </span></span>  
<span data-ttu-id="24f2c-197">**Wprowadź liczbę między 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="24f2c-197">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="24f2c-198">**1 jest zbyt mała.** </span><span class="sxs-lookup"><span data-stu-id="24f2c-198">**1 is too low.** </span></span>  
<span data-ttu-id="24f2c-199">**Wprowadź liczbę między 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="24f2c-199">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="24f2c-200">**2 jest poprawna. Odgadnięto go w 4 wyłącza.**</span><span class="sxs-lookup"><span data-stu-id="24f2c-200">**2 is correct. You guessed it in 4 turns.**</span></span>      <span data-ttu-id="24f2c-201">Zaktualizowany interfejs `WriteLine` danych wyjściowych jest zawarty w pliku śledzenia, w tym dane wyjściowe `WriteLine` , dodanego w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="24f2c-201">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>  
  
4.  <span data-ttu-id="24f2c-202">Przejdź z powrotem do odgadnięcia liczba aplikacji, a następnie wybierz jedno z przepływów pracy, które zostało uruchomione, zanim aktualizacje zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="24f2c-202">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="24f2c-203">Wersję aktualnie wybranego przepływu pracy można zidentyfikować, sprawdzając informacje o wersji, która jest wyświetlana poniżej oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="24f2c-203">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="24f2c-204">Wprowadź kilka prób i należy pamiętać, że stan aktualizacji dopasowanie `WriteLine` działania dane wyjściowe z poprzedniej wersji i nie obejmują odgadnięcia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="24f2c-204">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="24f2c-205">To dlatego te przepływy pracy korzystają z poprzednią definicję przepływu pracy, który nie ma `WriteLine` aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="24f2c-205">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>  
  
     <span data-ttu-id="24f2c-206">W następnym kroku [instrukcje: aktualizowanie definicji uruchomione wystąpienie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), uruchomienie `v1` wystąpienia przepływu pracy są aktualizowane i zawierają nową funkcjonalność w postaci `v2` wystąpień.</span><span class="sxs-lookup"><span data-stu-id="24f2c-206">In the next step, [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
