---
title: 'Wskazówki: tworzenie formularza MDI ze scalaniem menu i formantami ToolStrip'
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
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628790"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="0c040-102">Wskazówki: tworzenie formularza MDI ze scalaniem menu i formantami ToolStrip</span><span class="sxs-lookup"><span data-stu-id="0c040-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>

<span data-ttu-id="0c040-103">Przestrzeń nazw <xref:System.Windows.Forms?displayProperty=nameWithType> obsługuje aplikacje interfejsu wielu dokumentów (MDI), a kontrolka <xref:System.Windows.Forms.MenuStrip> obsługuje scalanie menu.</span><span class="sxs-lookup"><span data-stu-id="0c040-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="0c040-104">Formularze MDI mogą również <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0c040-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="0c040-105">W tym instruktażu pokazano, jak używać formantów <xref:System.Windows.Forms.ToolStripPanel> z formularzem MDI.</span><span class="sxs-lookup"><span data-stu-id="0c040-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="0c040-106">Formularz obsługuje również scalanie menu z menu podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="0c040-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="0c040-107">W tym instruktażu przedstawiono następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="0c040-107">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="0c040-108">Tworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0c040-108">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="0c040-109">Tworzenie menu głównego formularza.</span><span class="sxs-lookup"><span data-stu-id="0c040-109">Creating the main menu for your form.</span></span> <span data-ttu-id="0c040-110">Rzeczywista nazwa menu będzie się różnić.</span><span class="sxs-lookup"><span data-stu-id="0c040-110">The actual name of the menu will vary.</span></span>

- <span data-ttu-id="0c040-111">Dodawanie kontrolki <xref:System.Windows.Forms.ToolStripPanel> do **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="0c040-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>

- <span data-ttu-id="0c040-112">Tworzenie formularza podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="0c040-112">Creating a child form.</span></span>

- <span data-ttu-id="0c040-113">Rozmieszczanie kontrolek <xref:System.Windows.Forms.ToolStripPanel> według kolejności z.</span><span class="sxs-lookup"><span data-stu-id="0c040-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>

<span data-ttu-id="0c040-114">Po zakończeniu będziesz mieć formularz MDI obsługujący scalanie menu i ruchome kontrolki <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="0c040-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="0c040-115">Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Create a MDI form with menu Scales and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="0c040-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0c040-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0c040-116">Prerequisites</span></span>

<span data-ttu-id="0c040-117">Aby ukończyć ten przewodnik, musisz mieć program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0c040-117">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="0c040-118">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="0c040-118">Create the project</span></span>

1. <span data-ttu-id="0c040-119">W programie Visual Studio Utwórz projekt aplikacji systemu Windows o **nazwie MdiForm** (**plik** > **New** > **Project** > **Visual C#**  lub **Visual Basic** > **klasycznego pulpitu** > Windows Forms **aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="0c040-119">In Visual Studio, create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="0c040-120">W Projektant formularzy systemu Windows wybierz formularz.</span><span class="sxs-lookup"><span data-stu-id="0c040-120">In the Windows Forms Designer, select the form.</span></span>

3. <span data-ttu-id="0c040-121">W okno Właściwości ustaw wartość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> do `true`.</span><span class="sxs-lookup"><span data-stu-id="0c040-121">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>

## <a name="create-the-main-menu"></a><span data-ttu-id="0c040-122">Utwórz menu główne</span><span class="sxs-lookup"><span data-stu-id="0c040-122">Create the main menu</span></span>

<span data-ttu-id="0c040-123">Nadrzędny formularz MDI zawiera menu główne.</span><span class="sxs-lookup"><span data-stu-id="0c040-123">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="0c040-124">Menu główne ma jeden element menu o nazwie **window**.</span><span class="sxs-lookup"><span data-stu-id="0c040-124">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="0c040-125">Za pomocą elementu menu **okno** można tworzyć formularze podrzędne.</span><span class="sxs-lookup"><span data-stu-id="0c040-125">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="0c040-126">Elementy menu z formularzy podrzędnych są scalane z menu głównym.</span><span class="sxs-lookup"><span data-stu-id="0c040-126">Menu items from child forms are merged into the main menu.</span></span>

1. <span data-ttu-id="0c040-127">Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.MenuStrip> na formularz.</span><span class="sxs-lookup"><span data-stu-id="0c040-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>

2. <span data-ttu-id="0c040-128">Dodaj <xref:System.Windows.Forms.ToolStripMenuItem> do kontrolki <xref:System.Windows.Forms.MenuStrip> i nadaj jej nazwę **okno**.</span><span class="sxs-lookup"><span data-stu-id="0c040-128">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>

3. <span data-ttu-id="0c040-129">Wybierz kontrolkę <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="0c040-129">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

4. <span data-ttu-id="0c040-130">W okno Właściwości ustaw wartość właściwości <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> na `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="0c040-130">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>

5. <span data-ttu-id="0c040-131">Dodaj element SubItem do elementu menu **okno** , a następnie nadaj mu nazwę **Nowy**.</span><span class="sxs-lookup"><span data-stu-id="0c040-131">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>

6. <span data-ttu-id="0c040-132">W okno Właściwości kliknij pozycję **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="0c040-132">In the Properties window, click **Events**.</span></span>

7. <span data-ttu-id="0c040-133">Kliknij dwukrotnie zdarzenie <xref:System.Windows.Forms.ToolStripItem.Click>.</span><span class="sxs-lookup"><span data-stu-id="0c040-133">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

     <span data-ttu-id="0c040-134">Projektant formularzy systemu Windows generuje procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click>.</span><span class="sxs-lookup"><span data-stu-id="0c040-134">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

8. <span data-ttu-id="0c040-135">Wstaw następujący kod do programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0c040-135">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="0c040-136">Dodaj kontrolkę ToolStripPanel do przybornika</span><span class="sxs-lookup"><span data-stu-id="0c040-136">Add the ToolStripPanel control to the Toolbox</span></span>

<span data-ttu-id="0c040-137">W przypadku używania formantów <xref:System.Windows.Forms.MenuStrip> z formularzem MDI należy mieć kontrolkę <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="0c040-137">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="0c040-138">Musisz dodać formant <xref:System.Windows.Forms.ToolStripPanel> do **przybornika** , aby skompilować formularz MDI w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0c040-138">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="0c040-139">Otwórz **Przybornik**, a następnie kliknij kartę **wszystkie Windows Forms** , aby wyświetlić dostępne kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0c040-139">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>

2. <span data-ttu-id="0c040-140">Kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów, a następnie wybierz pozycję **Wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="0c040-140">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>

3. <span data-ttu-id="0c040-141">W oknie dialogowym **Wybierz elementy przybornika** przewiń w dół kolumnę **Nazwa** do momentu znalezienia **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="0c040-141">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>

4. <span data-ttu-id="0c040-142">Zaznacz pole wyboru przez **ToolStripPanel**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="0c040-142">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>

     <span data-ttu-id="0c040-143">Kontrolka <xref:System.Windows.Forms.ToolStripPanel> zostanie wyświetlona w **przyborniku**.</span><span class="sxs-lookup"><span data-stu-id="0c040-143">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>

## <a name="create-a-child-form"></a><span data-ttu-id="0c040-144">Tworzenie formularza podrzędnego</span><span class="sxs-lookup"><span data-stu-id="0c040-144">Create a child form</span></span>

<span data-ttu-id="0c040-145">W tej procedurze zdefiniujesz osobną klasę formularza podrzędnego, która ma własną kontrolkę <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="0c040-145">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="0c040-146">Elementy menu dla tego formularza są scalone z formularzami nadrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="0c040-146">The menu items for this form are merged with those of the parent form.</span></span>

1. <span data-ttu-id="0c040-147">Dodaj nowy formularz o nazwie `ChildForm` do projektu.</span><span class="sxs-lookup"><span data-stu-id="0c040-147">Add a new form named `ChildForm` to the project.</span></span>

     <span data-ttu-id="0c040-148">Aby uzyskać więcej informacji, zobacz [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0c040-148">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>

2. <span data-ttu-id="0c040-149">Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.MenuStrip> na formularz podrzędny.</span><span class="sxs-lookup"><span data-stu-id="0c040-149">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>

3. <span data-ttu-id="0c040-150">Kliknij symbol akcji projektanta <xref:System.Windows.Forms.MenuStrip> kontrolki (![małą czarną strzałkę](./media/designer-actions-glyph.gif)), a następnie wybierz pozycję **Edytuj elementy**.</span><span class="sxs-lookup"><span data-stu-id="0c040-150">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)), and then select **Edit Items**.</span></span>

4. <span data-ttu-id="0c040-151">W oknie dialogowym **Edytor kolekcji elementów** dodaj nowe <xref:System.Windows.Forms.ToolStripMenuItem> o nazwie **ChildMenuItem** do menu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="0c040-151">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>

     <span data-ttu-id="0c040-152">Aby uzyskać więcej informacji, zobacz [Edytor kolekcji elementów ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0c040-152">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>

## <a name="test-the-form"></a><span data-ttu-id="0c040-153">Testowanie formularza</span><span class="sxs-lookup"><span data-stu-id="0c040-153">Test the form</span></span>

1. <span data-ttu-id="0c040-154">Naciśnij klawisz **F5** , aby skompilować i uruchomić formularz.</span><span class="sxs-lookup"><span data-stu-id="0c040-154">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="0c040-155">Kliknij element menu **okno** , aby otworzyć menu, a następnie kliknij przycisk **Nowy**.</span><span class="sxs-lookup"><span data-stu-id="0c040-155">Click the **Window** menu item to open the menu, and then click **New**.</span></span>

     <span data-ttu-id="0c040-156">W obszarze klienta MDI formularza zostanie utworzony nowy formularz podrzędny.</span><span class="sxs-lookup"><span data-stu-id="0c040-156">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="0c040-157">Menu podrzędny formularz zostanie scalone z menu głównym.</span><span class="sxs-lookup"><span data-stu-id="0c040-157">The child form's menu is merged with the main menu.</span></span>

3. <span data-ttu-id="0c040-158">Zamknij formularz podrzędny.</span><span class="sxs-lookup"><span data-stu-id="0c040-158">Close the child form.</span></span>

     <span data-ttu-id="0c040-159">Menu podrzędne formularza zostanie usunięte z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="0c040-159">The child form's menu is removed from the main menu.</span></span>

4. <span data-ttu-id="0c040-160">Kliknij przycisk **nowe** kilka razy.</span><span class="sxs-lookup"><span data-stu-id="0c040-160">Click **New** several times.</span></span>

     <span data-ttu-id="0c040-161">Formularze podrzędne są automatycznie wyświetlane w elemencie menu **okna** , ponieważ właściwość <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> formantu <xref:System.Windows.Forms.MenuStrip> jest przypisana.</span><span class="sxs-lookup"><span data-stu-id="0c040-161">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>

## <a name="add-toolstrip-support"></a><span data-ttu-id="0c040-162">Dodaj obsługę elementu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="0c040-162">Add ToolStrip support</span></span>

<span data-ttu-id="0c040-163">W ramach tej procedury dodasz cztery <xref:System.Windows.Forms.ToolStrip> kontrolki do formularza nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="0c040-163">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="0c040-164">Każda kontrolka <xref:System.Windows.Forms.ToolStrip> jest dodawana wewnątrz kontrolki <xref:System.Windows.Forms.ToolStripPanel>, która jest zadokowana do krawędzi formularza.</span><span class="sxs-lookup"><span data-stu-id="0c040-164">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>

1. <span data-ttu-id="0c040-165">Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.ToolStripPanel> na formularz.</span><span class="sxs-lookup"><span data-stu-id="0c040-165">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>

2. <span data-ttu-id="0c040-166">Po wybraniu kontrolki <xref:System.Windows.Forms.ToolStripPanel> kliknij dwukrotnie kontrolkę <xref:System.Windows.Forms.ToolStrip> w **przyborniku**.</span><span class="sxs-lookup"><span data-stu-id="0c040-166">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>

     <span data-ttu-id="0c040-167">Formant <xref:System.Windows.Forms.ToolStrip> jest tworzony w kontrolce <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="0c040-167">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

3. <span data-ttu-id="0c040-168">Wybierz kontrolkę <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="0c040-168">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

4. <span data-ttu-id="0c040-169">W okno Właściwości zmień wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> kontrolki na <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="0c040-169">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>

     <span data-ttu-id="0c040-170">Formant <xref:System.Windows.Forms.ToolStripPanel> jest zadokowany do lewej strony formularza, pod menu głównym.</span><span class="sxs-lookup"><span data-stu-id="0c040-170">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="0c040-171">Rozmiar obszaru klienta MDI dopasowuje się do kontrolki <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="0c040-171">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

5. <span data-ttu-id="0c040-172">Powtórz kroki od 1 do 4.</span><span class="sxs-lookup"><span data-stu-id="0c040-172">Repeat steps 1 through 4.</span></span>

     <span data-ttu-id="0c040-173">Zadokuj nową kontrolkę <xref:System.Windows.Forms.ToolStripPanel> w górnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="0c040-173">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>

     <span data-ttu-id="0c040-174">Kontrolka <xref:System.Windows.Forms.ToolStripPanel> jest zadokowana pod menu głównym, ale z prawej strony pierwszej kontrolki <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="0c040-174">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="0c040-175">Ten krok przedstawia ważność porządku osi z w prawidłowym rozmieszczeniem <xref:System.Windows.Forms.ToolStripPanel> kontrolek.</span><span class="sxs-lookup"><span data-stu-id="0c040-175">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

6. <span data-ttu-id="0c040-176">Powtórz kroki od 1 do 4 dla dwóch kolejnych kontrolek <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="0c040-176">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

     <span data-ttu-id="0c040-177">Zadokuj nowe kontrolki <xref:System.Windows.Forms.ToolStripPanel> w prawo i u dołu formularza.</span><span class="sxs-lookup"><span data-stu-id="0c040-177">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>

## <a name="arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="0c040-178">Rozmieść kontrolki ToolStripPanel według kolejności Z</span><span class="sxs-lookup"><span data-stu-id="0c040-178">Arrange ToolStripPanel controls by Z-order</span></span>

<span data-ttu-id="0c040-179">Pozycja formantu <xref:System.Windows.Forms.ToolStripPanel> zadokowanego w formularzu MDI jest określana na podstawie położenia kontrolki w kolejności z.</span><span class="sxs-lookup"><span data-stu-id="0c040-179">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="0c040-180">Można łatwo rozmieścić porządek osi z kontrolek w oknie konspektu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0c040-180">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>

1. <span data-ttu-id="0c040-181">W menu **Widok** kliknij pozycję **inne okna**, a następnie kliknij pozycję **Konspekt dokumentu**.</span><span class="sxs-lookup"><span data-stu-id="0c040-181">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>

     <span data-ttu-id="0c040-182">Układ formantów <xref:System.Windows.Forms.ToolStripPanel> z poprzedniej procedury jest niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="0c040-182">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="0c040-183">Wynika to z faktu, że porządek osi z jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="0c040-183">This is because the z-order is not correct.</span></span> <span data-ttu-id="0c040-184">Użyj okna Konspekt dokumentu, aby zmienić porządek osi z kontrolek.</span><span class="sxs-lookup"><span data-stu-id="0c040-184">Use the Document Outline window to change the z-order of the controls.</span></span>

2. <span data-ttu-id="0c040-185">W oknie Konspekt dokumentu wybierz pozycję **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="0c040-185">In the Document Outline window, select **ToolStripPanel4**.</span></span>

3. <span data-ttu-id="0c040-186">Klikaj ponownie przycisk strzałki w dół, aż **ToolStripPanel4** znajduje się w dolnej części listy.</span><span class="sxs-lookup"><span data-stu-id="0c040-186">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>

     <span data-ttu-id="0c040-187">Formant **ToolStripPanel4** jest zadokowany w dolnej części formularza, pod innymi kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="0c040-187">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>

4. <span data-ttu-id="0c040-188">Wybierz pozycję **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="0c040-188">Select **ToolStripPanel2**.</span></span>

5. <span data-ttu-id="0c040-189">Kliknij przycisk strzałki w dół, aby umieścić formant trzeci na liście.</span><span class="sxs-lookup"><span data-stu-id="0c040-189">Click the down-arrow button one time to position the control third in the list.</span></span>

     <span data-ttu-id="0c040-190">Kontrolka **ToolStripPanel2** jest zadokowana w górnej części formularza, pod menu głównym i nad innymi kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="0c040-190">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>

6. <span data-ttu-id="0c040-191">Wybierz różne kontrolki w oknie **konspektu dokumentu** i przenieś je do różnych pozycji w kolejności z.</span><span class="sxs-lookup"><span data-stu-id="0c040-191">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="0c040-192">Zwróć uwagę na efekt porządku osi z na rozłożeniu zadokowanych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="0c040-192">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="0c040-193">Aby cofnąć zmiany, użyj klawiszy CTRL-Z lub **Cofnij** w menu **Edycja** .</span><span class="sxs-lookup"><span data-stu-id="0c040-193">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>

## <a name="checkpoint---test-your-form"></a><span data-ttu-id="0c040-194">Punkt kontrolny — testowanie formularza</span><span class="sxs-lookup"><span data-stu-id="0c040-194">Checkpoint - test your form</span></span>

1. <span data-ttu-id="0c040-195">Naciśnij klawisz **F5** , aby skompilować i uruchomić formularz.</span><span class="sxs-lookup"><span data-stu-id="0c040-195">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="0c040-196">Kliknij uchwyt kontrolki <xref:System.Windows.Forms.ToolStrip> i przeciągnij formant do różnych pozycji w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0c040-196">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>

     <span data-ttu-id="0c040-197">Kontrolkę <xref:System.Windows.Forms.ToolStrip> można przeciągnąć z jednej kontrolki <xref:System.Windows.Forms.ToolStripPanel> do innej.</span><span class="sxs-lookup"><span data-stu-id="0c040-197">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0c040-198">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="0c040-198">Next steps</span></span>

<span data-ttu-id="0c040-199">W tym instruktażu utworzono formularz nadrzędny MDI z kontrolkami <xref:System.Windows.Forms.ToolStrip> i scalaniem menu.</span><span class="sxs-lookup"><span data-stu-id="0c040-199">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="0c040-200">W wielu innych celach można użyć <xref:System.Windows.Forms.ToolStrip>ej rodziny formantów:</span><span class="sxs-lookup"><span data-stu-id="0c040-200">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="0c040-201">Utwórz menu skrótów dla kontrolek z <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="0c040-201">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="0c040-202">Aby uzyskać więcej informacji, zobacz temat [Omówienie składnika](contextmenu-component-overview-windows-forms.md)usługi.</span><span class="sxs-lookup"><span data-stu-id="0c040-202">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="0c040-203">Utworzono formularz z automatycznie wypełnionym menu standardowym.</span><span class="sxs-lookup"><span data-stu-id="0c040-203">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="0c040-204">Aby uzyskać więcej informacji, zobacz [Przewodnik: zapewnianie elementów menu standardowego w formularzu](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="0c040-204">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="0c040-205">Nadaj <xref:System.Windows.Forms.ToolStrip> kontrolę nad profesjonalnym wyglądem.</span><span class="sxs-lookup"><span data-stu-id="0c040-205">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="0c040-206">Aby uzyskać więcej informacji, zobacz [jak to zrobić: Ustawianie modułu renderowania ToolStrip dla aplikacji](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="0c040-206">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c040-207">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c040-207">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="0c040-208">Instrukcje: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="0c040-208">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="0c040-209">Instrukcje: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="0c040-209">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="0c040-210">Instrukcje: wstawianie kontrolki MenuStrip do menu rozwijanego MDI</span><span class="sxs-lookup"><span data-stu-id="0c040-210">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="0c040-211">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0c040-211">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
