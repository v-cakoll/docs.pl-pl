---
title: 'Porady: tworzenie działania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: deb1b6ca5c6fc996a015e32dd5e0c7b9bd6530fa
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44699998"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="e3d9f-102">Porady: tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="e3d9f-102">How to: Create an Activity</span></span>
<span data-ttu-id="e3d9f-103">Działania są jednostki podstawowe zachowanie w [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3d9f-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="e3d9f-104">Logika wykonania działania, które można zaimplementować w kodzie zarządzanym lub można ją wdrożyć za pomocą innych działań.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="e3d9f-105">W tym temacie pokazano, jak utworzyć dwóch działań.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="e3d9f-106">Pierwsze działanie jest proste działania, które używa kodu, aby zaimplementować logikę jego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="e3d9f-107">Implementacja drugiego działania jest zdefiniowana za pomocą innych działań.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="e3d9f-108">Te działania są używane w kolejnych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-108">These activities are used in following steps in the tutorial.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3d9f-109">Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="e3d9f-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-activity-library-project"></a><span data-ttu-id="e3d9f-110">Aby utworzyć projekt biblioteki działań</span><span class="sxs-lookup"><span data-stu-id="e3d9f-110">To create the activity library project</span></span>  
  
1.  <span data-ttu-id="e3d9f-111">Otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] i wybierz polecenie **New**, **projektu** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-111">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and choose **New**,  **Project** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="e3d9f-112">Rozwiń **inne typy projektów** w węźle **zainstalowane**, **szablony** listy i wybierz **Visual Studio Solutions**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-112">Expand the **Other Project Types** node in the **Installed**, **Templates** list and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="e3d9f-113">Wybierz **puste rozwiązanie** z **Visual Studio Solutions** listy.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-113">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="e3d9f-114">Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-114">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="e3d9f-115">Typ `WF45GettingStartedTutorial` w **nazwa** pole, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-115">Type `WF45GettingStartedTutorial` in the **Name** box and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="e3d9f-116">Kliknij prawym przyciskiem myszy **WF45GettingStartedTutorial** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-116">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e3d9f-117">Jeśli **Eksploratora rozwiązań** nie zostanie wyświetlone okno, wybierz **Eksploratora rozwiązań** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-117">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="e3d9f-118">W **zainstalowane** węzeł **Visual C#**, **przepływu pracy** (lub **języka Visual Basic**, **przepływu pracy**).</span><span class="sxs-lookup"><span data-stu-id="e3d9f-118">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span> <span data-ttu-id="e3d9f-119">Upewnij się, że **.NET Framework 4.5** wybrano [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] wersji listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-119">Ensure that **.NET Framework 4.5** is selected in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version drop-down list.</span></span> <span data-ttu-id="e3d9f-120">Wybierz **Biblioteka działań** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-120">Select **Activity Library** from the **Workflow** list.</span></span> <span data-ttu-id="e3d9f-121">Typ `NumberGuessWorkflowActivities` w **nazwa** pole, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-121">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3d9f-122">Zależności od tego, jaki język programowania jest skonfigurowany jako podstawowy język w programie Visual Studio, **Visual C#** lub **języka Visual Basic** węzła może znajdować się w **inne języki** w węźle **zainstalowane** węzła.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-122">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
6.  <span data-ttu-id="e3d9f-123">Kliknij prawym przyciskiem myszy **Activity1.xaml** w **Eksploratora rozwiązań** i wybierz polecenie **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-123">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="e3d9f-124">Kliknij przycisk **OK** o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-124">Click **OK** to confirm.</span></span>  
  
### <a name="to-create-the-readint-activity"></a><span data-ttu-id="e3d9f-125">Aby utworzyć działanie readint —</span><span class="sxs-lookup"><span data-stu-id="e3d9f-125">To create the ReadInt activity</span></span>  
  
1.  <span data-ttu-id="e3d9f-126">Wybierz **Dodaj nowy element** z **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-126">Choose **Add New Item** from the **Project** menu.</span></span>  
  
2.  <span data-ttu-id="e3d9f-127">W **zainstalowane**, **wspólne elementy** węzeł **przepływu pracy**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-127">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="e3d9f-128">Wybierz **działanie kodu** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-128">Select **Code Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="e3d9f-129">Typ `ReadInt` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-129">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="e3d9f-130">Zastąp istniejące `ReadInt` definicji przy użyciu następującej definicji.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-130">Replace the existing `ReadInt` definition with the following definition.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="e3d9f-131">`ReadInt` Pochodzi od klasy działania <xref:System.Activities.NativeActivity%601> zamiast <xref:System.Activities.CodeActivity>, co jest ustawieniem domyślnym dla szablonu działania kodu.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-131">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="e3d9f-132"><xref:System.Activities.CodeActivity%601> można użyć, jeśli działanie zapewnia pojedynczy wynik, która jest dostępna za pośrednictwem <xref:System.Activities.Activity%601.Result%2A> argument, ale <xref:System.Activities.CodeActivity%601> nie obsługuje korzystanie z zakładek, więc <xref:System.Activities.NativeActivity%601> jest używany.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-132"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>  
  
### <a name="to-create-the-prompt-activity"></a><span data-ttu-id="e3d9f-133">Aby utworzyć działanie monitu</span><span class="sxs-lookup"><span data-stu-id="e3d9f-133">To create the Prompt activity</span></span>  
  
1.  <span data-ttu-id="e3d9f-134">Naciśnij kombinację klawiszy CTRL+SHIFT+B. Projekt zostanie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-134">Press CTRL+SHIFT+B to build the project.</span></span> <span data-ttu-id="e3d9f-135">Kompilowanie projektu zapewniającą `ReadInt` działania w tym projekcie ma być używany do tworzenia niestandardowych działań w tym kroku.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-135">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>  
  
2.  <span data-ttu-id="e3d9f-136">Wybierz **Dodaj nowy element** z **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-136">Choose **Add New Item** from the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="e3d9f-137">W **zainstalowane**, **wspólne elementy** węzeł **przepływu pracy**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-137">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="e3d9f-138">Wybierz **działania** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-138">Select **Activity** from the **Workflow** list.</span></span>  
  
4.  <span data-ttu-id="e3d9f-139">Typ `Prompt` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-139">Type `Prompt` into the **Name** box and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="e3d9f-140">Kliknij dwukrotnie **Prompt.xaml** w **Eksploratora rozwiązań** do wyświetlenia w projektancie, jeśli nie jest już wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-140">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>  
  
6.  <span data-ttu-id="e3d9f-141">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działania, aby wyświetlić **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-141">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>  
  
7.  <span data-ttu-id="e3d9f-142">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-142">Click **Create Argument**.</span></span>  
  
8.  <span data-ttu-id="e3d9f-143">Typ `BookmarkName` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **ciąg** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-143">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
9. <span data-ttu-id="e3d9f-144">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-144">Click **Create Argument**.</span></span>  
  
10. <span data-ttu-id="e3d9f-145">Typ `Result` do **nazwa** pole, znajdujący się pod nowo dodanym `BookmarkName` argument, wybierz opcję **się** z **kierunek** listy rozwijanej wybierz **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-145">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
11. <span data-ttu-id="e3d9f-146">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-146">Click **Create Argument**.</span></span>  
  
12. <span data-ttu-id="e3d9f-147">Typ `Text` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **ciąg** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-147">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
     <span data-ttu-id="e3d9f-148">Te trzy argumenty są powiązane z argumentami odpowiedniego <xref:System.Activities.Statements.WriteLine> i `ReadInt` działań, które są dodawane do `Prompt` działania w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-148">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>  
  
13. <span data-ttu-id="e3d9f-149">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-149">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
14. <span data-ttu-id="e3d9f-150">Przeciągnij **sekwencji** działanie z **przepływ sterowania** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety **Monitu** projektanta działań.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-150">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e3d9f-151">Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-151">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
15. <span data-ttu-id="e3d9f-152">Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety **Sekwencji** działania.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>  
  
16. <span data-ttu-id="e3d9f-153">Powiązanie **tekstu** argument **WriteLine** działanie **tekstu** argument **monitu** działania, wpisując `Text` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole w **właściwości** okna, a następnie naciśnij klawisz TAB klucza dwa razy.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-153">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the TAB key two times.</span></span> <span data-ttu-id="e3d9f-154">Zamknięte okno technologii IntelliSense lista elementów członkowskich i zapisuje wartości właściwości, przenosząc wyboru Wyłącz właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-154">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="e3d9f-155">Można również ustawić tę właściwość, wpisując `Text` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole je.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-155">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e3d9f-156">Jeśli **okno właściwości** nie jest wyświetlany, wybierz opcję **okno właściwości** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-156">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
17. <span data-ttu-id="e3d9f-157">Przeciągnij **readint —** działanie z **NumberGuessWorkflowActivities** części **przybornika** i upuść je **sekwencji** działanie, tak że następuje **WriteLine** działania.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-157">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>  
  
18. <span data-ttu-id="e3d9f-158">Powiąż **Nazwa_zakładki** argument **readint —** działanie **Nazwa_zakładki** argument **monitu** działania, wpisując `BookmarkName` do **wprowadź wyrażenie VB** pole po prawej stronie **Nazwa_zakładki** argument **okno właściwości**, a następnie naciśnij klawisz TAB dwa czas, aby zamknąć okno technologii IntelliSense lista elementów członkowskich i zapisać właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-158">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the TAB key two times to close the IntelliSense list members window and save the property.</span></span>  
  
19. <span data-ttu-id="e3d9f-159">Powiązanie **wynik** argument **readint —** działanie **wynik** argument **monitu** działania, wpisując `Result` do **wprowadź wyrażenie VB** pole po prawej stronie **wynik** argument **okno właściwości**, a następnie naciśnij klawisz TAB dwa razy.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-159">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the TAB key two times.</span></span>  
  
20. <span data-ttu-id="e3d9f-160">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="e3d9f-160">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="e3d9f-161">Instrukcje dotyczące sposobu tworzenia przepływu pracy przy użyciu tych działań można znaleźć następnego kroku w tym samouczku [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="e3d9f-161">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d9f-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3d9f-162">See Also</span></span>  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [<span data-ttu-id="e3d9f-163">Projektowanie i implementowanie niestandardowych działań</span><span class="sxs-lookup"><span data-stu-id="e3d9f-163">Designing and Implementing Custom Activities</span></span>](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [<span data-ttu-id="e3d9f-164">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="e3d9f-164">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="e3d9f-165">Instrukcje: Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e3d9f-165">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="e3d9f-166">Używanie elementu ExpressionTextBox w projektancie działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="e3d9f-166">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
