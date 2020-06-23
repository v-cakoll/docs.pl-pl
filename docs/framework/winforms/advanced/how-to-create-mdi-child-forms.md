---
title: 'Porady: tworzenie formularzy podrzędnych MDI'
description: Dowiedz się, jak za pomocą programu Visual Studio utworzyć formularz podrzędny interfejsu wielu dokumentów (MDI), który wyświetla formant RichTextBox.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 7fe5cde342f0f5ee078f888b7492cd4618bea5c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903184"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="50066-103">Instrukcje: Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="50066-103">How to: Create MDI child forms</span></span>

<span data-ttu-id="50066-104">Formularze podrzędne MDI są ważnym elementem [aplikacji interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md), ponieważ stanowią one centrum interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="50066-104">MDI child forms are an essential element of [Multiple-Document Interface (MDI) applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="50066-105">W poniższej procedurze użyto programu Visual Studio do utworzenia formularza podrzędnego MDI, który wyświetla <xref:System.Windows.Forms.RichTextBox> kontrolkę podobną do większości aplikacji do przetwarzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="50066-105">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="50066-106">Podstawiając <xref:System.Windows.Forms> formant z innymi kontrolkami, takimi jak <xref:System.Windows.Forms.DataGridView> kontrolka, lub kombinacją formantów, można utworzyć okna podrzędne MDI (i przez rozszerzenie, aplikacje MDI) z różnymi możliwościami.</span><span class="sxs-lookup"><span data-stu-id="50066-106">By substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls, you can create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="50066-107">Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="50066-107">Create MDI child forms</span></span>

1. <span data-ttu-id="50066-108">Utwórz nowy projekt aplikacji Windows Forms w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50066-108">Create a new Windows Forms application project in Visual Studio.</span></span> <span data-ttu-id="50066-109">W oknie **Właściwości** formularza ustaw jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> Właściwość na `true` , a jej `WindowsState` Właściwość na `Maximized` .</span><span class="sxs-lookup"><span data-stu-id="50066-109">In the **Properties** window for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true` and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="50066-110">Oznacza to, że formularz jest kontenerem MDI dla okien podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="50066-110">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="50066-111">Na stronie `Toolbox` przeciągnij <xref:System.Windows.Forms.MenuStrip> kontrolkę do formularza.</span><span class="sxs-lookup"><span data-stu-id="50066-111">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="50066-112">Ustaw jej `Text` Właściwość na **plik**.</span><span class="sxs-lookup"><span data-stu-id="50066-112">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="50066-113">Kliknij przycisk wielokropka (...) obok właściwości **Items** , a następnie kliknij przycisk **Dodaj** , aby dodać dwa podrzędne elementy menu pasków narzędzi.</span><span class="sxs-lookup"><span data-stu-id="50066-113">Click the ellipsis (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="50066-114">Ustaw `Text` Właściwość dla tych elementów na **New** i **window**.</span><span class="sxs-lookup"><span data-stu-id="50066-114">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="50066-115">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="50066-115">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

5. <span data-ttu-id="50066-116">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **formularz systemu Windows** (w Visual Basic lub w języku Visual C#) lub **Windows Forms aplikacji (.NET)** (w Visual C++) w okienku **Szablony** .</span><span class="sxs-lookup"><span data-stu-id="50066-116">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in Visual C++) from the **Templates** pane.</span></span> <span data-ttu-id="50066-117">W polu **Nazwa** wpisz **Form2**.</span><span class="sxs-lookup"><span data-stu-id="50066-117">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="50066-118">Wybierz pozycję **Otwórz** , aby dodać formularz do projektu.</span><span class="sxs-lookup"><span data-stu-id="50066-118">Select **Open** to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="50066-119">Formularz podrzędny MDI utworzony w tym kroku jest standardowym formularzem systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="50066-119">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="50066-120">W związku z tym ma <xref:System.Windows.Forms.Form.Opacity%2A> Właściwość, która umożliwia kontrolowanie przejrzystości formularza.</span><span class="sxs-lookup"><span data-stu-id="50066-120">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="50066-121">Jednak <xref:System.Windows.Forms.Form.Opacity%2A> Właściwość została zaprojektowana dla okien najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="50066-121">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="50066-122">Nie należy używać go z formularzami podrzędnymi MDI, ponieważ mogą wystąpić problemy z malowaniem.</span><span class="sxs-lookup"><span data-stu-id="50066-122">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="50066-123">Ten formularz będzie szablonem dla formularzy podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="50066-123">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="50066-124">Zostanie otwarty **Projektant formularzy systemu Windows** , który wyświetla **Form2**.</span><span class="sxs-lookup"><span data-stu-id="50066-124">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="50066-125">Z **przybornika**przeciągnij formant **RichTextBox** do formularza.</span><span class="sxs-lookup"><span data-stu-id="50066-125">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="50066-126">W oknie **Właściwości** Ustaw `Anchor` Właściwość na **Top, Left** i `Dock` Właściwość na wartość **Fill**.</span><span class="sxs-lookup"><span data-stu-id="50066-126">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="50066-127">Powoduje to <xref:System.Windows.Forms.RichTextBox> , że formant wypełnia całkowicie obszar formularza podrzędnego MDI, nawet gdy zmieniany jest rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="50066-127">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="50066-128">Kliknij dwukrotnie element menu **Nowy** , aby utworzyć <xref:System.Windows.Forms.Control.Click> dla niego procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="50066-128">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="50066-129">Wstaw kod podobny do poniższego, aby utworzyć nowy formularz podrzędny MDI, gdy użytkownik kliknie **Nowy** element menu.</span><span class="sxs-lookup"><span data-stu-id="50066-129">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="50066-130">W poniższym przykładzie program obsługi zdarzeń obsługuje <xref:System.Windows.Forms.Control.Click> zdarzenie dla `MenuItem2` .</span><span class="sxs-lookup"><span data-stu-id="50066-130">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="50066-131">Należy pamiętać, że w zależności od konkretnej architektury aplikacji **Nowy** element menu może nie być `MenuItem2` .</span><span class="sxs-lookup"><span data-stu-id="50066-131">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

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

   <span data-ttu-id="50066-132">W języku C++ Dodaj następującą `#include` dyrektywę w górnej części formularza Form1. h:</span><span class="sxs-lookup"><span data-stu-id="50066-132">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="50066-133">Z listy rozwijanej w górnej części okna **Właściwości** wybierz pasek menu, który odpowiada pasek menu **plik** i ustaw <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> Właściwość na okno <xref:System.Windows.Forms.ToolStripMenuItem> .</span><span class="sxs-lookup"><span data-stu-id="50066-133">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="50066-134">Dzięki temu menu **okno** będzie obsługiwać listę otwartych okien podrzędnych MDI ze znacznikiem wyboru obok aktywnego okna podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="50066-134">This enables the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="50066-135">Naciśnij klawisz **F5** , aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="50066-135">Press **F5** to run the application.</span></span> <span data-ttu-id="50066-136">Wybierając pozycję **Nowy** w menu **plik** , można utworzyć nowe formularze podrzędne MDI, które są śledzone w elemencie menu **okno** .</span><span class="sxs-lookup"><span data-stu-id="50066-136">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="50066-137">Gdy formularz podrzędny MDI ma <xref:System.Windows.Forms.MainMenu> składnik (z, zazwyczaj strukturę menu elementów menu) i jest otwarty w ramach formularza nadrzędnego MDI, który ma <xref:System.Windows.Forms.MainMenu> składnik (z, zazwyczaj strukturę menu elementów menu), elementy menu zostaną scalone automatycznie, jeśli ustawisz <xref:System.Windows.Forms.MenuItem.MergeType%2A> Właściwość (i opcjonalnie <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> Właściwość).</span><span class="sxs-lookup"><span data-stu-id="50066-137">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="50066-138">Ustaw <xref:System.Windows.Forms.MenuItem.MergeType%2A> Właściwość obu <xref:System.Windows.Forms.MainMenu> składników i wszystkich elementów menu w formularzu podrzędnym na <xref:System.Windows.Forms.MenuMerge.MergeItems> .</span><span class="sxs-lookup"><span data-stu-id="50066-138">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="50066-139">Ponadto ustaw <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> Właściwość tak, aby elementy menu z obu menu były wyświetlane w odpowiedniej kolejności.</span><span class="sxs-lookup"><span data-stu-id="50066-139">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="50066-140">Ponadto należy pamiętać, że po zamknięciu formularza nadrzędnego MDI każdy z formularzy podrzędnych MDI zgłasza <xref:System.Windows.Forms.Form.Closing> zdarzenie <xref:System.Windows.Forms.Form.Closing> , zanim zostanie zgłoszone zdarzenie dla elementu nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="50066-140">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="50066-141">Anulowanie zdarzenia elementu podrzędnego MDI <xref:System.Windows.Forms.Form.Closing> nie uniemożliwi <xref:System.Windows.Forms.Form.Closing> wypróbowania zdarzenia elementu nadrzędnego MDI; jednak <xref:System.ComponentModel.CancelEventArgs> argument dla zdarzenia elementu nadrzędnego MDI <xref:System.Windows.Forms.Form.Closing> zostanie teraz ustawiony na wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="50066-141">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="50066-142">Można wymusić zamknięcie elementu nadrzędnego i wszystkich formularzy podrzędnych MDI przez ustawienie <xref:System.ComponentModel.CancelEventArgs> argumentu na `false` .</span><span class="sxs-lookup"><span data-stu-id="50066-142">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="50066-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50066-143">See also</span></span>

- [<span data-ttu-id="50066-144">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="50066-144">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="50066-145">Porady: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="50066-145">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="50066-146">Instrukcje: określanie elementu podrzędnego MDI Active</span><span class="sxs-lookup"><span data-stu-id="50066-146">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="50066-147">Instrukcje: wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="50066-147">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="50066-148">Porady: aranżowanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="50066-148">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
