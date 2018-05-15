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
ms.openlocfilehash: c0e3a9471afd05ec0e07e8d8a71ffd76c91ec14d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="391e8-102">Wskazówki: zapewnianie elementów menu standardowego dla formularza</span><span class="sxs-lookup"><span data-stu-id="391e8-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>
<span data-ttu-id="391e8-103">Można zapewnić standardowe menu formularzy z <xref:System.Windows.Forms.MenuStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="391e8-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="391e8-104">W tym przewodniku przedstawiono sposób użycia <xref:System.Windows.Forms.MenuStrip> formantu, aby utworzyć standardowe menu.</span><span class="sxs-lookup"><span data-stu-id="391e8-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="391e8-105">Formularz reaguje także po wybraniu elementu menu.</span><span class="sxs-lookup"><span data-stu-id="391e8-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="391e8-106">Następujące zadania są przedstawione w tym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="391e8-106">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="391e8-107">Tworzenie projektu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="391e8-107">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="391e8-108">Tworzenie menu standardowego.</span><span class="sxs-lookup"><span data-stu-id="391e8-108">Creating a standard menu.</span></span>  
  
-   <span data-ttu-id="391e8-109">Tworzenie <xref:System.Windows.Forms.StatusStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="391e8-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
-   <span data-ttu-id="391e8-110">Obsługa wyboru elementu menu.</span><span class="sxs-lookup"><span data-stu-id="391e8-110">Handling menu item selection.</span></span>  
  
 <span data-ttu-id="391e8-111">Gdy skończysz, konieczne będzie formularza z standardowe menu, która wyświetla zaznaczenia elementów menu w <xref:System.Windows.Forms.StatusStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="391e8-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 <span data-ttu-id="391e8-112">Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: Podaj standardowe elementy Menu do formularza](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="391e8-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="391e8-113">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="391e8-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="391e8-114">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="391e8-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="391e8-115">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="391e8-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="391e8-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="391e8-116">Prerequisites</span></span>  
 <span data-ttu-id="391e8-117">W celu przeprowadzenia tego instruktażu potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="391e8-117">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="391e8-118">Wystarczających uprawnień, aby mieć możliwość tworzenia i uruchamiania projektów aplikacji formularzy systemu Windows na komputerze, którym jest zainstalowany program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="391e8-118">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="391e8-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="391e8-119">Creating the Project</span></span>  
 <span data-ttu-id="391e8-120">Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="391e8-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="391e8-121">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="391e8-121">To create the project</span></span>  
  
1.  <span data-ttu-id="391e8-122">Utwórz projekt aplikacji systemu Windows o nazwie **StandardMenuForm**.</span><span class="sxs-lookup"><span data-stu-id="391e8-122">Create a Windows application project called **StandardMenuForm**.</span></span>  
  
     <span data-ttu-id="391e8-123">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="391e8-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="391e8-124">W narzędziu Projektant dla formularzy systemu Windows wybierz formularza.</span><span class="sxs-lookup"><span data-stu-id="391e8-124">In the Windows Forms Designer, select the form.</span></span>  
  
## <a name="creating-a-standard-menu"></a><span data-ttu-id="391e8-125">Tworzenie Menu standardowego</span><span class="sxs-lookup"><span data-stu-id="391e8-125">Creating a Standard Menu</span></span>  
 <span data-ttu-id="391e8-126">Projektant formularzy systemu Windows może automatycznie wypełnić <xref:System.Windows.Forms.MenuStrip> kontrolki z elementów menu standardowego.</span><span class="sxs-lookup"><span data-stu-id="391e8-126">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>  
  
#### <a name="to-create-a-standard-menu"></a><span data-ttu-id="391e8-127">Aby utworzyć standardowe menu</span><span class="sxs-lookup"><span data-stu-id="391e8-127">To create a standard menu</span></span>  
  
1.  <span data-ttu-id="391e8-128">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="391e8-128">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>  
  
2.  <span data-ttu-id="391e8-129">Kliknij przycisk <xref:System.Windows.Forms.MenuStrip> kontrolki symbolu tagu (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) i wybierz **Wstaw elementy standardowe**.</span><span class="sxs-lookup"><span data-stu-id="391e8-129">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>  
  
     <span data-ttu-id="391e8-130"><xref:System.Windows.Forms.MenuStrip> Kontroli jest wypełniane przy użyciu elementów menu standardowego.</span><span class="sxs-lookup"><span data-stu-id="391e8-130">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>  
  
3.  <span data-ttu-id="391e8-131">Kliknij przycisk **pliku** element menu, aby zobaczyć jego elementy menu domyślne i odpowiadające im ikony.</span><span class="sxs-lookup"><span data-stu-id="391e8-131">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>  
  
## <a name="creating-a-statusstrip-control"></a><span data-ttu-id="391e8-132">Tworzenie StatusStrip — formant</span><span class="sxs-lookup"><span data-stu-id="391e8-132">Creating a StatusStrip Control</span></span>  
 <span data-ttu-id="391e8-133">Użyj <xref:System.Windows.Forms.StatusStrip> formantu, aby wyświetlić stan dla aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="391e8-133">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="391e8-134">W tym przykładzie bieżący wybrane przez użytkownika elementy menu są wyświetlane w <xref:System.Windows.Forms.StatusStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="391e8-134">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
#### <a name="to-create-a-statusstrip-control"></a><span data-ttu-id="391e8-135">Aby utworzyć StatusStrip — formant</span><span class="sxs-lookup"><span data-stu-id="391e8-135">To create a StatusStrip control</span></span>  
  
1.  <span data-ttu-id="391e8-136">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.StatusStrip> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="391e8-136">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>  
  
     <span data-ttu-id="391e8-137"><xref:System.Windows.Forms.StatusStrip> Kontroli stacje dokujące automatycznie do dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="391e8-137">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>  
  
2.  <span data-ttu-id="391e8-138">Kliknij przycisk <xref:System.Windows.Forms.StatusStrip> przycisku rozwijanego kontrolki i wybierz **StatusLabel** można dodać <xref:System.Windows.Forms.ToolStripStatusLabel> formant <xref:System.Windows.Forms.StatusStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="391e8-138">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="handling-item-selection"></a><span data-ttu-id="391e8-139">Wybór elementu obsługi</span><span class="sxs-lookup"><span data-stu-id="391e8-139">Handling Item Selection</span></span>  
 <span data-ttu-id="391e8-140">Obsługa <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzenia odpowiada po wybraniu elementu menu.</span><span class="sxs-lookup"><span data-stu-id="391e8-140">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>  
  
#### <a name="to-handle-item-selection"></a><span data-ttu-id="391e8-141">Do obsługi Zaznaczanie elementów</span><span class="sxs-lookup"><span data-stu-id="391e8-141">To handle item selection</span></span>  
  
1.  <span data-ttu-id="391e8-142">Kliknij przycisk **pliku** element menu, który został utworzony w tworzenie sekcji standardowe Menu.</span><span class="sxs-lookup"><span data-stu-id="391e8-142">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>  
  
2.  <span data-ttu-id="391e8-143">W **właściwości** okna, kliknij przycisk **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="391e8-143">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="391e8-144">Kliknij dwukrotnie <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="391e8-144">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
     <span data-ttu-id="391e8-145">Projektant formularzy systemu Windows generuje programu obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="391e8-145">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
4.  <span data-ttu-id="391e8-146">Wstaw następujący kod do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="391e8-146">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  <span data-ttu-id="391e8-147">Wstaw `UpdateStatus` definicję metody narzędzie do formularza.</span><span class="sxs-lookup"><span data-stu-id="391e8-147">Insert the `UpdateStatus` utility method definition into the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a><span data-ttu-id="391e8-148">Punkt kontrolny</span><span class="sxs-lookup"><span data-stu-id="391e8-148">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="391e8-149">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="391e8-149">To test your form</span></span>  
  
1.  <span data-ttu-id="391e8-150">Naciśnij klawisz F5, aby skompilować i uruchomić formularza.</span><span class="sxs-lookup"><span data-stu-id="391e8-150">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="391e8-151">Kliknij przycisk **pliku** element menu, aby otworzyć menu.</span><span class="sxs-lookup"><span data-stu-id="391e8-151">Click the **File** menu item to open the menu.</span></span>  
  
3.  <span data-ttu-id="391e8-152">Na **pliku** menu, kliknij jeden z elementów, aby go wybrać.</span><span class="sxs-lookup"><span data-stu-id="391e8-152">On the **File** menu, click one of the items to select it.</span></span>  
  
     <span data-ttu-id="391e8-153"><xref:System.Windows.Forms.StatusStrip> Kontrola Wyświetla wybrany element.</span><span class="sxs-lookup"><span data-stu-id="391e8-153">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="391e8-154">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="391e8-154">Next Steps</span></span>  
 <span data-ttu-id="391e8-155">W tym przewodniku utworzono formularza standardowe menu.</span><span class="sxs-lookup"><span data-stu-id="391e8-155">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="391e8-156">Można użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:</span><span class="sxs-lookup"><span data-stu-id="391e8-156">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="391e8-157">Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="391e8-157">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="391e8-158">Aby uzyskać więcej informacji, zobacz [informacje o składniku ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="391e8-158">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="391e8-159">Tworzenie wielu formularza interfejsu (MDI) dokumentu z dokowanie <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="391e8-159">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="391e8-160">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie formularza MDI za pomocą scalania Menu i formantami ToolStrip](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="391e8-160">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
-   <span data-ttu-id="391e8-161">Nadaj Twojej <xref:System.Windows.Forms.ToolStrip> profesjonalny wygląd kontrolki.</span><span class="sxs-lookup"><span data-stu-id="391e8-161">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="391e8-162">Aby uzyskać więcej informacji, zobacz [porady: ustawienie modułu renderowania ToolStrip dla aplikacji](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="391e8-162">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="391e8-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="391e8-163">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="391e8-164">MenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="391e8-164">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
