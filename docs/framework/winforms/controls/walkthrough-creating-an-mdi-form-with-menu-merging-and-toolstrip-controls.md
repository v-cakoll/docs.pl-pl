---
title: 'Przewodnik: tworzenie formularza MDI ze scalaniem menu i kontrolkami ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: 5853760231cbece27805923c009d83e16c9b0a5e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211558"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="ccd56-102">Przewodnik: tworzenie formularza MDI ze scalaniem menu i kontrolkami ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ccd56-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>

<span data-ttu-id="ccd56-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw obsługuje wiele aplikacji interfejsu (MDI) dokumentu i <xref:System.Windows.Forms.MenuStrip> kontrolka obsługuje scalania menu.</span><span class="sxs-lookup"><span data-stu-id="ccd56-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="ccd56-104">Formularze MDI może również <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ccd56-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="ccd56-105">W tym instruktażu przedstawiono sposób użycia <xref:System.Windows.Forms.ToolStripPanel> formanty z formularza MDI.</span><span class="sxs-lookup"><span data-stu-id="ccd56-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="ccd56-106">Formularz obsługuje także menu scalanie z menu podrzędne.</span><span class="sxs-lookup"><span data-stu-id="ccd56-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="ccd56-107">Następujące zadania są przedstawione w niniejszym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="ccd56-107">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="ccd56-108">Tworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ccd56-108">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="ccd56-109">Tworzenie menu głównego dla formularza użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ccd56-109">Creating the main menu for your form.</span></span> <span data-ttu-id="ccd56-110">Rzeczywista nazwa menu będą się różnić.</span><span class="sxs-lookup"><span data-stu-id="ccd56-110">The actual name of the menu will vary.</span></span>

- <span data-ttu-id="ccd56-111">Dodawanie <xref:System.Windows.Forms.ToolStripPanel> kontrolę **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>

- <span data-ttu-id="ccd56-112">Tworzenie formularza podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ccd56-112">Creating a child form.</span></span>

- <span data-ttu-id="ccd56-113">Rozmieszczanie <xref:System.Windows.Forms.ToolStripPanel> formanty według porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="ccd56-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>

<span data-ttu-id="ccd56-114">Po zakończeniu będziesz mieć formularza MDI, która obsługuje scalania menu i ruchome <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ccd56-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="ccd56-115">Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Tworzenie formularza MDI za pomocą scalania Menu i formantów ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ccd56-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ccd56-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ccd56-116">Prerequisites</span></span>

<span data-ttu-id="ccd56-117">Visual Studio w celu przeprowadzenia tego instruktażu jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="ccd56-117">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="ccd56-118">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="ccd56-118">Create the project</span></span>

1. <span data-ttu-id="ccd56-119">W programie Visual Studio Utwórz projekt aplikacji Windows o nazwie **MdiForm** (**pliku** > **New** > **projektu**  >  **Visual C#**  lub **języka Visual Basic** > **Classic Desktop**  >   **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="ccd56-119">In Visual Studio, create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="ccd56-120">W programie Windows Forms Designer wybierz formularz.</span><span class="sxs-lookup"><span data-stu-id="ccd56-120">In the Windows Forms Designer, select the form.</span></span>

3. <span data-ttu-id="ccd56-121">W oknie właściwości ustaw wartość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> do `true`.</span><span class="sxs-lookup"><span data-stu-id="ccd56-121">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>

## <a name="create-the-main-menu"></a><span data-ttu-id="ccd56-122">Tworzenie menu głównego</span><span class="sxs-lookup"><span data-stu-id="ccd56-122">Create the main menu</span></span>

<span data-ttu-id="ccd56-123">Formularza nadrzędnego MDI zawiera menu głównego.</span><span class="sxs-lookup"><span data-stu-id="ccd56-123">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="ccd56-124">Menu główne ma jeden element menu o nazwie **okna**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-124">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="ccd56-125">Za pomocą **okna** element menu może tworzenie formularzy podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="ccd56-125">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="ccd56-126">Elementy menu z formularze podrzędne są scalane w menu głównym.</span><span class="sxs-lookup"><span data-stu-id="ccd56-126">Menu items from child forms are merged into the main menu.</span></span>

1. <span data-ttu-id="ccd56-127">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> formant na formularzu.</span><span class="sxs-lookup"><span data-stu-id="ccd56-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>

2. <span data-ttu-id="ccd56-128">Dodaj <xref:System.Windows.Forms.ToolStripMenuItem> do <xref:System.Windows.Forms.MenuStrip> kontroli i nadaj mu nazwę **okna**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-128">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>

3. <span data-ttu-id="ccd56-129">Wybierz <xref:System.Windows.Forms.MenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ccd56-129">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

4. <span data-ttu-id="ccd56-130">W oknie właściwości ustaw wartość <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwość `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="ccd56-130">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>

5. <span data-ttu-id="ccd56-131">Dodaj podelement do **okna** element menu, a następnie nazwę podelement **New**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-131">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>

6. <span data-ttu-id="ccd56-132">W oknie dialogowym właściwości kliknij **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-132">In the Properties window, click **Events**.</span></span>

7. <span data-ttu-id="ccd56-133">Kliknij dwukrotnie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ccd56-133">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

     <span data-ttu-id="ccd56-134">Windows Forms Designer generuje moduł obsługi zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ccd56-134">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

8. <span data-ttu-id="ccd56-135">Wstaw następujący kod do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ccd56-135">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="ccd56-136">Dodawanie ToolStripPanel, kontrolka do przybornika</span><span class="sxs-lookup"><span data-stu-id="ccd56-136">Add the ToolStripPanel control to the Toolbox</span></span>

<span data-ttu-id="ccd56-137">Kiedy używasz <xref:System.Windows.Forms.MenuStrip> formanty z formularza MDI konieczne jest posiadanie <xref:System.Windows.Forms.ToolStripPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ccd56-137">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="ccd56-138">Należy dodać <xref:System.Windows.Forms.ToolStripPanel> kontrolę **przybornika** Tworzenie formularza MDI w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="ccd56-138">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="ccd56-139">Otwórz **przybornika**, a następnie kliknij przycisk **wszystkie formularze Windows** kartę, aby wyświetlić dostępne kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ccd56-139">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>

2. <span data-ttu-id="ccd56-140">Kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów i wybierz **wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-140">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>

3. <span data-ttu-id="ccd56-141">W **wybierz elementy przybornika** okno dialogowe, przewiń w dół **nazwa** kolumny, aż znajdziesz **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-141">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>

4. <span data-ttu-id="ccd56-142">Zaznacz pole wyboru przy **ToolStripPanel**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-142">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>

     <span data-ttu-id="ccd56-143"><xref:System.Windows.Forms.ToolStripPanel> Formant jest widoczny w **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-143">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>

## <a name="create-a-child-form"></a><span data-ttu-id="ccd56-144">Tworzenie formularza podrzędnego</span><span class="sxs-lookup"><span data-stu-id="ccd56-144">Create a child form</span></span>

<span data-ttu-id="ccd56-145">W tej procedurze, zdefiniujesz klasę formularza oddzielny podrzędną, który ma swój własny <xref:System.Windows.Forms.MenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ccd56-145">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="ccd56-146">Elementy menu dla tego formularza są scalane z tymi z formularza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ccd56-146">The menu items for this form are merged with those of the parent form.</span></span>

1. <span data-ttu-id="ccd56-147">Dodaj nowy formularz o nazwie `ChildForm` do projektu.</span><span class="sxs-lookup"><span data-stu-id="ccd56-147">Add a new form named `ChildForm` to the project.</span></span>

     <span data-ttu-id="ccd56-148">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie formularzy Windows do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ccd56-148">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>

2. <span data-ttu-id="ccd56-149">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> formant na formularzu podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="ccd56-149">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>

3. <span data-ttu-id="ccd56-150">Kliknij przycisk <xref:System.Windows.Forms.MenuStrip> symbol tagu inteligentnego kontrolki (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), a następnie wybierz pozycję **Edytuj elementy**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-150">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>

4. <span data-ttu-id="ccd56-151">W **Edytor kolekcji elementów** okna dialogowego Dodaj nowy <xref:System.Windows.Forms.ToolStripMenuItem> o nazwie **ChildMenuItem** do menu podrzędne.</span><span class="sxs-lookup"><span data-stu-id="ccd56-151">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>

     <span data-ttu-id="ccd56-152">Aby uzyskać więcej informacji, zobacz [Edytor kolekcji elementów ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ccd56-152">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>

## <a name="test-the-form"></a><span data-ttu-id="ccd56-153">Przetestuj formularz</span><span class="sxs-lookup"><span data-stu-id="ccd56-153">Test the form</span></span>

1. <span data-ttu-id="ccd56-154">Naciśnij klawisz **F5** Aby skompilować i uruchomić formularz.</span><span class="sxs-lookup"><span data-stu-id="ccd56-154">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="ccd56-155">Kliknij przycisk **okna** element menu, aby otworzyć menu, a następnie kliknij przycisk **New**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-155">Click the **Window** menu item to open the menu, and then click **New**.</span></span>

     <span data-ttu-id="ccd56-156">Nowy formularz podrzędny jest tworzony w obszar klienta MDI formularza.</span><span class="sxs-lookup"><span data-stu-id="ccd56-156">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="ccd56-157">Menu formularz podrzędny jest scalany z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="ccd56-157">The child form's menu is merged with the main menu.</span></span>

3. <span data-ttu-id="ccd56-158">Zamknij formularz podrzędny.</span><span class="sxs-lookup"><span data-stu-id="ccd56-158">Close the child form.</span></span>

     <span data-ttu-id="ccd56-159">Formularz podrzędny menu zostanie usunięty z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="ccd56-159">The child form's menu is removed from the main menu.</span></span>

4. <span data-ttu-id="ccd56-160">Kliknij przycisk **New** kilka razy.</span><span class="sxs-lookup"><span data-stu-id="ccd56-160">Click **New** several times.</span></span>

     <span data-ttu-id="ccd56-161">Formularze podrzędne są automatycznie wyświetlane w obszarze **okna** element menu, ponieważ <xref:System.Windows.Forms.MenuStrip> kontrolki <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwość jest przypisana.</span><span class="sxs-lookup"><span data-stu-id="ccd56-161">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>

## <a name="add-toolstrip-support"></a><span data-ttu-id="ccd56-162">Dodanie obsługi elementu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ccd56-162">Add ToolStrip support</span></span>

<span data-ttu-id="ccd56-163">W ramach tej procedury dodasz cztery <xref:System.Windows.Forms.ToolStrip> formantów do formularza nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="ccd56-163">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="ccd56-164">Każdy <xref:System.Windows.Forms.ToolStrip> formant jest dodawany wewnątrz <xref:System.Windows.Forms.ToolStripPanel> formant, który jest zadokowany do krawędzi formularza.</span><span class="sxs-lookup"><span data-stu-id="ccd56-164">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>

1. <span data-ttu-id="ccd56-165">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ToolStripPanel> formant na formularzu.</span><span class="sxs-lookup"><span data-stu-id="ccd56-165">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>

2. <span data-ttu-id="ccd56-166">Za pomocą <xref:System.Windows.Forms.ToolStripPanel> zaznaczony formant, kliknij dwukrotnie <xref:System.Windows.Forms.ToolStrip> w kontrolce **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-166">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>

     <span data-ttu-id="ccd56-167">A <xref:System.Windows.Forms.ToolStrip> formant zostanie utworzony w <xref:System.Windows.Forms.ToolStripPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ccd56-167">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

3. <span data-ttu-id="ccd56-168">Wybierz <xref:System.Windows.Forms.ToolStripPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ccd56-168">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

4. <span data-ttu-id="ccd56-169">W oknie Właściwości zmień wartość kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="ccd56-169">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>

     <span data-ttu-id="ccd56-170"><xref:System.Windows.Forms.ToolStripPanel> Kontrolować doków do formularza, pod menu głównego po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="ccd56-170">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="ccd56-171">Obszar klienta MDI dopasowuje się do rozmiaru <xref:System.Windows.Forms.ToolStripPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ccd56-171">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

5. <span data-ttu-id="ccd56-172">Powtórz kroki od 1 do 4.</span><span class="sxs-lookup"><span data-stu-id="ccd56-172">Repeat steps 1 through 4.</span></span>

     <span data-ttu-id="ccd56-173">Dokowanie nowy <xref:System.Windows.Forms.ToolStripPanel> kontrolki w górnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="ccd56-173">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>

     <span data-ttu-id="ccd56-174"><xref:System.Windows.Forms.ToolStripPanel> Kontroli jest zadokowany pod menu głównego, ale po prawej stronie pierwszej <xref:System.Windows.Forms.ToolStripPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ccd56-174">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="ccd56-175">W tym kroku przedstawiono znaczenie porządek poprawnie pozycjonowania <xref:System.Windows.Forms.ToolStripPanel> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ccd56-175">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

6. <span data-ttu-id="ccd56-176">Powtórz kroki od 1 do 4 dla dwóch więcej <xref:System.Windows.Forms.ToolStripPanel> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ccd56-176">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

     <span data-ttu-id="ccd56-177">Dokowanie nowy <xref:System.Windows.Forms.ToolStripPanel> kontrolek w prawo i w dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="ccd56-177">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>

## <a name="arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="ccd56-178">Rozmieść według porządku osi Z pomocą kontrolek ToolStripPanel</span><span class="sxs-lookup"><span data-stu-id="ccd56-178">Arrange ToolStripPanel controls by Z-order</span></span>

<span data-ttu-id="ccd56-179">Położenie zadokowanego <xref:System.Windows.Forms.ToolStripPanel> kontrolkę w formularzu MDI jest określana przez położenie formantu w porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="ccd56-179">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="ccd56-180">Łatwo można rozmieścić porządek formantów w okno konspektu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ccd56-180">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>

1. <span data-ttu-id="ccd56-181">W **widoku** menu, kliknij przycisk **Windows inne**, a następnie kliknij przycisk **konspekt dokumentu**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-181">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>

     <span data-ttu-id="ccd56-182">Rozmieszczenie swoje <xref:System.Windows.Forms.ToolStripPanel> kontrolek z poprzedniej procedury jest niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="ccd56-182">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="ccd56-183">Jest to spowodowane porządku osi jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ccd56-183">This is because the z-order is not correct.</span></span> <span data-ttu-id="ccd56-184">Okno konspektu dokumentu do zmiany kolejności z formantów.</span><span class="sxs-lookup"><span data-stu-id="ccd56-184">Use the Document Outline window to change the z-order of the controls.</span></span>

2. <span data-ttu-id="ccd56-185">W oknie konspekt dokumentu wybierz **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-185">In the Document Outline window, select **ToolStripPanel4**.</span></span>

3. <span data-ttu-id="ccd56-186">Kliknij przycisk strzałki w dół wielokrotnie, dopóki **ToolStripPanel4** znajduje się w dolnej części listy.</span><span class="sxs-lookup"><span data-stu-id="ccd56-186">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>

     <span data-ttu-id="ccd56-187">**ToolStripPanel4** kontroli jest zadokowana do dolnej części formularza, poniżej innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="ccd56-187">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>

4. <span data-ttu-id="ccd56-188">Wybierz **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="ccd56-188">Select **ToolStripPanel2**.</span></span>

5. <span data-ttu-id="ccd56-189">Kliknij jeden raz przycisk strzałki w dół, aby położenie formantu trzeci na liście.</span><span class="sxs-lookup"><span data-stu-id="ccd56-189">Click the down-arrow button one time to position the control third in the list.</span></span>

     <span data-ttu-id="ccd56-190">**ToolStripPanel2** kontroli jest zadokowany do górnej części formularza, pod menu głównego i nowszych innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="ccd56-190">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>

6. <span data-ttu-id="ccd56-191">Wybierz różne formanty w **konspekt dokumentu** okna i przenoszenia ich do różnych pozycji w porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="ccd56-191">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="ccd56-192">Należy pamiętać, efekt porządku osi z o rozmieszczaniu zadokowanych formantów.</span><span class="sxs-lookup"><span data-stu-id="ccd56-192">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="ccd56-193">Użyj klawiszy CTRL-Z lub **Cofnij** na **Edytuj** menu, aby cofnąć zmiany.</span><span class="sxs-lookup"><span data-stu-id="ccd56-193">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>

## <a name="checkpoint---test-your-form"></a><span data-ttu-id="ccd56-194">Punkt kontrolny — testowanie formularza</span><span class="sxs-lookup"><span data-stu-id="ccd56-194">Checkpoint - test your form</span></span>

1. <span data-ttu-id="ccd56-195">Naciśnij klawisz **F5** Aby skompilować i uruchomić formularz.</span><span class="sxs-lookup"><span data-stu-id="ccd56-195">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="ccd56-196">Kliknij przycisk uchwyt zmiany z <xref:System.Windows.Forms.ToolStrip> kontroli i przeciągnij formant w różnych miejscach na formularzu.</span><span class="sxs-lookup"><span data-stu-id="ccd56-196">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>

     <span data-ttu-id="ccd56-197">Można przeciągnąć <xref:System.Windows.Forms.ToolStrip> formant z jednej <xref:System.Windows.Forms.ToolStripPanel> formantu do innego.</span><span class="sxs-lookup"><span data-stu-id="ccd56-197">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ccd56-198">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ccd56-198">Next steps</span></span>

<span data-ttu-id="ccd56-199">W tym przewodniku zostały utworzone za pomocą formularza nadrzędnego MDI <xref:System.Windows.Forms.ToolStrip> kontrolek i scalanie menu.</span><span class="sxs-lookup"><span data-stu-id="ccd56-199">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="ccd56-200">Możesz użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:</span><span class="sxs-lookup"><span data-stu-id="ccd56-200">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="ccd56-201">Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="ccd56-201">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="ccd56-202">Aby uzyskać więcej informacji, zobacz [— informacje o składniku ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ccd56-202">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="ccd56-203">Formularz utworzony za pomocą automatycznie wypełnione standardowe menu.</span><span class="sxs-lookup"><span data-stu-id="ccd56-203">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="ccd56-204">Aby uzyskać więcej informacji, zobacz [instruktażu: Zapewnianie elementów Menu standardowego dla formularza](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="ccd56-204">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="ccd56-205">Nadaj swojej <xref:System.Windows.Forms.ToolStrip> profesjonalny wygląd kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ccd56-205">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="ccd56-206">Aby uzyskać więcej informacji, zobacz [jak: Ustawienie modułu renderowania ToolStrip dla aplikacji](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="ccd56-206">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ccd56-207">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccd56-207">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="ccd56-208">Instrukcje: Tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="ccd56-208">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="ccd56-209">Instrukcje: Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="ccd56-209">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="ccd56-210">Instrukcje: Wstawianie elementu MenuStrip do Menu rozwijanego MDI</span><span class="sxs-lookup"><span data-stu-id="ccd56-210">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="ccd56-211">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="ccd56-211">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
