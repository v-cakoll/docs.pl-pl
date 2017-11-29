---
title: "Porady: hostowanie wielu wersji przepływu pracy Side-by-Side"
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
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 713417131338dd683906eb2de56e615d4aa13c10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="dd6dd-102">Porady: hostowanie wielu wersji przepływu pracy Side-by-Side</span><span class="sxs-lookup"><span data-stu-id="dd6dd-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>
<span data-ttu-id="dd6dd-103">`WorkflowIdentity`Umożliwia deweloperom aplikacji przepływu pracy skojarzyć nazwę i wersję z definicji przepływu pracy, a te informacje mają być skojarzone z wystąpieniem przepływu pracy utrwalonych.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="dd6dd-104">Informacje o tożsamości mogą posłużyć deweloperzy aplikacji przepływu pracy na potrzeby scenariuszy, takich jak side-by-side wykonywanie wielu wersji definicji przepływu pracy i udostępnia inne funkcje, takie jak aktualizacja dynamiczna podstawy.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="dd6dd-105">Ten krok samouczka przedstawiono sposób użycia `WorkflowIdentity` do obsługi wielu wersji przepływu pracy w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd6dd-106">Aby pobrać wersję zakończone lub wyświetlić Przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="dd6dd-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="dd6dd-107">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="dd6dd-107">In this topic</span></span>  
 <span data-ttu-id="dd6dd-108">W tym kroku samouczka `WriteLine` działań w przepływie pracy są modyfikować, aby uzyskać dodatkowe informacje, a nowy `WriteLine` dodaniu działania.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="dd6dd-109">Kopia oryginalnego zestawu przepływu pracy jest przechowywana, a aplikacja hosta jest aktualizowana, co umożliwia uruchamianie zarówno oryginalny i zaktualizowany przepływ pracy w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>  
  
-   [<span data-ttu-id="dd6dd-110">Aby utworzyć kopię projektu NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="dd6dd-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [<span data-ttu-id="dd6dd-111">Aby zaktualizować przepływy pracy</span><span class="sxs-lookup"><span data-stu-id="dd6dd-111">To update the workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [<span data-ttu-id="dd6dd-112">Aby zaktualizować StateMachine przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dd6dd-112">To update the StateMachine workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [<span data-ttu-id="dd6dd-113">Aby zaktualizować schemat blokowy przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dd6dd-113">To update the Flowchart workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [<span data-ttu-id="dd6dd-114">Aby zaktualizować sekwencyjnego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dd6dd-114">To update the Sequential workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [<span data-ttu-id="dd6dd-115">Aby zaktualizować WorkflowVersionMap uwzględnienie poprzednie wersje przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dd6dd-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="dd6dd-116">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="dd6dd-116">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  <span data-ttu-id="dd6dd-117">Przed wykonaniem kroków w tym temacie, uruchom aplikację, uruchom kilka przepływy pracy każdego typu, a dzięki jednego lub dwóch prób dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="dd6dd-118">Te utrwalonych przepływów pracy są używane w tym kroku i następujący krok, [porady: aktualizacji definicji wystąpienia przepływu pracy systemem](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="dd6dd-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd6dd-119">Każdy krok samouczka Wprowadzenie zależy od poprzednich kroków.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="dd6dd-120">Jeśli poprzednie kroki nie została ukończona, można pobrać ukończoną wersję samouczek z [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="dd6dd-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
###  <span data-ttu-id="dd6dd-121"><a name="BKMK_BackupCopy"></a>Aby utworzyć kopię projektu NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="dd6dd-121"><a name="BKMK_BackupCopy"></a> To make a copy of the NumberGuessWorkflowActivities project</span></span>  
  
1.  <span data-ttu-id="dd6dd-122">Otwórz **WF45GettingStartedTutorial** rozwiązania [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] Jeśli nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-122">Open the **WF45GettingStartedTutorial** solution in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] if it is not open.</span></span>  
  
2.  <span data-ttu-id="dd6dd-123">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-123">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="dd6dd-124">Zamknij **WF45GettingStartedTutorial** rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-124">Close the **WF45GettingStartedTutorial** solution.</span></span>  
  
4.  <span data-ttu-id="dd6dd-125">Otwórz Eksploratora Windows i przejdź do folderu, w którym znajdują się rozwiązania samouczka plików i folderów projektu.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>  
  
5.  <span data-ttu-id="dd6dd-126">Utwórz nowy folder o nazwie **PreviousVersions** w tym samym folderze co **NumberGuessWorkflowHost** i **NumberGuessWorkflowActivities**.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="dd6dd-127">Ten folder jest wykorzystywany do zawierają zestawy, które znajdują się różne wersje przepływów pracy, używany w kolejnych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>  
  
6.  <span data-ttu-id="dd6dd-128">Przejdź do **NumberGuessWorkflowActivities\bin\debug** folder (lub **bin\release** w zależności od ustawienia projektu).</span><span class="sxs-lookup"><span data-stu-id="dd6dd-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="dd6dd-129">Kopiuj **NumberGuessWorkflowActivities.dll** i wklej ją do **PreviousVersions** folderu.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>  
  
7.  <span data-ttu-id="dd6dd-130">Zmień nazwę **NumberGuessWorkflowActivities.dll** w **PreviousVersions** folder **NumberGuessWorkflowActivities_v1.dll**.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd6dd-131">Kroki opisane w tym temacie prezentują jednym ze sposobów zarządzania zestawy zawiera wiele wersji przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="dd6dd-132">Ponadto można użyć innych metod, takich jak silnych nazw zestawów i rejestrowania ich w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>  
  
8.  <span data-ttu-id="dd6dd-133">Utwórz nowy folder o nazwie **NumberGuessWorkflowActivities_du** w tym samym folderze co **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**i nowo dodaje **PreviousVersions** folderu i skopiuj wszystkie pliki i podfoldery z **NumberGuessWorkflowActivities** do nowego folderu  **NumberGuessWorkflowActivities_du** folderu.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="dd6dd-134">Tej kopii zapasowej projektu dla początkowej wersji działania jest używana w [porady: aktualizacji definicji wystąpienia przepływu pracy systemem](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span><span class="sxs-lookup"><span data-stu-id="dd6dd-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>  
  
9. <span data-ttu-id="dd6dd-135">Otwórz ponownie **WF45GettingStartedTutorial** rozwiązania [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd6dd-135">Re-open the **WF45GettingStartedTutorial** solution in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
###  <span data-ttu-id="dd6dd-136"><a name="BKMK_UpdateWorkflows"></a>Aby zaktualizować przepływy pracy</span><span class="sxs-lookup"><span data-stu-id="dd6dd-136"><a name="BKMK_UpdateWorkflows"></a> To update the workflows</span></span>  
 <span data-ttu-id="dd6dd-137">W tej sekcji zaktualizowano definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="dd6dd-138">Dwa `WriteLine` działań, które Prześlij opinię na temat wynik użytkownika są zaktualizowane, a nowy `WriteLine` działania zostanie dodany, który udostępnia dodatkowe informacje o gry po odgadnąć jest liczba.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>  
  
####  <span data-ttu-id="dd6dd-139"><a name="BKMK_UpdateStateMachine"></a>Aby zaktualizować StateMachine przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dd6dd-139"><a name="BKMK_UpdateStateMachine"></a> To update the StateMachine workflow</span></span>  
  
1.  <span data-ttu-id="dd6dd-140">W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **StateMachineNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="dd6dd-141">Kliknij dwukrotnie **odgadnąć niepoprawne** przejście komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>  
  
3.  <span data-ttu-id="dd6dd-142">Aktualizacja `Text` z lewej `WriteLine` w `If` działania.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
4.  <span data-ttu-id="dd6dd-143">Aktualizacja `Text` z prawej krawędzi `WriteLine` w `If` działania.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
5.  <span data-ttu-id="dd6dd-144">Wróć do ogólnych stanu widoku maszyny w Projektancie przepływów pracy, klikając **StateMachine** w łączach wyświetlanej w górnej części projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
6.  <span data-ttu-id="dd6dd-145">Kliknij dwukrotnie **odgadnąć poprawne** przejście komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-145">Double-click the **Guess Correct** transition on the state machine.</span></span>  
  
7.  <span data-ttu-id="dd6dd-146">Przeciągnij **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść ją na **akcji Upuść działanie tutaj** etykieta przejście.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>  
  
8.  <span data-ttu-id="dd6dd-147">Wpisz następujące wyrażenie w `Text` pole właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-147">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <span data-ttu-id="dd6dd-148"><a name="BKMK_UpdateFlowchart"></a>Aby zaktualizować schemat blokowy przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dd6dd-148"><a name="BKMK_UpdateFlowchart"></a> To update the Flowchart workflow</span></span>  
  
1.  <span data-ttu-id="dd6dd-149">W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **FlowchartNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="dd6dd-150">Aktualizacja `Text` z lewej `WriteLine` działania.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  <span data-ttu-id="dd6dd-151">Aktualizacja `Text` z prawej krawędzi `WriteLine` działania.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  <span data-ttu-id="dd6dd-152">Przeciągnij **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść go w punkcie upuszczania `True` akcji najwyższy węzeł `FlowDecision` .</span><span class="sxs-lookup"><span data-stu-id="dd6dd-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="dd6dd-153">`WriteLine` Działania zostanie dodane do schematu blokowego i połączony z `True` akcji `FlowDecision`.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>  
  
5.  <span data-ttu-id="dd6dd-154">Wpisz następujące wyrażenie w `Text` pole właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-154">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <span data-ttu-id="dd6dd-155"><a name="BKMK_UpdateSequential"></a>Aby zaktualizować sekwencyjnego przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dd6dd-155"><a name="BKMK_UpdateSequential"></a> To update the Sequential workflow</span></span>  
  
1.  <span data-ttu-id="dd6dd-156">W **Eksploratora rozwiązań**w obszarze **NumberGuessWorkflowActivities** projektu, kliknij dwukrotnie **SequentialNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="dd6dd-157">Aktualizacja `Text` z lewej `WriteLine` w `If` działania.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  <span data-ttu-id="dd6dd-158">Aktualizacja `Text` z prawej krawędzi `WriteLine` działania w `If` działania.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  <span data-ttu-id="dd6dd-159">Przeciągnij **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść je po **DoWhile** działania, aby  **WriteLine** jest ostatnie działanie w folderze głównym `Sequence` działania.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>  
  
5.  <span data-ttu-id="dd6dd-160">Wpisz następujące wyrażenie w `Text` pole właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-160">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
###  <span data-ttu-id="dd6dd-161"><a name="BKMK_UpdateWorkflowVersionMap"></a>Aby zaktualizować WorkflowVersionMap uwzględnienie poprzednie wersje przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dd6dd-161"><a name="BKMK_UpdateWorkflowVersionMap"></a> To update WorkflowVersionMap to include the previous workflow versions</span></span>  
  
1.  <span data-ttu-id="dd6dd-162">Kliknij dwukrotnie **WorkflowVersionMap.cs** (lub **WorkflowVersionMap.vb**) w obszarze **NumberGuessWorkflowHost** projektu, aby go otworzyć.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>  
  
2.  <span data-ttu-id="dd6dd-163">Dodaj następujące `using` (lub `Imports`) instrukcje na początku pliku z innym `using` (lub `Imports`) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Reflection  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Reflection;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="dd6dd-164">Dodaj trzy nowe tożsamości przepływu pracy poniżej trzy deklaracje tożsamości istniejącego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="dd6dd-165">Te nowe `v1` tożsamości będą używane w przepływie pracy zawierają definicje poprawne przepływu pracy do przepływów pracy zostało uruchomione przed aktualizacje zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>  
  
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
  
4.  <span data-ttu-id="dd6dd-166">W `WorkflowVersionMap` konstruktora, aktualizacja `Version` właściwości trzy bieżącej tożsamości przepływu pracy do `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>  
  
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
  
     <span data-ttu-id="dd6dd-167">Kod, który dodaje bieżące wersje przepływy pracy do słownika są używane bieżące wersje, które odwołują się do projektu, więc kod, który inicjuje definicji przepływu pracy musi zostać zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>  
  
5.  <span data-ttu-id="dd6dd-168">Dodaj następujący kod w Konstruktorze zaraz po kod, który dodaje bieżącej wersji do słownika.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>  
  
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
  
     <span data-ttu-id="dd6dd-169">Tymi tożsamościami przepływu pracy są skojarzone z początkowej wersji odpowiedniej definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>  
  
6.  <span data-ttu-id="dd6dd-170">Następnie Załaduj zestaw, który zawiera początkowej wersji definicji przepływu pracy i tworzenie i dodawanie odpowiedniej definicji przepływu pracy do słownika.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>  
  
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
  
     <span data-ttu-id="dd6dd-171">Poniższy przykład jest pełna lista dla zaktualizowanego `WorkflowVersionMap` klasy.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>  
  
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
  
###  <span data-ttu-id="dd6dd-172"><a name="BKMK_BuildAndRun"></a>Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="dd6dd-172"><a name="BKMK_BuildAndRun"></a> To build and run the application</span></span>  
  
1.  <span data-ttu-id="dd6dd-173">Naciśnij klawisze CTRL + SHIFT + B do skompilowania aplikacji, a następnie klawisz CTRL + F5, aby rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>  
  
2.  <span data-ttu-id="dd6dd-174">Uruchamianie nowego przepływu pracy, klikając **nowej gry**.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="dd6dd-175">Wersja tego przepływu pracy jest wyświetlany w oknie stanu i odzwierciedla zaktualizowaną wersję z skojarzony `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="dd6dd-176">Zanotuj `InstanceId` , można przejrzeć plik śledzenia dla przepływu pracy, po jego ukończeniu, a następnie wprowadź prób, aż do zakończenia gry.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="dd6dd-177">Należy zwrócić uwagę, jak wynik użytkownika jest wyświetlany w informacji wyświetlanych w oknie stanu na podstawie aktualizacji do `WriteLine` działań.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>  
  
 <span data-ttu-id="dd6dd-178">**Wprowadź liczbę z przedziału od 1 do 10**</span><span class="sxs-lookup"><span data-stu-id="dd6dd-178">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="dd6dd-179">**5 jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-179">**5 is too high.** </span></span>  
<span data-ttu-id="dd6dd-180">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-180">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="dd6dd-181">**3 jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-181">**3 is too high.** </span></span>  
<span data-ttu-id="dd6dd-182">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-182">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="dd6dd-183">**1 jest zbyt niski.** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-183">**1 is too low.** </span></span>  
<span data-ttu-id="dd6dd-184">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-184">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="dd6dd-185">**Gratulacje, odgadnąć numer w włącza 4.**</span><span class="sxs-lookup"><span data-stu-id="dd6dd-185">**Congratulations, you guessed the number in 4 turns.**</span></span>    
    > [!NOTE]
    >  <span data-ttu-id="dd6dd-186">Zaktualizowany tekst z `WriteLine` działania jest wyświetlane, ale dane wyjściowe końcowych `WriteLine` nie jest działanie, które zostały dodane w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-186">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="dd6dd-187">To okno stanu jest aktualizowana przez `PersistableIdle` obsługi.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-187">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="dd6dd-188">Ponieważ zakończeniu przepływu pracy, a nie przechodzi bezczynności po ostatnie działanie `PersistableIdle` program obsługi nie jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-188">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="dd6dd-189">Jednak podobny komunikat jest wyświetlany w oknie stanu przez `Completed` obsługi.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-189">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="dd6dd-190">W razie potrzeby kodu została dodana do `Completed` obsługi można wyodrębnić tekst z `StringWriter` i wyświetl ją w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-190">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>  
  
3.  <span data-ttu-id="dd6dd-191">Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowHost\bin\debug** folder (lub **bin\release** w zależności od ustawienia projektu), a następnie otwórz plik śledzenia za pomocą Notatnika, który odpowiada Ukończono przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-191">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="dd6dd-192">Jeśli nie wprowadzono uwagę `InstanceId`, plik śledzenia poprawne można zidentyfikować przy użyciu **Data modyfikacji** informacji w Eksploratorze Windows.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-192">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>  
  
 <span data-ttu-id="dd6dd-193">**Wprowadź liczbę z przedziału od 1 do 10**</span><span class="sxs-lookup"><span data-stu-id="dd6dd-193">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="dd6dd-194">**5 jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-194">**5 is too high.** </span></span>  
<span data-ttu-id="dd6dd-195">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-195">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="dd6dd-196">**3 jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-196">**3 is too high.** </span></span>  
<span data-ttu-id="dd6dd-197">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-197">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="dd6dd-198">**1 jest zbyt niski.** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-198">**1 is too low.** </span></span>  
<span data-ttu-id="dd6dd-199">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="dd6dd-199">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="dd6dd-200">**2 jest poprawna. Odgadnięto go w włącza 4.**</span><span class="sxs-lookup"><span data-stu-id="dd6dd-200">**2 is correct. You guessed it in 4 turns.**</span></span>      <span data-ttu-id="dd6dd-201">Zaktualizowany interfejs `WriteLine` danych wyjściowych jest zawarty w pliku śledzenia, w tym dane wyjściowe `WriteLine` , dodanego w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-201">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>  
  
4.  <span data-ttu-id="dd6dd-202">Wrócić do numerów guessing aplikacji i wybierz jedną z przepływów pracy, które zostało uruchomione, zanim aktualizacje zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-202">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="dd6dd-203">Wersja aktualnie wybranego przepływu pracy można zidentyfikować, analizując informacje o wersji, która jest wyświetlana poniżej oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-203">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="dd6dd-204">Wprowadź kilka prób i należy pamiętać, że stan aktualizacji dopasowania `WriteLine` działania dane wyjściowe z poprzedniej wersji, a nie dołączaj wynik użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-204">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="dd6dd-205">Wynika to z faktu te przepływy pracy korzystają z poprzednich definicji przepływu pracy, który nie ma `WriteLine` aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-205">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>  
  
     <span data-ttu-id="dd6dd-206">W następnym kroku [porady: aktualizacji definicji wystąpienia przepływu pracy z](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), działanie `v1` wystąpienia przepływu pracy są aktualizowane i zawierają nowe funkcje, co `v2` wystąpień.</span><span class="sxs-lookup"><span data-stu-id="dd6dd-206">In the next step, [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
