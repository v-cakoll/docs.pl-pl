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
ms.openlocfilehash: c0275d3af0c12eb8edacc1711c8eead45eeca75e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466946"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="eb81b-102">Wskazówki: zapewnianie elementów menu standardowego dla formularza</span><span class="sxs-lookup"><span data-stu-id="eb81b-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>
<span data-ttu-id="eb81b-103">Możesz podać standardowe menu formularzy przy użyciu <xref:System.Windows.Forms.MenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="eb81b-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="eb81b-104">W tym instruktażu przedstawiono sposób użycia <xref:System.Windows.Forms.MenuStrip> formantu, aby utworzyć standardowe menu.</span><span class="sxs-lookup"><span data-stu-id="eb81b-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="eb81b-105">Formularz również reaguje, gdy użytkownik wybierze element menu.</span><span class="sxs-lookup"><span data-stu-id="eb81b-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="eb81b-106">Następujące zadania są przedstawione w niniejszym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="eb81b-106">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="eb81b-107">Tworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="eb81b-107">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="eb81b-108">Tworzenie standardowego menu.</span><span class="sxs-lookup"><span data-stu-id="eb81b-108">Creating a standard menu.</span></span>  
  
-   <span data-ttu-id="eb81b-109">Tworzenie <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="eb81b-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
-   <span data-ttu-id="eb81b-110">Obsługa wyboru elementu menu.</span><span class="sxs-lookup"><span data-stu-id="eb81b-110">Handling menu item selection.</span></span>  
  
 <span data-ttu-id="eb81b-111">Po zakończeniu będziesz mieć formularza przy użyciu standardowego menu, które wyświetla zaznaczenia elementów menu w <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="eb81b-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 <span data-ttu-id="eb81b-112">Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Podaj standardowych elementów Menu do formularza](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="eb81b-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb81b-113">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="eb81b-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="eb81b-114">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="eb81b-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="eb81b-115">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="eb81b-115">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eb81b-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="eb81b-116">Prerequisites</span></span>  
 <span data-ttu-id="eb81b-117">Aby ukończyć ten przewodnik, potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="eb81b-117">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="eb81b-118">Wystarczające uprawnienia, aby można było utworzyć i uruchomić projekty aplikacji Windows Forms na komputerze, w którym jest zainstalowany program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eb81b-118">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="eb81b-119">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="eb81b-119">Creating the Project</span></span>  
 <span data-ttu-id="eb81b-120">Pierwszym krokiem jest tworzenie projektu i konfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="eb81b-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="eb81b-121">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="eb81b-121">To create the project</span></span>  
  
1.  <span data-ttu-id="eb81b-122">Utwórz projekt aplikacji Windows, o nazwie **StandardMenuForm** (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms Aplikacja**).</span><span class="sxs-lookup"><span data-stu-id="eb81b-122">Create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="eb81b-123">W programie Windows Forms Designer wybierz formularz.</span><span class="sxs-lookup"><span data-stu-id="eb81b-123">In the Windows Forms Designer, select the form.</span></span>  
  
## <a name="creating-a-standard-menu"></a><span data-ttu-id="eb81b-124">Tworzenie standardowego Menu</span><span class="sxs-lookup"><span data-stu-id="eb81b-124">Creating a Standard Menu</span></span>  
 <span data-ttu-id="eb81b-125">Windows Forms Designer może automatycznie wypełnić <xref:System.Windows.Forms.MenuStrip> kontrolki z elementów menu standardowego.</span><span class="sxs-lookup"><span data-stu-id="eb81b-125">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>  
  
#### <a name="to-create-a-standard-menu"></a><span data-ttu-id="eb81b-126">Aby utworzyć menu standardowe</span><span class="sxs-lookup"><span data-stu-id="eb81b-126">To create a standard menu</span></span>  
  
1.  <span data-ttu-id="eb81b-127">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="eb81b-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>  
  
2.  <span data-ttu-id="eb81b-128">Kliknij przycisk <xref:System.Windows.Forms.MenuStrip> symbol tagu inteligentnego kontrolki (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) i wybierz **Wstaw elementy standardowe**.</span><span class="sxs-lookup"><span data-stu-id="eb81b-128">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>  
  
     <span data-ttu-id="eb81b-129"><xref:System.Windows.Forms.MenuStrip> Kontrolka zostanie wypełniona elementów menu standardowego.</span><span class="sxs-lookup"><span data-stu-id="eb81b-129">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>  
  
3.  <span data-ttu-id="eb81b-130">Kliknij przycisk **pliku** element menu, aby zobaczyć jego elementy menu domyślne i odpowiadające im ikony.</span><span class="sxs-lookup"><span data-stu-id="eb81b-130">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>  
  
## <a name="creating-a-statusstrip-control"></a><span data-ttu-id="eb81b-131">Tworzenie StatusStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="eb81b-131">Creating a StatusStrip Control</span></span>  
 <span data-ttu-id="eb81b-132">Użyj <xref:System.Windows.Forms.StatusStrip> formantu, aby wyświetlić stan dla aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="eb81b-132">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="eb81b-133">W bieżącym przykładzie wybrane przez użytkownika elementy menu są wyświetlane w <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="eb81b-133">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
#### <a name="to-create-a-statusstrip-control"></a><span data-ttu-id="eb81b-134">Aby utworzyć StatusStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="eb81b-134">To create a StatusStrip control</span></span>  
  
1.  <span data-ttu-id="eb81b-135">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.StatusStrip> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="eb81b-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>  
  
     <span data-ttu-id="eb81b-136"><xref:System.Windows.Forms.StatusStrip> Kontroli automatycznie dokowane do dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="eb81b-136">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>  
  
2.  <span data-ttu-id="eb81b-137">Kliknij przycisk <xref:System.Windows.Forms.StatusStrip> przycisk listy rozwijanej i wybierz formantu **StatusLabel** dodać <xref:System.Windows.Forms.ToolStripStatusLabel> kontrolę <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="eb81b-137">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="handling-item-selection"></a><span data-ttu-id="eb81b-138">Wybór elementu obsługi</span><span class="sxs-lookup"><span data-stu-id="eb81b-138">Handling Item Selection</span></span>  
 <span data-ttu-id="eb81b-139">Obsługa <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzenie, aby odpowiadać, gdy użytkownik wybierze element menu.</span><span class="sxs-lookup"><span data-stu-id="eb81b-139">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>  
  
#### <a name="to-handle-item-selection"></a><span data-ttu-id="eb81b-140">Aby obsłużyć Wybór elementu</span><span class="sxs-lookup"><span data-stu-id="eb81b-140">To handle item selection</span></span>  
  
1.  <span data-ttu-id="eb81b-141">Kliknij przycisk **pliku** elementu menu, który został utworzony w tworzenie sekcji standardowe Menu.</span><span class="sxs-lookup"><span data-stu-id="eb81b-141">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>  
  
2.  <span data-ttu-id="eb81b-142">W **właściwości** okna, kliknij przycisk **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="eb81b-142">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="eb81b-143">Kliknij dwukrotnie <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="eb81b-143">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
     <span data-ttu-id="eb81b-144">Windows Forms Designer generuje moduł obsługi zdarzenia <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="eb81b-144">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
4.  <span data-ttu-id="eb81b-145">Wstaw następujący kod do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="eb81b-145">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  <span data-ttu-id="eb81b-146">Wstaw `UpdateStatus` definicję metody narzędzie do formularza.</span><span class="sxs-lookup"><span data-stu-id="eb81b-146">Insert the `UpdateStatus` utility method definition into the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a><span data-ttu-id="eb81b-147">Punkt kontrolny</span><span class="sxs-lookup"><span data-stu-id="eb81b-147">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="eb81b-148">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="eb81b-148">To test your form</span></span>  
  
1.  <span data-ttu-id="eb81b-149">Naciśnij klawisz F5, aby skompilować i uruchomić formularz.</span><span class="sxs-lookup"><span data-stu-id="eb81b-149">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="eb81b-150">Kliknij przycisk **pliku** element menu, aby otworzyć menu.</span><span class="sxs-lookup"><span data-stu-id="eb81b-150">Click the **File** menu item to open the menu.</span></span>  
  
3.  <span data-ttu-id="eb81b-151">Na **pliku** menu, kliknij jeden z elementów, aby go zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="eb81b-151">On the **File** menu, click one of the items to select it.</span></span>  
  
     <span data-ttu-id="eb81b-152"><xref:System.Windows.Forms.StatusStrip> Kontrolka Wyświetla wybrany element.</span><span class="sxs-lookup"><span data-stu-id="eb81b-152">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="eb81b-153">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="eb81b-153">Next Steps</span></span>  
 <span data-ttu-id="eb81b-154">W tym instruktażu utworzono formularza standardowe menu.</span><span class="sxs-lookup"><span data-stu-id="eb81b-154">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="eb81b-155">Możesz użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:</span><span class="sxs-lookup"><span data-stu-id="eb81b-155">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="eb81b-156">Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="eb81b-156">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="eb81b-157">Aby uzyskać więcej informacji, zobacz [— informacje o składniku ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="eb81b-157">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="eb81b-158">Tworzenie wielu formularza interfejsu (MDI) dokumentu z dokowanie <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="eb81b-158">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="eb81b-159">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie formularza MDI za pomocą scalania Menu i formantami ToolStrip](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="eb81b-159">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
-   <span data-ttu-id="eb81b-160">Nadaj swojej <xref:System.Windows.Forms.ToolStrip> profesjonalny wygląd kontrolki.</span><span class="sxs-lookup"><span data-stu-id="eb81b-160">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="eb81b-161">Aby uzyskać więcej informacji, zobacz [porady: ustawienie modułu renderowania ToolStrip dla aplikacji](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="eb81b-161">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb81b-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb81b-162">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="eb81b-163">MenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="eb81b-163">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
