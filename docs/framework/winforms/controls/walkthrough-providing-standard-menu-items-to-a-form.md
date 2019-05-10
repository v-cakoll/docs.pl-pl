---
title: 'Przewodnik: zapewnianie elementów menu standardowego dla formularza'
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
ms.openlocfilehash: ebfacadfee3ea069359a72ea0402751e9e6280d7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211489"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="6593f-102">Przewodnik: zapewnianie elementów menu standardowego dla formularza</span><span class="sxs-lookup"><span data-stu-id="6593f-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>

<span data-ttu-id="6593f-103">Możesz podać standardowe menu formularzy przy użyciu <xref:System.Windows.Forms.MenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6593f-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="6593f-104">W tym instruktażu przedstawiono sposób użycia <xref:System.Windows.Forms.MenuStrip> formantu, aby utworzyć standardowe menu.</span><span class="sxs-lookup"><span data-stu-id="6593f-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="6593f-105">Formularz również reaguje, gdy użytkownik wybierze element menu.</span><span class="sxs-lookup"><span data-stu-id="6593f-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="6593f-106">Następujące zadania są przedstawione w niniejszym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="6593f-106">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="6593f-107">Tworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6593f-107">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="6593f-108">Tworzenie standardowego menu.</span><span class="sxs-lookup"><span data-stu-id="6593f-108">Creating a standard menu.</span></span>

- <span data-ttu-id="6593f-109">Tworzenie <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6593f-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

- <span data-ttu-id="6593f-110">Obsługa wyboru elementu menu.</span><span class="sxs-lookup"><span data-stu-id="6593f-110">Handling menu item selection.</span></span>

<span data-ttu-id="6593f-111">Po zakończeniu będziesz mieć formularza przy użyciu standardowego menu, które wyświetla zaznaczenia elementów menu w <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6593f-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

<span data-ttu-id="6593f-112">Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Zapewnianie elementów Menu standardowego dla formularza](how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="6593f-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6593f-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="6593f-113">Prerequisites</span></span>

<span data-ttu-id="6593f-114">Visual Studio w celu przeprowadzenia tego instruktażu jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="6593f-114">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="6593f-115">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="6593f-115">Create the project</span></span>

1. <span data-ttu-id="6593f-116">W programie Visual Studio Utwórz projekt aplikacji Windows o nazwie **StandardMenuForm** (**pliku** > **New** > **projektu**   >  **Visual C#**  lub **języka Visual Basic** > **Classic Desktop**  >  **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="6593f-116">In Visual Studio, create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="6593f-117">W programie Windows Forms Designer wybierz formularz.</span><span class="sxs-lookup"><span data-stu-id="6593f-117">In the Windows Forms Designer, select the form.</span></span>

## <a name="create-a-standard-menu"></a><span data-ttu-id="6593f-118">Utwórz standardowe menu</span><span class="sxs-lookup"><span data-stu-id="6593f-118">Create a standard menu</span></span>

<span data-ttu-id="6593f-119">Windows Forms Designer może automatycznie wypełnić <xref:System.Windows.Forms.MenuStrip> kontrolki z elementów menu standardowego.</span><span class="sxs-lookup"><span data-stu-id="6593f-119">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>

1. <span data-ttu-id="6593f-120">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="6593f-120">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>

2. <span data-ttu-id="6593f-121">Kliknij przycisk <xref:System.Windows.Forms.MenuStrip> symbol tagu inteligentnego kontrolki (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) i wybierz **Wstaw elementy standardowe**.</span><span class="sxs-lookup"><span data-stu-id="6593f-121">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>

     <span data-ttu-id="6593f-122"><xref:System.Windows.Forms.MenuStrip> Kontrolka zostanie wypełniona elementów menu standardowego.</span><span class="sxs-lookup"><span data-stu-id="6593f-122">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>

3. <span data-ttu-id="6593f-123">Kliknij przycisk **pliku** element menu, aby zobaczyć jego elementy menu domyślne i odpowiadające im ikony.</span><span class="sxs-lookup"><span data-stu-id="6593f-123">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>

## <a name="create-a-statusstrip-control"></a><span data-ttu-id="6593f-124">Utwórz StatusStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6593f-124">Create a StatusStrip control</span></span>

<span data-ttu-id="6593f-125">Użyj <xref:System.Windows.Forms.StatusStrip> formantu, aby wyświetlić stan dla aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6593f-125">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="6593f-126">W bieżącym przykładzie wybrane przez użytkownika elementy menu są wyświetlane w <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6593f-126">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

1. <span data-ttu-id="6593f-127">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.StatusStrip> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="6593f-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>

     <span data-ttu-id="6593f-128"><xref:System.Windows.Forms.StatusStrip> Kontroli automatycznie dokowane do dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="6593f-128">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>

2. <span data-ttu-id="6593f-129">Kliknij przycisk <xref:System.Windows.Forms.StatusStrip> przycisk listy rozwijanej i wybierz formantu **StatusLabel** dodać <xref:System.Windows.Forms.ToolStripStatusLabel> kontrolę <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6593f-129">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>

## <a name="handle-item-selection"></a><span data-ttu-id="6593f-130">Wybór elementu uchwytu</span><span class="sxs-lookup"><span data-stu-id="6593f-130">Handle item selection</span></span>

<span data-ttu-id="6593f-131">Obsługa <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzenie, aby odpowiadać, gdy użytkownik wybierze element menu.</span><span class="sxs-lookup"><span data-stu-id="6593f-131">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>

1. <span data-ttu-id="6593f-132">Kliknij przycisk **pliku** elementu menu, który został utworzony w tworzenie sekcji standardowe Menu.</span><span class="sxs-lookup"><span data-stu-id="6593f-132">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>

2. <span data-ttu-id="6593f-133">W **właściwości** okna, kliknij przycisk **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="6593f-133">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="6593f-134">Kliknij dwukrotnie <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6593f-134">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

     <span data-ttu-id="6593f-135">Windows Forms Designer generuje moduł obsługi zdarzenia <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6593f-135">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

4. <span data-ttu-id="6593f-136">Wstaw następujący kod do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6593f-136">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. <span data-ttu-id="6593f-137">Wstaw `UpdateStatus` definicję metody narzędzie do formularza.</span><span class="sxs-lookup"><span data-stu-id="6593f-137">Insert the `UpdateStatus` utility method definition into the form.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a><span data-ttu-id="6593f-138">Punkt kontrolny — testowanie formularza</span><span class="sxs-lookup"><span data-stu-id="6593f-138">Checkpoint -test your form</span></span>

1. <span data-ttu-id="6593f-139">Naciśnij klawisz **F5** Aby skompilować i uruchomić formularz.</span><span class="sxs-lookup"><span data-stu-id="6593f-139">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="6593f-140">Kliknij przycisk **pliku** element menu, aby otworzyć menu.</span><span class="sxs-lookup"><span data-stu-id="6593f-140">Click the **File** menu item to open the menu.</span></span>

3. <span data-ttu-id="6593f-141">Na **pliku** menu, kliknij jeden z elementów, aby go zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="6593f-141">On the **File** menu, click one of the items to select it.</span></span>

     <span data-ttu-id="6593f-142"><xref:System.Windows.Forms.StatusStrip> Kontrolka Wyświetla wybrany element.</span><span class="sxs-lookup"><span data-stu-id="6593f-142">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6593f-143">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="6593f-143">Next steps</span></span>

<span data-ttu-id="6593f-144">W tym instruktażu utworzono formularza standardowe menu.</span><span class="sxs-lookup"><span data-stu-id="6593f-144">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="6593f-145">Możesz użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:</span><span class="sxs-lookup"><span data-stu-id="6593f-145">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="6593f-146">Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="6593f-146">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="6593f-147">Aby uzyskać więcej informacji, zobacz [— informacje o składniku ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6593f-147">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="6593f-148">Tworzenie wielu formularza interfejsu (MDI) dokumentu z dokowanie <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6593f-148">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="6593f-149">Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie formularza MDI za pomocą scalania Menu i formantami ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6593f-149">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

- <span data-ttu-id="6593f-150">Nadaj swojej <xref:System.Windows.Forms.ToolStrip> profesjonalny wygląd kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6593f-150">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="6593f-151">Aby uzyskać więcej informacji, zobacz [jak: Ustawienie modułu renderowania ToolStrip dla aplikacji](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="6593f-151">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6593f-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6593f-152">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="6593f-153">MenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6593f-153">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
