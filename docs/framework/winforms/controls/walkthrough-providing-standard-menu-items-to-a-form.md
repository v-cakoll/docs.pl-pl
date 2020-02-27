---
title: 'Wskazówki: zapewnianie elementów menu standardowego dla formularza'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628777"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="74dd9-102">Wskazówki: zapewnianie elementów menu standardowego dla formularza</span><span class="sxs-lookup"><span data-stu-id="74dd9-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>

<span data-ttu-id="74dd9-103">Możesz dostarczyć menu standardowe dla formularzy z kontrolką <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="74dd9-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="74dd9-104">W tym instruktażu pokazano, jak za pomocą formantu <xref:System.Windows.Forms.MenuStrip> utworzyć standardowy menu.</span><span class="sxs-lookup"><span data-stu-id="74dd9-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="74dd9-105">Formularz również reaguje, gdy użytkownik wybierze element menu.</span><span class="sxs-lookup"><span data-stu-id="74dd9-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="74dd9-106">W tym instruktażu przedstawiono następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="74dd9-106">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="74dd9-107">Tworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="74dd9-107">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="74dd9-108">Tworzenie standardowego menu.</span><span class="sxs-lookup"><span data-stu-id="74dd9-108">Creating a standard menu.</span></span>

- <span data-ttu-id="74dd9-109">Tworzenie kontrolki <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="74dd9-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

- <span data-ttu-id="74dd9-110">Obsługa wyboru elementu menu.</span><span class="sxs-lookup"><span data-stu-id="74dd9-110">Handling menu item selection.</span></span>

<span data-ttu-id="74dd9-111">Gdy skończysz, będziesz mieć formularz z menu standardowym, w którym wyświetlane są wybrane elementy menu w kontrolce <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="74dd9-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

<span data-ttu-id="74dd9-112">Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: zapewnianie elementów menu standardowego w formularzu](how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="74dd9-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74dd9-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="74dd9-113">Prerequisites</span></span>

<span data-ttu-id="74dd9-114">Aby ukończyć ten przewodnik, musisz mieć program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="74dd9-114">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="74dd9-115">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="74dd9-115">Create the project</span></span>

1. <span data-ttu-id="74dd9-116">W programie Visual Studio Utwórz projekt aplikacji systemu Windows o **nazwie StandardMenuForm** (**plik** > **New** > **Project** > **Visual C#**  lub **Visual Basic** > **klasycznego pulpitu** > Windows Forms **aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="74dd9-116">In Visual Studio, create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="74dd9-117">W Projektant formularzy systemu Windows wybierz formularz.</span><span class="sxs-lookup"><span data-stu-id="74dd9-117">In the Windows Forms Designer, select the form.</span></span>

## <a name="create-a-standard-menu"></a><span data-ttu-id="74dd9-118">Tworzenie menu standardowego</span><span class="sxs-lookup"><span data-stu-id="74dd9-118">Create a standard menu</span></span>

<span data-ttu-id="74dd9-119">Projektant formularzy systemu Windows może automatycznie wypełnić formant <xref:System.Windows.Forms.MenuStrip> za pomocą standardowych elementów menu.</span><span class="sxs-lookup"><span data-stu-id="74dd9-119">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>

1. <span data-ttu-id="74dd9-120">Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.MenuStrip> na formularz.</span><span class="sxs-lookup"><span data-stu-id="74dd9-120">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>

2. <span data-ttu-id="74dd9-121">Kliknij symbol akcji projektanta <xref:System.Windows.Forms.MenuStrip> kontrolki (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) i wybierz pozycję **Wstaw elementy standardowe**.</span><span class="sxs-lookup"><span data-stu-id="74dd9-121">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Insert Standard Items**.</span></span>

     <span data-ttu-id="74dd9-122">Formant <xref:System.Windows.Forms.MenuStrip> zostanie wypełniony elementami menu Standard.</span><span class="sxs-lookup"><span data-stu-id="74dd9-122">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>

3. <span data-ttu-id="74dd9-123">Kliknij element menu **plik** , aby wyświetlić jego domyślne elementy menu i odpowiadające im ikony.</span><span class="sxs-lookup"><span data-stu-id="74dd9-123">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>

## <a name="create-a-statusstrip-control"></a><span data-ttu-id="74dd9-124">Tworzenie kontrolki StatusStrip</span><span class="sxs-lookup"><span data-stu-id="74dd9-124">Create a StatusStrip control</span></span>

<span data-ttu-id="74dd9-125">Użyj kontrolki <xref:System.Windows.Forms.StatusStrip>, aby wyświetlić stan aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="74dd9-125">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="74dd9-126">W bieżącym przykładzie elementy menu wybrane przez użytkownika są wyświetlane w kontrolce <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="74dd9-126">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

1. <span data-ttu-id="74dd9-127">Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.StatusStrip> na formularz.</span><span class="sxs-lookup"><span data-stu-id="74dd9-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>

     <span data-ttu-id="74dd9-128">Formant <xref:System.Windows.Forms.StatusStrip> automatycznie zadokuje w dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="74dd9-128">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>

2. <span data-ttu-id="74dd9-129">Kliknij przycisk listy rozwijanej <xref:System.Windows.Forms.StatusStrip> kontrolki i wybierz pozycję **StatusLabel** , aby dodać kontrolkę <xref:System.Windows.Forms.ToolStripStatusLabel> do kontrolki <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="74dd9-129">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>

## <a name="handle-item-selection"></a><span data-ttu-id="74dd9-130">Obsługuj zaznaczenie elementu</span><span class="sxs-lookup"><span data-stu-id="74dd9-130">Handle item selection</span></span>

<span data-ttu-id="74dd9-131">Obsługuj zdarzenie <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>, aby odpowiedzieć, gdy użytkownik wybierze element menu.</span><span class="sxs-lookup"><span data-stu-id="74dd9-131">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>

1. <span data-ttu-id="74dd9-132">Kliknij element menu **plik** , który został utworzony w sekcji Tworzenie standardowego menu.</span><span class="sxs-lookup"><span data-stu-id="74dd9-132">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>

2. <span data-ttu-id="74dd9-133">W oknie **Właściwości** kliknij pozycję **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="74dd9-133">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="74dd9-134">Kliknij dwukrotnie zdarzenie <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.</span><span class="sxs-lookup"><span data-stu-id="74dd9-134">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

     <span data-ttu-id="74dd9-135">Projektant formularzy systemu Windows generuje procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.</span><span class="sxs-lookup"><span data-stu-id="74dd9-135">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

4. <span data-ttu-id="74dd9-136">Wstaw następujący kod do programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="74dd9-136">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. <span data-ttu-id="74dd9-137">Wstaw definicję metody `UpdateStatus` narzędzia do formularza.</span><span class="sxs-lookup"><span data-stu-id="74dd9-137">Insert the `UpdateStatus` utility method definition into the form.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a><span data-ttu-id="74dd9-138">Punkt kontrolny — testowanie formularza</span><span class="sxs-lookup"><span data-stu-id="74dd9-138">Checkpoint -test your form</span></span>

1. <span data-ttu-id="74dd9-139">Naciśnij klawisz **F5** , aby skompilować i uruchomić formularz.</span><span class="sxs-lookup"><span data-stu-id="74dd9-139">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="74dd9-140">Kliknij element menu **plik** , aby otworzyć menu.</span><span class="sxs-lookup"><span data-stu-id="74dd9-140">Click the **File** menu item to open the menu.</span></span>

3. <span data-ttu-id="74dd9-141">W menu **plik** kliknij jeden z elementów, aby go zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="74dd9-141">On the **File** menu, click one of the items to select it.</span></span>

     <span data-ttu-id="74dd9-142">Kontrolka <xref:System.Windows.Forms.StatusStrip> Wyświetla wybrany element.</span><span class="sxs-lookup"><span data-stu-id="74dd9-142">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>

## <a name="next-steps"></a><span data-ttu-id="74dd9-143">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="74dd9-143">Next steps</span></span>

<span data-ttu-id="74dd9-144">W tym instruktażu utworzono formularz z menu standardowym.</span><span class="sxs-lookup"><span data-stu-id="74dd9-144">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="74dd9-145">W wielu innych celach można użyć <xref:System.Windows.Forms.ToolStrip>ej rodziny formantów:</span><span class="sxs-lookup"><span data-stu-id="74dd9-145">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="74dd9-146">Utwórz menu skrótów dla kontrolek z <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="74dd9-146">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="74dd9-147">Aby uzyskać więcej informacji, zobacz temat [Omówienie składnika](contextmenu-component-overview-windows-forms.md)usługi.</span><span class="sxs-lookup"><span data-stu-id="74dd9-147">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="74dd9-148">Utwórz formularz interfejsu wielu dokumentów (MDI) z kontrolkami <xref:System.Windows.Forms.ToolStrip> dokowania.</span><span class="sxs-lookup"><span data-stu-id="74dd9-148">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="74dd9-149">Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie formularza MDI za pomocą scalania menu i formantów ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="74dd9-149">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

- <span data-ttu-id="74dd9-150">Nadaj <xref:System.Windows.Forms.ToolStrip> kontrolę nad profesjonalnym wyglądem.</span><span class="sxs-lookup"><span data-stu-id="74dd9-150">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="74dd9-151">Aby uzyskać więcej informacji, zobacz [jak to zrobić: Ustawianie modułu renderowania ToolStrip dla aplikacji](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="74dd9-151">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74dd9-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74dd9-152">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="74dd9-153">MenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="74dd9-153">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
