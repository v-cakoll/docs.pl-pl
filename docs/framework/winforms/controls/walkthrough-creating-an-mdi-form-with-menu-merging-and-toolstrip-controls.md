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
ms.openlocfilehash: 6236190340833e3f8810387e51ad53e1cb10d37b
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525662"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="08dd9-102">Wskazówki: tworzenie formularza MDI ze scalaniem menu i formantami ToolStrip</span><span class="sxs-lookup"><span data-stu-id="08dd9-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="08dd9-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw obsługuje wiele aplikacji interfejsu (MDI) dokumentu i <xref:System.Windows.Forms.MenuStrip> kontrolka obsługuje scalania menu.</span><span class="sxs-lookup"><span data-stu-id="08dd9-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="08dd9-104">Formularze MDI może również <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="08dd9-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="08dd9-105">W tym instruktażu przedstawiono sposób użycia <xref:System.Windows.Forms.ToolStripPanel> formanty z formularza MDI.</span><span class="sxs-lookup"><span data-stu-id="08dd9-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="08dd9-106">Formularz obsługuje także menu scalanie z menu podrzędne.</span><span class="sxs-lookup"><span data-stu-id="08dd9-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="08dd9-107">Następujące zadania są przedstawione w niniejszym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="08dd9-107">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="08dd9-108">Tworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="08dd9-108">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="08dd9-109">Tworzenie menu głównego dla formularza użytkownika.</span><span class="sxs-lookup"><span data-stu-id="08dd9-109">Creating the main menu for your form.</span></span> <span data-ttu-id="08dd9-110">Rzeczywista nazwa menu będą się różnić.</span><span class="sxs-lookup"><span data-stu-id="08dd9-110">The actual name of the menu will vary.</span></span>  
  
-   <span data-ttu-id="08dd9-111">Dodawanie <xref:System.Windows.Forms.ToolStripPanel> kontrolę **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>  
  
-   <span data-ttu-id="08dd9-112">Tworzenie formularza podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="08dd9-112">Creating a child form.</span></span>  
  
-   <span data-ttu-id="08dd9-113">Rozmieszczanie <xref:System.Windows.Forms.ToolStripPanel> formanty według porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="08dd9-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>  
  
 <span data-ttu-id="08dd9-114">Po zakończeniu będziesz mieć formularza MDI, która obsługuje scalania menu i ruchome <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="08dd9-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="08dd9-115">Aby skopiować kod, w tym temacie na jednej liście, zobacz [porady: Tworzenie formularza MDI za pomocą scalania Menu i formantów ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="08dd9-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08dd9-116">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="08dd9-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="08dd9-117">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="08dd9-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="08dd9-118">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="08dd9-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="08dd9-119">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="08dd9-119">Prerequisites</span></span>  
 <span data-ttu-id="08dd9-120">Aby ukończyć ten przewodnik, potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="08dd9-120">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="08dd9-121">Wystarczające uprawnienia, aby można było utworzyć i uruchomić projekty aplikacji Windows Forms na komputerze, w którym jest zainstalowany program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="08dd9-121">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="08dd9-122">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="08dd9-122">Creating the Project</span></span>  
 <span data-ttu-id="08dd9-123">Pierwszym krokiem jest tworzenie projektu i konfigurowanie formularza.</span><span class="sxs-lookup"><span data-stu-id="08dd9-123">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="08dd9-124">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="08dd9-124">To create the project</span></span>  
  
1.  <span data-ttu-id="08dd9-125">Utwórz projekt aplikacji Windows, o nazwie **MdiForm** (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="08dd9-125">Create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="08dd9-126">W programie Windows Forms Designer wybierz formularz.</span><span class="sxs-lookup"><span data-stu-id="08dd9-126">In the Windows Forms Designer, select the form.</span></span>  
  
3.  <span data-ttu-id="08dd9-127">W oknie właściwości ustaw wartość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> do `true`.</span><span class="sxs-lookup"><span data-stu-id="08dd9-127">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>  
  
## <a name="creating-the-main-menu"></a><span data-ttu-id="08dd9-128">Tworzenie Menu głównego</span><span class="sxs-lookup"><span data-stu-id="08dd9-128">Creating the Main Menu</span></span>  
 <span data-ttu-id="08dd9-129">Formularza nadrzędnego MDI zawiera menu głównego.</span><span class="sxs-lookup"><span data-stu-id="08dd9-129">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="08dd9-130">Menu główne ma jeden element menu o nazwie **okna**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-130">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="08dd9-131">Za pomocą **okna** element menu może tworzenie formularzy podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="08dd9-131">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="08dd9-132">Elementy menu z formularze podrzędne są scalane w menu głównym.</span><span class="sxs-lookup"><span data-stu-id="08dd9-132">Menu items from child forms are merged into the main menu.</span></span>  
  
#### <a name="to-create-the-main-menu"></a><span data-ttu-id="08dd9-133">Aby utworzyć menu głównego</span><span class="sxs-lookup"><span data-stu-id="08dd9-133">To create the Main menu</span></span>  
  
1.  <span data-ttu-id="08dd9-134">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> formant na formularzu.</span><span class="sxs-lookup"><span data-stu-id="08dd9-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>  
  
2.  <span data-ttu-id="08dd9-135">Dodaj <xref:System.Windows.Forms.ToolStripMenuItem> do <xref:System.Windows.Forms.MenuStrip> kontroli i nadaj mu nazwę **okna**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-135">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>  
  
3.  <span data-ttu-id="08dd9-136">Wybierz <xref:System.Windows.Forms.MenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="08dd9-136">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
4.  <span data-ttu-id="08dd9-137">W oknie właściwości ustaw wartość <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwość `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="08dd9-137">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>  
  
5.  <span data-ttu-id="08dd9-138">Dodaj podelement do **okna** element menu, a następnie nazwę podelement **New**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-138">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>  
  
6.  <span data-ttu-id="08dd9-139">W oknie dialogowym właściwości kliknij **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-139">In the Properties window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="08dd9-140">Kliknij dwukrotnie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="08dd9-140">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
     <span data-ttu-id="08dd9-141">Windows Forms Designer generuje moduł obsługi zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="08dd9-141">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
8.  <span data-ttu-id="08dd9-142">Wstaw następujący kod do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="08dd9-142">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="08dd9-143">Dodawanie ToolStripPanel, kontrolka do przybornika</span><span class="sxs-lookup"><span data-stu-id="08dd9-143">Adding the ToolStripPanel Control to the Toolbox</span></span>  
 <span data-ttu-id="08dd9-144">Kiedy używasz <xref:System.Windows.Forms.MenuStrip> formanty z formularza MDI konieczne jest posiadanie <xref:System.Windows.Forms.ToolStripPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="08dd9-144">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="08dd9-145">Należy dodać <xref:System.Windows.Forms.ToolStripPanel> kontrolę **przybornika** Tworzenie formularza MDI w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="08dd9-145">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="08dd9-146">Aby dodać ToolStripPanel, kontrolka do przybornika</span><span class="sxs-lookup"><span data-stu-id="08dd9-146">To add the ToolStripPanel control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="08dd9-147">Otwórz **przybornika**, a następnie kliknij przycisk **wszystkie formularze Windows** kartę, aby wyświetlić dostępne kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="08dd9-147">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>  
  
2.  <span data-ttu-id="08dd9-148">Kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów i wybierz **wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-148">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>  
  
3.  <span data-ttu-id="08dd9-149">W **wybierz elementy przybornika** okno dialogowe, przewiń w dół **nazwa** kolumny, aż znajdziesz **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-149">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>  
  
4.  <span data-ttu-id="08dd9-150">Zaznacz pole wyboru przy **ToolStripPanel**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-150">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="08dd9-151"><xref:System.Windows.Forms.ToolStripPanel> Formant jest widoczny w **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-151">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>  
  
## <a name="creating-a-child-form"></a><span data-ttu-id="08dd9-152">Tworzenie formularza podrzędnego</span><span class="sxs-lookup"><span data-stu-id="08dd9-152">Creating a Child Form</span></span>  
 <span data-ttu-id="08dd9-153">W tej procedurze, zdefiniujesz klasę formularza oddzielny podrzędną, który ma swój własny <xref:System.Windows.Forms.MenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="08dd9-153">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="08dd9-154">Elementy menu dla tego formularza są scalane z tymi z formularza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="08dd9-154">The menu items for this form are merged with those of the parent form.</span></span>  
  
#### <a name="to-define-a-child-form"></a><span data-ttu-id="08dd9-155">Aby zdefiniować formularz podrzędny</span><span class="sxs-lookup"><span data-stu-id="08dd9-155">To define a child form</span></span>  
  
1.  <span data-ttu-id="08dd9-156">Dodaj nowy formularz o nazwie `ChildForm` do projektu.</span><span class="sxs-lookup"><span data-stu-id="08dd9-156">Add a new form named `ChildForm` to the project.</span></span>  
  
     <span data-ttu-id="08dd9-157">Aby uzyskać więcej informacji, zobacz [porady: dodawanie formularzy Windows do projektu](https://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="08dd9-157">For more information, see [How to: Add Windows Forms to a Project](https://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
2.  <span data-ttu-id="08dd9-158">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> formant na formularzu podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="08dd9-158">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>  
  
3.  <span data-ttu-id="08dd9-159">Kliknij przycisk <xref:System.Windows.Forms.MenuStrip> symbol tagu inteligentnego kontrolki (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), a następnie wybierz pozycję **Edytuj elementy**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-159">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>  
  
4.  <span data-ttu-id="08dd9-160">W **Edytor kolekcji elementów** okna dialogowego Dodaj nowy <xref:System.Windows.Forms.ToolStripMenuItem> o nazwie **ChildMenuItem** do menu podrzędne.</span><span class="sxs-lookup"><span data-stu-id="08dd9-160">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>  
  
     <span data-ttu-id="08dd9-161">Aby uzyskać więcej informacji, zobacz [Edytor kolekcji elementów ToolStrip](https://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span><span class="sxs-lookup"><span data-stu-id="08dd9-161">For more information, see [ToolStrip Items Collection Editor](https://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span></span>  
  
## <a name="testing-the-form"></a><span data-ttu-id="08dd9-162">Testowanie formularza</span><span class="sxs-lookup"><span data-stu-id="08dd9-162">Testing the Form</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="08dd9-163">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="08dd9-163">To test your form</span></span>  
  
1.  <span data-ttu-id="08dd9-164">Naciśnij klawisz F5, aby skompilować i uruchomić formularz.</span><span class="sxs-lookup"><span data-stu-id="08dd9-164">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="08dd9-165">Kliknij przycisk **okna** element menu, aby otworzyć menu, a następnie kliknij przycisk **New**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-165">Click the **Window** menu item to open the menu, and then click **New**.</span></span>  
  
     <span data-ttu-id="08dd9-166">Nowy formularz podrzędny jest tworzony w obszar klienta MDI formularza.</span><span class="sxs-lookup"><span data-stu-id="08dd9-166">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="08dd9-167">Menu formularz podrzędny jest scalany z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="08dd9-167">The child form's menu is merged with the main menu.</span></span>  
  
3.  <span data-ttu-id="08dd9-168">Zamknij formularz podrzędny.</span><span class="sxs-lookup"><span data-stu-id="08dd9-168">Close the child form.</span></span>  
  
     <span data-ttu-id="08dd9-169">Formularz podrzędny menu zostanie usunięty z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="08dd9-169">The child form's menu is removed from the main menu.</span></span>  
  
4.  <span data-ttu-id="08dd9-170">Kliknij przycisk **New** kilka razy.</span><span class="sxs-lookup"><span data-stu-id="08dd9-170">Click **New** several times.</span></span>  
  
     <span data-ttu-id="08dd9-171">Formularze podrzędne są automatycznie wyświetlane w obszarze **okna** element menu, ponieważ <xref:System.Windows.Forms.MenuStrip> kontrolki <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwość jest przypisana.</span><span class="sxs-lookup"><span data-stu-id="08dd9-171">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>  
  
## <a name="adding-toolstrip-support"></a><span data-ttu-id="08dd9-172">Dodanie obsługi elementu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="08dd9-172">Adding ToolStrip Support</span></span>  
 <span data-ttu-id="08dd9-173">W ramach tej procedury dodasz cztery <xref:System.Windows.Forms.ToolStrip> formantów do formularza nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="08dd9-173">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="08dd9-174">Każdy <xref:System.Windows.Forms.ToolStrip> formant jest dodawany wewnątrz <xref:System.Windows.Forms.ToolStripPanel> formant, który jest zadokowany do krawędzi formularza.</span><span class="sxs-lookup"><span data-stu-id="08dd9-174">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a><span data-ttu-id="08dd9-175">Aby dodać kontrolki ToolStrip formularza nadrzędnego MDI</span><span class="sxs-lookup"><span data-stu-id="08dd9-175">To add ToolStrip controls to the MDI parent form</span></span>  
  
1.  <span data-ttu-id="08dd9-176">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ToolStripPanel> formant na formularzu.</span><span class="sxs-lookup"><span data-stu-id="08dd9-176">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>  
  
2.  <span data-ttu-id="08dd9-177">Za pomocą <xref:System.Windows.Forms.ToolStripPanel> zaznaczony formant, kliknij dwukrotnie <xref:System.Windows.Forms.ToolStrip> w kontrolce **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-177">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>  
  
     <span data-ttu-id="08dd9-178">A <xref:System.Windows.Forms.ToolStrip> formant zostanie utworzony w <xref:System.Windows.Forms.ToolStripPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="08dd9-178">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
3.  <span data-ttu-id="08dd9-179">Wybierz <xref:System.Windows.Forms.ToolStripPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="08dd9-179">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
4.  <span data-ttu-id="08dd9-180">W oknie Właściwości zmień wartość kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="08dd9-180">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>  
  
     <span data-ttu-id="08dd9-181"><xref:System.Windows.Forms.ToolStripPanel> Kontrolować doków do formularza, pod menu głównego po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="08dd9-181">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="08dd9-182">Obszar klienta MDI dopasowuje się do rozmiaru <xref:System.Windows.Forms.ToolStripPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="08dd9-182">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
5.  <span data-ttu-id="08dd9-183">Powtórz kroki od 1 do 4.</span><span class="sxs-lookup"><span data-stu-id="08dd9-183">Repeat steps 1 through 4.</span></span>  
  
     <span data-ttu-id="08dd9-184">Dokowanie nowy <xref:System.Windows.Forms.ToolStripPanel> kontrolki w górnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="08dd9-184">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>  
  
     <span data-ttu-id="08dd9-185"><xref:System.Windows.Forms.ToolStripPanel> Kontroli jest zadokowany pod menu głównego, ale po prawej stronie pierwszej <xref:System.Windows.Forms.ToolStripPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="08dd9-185">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="08dd9-186">W tym kroku przedstawiono znaczenie porządek poprawnie pozycjonowania <xref:System.Windows.Forms.ToolStripPanel> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="08dd9-186">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
6.  <span data-ttu-id="08dd9-187">Powtórz kroki od 1 do 4 dla dwóch więcej <xref:System.Windows.Forms.ToolStripPanel> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="08dd9-187">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
     <span data-ttu-id="08dd9-188">Dokowanie nowy <xref:System.Windows.Forms.ToolStripPanel> kontrolek w prawo i w dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="08dd9-188">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="08dd9-189">Rozmieszczanie kontrolek ToolStripPanel według porządku osi Z</span><span class="sxs-lookup"><span data-stu-id="08dd9-189">Arranging ToolStripPanel Controls by Z-order</span></span>  
 <span data-ttu-id="08dd9-190">Położenie zadokowanego <xref:System.Windows.Forms.ToolStripPanel> kontrolkę w formularzu MDI jest określana przez położenie formantu w porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="08dd9-190">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="08dd9-191">Łatwo można rozmieścić porządek formantów w okno konspektu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="08dd9-191">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="08dd9-192">Aby rozmieścić formanty ToolStripPanel według porządku osi Z</span><span class="sxs-lookup"><span data-stu-id="08dd9-192">To arrange ToolStripPanel controls by Z-order</span></span>  
  
1.  <span data-ttu-id="08dd9-193">W **widoku** menu, kliknij przycisk **Windows inne**, a następnie kliknij przycisk **konspekt dokumentu**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-193">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>  
  
     <span data-ttu-id="08dd9-194">Rozmieszczenie swoje <xref:System.Windows.Forms.ToolStripPanel> kontrolek z poprzedniej procedury jest niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="08dd9-194">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="08dd9-195">Jest to spowodowane porządku osi jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="08dd9-195">This is because the z-order is not correct.</span></span> <span data-ttu-id="08dd9-196">Okno konspektu dokumentu do zmiany kolejności z formantów.</span><span class="sxs-lookup"><span data-stu-id="08dd9-196">Use the Document Outline window to change the z-order of the controls.</span></span>  
  
2.  <span data-ttu-id="08dd9-197">W oknie konspekt dokumentu wybierz **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-197">In the Document Outline window, select **ToolStripPanel4**.</span></span>  
  
3.  <span data-ttu-id="08dd9-198">Kliknij przycisk strzałki w dół wielokrotnie, dopóki **ToolStripPanel4** znajduje się w dolnej części listy.</span><span class="sxs-lookup"><span data-stu-id="08dd9-198">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>  
  
     <span data-ttu-id="08dd9-199">**ToolStripPanel4** kontroli jest zadokowana do dolnej części formularza, poniżej innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="08dd9-199">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>  
  
4.  <span data-ttu-id="08dd9-200">Wybierz **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="08dd9-200">Select **ToolStripPanel2**.</span></span>  
  
5.  <span data-ttu-id="08dd9-201">Kliknij jeden raz przycisk strzałki w dół, aby położenie formantu trzeci na liście.</span><span class="sxs-lookup"><span data-stu-id="08dd9-201">Click the down-arrow button one time to position the control third in the list.</span></span>  
  
     <span data-ttu-id="08dd9-202">**ToolStripPanel2** kontroli jest zadokowany do górnej części formularza, pod menu głównego i nowszych innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="08dd9-202">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>  
  
6.  <span data-ttu-id="08dd9-203">Wybierz różne formanty w **konspekt dokumentu** okna i przenoszenia ich do różnych pozycji w porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="08dd9-203">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="08dd9-204">Należy pamiętać, efekt porządku osi z o rozmieszczaniu zadokowanych formantów.</span><span class="sxs-lookup"><span data-stu-id="08dd9-204">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="08dd9-205">Użyj klawiszy CTRL-Z lub **Cofnij** na **Edytuj** menu, aby cofnąć zmiany.</span><span class="sxs-lookup"><span data-stu-id="08dd9-205">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="08dd9-206">Punkt kontrolny</span><span class="sxs-lookup"><span data-stu-id="08dd9-206">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="08dd9-207">Aby przetestować formularz</span><span class="sxs-lookup"><span data-stu-id="08dd9-207">To test your form</span></span>  
  
1.  <span data-ttu-id="08dd9-208">Naciśnij klawisz F5, aby skompilować i uruchomić formularz.</span><span class="sxs-lookup"><span data-stu-id="08dd9-208">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="08dd9-209">Kliknij przycisk uchwyt zmiany z <xref:System.Windows.Forms.ToolStrip> kontroli i przeciągnij formant w różnych miejscach na formularzu.</span><span class="sxs-lookup"><span data-stu-id="08dd9-209">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>  
  
     <span data-ttu-id="08dd9-210">Można przeciągnąć <xref:System.Windows.Forms.ToolStrip> formant z jednej <xref:System.Windows.Forms.ToolStripPanel> formantu do innego.</span><span class="sxs-lookup"><span data-stu-id="08dd9-210">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="08dd9-211">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="08dd9-211">Next Steps</span></span>  
 <span data-ttu-id="08dd9-212">W tym przewodniku zostały utworzone za pomocą formularza nadrzędnego MDI <xref:System.Windows.Forms.ToolStrip> kontrolek i scalanie menu.</span><span class="sxs-lookup"><span data-stu-id="08dd9-212">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="08dd9-213">Możesz użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:</span><span class="sxs-lookup"><span data-stu-id="08dd9-213">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="08dd9-214">Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="08dd9-214">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="08dd9-215">Aby uzyskać więcej informacji, zobacz [— informacje o składniku ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="08dd9-215">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="08dd9-216">Formularz utworzony za pomocą automatycznie wypełnione standardowe menu.</span><span class="sxs-lookup"><span data-stu-id="08dd9-216">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="08dd9-217">Aby uzyskać więcej informacji, zobacz [wskazówki: zapewnianie standardowych elementów Menu do formularza](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="08dd9-217">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="08dd9-218">Nadaj swojej <xref:System.Windows.Forms.ToolStrip> profesjonalny wygląd kontrolki.</span><span class="sxs-lookup"><span data-stu-id="08dd9-218">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="08dd9-219">Aby uzyskać więcej informacji, zobacz [porady: ustawienie modułu renderowania ToolStrip dla aplikacji](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="08dd9-219">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08dd9-220">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08dd9-220">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="08dd9-221">Instrukcje: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="08dd9-221">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="08dd9-222">Instrukcje: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="08dd9-222">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="08dd9-223">Instrukcje: wstawianie kontrolki MenuStrip do menu rozwijanego MDI</span><span class="sxs-lookup"><span data-stu-id="08dd9-223">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [<span data-ttu-id="08dd9-224">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="08dd9-224">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
