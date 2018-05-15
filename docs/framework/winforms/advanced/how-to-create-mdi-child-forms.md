---
title: 'Porady: tworzenie formularzy podrzędnych MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: d4351e88de896f366ae2c4050f0e1c32aa0188a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="cfd98-102">Porady: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="cfd98-102">How to: Create MDI Child Forms</span></span>
<span data-ttu-id="cfd98-103">Formularze podrzędne MDI jest podstawowym elementem [aplikacje interfejsu wielu dokumentów (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), jak te są Centrum interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="cfd98-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) Applications](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>  
  
 <span data-ttu-id="cfd98-104">W poniższej procedurze utworzysz formularz podrzędny MDI, który wyświetla <xref:System.Windows.Forms.RichTextBox> kontroli podobna do innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfd98-104">In the following procedure, you will create MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="cfd98-105">Zastępowanie <xref:System.Windows.Forms> sterować za pomocą inne formanty, takie jak <xref:System.Windows.Forms.DataGridView> kontroli oraz ich kombinacjami formantów umożliwia tworzenie okien podrzędnych MDI (a przez rozszerzenie, aplikacje MDI) z różnych możliwości.</span><span class="sxs-lookup"><span data-stu-id="cfd98-105">Substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls enables you to create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfd98-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="cfd98-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cfd98-107">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="cfd98-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cfd98-108">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="cfd98-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-mdi-child-forms"></a><span data-ttu-id="cfd98-109">Do tworzenia formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="cfd98-109">To create MDI child forms</span></span>  
  
1.  <span data-ttu-id="cfd98-110">Utwórz nowy projekt formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cfd98-110">Create a new Windows Forms project.</span></span> <span data-ttu-id="cfd98-111">W **okna właściwości** formularza, ustaw jej <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`i jego `WindowsState` właściwości `Maximized`.</span><span class="sxs-lookup"><span data-stu-id="cfd98-111">In **the Properties Windows** for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`, and its `WindowsState` property to `Maximized`.</span></span>  
  
     <span data-ttu-id="cfd98-112">Określa formularza jako kontenera okien podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="cfd98-112">This designates the form as an MDI container for child windows.</span></span>  
  
2.  <span data-ttu-id="cfd98-113">Z `Toolbox`, przeciągnij <xref:System.Windows.Forms.MenuStrip> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="cfd98-113">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="cfd98-114">Ustaw jego `Text` właściwości **pliku**.</span><span class="sxs-lookup"><span data-stu-id="cfd98-114">Set its `Text` property to **File**.</span></span>  
  
3.  <span data-ttu-id="cfd98-115">Kliknij przycisk wielokropka (...) obok pozycji **elementów** właściwości, a następnie kliknij przycisk **Dodaj** można dodać dwóch elementów menu paska narzędzia podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="cfd98-115">Click the ellipses (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="cfd98-116">Ustaw `Text` właściwości dla tych elementów do **nowy** i **okna**.</span><span class="sxs-lookup"><span data-stu-id="cfd98-116">Set the `Text` property for these items to **New** and **Window**.</span></span>  
  
4.  <span data-ttu-id="cfd98-117">W **Eksploratora rozwiązań**, kliknij projekt prawym przyciskiem myszy, wskaż polecenie **Dodaj**, a następnie wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="cfd98-117">In **Solution Explorer**, right-click the project, point to **Add**, and then select **Add New Item**.</span></span>  
  
5.  <span data-ttu-id="cfd98-118">W **Dodaj nowy element** okno dialogowe, wybierz opcję **formularza systemu Windows** (w języku Visual Basic lub języka Visual C#) lub **aplikacji formularzy systemu Windows (.NET)** (w [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) z  **Szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="cfd98-118">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) from the **Templates** pane.</span></span> <span data-ttu-id="cfd98-119">W **nazwa** pozycję Nazwa formularza **formularz2**.</span><span class="sxs-lookup"><span data-stu-id="cfd98-119">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="cfd98-120">Kliknij przycisk **Otwórz** przycisk, aby dodać formularza do projektu.</span><span class="sxs-lookup"><span data-stu-id="cfd98-120">Click the **Open** button to add the form to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cfd98-121">Formularz podrzędny MDI utworzone w tym kroku jest standardowe formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cfd98-121">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="cfd98-122">W efekcie ma <xref:System.Windows.Forms.Form.Opacity%2A> właściwość, która umożliwia kontrolowanie przezroczystości formularza.</span><span class="sxs-lookup"><span data-stu-id="cfd98-122">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="cfd98-123">Jednak <xref:System.Windows.Forms.Form.Opacity%2A> właściwość została zaprojektowana dla systemu windows najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="cfd98-123">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="cfd98-124">Nie należy używać go z formularzy podrzędnych MDI, jak mogą wystąpić problemy rysowania.</span><span class="sxs-lookup"><span data-stu-id="cfd98-124">Do not use it with MDI child forms, as painting problems can occur.</span></span>  
  
     <span data-ttu-id="cfd98-125">Ten formularz będzie szablonu dla formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="cfd98-125">This form will be the template for your MDI child forms.</span></span>  
  
     <span data-ttu-id="cfd98-126">**Projektant formularzy systemu Windows** otwiera wyświetlanie **formularz2**.</span><span class="sxs-lookup"><span data-stu-id="cfd98-126">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>  
  
6.  <span data-ttu-id="cfd98-127">Z **przybornika**, przeciągnij **RichTextBox** sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="cfd98-127">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>  
  
7.  <span data-ttu-id="cfd98-128">W **właściwości** ustaw `Anchor` właściwości **, lewa górna** i `Dock` właściwości **wypełnienia**.</span><span class="sxs-lookup"><span data-stu-id="cfd98-128">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>  
  
     <span data-ttu-id="cfd98-129">Powoduje to <xref:System.Windows.Forms.RichTextBox> sterowania, aby wypełnić obszar formularz podrzędny MDI, nawet wtedy, gdy zmieni się rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="cfd98-129">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>  
  
8.  <span data-ttu-id="cfd98-130">Kliknij dwukrotnie **nowy** element menu, aby utworzyć <xref:System.Windows.Forms.Control.Click> obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cfd98-130">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>  
  
9. <span data-ttu-id="cfd98-131">Wstawianie kodu podobne do następujących czynności, aby utworzyć nowy formularz podrzędny MDI, gdy użytkownik kliknie **nowy** elementu menu.</span><span class="sxs-lookup"><span data-stu-id="cfd98-131">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cfd98-132">W poniższym przykładzie obsługuje program obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> zdarzenia dla `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="cfd98-132">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="cfd98-133">Należy pamiętać, że, w zależności od specyfiki architektury aplikacji, z **nowy** element menu nie mogą być `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="cfd98-133">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>  
  
    ```vb  
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click  
       Dim NewMDIChild As New Form2()  
       'Set the Parent Form of the Child window.  
       NewMDIChild.MdiParent = Me  
       'Display the new form.  
       NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    protected void MDIChildNew_Click(object sender, System.EventArgs e){  
       Form2 newMDIChild = new Form2();  
       // Set the Parent Form of the Child window.  
       newMDIChild.MdiParent = this;  
       // Display the new form.  
       newMDIChild.Show();  
    }  
    ```  
  
    ```cpp  
    private:  
       void menuItem2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          Form2^ newMDIChild = gcnew Form2();  
          // Set the Parent Form of the Child window.  
          newMDIChild->MdiParent = this;  
          // Display the new form.  
          newMDIChild->Show();  
       }  
    ```  
  
     <span data-ttu-id="cfd98-134">W [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], Dodaj następujący `#include` dyrektywy w górnej części Form1.h:</span><span class="sxs-lookup"><span data-stu-id="cfd98-134">In [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], add the following `#include` directive at the top of Form1.h:</span></span>  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. <span data-ttu-id="cfd98-135">Na liście rozwijanej na górze **właściwości** okna, wybierz paska menu, która odpowiada **pliku** paska menu i zestaw <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwości do okna <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="cfd98-135">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
     <span data-ttu-id="cfd98-136">Spowoduje to włączenie **okna** menu, aby utrzymywać listę okien podrzędnych MDI znacznik wyboru obok okna podrzędnego active.</span><span class="sxs-lookup"><span data-stu-id="cfd98-136">This will enable the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>  
  
11. <span data-ttu-id="cfd98-137">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="cfd98-137">Press F5 to run the application.</span></span> <span data-ttu-id="cfd98-138">Wybierając **nowy** z **pliku** menu, można utworzyć nowego formularzy podrzędnych MDI, które są przechowywane informacje o w **okna** elementu menu.</span><span class="sxs-lookup"><span data-stu-id="cfd98-138">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cfd98-139">Gdy formularz podrzędny MDI ma <xref:System.Windows.Forms.MainMenu> składnik (z, zazwyczaj struktury menu elementów menu) i jest otwarty w formularza nadrzędnego MDI, który ma <xref:System.Windows.Forms.MainMenu> składnik (z, zazwyczaj struktury menu elementów menu), automatycznie scali elementów menu Jeśli ustawiono <xref:System.Windows.Forms.MenuItem.MergeType%2A> właściwości (i opcjonalnie <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> właściwości).</span><span class="sxs-lookup"><span data-stu-id="cfd98-139">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="cfd98-140">Ustaw <xref:System.Windows.Forms.MenuItem.MergeType%2A> właściwość obu <xref:System.Windows.Forms.MainMenu> składników i wszystkich elementów menu do formularza podrzędnego <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span><span class="sxs-lookup"><span data-stu-id="cfd98-140">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="cfd98-141">Ponadto, ustawić <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> właściwości, aby elementów menu z obu menu są wyświetlane w odpowiedni sposób.</span><span class="sxs-lookup"><span data-stu-id="cfd98-141">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="cfd98-142">Ponadto należy pamiętać, że po zamknięciu formularza nadrzędnego MDI każdego elementu podrzędnego MDI formularzy zgłasza <xref:System.Windows.Forms.Form.Closing> zdarzeń przed <xref:System.Windows.Forms.Form.Closing> nadrzędnego MDI zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cfd98-142">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="cfd98-143">Anulowanie podrzędnych MDI <xref:System.Windows.Forms.Form.Closing> zdarzeń nie zapobiega element nadrzędny MDI <xref:System.Windows.Forms.Form.Closing> zdarzenia z zgłaszanych; jednak <xref:System.ComponentModel.CancelEventArgs> argument element nadrzędny MDI <xref:System.Windows.Forms.Form.Closing> zdarzeń zostanie teraz ustawiony na `true`.</span><span class="sxs-lookup"><span data-stu-id="cfd98-143">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="cfd98-144">Możesz wymusić element nadrzędny MDI i wszystkie formularze podrzędne MDI, aby zamknąć przez ustawienie <xref:System.ComponentModel.CancelEventArgs> argument `false`.</span><span class="sxs-lookup"><span data-stu-id="cfd98-144">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd98-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfd98-145">See Also</span></span>  
 [<span data-ttu-id="cfd98-146">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="cfd98-146">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="cfd98-147">Instrukcje: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="cfd98-147">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="cfd98-148">Instrukcje: określanie elementu podrzędnego MDI Active</span><span class="sxs-lookup"><span data-stu-id="cfd98-148">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="cfd98-149">Instrukcje: wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="cfd98-149">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="cfd98-150">Instrukcje: aranżowanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="cfd98-150">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
