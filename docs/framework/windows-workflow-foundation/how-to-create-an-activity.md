---
title: 'Porady: tworzenie działania'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 8aa6900b26bbe9f77fe0802a7929febe5af61269
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539619"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="fa7ad-102">Porady: tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="fa7ad-102">How to: Create an Activity</span></span>

<span data-ttu-id="fa7ad-103">Działania są jednostki podstawowe zachowanie w [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa7ad-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="fa7ad-104">Logika wykonania działania, które można zaimplementować w kodzie zarządzanym lub można ją wdrożyć za pomocą innych działań.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="fa7ad-105">W tym temacie pokazano, jak utworzyć dwóch działań.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="fa7ad-106">Pierwsze działanie jest proste działania, które używa kodu, aby zaimplementować logikę jego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="fa7ad-107">Implementacja drugiego działania jest zdefiniowana za pomocą innych działań.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="fa7ad-108">Te działania są używane w kolejnych krokach samouczka.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-108">These activities are used in following steps in the tutorial.</span></span>

> [!NOTE]
> <span data-ttu-id="fa7ad-109">Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="fa7ad-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="fa7ad-110">Utwórz projekt biblioteki działań</span><span class="sxs-lookup"><span data-stu-id="fa7ad-110">Create the activity library project</span></span>

1.  <span data-ttu-id="fa7ad-111">Otwórz program Visual Studio i wybierz polecenie **New** > **projektu** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-111">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2.  <span data-ttu-id="fa7ad-112">W **nowy projekt** okna dialogowego, w obszarze **zainstalowane** kategorii, wybierz opcję **Visual C#** > **przepływu pracy** (lub **Języka Visual Basic** > **przepływu pracy**).</span><span class="sxs-lookup"><span data-stu-id="fa7ad-112">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="fa7ad-113">Jeśli nie widzisz **przepływu pracy** kategorii szablonu, użytkownik może być konieczne zainstalowanie **Windows Workflow Foundation** składnika programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-113">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="fa7ad-114">Wybierz **Otwórz Instalator programu Visual Studio** linku w lewej części **nowy projekt** okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-114">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="fa7ad-115">Instalator programu Visual Studio wybierz **poszczególne składniki** kartę. Następnie w obszarze **działań programistycznych** kategorii, wybierz opcję **Windows Workflow Foundation** składnika.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-115">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="fa7ad-116">Wybierz **Modyfikuj** do instalacji składnika należy.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-116">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="fa7ad-117">Wybierz **Biblioteka działań** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-117">Select the **Activity Library** project template.</span></span> <span data-ttu-id="fa7ad-118">Typ `NumberGuessWorkflowActivities` w **nazwa** pole, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-118">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4.  <span data-ttu-id="fa7ad-119">Kliknij prawym przyciskiem myszy **Activity1.xaml** w **Eksploratora rozwiązań** i wybierz polecenie **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-119">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="fa7ad-120">Kliknij przycisk **OK** o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-120">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="fa7ad-121">Utwórz działanie readint —</span><span class="sxs-lookup"><span data-stu-id="fa7ad-121">Create the ReadInt activity</span></span>

1.  <span data-ttu-id="fa7ad-122">Wybierz **Dodaj nowy element** z **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-122">Choose **Add New Item** from the **Project** menu.</span></span>

2.  <span data-ttu-id="fa7ad-123">W **zainstalowane** > **wspólne elementy** węzeł **przepływu pracy**.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-123">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="fa7ad-124">Wybierz **działanie kodu** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-124">Select **Code Activity** from the **Workflow** list.</span></span>

3.  <span data-ttu-id="fa7ad-125">Typ `ReadInt` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-125">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4.  <span data-ttu-id="fa7ad-126">Zastąp istniejące `ReadInt` definicji przy użyciu następującej definicji.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-126">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="fa7ad-127">`ReadInt` Pochodzi od klasy działania <xref:System.Activities.NativeActivity%601> zamiast <xref:System.Activities.CodeActivity>, co jest ustawieniem domyślnym dla szablonu działania kodu.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-127">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="fa7ad-128"><xref:System.Activities.CodeActivity%601> można użyć, jeśli działanie zapewnia pojedynczy wynik, która jest dostępna za pośrednictwem <xref:System.Activities.Activity%601.Result%2A> argument, ale <xref:System.Activities.CodeActivity%601> nie obsługuje korzystanie z zakładek, więc <xref:System.Activities.NativeActivity%601> jest używany.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-128"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="fa7ad-129">Utwórz działanie monitu</span><span class="sxs-lookup"><span data-stu-id="fa7ad-129">Create the Prompt activity</span></span>

1.  <span data-ttu-id="fa7ad-130">Naciśnij klawisz **Ctrl**+**Shift**+**B** do skompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-130">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="fa7ad-131">Kompilowanie projektu zapewniającą `ReadInt` działania w tym projekcie ma być używany do tworzenia niestandardowych działań w tym kroku.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-131">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2.  <span data-ttu-id="fa7ad-132">Wybierz **Dodaj nowy element** z **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-132">Choose **Add New Item** from the **Project** menu.</span></span>

3.  <span data-ttu-id="fa7ad-133">W **zainstalowane** > **wspólne elementy** węzeł **przepływu pracy**.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-133">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="fa7ad-134">Wybierz **działania** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-134">Select **Activity** from the **Workflow** list.</span></span>

4.  <span data-ttu-id="fa7ad-135">Typ `Prompt` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-135">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5.  <span data-ttu-id="fa7ad-136">Kliknij dwukrotnie **Prompt.xaml** w **Eksploratora rozwiązań** do wyświetlenia w projektancie, jeśli nie jest już wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-136">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6.  <span data-ttu-id="fa7ad-137">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działania, aby wyświetlić **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-137">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7.  <span data-ttu-id="fa7ad-138">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-138">Click **Create Argument**.</span></span>

8.  <span data-ttu-id="fa7ad-139">Typ `BookmarkName` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **ciąg** z **Typ argumentu** listy rozwijanej, a następnie klawisz **Enter** można zapisać argumentu.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-139">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="fa7ad-140">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-140">Click **Create Argument**.</span></span>

10. <span data-ttu-id="fa7ad-141">Typ `Result` do **nazwa** pole, znajdujący się pod nowo dodanym `BookmarkName` argument, wybierz opcję **się** z **kierunek** listy rozwijanej wybierz **Int32** z **typ argumentu** listy rozwijanej, a następnie klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-141">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="fa7ad-142">Kliknij przycisk **utworzenia argumentu**.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-142">Click **Create Argument**.</span></span>

12. <span data-ttu-id="fa7ad-143">Typ `Text` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **ciąg** z **Typ argumentu** listy rozwijanej, a następnie klawisz **Enter** można zapisać argumentu.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-143">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="fa7ad-144">Te trzy argumenty są powiązane z argumentami odpowiedniego <xref:System.Activities.Statements.WriteLine> i `ReadInt` działań, które są dodawane do `Prompt` działania w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-144">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="fa7ad-145">Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć **argumenty** okienka.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-145">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="fa7ad-146">Przeciągnij **sekwencji** działanie z **przepływ sterowania** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety **Monitu** projektanta działań.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-146">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="fa7ad-147">Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-147">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="fa7ad-148">Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety **Sekwencji** działania.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-148">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="fa7ad-149">Powiązanie **tekstu** argument **WriteLine** działanie **tekstu** argument **monitu** działania, wpisując `Text` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole w **właściwości** okna, a następnie naciśnij klawisz **kartę** klucz dwa razy.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-149">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="fa7ad-150">Zamknięte okno technologii IntelliSense lista elementów członkowskich i zapisuje wartości właściwości, przenosząc wyboru Wyłącz właściwości.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-150">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="fa7ad-151">Można również ustawić tę właściwość, wpisując `Text` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole je.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-151">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="fa7ad-152">Jeśli **okno właściwości** nie jest wyświetlany, wybierz opcję **okno właściwości** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-152">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="fa7ad-153">Przeciągnij **readint —** działanie z **NumberGuessWorkflowActivities** części **przybornika** i upuść je **sekwencji** działanie, tak że następuje **WriteLine** działania.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-153">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="fa7ad-154">Powiąż **Nazwa_zakładki** argument **readint —** działanie **Nazwa_zakładki** argument **monitu** działania, wpisując `BookmarkName` do **wprowadź wyrażenie VB** pole po prawej stronie **Nazwa_zakładki** argument **okno właściwości**, a następnie naciśnij klawisz **Kartę** dwa razy, aby zamknąć okno technologii IntelliSense listy elementów członkowskich, a następnie Zapisz właściwość klucza.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-154">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="fa7ad-155">Powiązanie **wynik** argument **readint —** działanie **wynik** argument **monitu** działania, wpisując `Result` do **wprowadź wyrażenie VB** pole po prawej stronie **wynik** argument **okno właściwości**, a następnie naciśnij klawisz **kartę** klucza dwa razy.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-155">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="fa7ad-156">Naciśnij klawisz **Ctrl**+**Shift**+**B** do skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="fa7ad-156">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fa7ad-157">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fa7ad-157">Next steps</span></span>

<span data-ttu-id="fa7ad-158">Instrukcje dotyczące sposobu tworzenia przepływu pracy przy użyciu tych działań można znaleźć następnego kroku w tym samouczku [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="fa7ad-158">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fa7ad-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa7ad-159">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="fa7ad-160">Projektowanie i implementowanie niestandardowych działań</span><span class="sxs-lookup"><span data-stu-id="fa7ad-160">Designing and Implementing Custom Activities</span></span>](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="fa7ad-161">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="fa7ad-161">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
- [<span data-ttu-id="fa7ad-162">Instrukcje: Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fa7ad-162">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)
- [<span data-ttu-id="fa7ad-163">Używanie elementu ExpressionTextBox w projektancie działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="fa7ad-163">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)