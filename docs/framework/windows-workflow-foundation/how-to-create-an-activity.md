---
title: 'Instrukcje: Tworzenie działania'
description: 'W tym artykule opisano sposób tworzenia dwóch działań w programie Workflow Foundation: jeden, który używa kodu do implementowania logiki i jednego zdefiniowanego przy użyciu innych działań.'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: dae099d102b0c85d09a1ef8bcce56e8a9096bd20
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419593"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="a3979-103">Instrukcje: Tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="a3979-103">How to: Create an Activity</span></span>

<span data-ttu-id="a3979-104">Działania są podstawową jednostką zachowania w programie [!INCLUDE[wf1](../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a3979-104">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="a3979-105">Logikę wykonywania działania można zaimplementować w kodzie zarządzanym lub można ją zaimplementować przy użyciu innych działań.</span><span class="sxs-lookup"><span data-stu-id="a3979-105">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="a3979-106">W tym temacie przedstawiono sposób tworzenia dwóch działań.</span><span class="sxs-lookup"><span data-stu-id="a3979-106">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="a3979-107">Pierwsze działanie to proste działanie, które używa kodu do zaimplementowania logiki wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a3979-107">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="a3979-108">Implementacja drugiego działania jest definiowana przy użyciu innych działań.</span><span class="sxs-lookup"><span data-stu-id="a3979-108">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="a3979-109">Te działania są używane w następujących krokach w samouczku.</span><span class="sxs-lookup"><span data-stu-id="a3979-109">These activities are used in following steps in the tutorial.</span></span>

> [!NOTE]
> <span data-ttu-id="a3979-110">Aby pobrać kompletną wersję samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="a3979-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="a3979-111">Utwórz projekt biblioteki działań</span><span class="sxs-lookup"><span data-stu-id="a3979-111">Create the activity library project</span></span>

1. <span data-ttu-id="a3979-112">Otwórz program Visual Studio i wybierz pozycję **Nowy**  >  **projekt** z menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="a3979-112">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2. <span data-ttu-id="a3979-113">W oknie dialogowym **Nowy projekt** w obszarze **zainstalowana** Kategoria wybierz pozycję przepływ pracy w **języku Visual C#**  >  **Workflow** (lub **Visual Basic**  >  **przepływ pracy**).</span><span class="sxs-lookup"><span data-stu-id="a3979-113">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="a3979-114">Jeśli nie widzisz kategorii szablonów **przepływu pracy** , może być konieczne zainstalowanie składnika **Windows Workflow Foundation** programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3979-114">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="a3979-115">Wybierz łącze **otwórz Instalator programu Visual Studio** po lewej stronie okna dialogowego **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="a3979-115">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="a3979-116">W Instalator programu Visual Studio wybierz kartę **poszczególne składniki** . Następnie w kategorii **działania deweloperskie** wybierz składnik **Windows Workflow Foundation** .</span><span class="sxs-lookup"><span data-stu-id="a3979-116">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="a3979-117">Wybierz pozycję **Modyfikuj** , aby zainstalować składnik.</span><span class="sxs-lookup"><span data-stu-id="a3979-117">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="a3979-118">Wybierz szablon projektu **Biblioteka działań** .</span><span class="sxs-lookup"><span data-stu-id="a3979-118">Select the **Activity Library** project template.</span></span> <span data-ttu-id="a3979-119">Wpisz `NumberGuessWorkflowActivities` w polu **Nazwa** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a3979-119">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4. <span data-ttu-id="a3979-120">Kliknij prawym przyciskiem myszy **zakończeniu. XAML** w **Eksplorator rozwiązań** i wybierz polecenie **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="a3979-120">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="a3979-121">Kliknij przycisk **OK** , aby potwierdzić.</span><span class="sxs-lookup"><span data-stu-id="a3979-121">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="a3979-122">Tworzenie działania ReadInt</span><span class="sxs-lookup"><span data-stu-id="a3979-122">Create the ReadInt activity</span></span>

1. <span data-ttu-id="a3979-123">Wybierz pozycję **Dodaj nowy element** z menu **projekt** .</span><span class="sxs-lookup"><span data-stu-id="a3979-123">Choose **Add New Item** from the **Project** menu.</span></span>

2. <span data-ttu-id="a3979-124">W węźle **zainstalowane**  >  **elementy wspólne** wybierz pozycję **przepływ pracy**.</span><span class="sxs-lookup"><span data-stu-id="a3979-124">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="a3979-125">Wybierz **działanie Code** z listy **przepływów pracy** .</span><span class="sxs-lookup"><span data-stu-id="a3979-125">Select **Code Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="a3979-126">Wpisz tekst `ReadInt` w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="a3979-126">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4. <span data-ttu-id="a3979-127">Zastąp istniejącą `ReadInt` definicję następującą definicją.</span><span class="sxs-lookup"><span data-stu-id="a3979-127">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="a3979-128">`ReadInt`Działanie pochodzi od <xref:System.Activities.NativeActivity%601> zamiast <xref:System.Activities.CodeActivity> , czyli domyślnego dla szablonu działania kodu.</span><span class="sxs-lookup"><span data-stu-id="a3979-128">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="a3979-129"><xref:System.Activities.CodeActivity%601>może być używany, jeśli działanie zawiera pojedynczy wynik, który jest udostępniany przez <xref:System.Activities.Activity%601.Result%2A> argument, ale nie <xref:System.Activities.CodeActivity%601> obsługuje użycia zakładek, więc <xref:System.Activities.NativeActivity%601> jest używany.</span><span class="sxs-lookup"><span data-stu-id="a3979-129"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="a3979-130">Utwórz działanie monitu</span><span class="sxs-lookup"><span data-stu-id="a3979-130">Create the Prompt activity</span></span>

1. <span data-ttu-id="a3979-131">Naciśnij **klawisze CTRL** + **SHIFT** + **B** , aby skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="a3979-131">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="a3979-132">Kompilowanie projektu umożliwia `ReadInt` działanie w tym projekcie do użycia w celu utworzenia niestandardowego działania z tego kroku.</span><span class="sxs-lookup"><span data-stu-id="a3979-132">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2. <span data-ttu-id="a3979-133">Wybierz pozycję **Dodaj nowy element** z menu **projekt** .</span><span class="sxs-lookup"><span data-stu-id="a3979-133">Choose **Add New Item** from the **Project** menu.</span></span>

3. <span data-ttu-id="a3979-134">W węźle **zainstalowane**  >  **elementy wspólne** wybierz pozycję **przepływ pracy**.</span><span class="sxs-lookup"><span data-stu-id="a3979-134">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="a3979-135">Wybierz **działanie** z listy **przepływów pracy** .</span><span class="sxs-lookup"><span data-stu-id="a3979-135">Select **Activity** from the **Workflow** list.</span></span>

4. <span data-ttu-id="a3979-136">Wpisz tekst `Prompt` w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="a3979-136">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5. <span data-ttu-id="a3979-137">Kliknij dwukrotnie pozycję **Prompt. XAML** w **Eksplorator rozwiązań** , aby wyświetlić ją w projektancie, jeśli nie jest jeszcze wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="a3979-137">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6. <span data-ttu-id="a3979-138">Kliknij pozycję **argumenty** w lewym dolnym rogu projektanta działań, aby wyświetlić okienko **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="a3979-138">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7. <span data-ttu-id="a3979-139">Kliknij przycisk **Utwórz argument**.</span><span class="sxs-lookup"><span data-stu-id="a3979-139">Click **Create Argument**.</span></span>

8. <span data-ttu-id="a3979-140">Wpisz tekst w `BookmarkName` polu **Nazwa** , wybierz **pozycję z** listy rozwijanej **kierunek** , wybierz pozycję **ciąg** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz **Enter** , aby zapisać argument.</span><span class="sxs-lookup"><span data-stu-id="a3979-140">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="a3979-141">Kliknij przycisk **Utwórz argument**.</span><span class="sxs-lookup"><span data-stu-id="a3979-141">Click **Create Argument**.</span></span>

10. <span data-ttu-id="a3979-142">Wpisz `Result` w polu **Nazwa** , który znajduje się pod nowo dodanym `BookmarkName` argumentem **Out** , wybierz pozycję z listy rozwijanej **kierunek** , wybierz pozycję **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="a3979-142">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="a3979-143">Kliknij przycisk **Utwórz argument**.</span><span class="sxs-lookup"><span data-stu-id="a3979-143">Click **Create Argument**.</span></span>

12. <span data-ttu-id="a3979-144">Wpisz tekst w `Text` polu **Nazwa** , wybierz **pozycję z** listy rozwijanej **kierunek** , wybierz pozycję **ciąg** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz **Enter** , aby zapisać argument.</span><span class="sxs-lookup"><span data-stu-id="a3979-144">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="a3979-145">Te trzy argumenty są powiązane z odpowiednimi argumentami <xref:System.Activities.Statements.WriteLine> i `ReadInt` działaniami, które są dodawane do `Prompt` działania w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="a3979-145">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="a3979-146">Kliknij pozycję **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć okienko **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="a3979-146">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="a3979-147">Przeciągnij aktywność **sekwencji** z sekcji **przepływ sterowania** w **przyborniku** i upuść ją na **działanie upuść w tym miejscu** w projektancie działań **monitu** .</span><span class="sxs-lookup"><span data-stu-id="a3979-147">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="a3979-148">Jeśli okno **Przybornik** nie jest wyświetlane, wybierz pozycję **Przybornik** z menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="a3979-148">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="a3979-149">Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je na **działanie Drop tutaj** etykieta działania **sekwencji** .</span><span class="sxs-lookup"><span data-stu-id="a3979-149">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="a3979-150">Powiąż argument **Text** działania **WriteLine** z argumentem **Text** działania **Prompt** , wpisując w polu `Text` **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** w oknie **Właściwości** , a następnie naciśnij klawisz **Tab** dwa razy.</span><span class="sxs-lookup"><span data-stu-id="a3979-150">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="a3979-151">Spowoduje to odrzucenie okna członków listy IntelliSense i zapisanie wartości właściwości poprzez przeniesienie zaznaczenia poza właściwość.</span><span class="sxs-lookup"><span data-stu-id="a3979-151">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="a3979-152">Tę właściwość można również ustawić, wpisując `Text` w polu **wprowadź wyrażenie języka C#** lub wprowadzając pole **wyrażenia VB** w samym działaniu.</span><span class="sxs-lookup"><span data-stu-id="a3979-152">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="a3979-153">Jeśli **okno właściwości** nie jest wyświetlane, wybierz pozycję **okno właściwości** w menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="a3979-153">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="a3979-154">Przeciągnij działanie **ReadInt** z sekcji **NumberGuessWorkflowActivities** w **przyborniku** i upuść je w działaniu **sekwencji** , tak aby była zgodna z działaniem **WriteLine** .</span><span class="sxs-lookup"><span data-stu-id="a3979-154">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="a3979-155">Powiąż argument **BookmarkName** działania **ReadInt** z argumentem **BookmarkName** działania **Prompt** , wpisując w `BookmarkName` polu **wprowadź wyrażenie VB** z prawej strony argumentu **zakładkaname** w **oknie właściwości**, a następnie naciśnij klawisz **Tab** dwa razy, aby zamknąć okno członków listy IntelliSense i zapisać właściwość.</span><span class="sxs-lookup"><span data-stu-id="a3979-155">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="a3979-156">Powiązanie argumentu **wynik** działania **ReadInt** z argumentem **wynik** działania **monitu** , wpisując `Result` w polu **wprowadź wyrażenie VB** z prawej strony argumentu **wynik** w **oknie właściwości**, a następnie naciskając klawisz **Tab** dwa razy.</span><span class="sxs-lookup"><span data-stu-id="a3979-156">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="a3979-157">Naciśnij **klawisze CTRL** + **SHIFT** + **B** , aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="a3979-157">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a3979-158">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a3979-158">Next steps</span></span>

<span data-ttu-id="a3979-159">Aby uzyskać instrukcje dotyczące sposobu tworzenia przepływu pracy przy użyciu tych działań, zobacz następny krok w samouczku [: tworzenie przepływu pracy](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="a3979-159">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a3979-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3979-160">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="a3979-161">Projektowanie i implementowanie niestandardowych działań</span><span class="sxs-lookup"><span data-stu-id="a3979-161">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="a3979-162">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="a3979-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="a3979-163">Instrukcje: Tworzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a3979-163">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="a3979-164">Używanie elementu ExpressionTextBox w projektancie działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a3979-164">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
