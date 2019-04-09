---
title: 'Instrukcje: Tworzenie formularzy podrzędnych MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 83f94830eec1d82112719a48e8ea98e2503f4542
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124530"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="64297-102">Instrukcje: Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="64297-102">How to: Create MDI Child Forms</span></span>
<span data-ttu-id="64297-103">Formularze podrzędne MDI jest podstawowym elementem [aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md), jak te formularze są środek interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="64297-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>  
  
 <span data-ttu-id="64297-104">W poniższej procedurze utworzysz formularz podrzędny MDI, która wyświetla <xref:System.Windows.Forms.RichTextBox> kontrolki, podobne do innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64297-104">In the following procedure, you will create MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="64297-105">Podstawianie <xref:System.Windows.Forms> kontrolką inne formanty, takie jak <xref:System.Windows.Forms.DataGridView> formantu lub kombinację kontrolki pozwala na tworzenie elementu podrzędnego MDI systemu windows (a w konsekwencji, aplikacje MDI) z różnych możliwości.</span><span class="sxs-lookup"><span data-stu-id="64297-105">Substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls enables you to create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64297-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="64297-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="64297-107">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="64297-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="64297-108">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="64297-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-mdi-child-forms"></a><span data-ttu-id="64297-109">Umożliwia tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="64297-109">To create MDI child forms</span></span>  
  
1.  <span data-ttu-id="64297-110">Utwórz nowy projekt Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="64297-110">Create a new Windows Forms project.</span></span> <span data-ttu-id="64297-111">W **Windows właściwości** formularza, ustaw jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`, a jego `WindowsState` właściwość `Maximized`.</span><span class="sxs-lookup"><span data-stu-id="64297-111">In **the Properties Windows** for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`, and its `WindowsState` property to `Maximized`.</span></span>  
  
     <span data-ttu-id="64297-112">Określa formularza jako kontenera okien podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="64297-112">This designates the form as an MDI container for child windows.</span></span>  
  
2.  <span data-ttu-id="64297-113">Z `Toolbox`, przeciągnij <xref:System.Windows.Forms.MenuStrip> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="64297-113">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="64297-114">Ustaw jego `Text` właściwości **pliku**.</span><span class="sxs-lookup"><span data-stu-id="64297-114">Set its `Text` property to **File**.</span></span>  
  
3.  <span data-ttu-id="64297-115">Kliknij przycisk z wielokropkiem (...) obok pozycji **elementów** właściwości, a następnie kliknij przycisk **Dodaj** można dodać dwa elementy menu paska narzędzi podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="64297-115">Click the ellipses (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="64297-116">Ustaw `Text` właściwości dla tych elementów do **New** i **okna**.</span><span class="sxs-lookup"><span data-stu-id="64297-116">Set the `Text` property for these items to **New** and **Window**.</span></span>  
  
4.  <span data-ttu-id="64297-117">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, wskaż **Dodaj**, a następnie wybierz pozycję **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="64297-117">In **Solution Explorer**, right-click the project, point to **Add**, and then select **Add New Item**.</span></span>  
  
5.  <span data-ttu-id="64297-118">W **Dodaj nowy element** okno dialogowe, wybierz opcję **formularza Windows** (w języku Visual Basic lub języka Visual C#) lub **Windows Forms aplikacji (.NET)** (w [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) z  **Szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="64297-118">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) from the **Templates** pane.</span></span> <span data-ttu-id="64297-119">W **nazwa** pola, określ nazwę formularza **formularz2**.</span><span class="sxs-lookup"><span data-stu-id="64297-119">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="64297-120">Kliknij przycisk **Otwórz** przycisk, aby dodać formularz do projektu.</span><span class="sxs-lookup"><span data-stu-id="64297-120">Click the **Open** button to add the form to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64297-121">Formularz podrzędny MDI, który został utworzony w tym kroku jest standardowy formularz Windows.</span><span class="sxs-lookup"><span data-stu-id="64297-121">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="64297-122">W efekcie ma <xref:System.Windows.Forms.Form.Opacity%2A> właściwość, która umożliwia kontrolowanie przezroczystości formularza.</span><span class="sxs-lookup"><span data-stu-id="64297-122">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="64297-123">Jednak <xref:System.Windows.Forms.Form.Opacity%2A> właściwość została zaprojektowana dla okien najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="64297-123">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="64297-124">Nie używaj go za pomocą formularzy podrzędnych MDI, jak mogą wystąpić problemy malowania.</span><span class="sxs-lookup"><span data-stu-id="64297-124">Do not use it with MDI child forms, as painting problems can occur.</span></span>  
  
     <span data-ttu-id="64297-125">Ten formularz będzie szablonu dla formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="64297-125">This form will be the template for your MDI child forms.</span></span>  
  
     <span data-ttu-id="64297-126">**Windows Forms Designer** otwiera się i wyświetla **formularz2**.</span><span class="sxs-lookup"><span data-stu-id="64297-126">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>  
  
6.  <span data-ttu-id="64297-127">Z **przybornika**, przeciągnij **RichTextBox** formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="64297-127">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>  
  
7.  <span data-ttu-id="64297-128">W **właściwości** oknie `Anchor` właściwości **, lewa górna** i `Dock` właściwości **wypełnienia**.</span><span class="sxs-lookup"><span data-stu-id="64297-128">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>  
  
     <span data-ttu-id="64297-129">Powoduje to, że <xref:System.Windows.Forms.RichTextBox> sterowania, aby całkowicie wypełnić obszaru formularz podrzędny MDI, nawet w przypadku, gdy zmieniany jest rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="64297-129">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>  
  
8.  <span data-ttu-id="64297-130">Kliknij dwukrotnie **New** element menu, aby utworzyć <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="64297-130">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>  
  
9. <span data-ttu-id="64297-131">Wstawianie kodu podobne do następujących czynności, aby utworzyć nowy formularz podrzędny MDI, gdy użytkownik kliknie **New** elementu menu.</span><span class="sxs-lookup"><span data-stu-id="64297-131">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64297-132">W poniższym przykładzie obsługuje program obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> zdarzenie `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="64297-132">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="64297-133">Należy pamiętać, w zależności od specyfiki architektury aplikacji, usługi **New** element menu może nie być `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="64297-133">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>  
  
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
  
     <span data-ttu-id="64297-134">W [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], Dodaj następujący kod `#include` dyrektywę w górnej części Form1.h:</span><span class="sxs-lookup"><span data-stu-id="64297-134">In [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], add the following `#include` directive at the top of Form1.h:</span></span>  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. <span data-ttu-id="64297-135">Na liście rozwijanej w górnej części **właściwości** okna, wybierz pasek menu, który odpowiada **pliku** paska menu i ustaw <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwości w oknie <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="64297-135">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
     <span data-ttu-id="64297-136">Spowoduje to włączenie **okna** menu, aby utrzymywać listę otwartych okien podrzędnych MDI znacznik wyboru obok okna podrzędnego active.</span><span class="sxs-lookup"><span data-stu-id="64297-136">This will enable the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>  
  
11. <span data-ttu-id="64297-137">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="64297-137">Press F5 to run the application.</span></span> <span data-ttu-id="64297-138">Wybierając **New** z **pliku** menu, można utworzyć nowych formularzy podrzędnych MDI, które są przechowywane informacje o w **okna** elementu menu.</span><span class="sxs-lookup"><span data-stu-id="64297-138">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64297-139">Jeśli formularz podrzędny MDI ma <xref:System.Windows.Forms.MainMenu> składnika (z, zwykle struktury menu elementów menu) i jest otwarty w ramach formularza nadrzędnego MDI, która ma <xref:System.Windows.Forms.MainMenu> składnik (z, zwykle struktury menu elementów menu), menu, automatycznie scali elementów Jeśli ustawiono <xref:System.Windows.Forms.MenuItem.MergeType%2A> właściwości (i ewentualnie <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> właściwości).</span><span class="sxs-lookup"><span data-stu-id="64297-139">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="64297-140">Ustaw <xref:System.Windows.Forms.MenuItem.MergeType%2A> właściwość obu <xref:System.Windows.Forms.MainMenu> składników i wszystkie elementy menu formularza podrzędnego <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span><span class="sxs-lookup"><span data-stu-id="64297-140">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="64297-141">Ponadto, ustawić <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> właściwość tak, aby elementy menu, zarówno menu są wyświetlane w odpowiedni sposób.</span><span class="sxs-lookup"><span data-stu-id="64297-141">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="64297-142">Ponadto należy pamiętać o tym, że po zamknięciu formularza nadrzędnego MDI każdego elementu podrzędnego MDI formularzy zgłasza <xref:System.Windows.Forms.Form.Closing> zdarzenie przed <xref:System.Windows.Forms.Form.Closing> jest wywoływane zdarzenie nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="64297-142">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="64297-143">Anulowanie podrzędnym MDI <xref:System.Windows.Forms.Form.Closing> zdarzeń nie zapobiega nadrzędny MDI <xref:System.Windows.Forms.Form.Closing> zdarzenia wywoływane; jednak <xref:System.ComponentModel.CancelEventArgs> argumentu dla elementu nadrzędnego MDI <xref:System.Windows.Forms.Form.Closing> zdarzenie zostanie teraz ustawiony na `true`.</span><span class="sxs-lookup"><span data-stu-id="64297-143">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="64297-144">Można wymusić nadrzędnych MDI i wszystkie formularze podrzędne MDI, aby zamknąć, ustawiając <xref:System.ComponentModel.CancelEventArgs> argument `false`.</span><span class="sxs-lookup"><span data-stu-id="64297-144">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64297-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64297-145">See also</span></span>

- [<span data-ttu-id="64297-146">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="64297-146">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="64297-147">Instrukcje: Tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="64297-147">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="64297-148">Instrukcje: Określanie elementu podrzędnego MDI Active</span><span class="sxs-lookup"><span data-stu-id="64297-148">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="64297-149">Instrukcje: Wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="64297-149">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="64297-150">Instrukcje: Rozmieszczanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="64297-150">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
