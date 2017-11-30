---
title: 'Porady: usuwanie elementu ToolStripMenuItem z menu rozwijanego MDI (Formularze systemu Windows)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b265544b45ad0614985fdc1d8dbf6f9c0b909ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="20fd1-102">Porady: usuwanie elementu ToolStripMenuItem z menu rozwijanego MDI (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="20fd1-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="20fd1-103">W niektórych aplikacjach rodzaj okno podrzędne interfejsu wielu dokumentów (MDI) może się różnić od nadrzędnego okna MDI.</span><span class="sxs-lookup"><span data-stu-id="20fd1-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="20fd1-104">Na przykład element nadrzędny MDI może być arkusza kalkulacyjnego i podrzędnych MDI może być wykresu.</span><span class="sxs-lookup"><span data-stu-id="20fd1-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="20fd1-105">W takim przypadku chcesz zaktualizować zawartość element nadrzędny MDI menu z zawartością menu podrzędnego MDI jako okien podrzędnych MDI różnego rodzaju są uaktywnione.</span><span class="sxs-lookup"><span data-stu-id="20fd1-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="20fd1-106">W poniższej procedurze użyto <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości, aby usunąć element menu z listy rozwijanej części menu nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="20fd1-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="20fd1-107">Zamknięcie okna podrzędnego MDI przywraca elementów usuniętych menu menu nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="20fd1-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="20fd1-108">Aby usunąć elementu MenuStrip z menu rozwijanego MDI</span><span class="sxs-lookup"><span data-stu-id="20fd1-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1.  <span data-ttu-id="20fd1-109">Tworzenie formularza i ustawić jej <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="20fd1-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="20fd1-110">Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="20fd1-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="20fd1-111">Dodaj element menu najwyższego poziomu do `Form1` <xref:System.Windows.Forms.MenuStrip> i ustawić jej <xref:System.Windows.Forms.Control.Text%2A> właściwości `&File`.</span><span class="sxs-lookup"><span data-stu-id="20fd1-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4.  <span data-ttu-id="20fd1-112">Dodaj trzy elementy podmenu do `&File` element menu i zestaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Open`, `&Import from`, i `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="20fd1-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5.  <span data-ttu-id="20fd1-113">Dodaj dwa elementy podmenu do `&Import from` elementu podmenu i zestaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Word` i `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="20fd1-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6.  <span data-ttu-id="20fd1-114">Dodawanie formularza do projektu, należy dodać <xref:System.Windows.Forms.MenuStrip> formularza i zestawu <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość `Form2` <xref:System.Windows.Forms.MenuStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="20fd1-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="20fd1-115">Dodaj element menu najwyższego poziomu do `Form2` <xref:System.Windows.Forms.MenuStrip> i ustawić jej <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&File`.</span><span class="sxs-lookup"><span data-stu-id="20fd1-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8.  <span data-ttu-id="20fd1-116">Dodaj `&Import from` elementu podmenu w celu `&File` menu `Form2`i Dodaj `&Word` elementu podmenu w celu `&File` menu.</span><span class="sxs-lookup"><span data-stu-id="20fd1-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="20fd1-117">Ustaw <xref:System.Windows.Forms.MergeAction> i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości `Form2` elementów menu, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="20fd1-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="20fd1-118">Element menu formularz2</span><span class="sxs-lookup"><span data-stu-id="20fd1-118">Form2 menu item</span></span>|<span data-ttu-id="20fd1-119">Wartość MergeAction</span><span class="sxs-lookup"><span data-stu-id="20fd1-119">MergeAction value</span></span>|<span data-ttu-id="20fd1-120">Wartość MergeIndex</span><span class="sxs-lookup"><span data-stu-id="20fd1-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="20fd1-121">Plik</span><span class="sxs-lookup"><span data-stu-id="20fd1-121">File</span></span>|<span data-ttu-id="20fd1-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="20fd1-122">MatchOnly</span></span>|<span data-ttu-id="20fd1-123">-1</span><span class="sxs-lookup"><span data-stu-id="20fd1-123">-1</span></span>|  
    |<span data-ttu-id="20fd1-124">Importuj z</span><span class="sxs-lookup"><span data-stu-id="20fd1-124">Import from</span></span>|<span data-ttu-id="20fd1-125">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="20fd1-125">MatchOnly</span></span>|<span data-ttu-id="20fd1-126">-1</span><span class="sxs-lookup"><span data-stu-id="20fd1-126">-1</span></span>|  
    |<span data-ttu-id="20fd1-127">Word</span><span class="sxs-lookup"><span data-stu-id="20fd1-127">Word</span></span>|<span data-ttu-id="20fd1-128">Usuń</span><span class="sxs-lookup"><span data-stu-id="20fd1-128">Remove</span></span>|<span data-ttu-id="20fd1-129">-1</span><span class="sxs-lookup"><span data-stu-id="20fd1-129">-1</span></span>|  
  
10. <span data-ttu-id="20fd1-130">W `Form1`, utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenie `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="20fd1-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="20fd1-131">W ramach programu obsługi zdarzeń, Wstaw kod podobny do poniższego przykładu kodu można tworzyć i wyświetlać nowych wystąpień `Form2` jako elementy podrzędne MDI `Form1`:</span><span class="sxs-lookup"><span data-stu-id="20fd1-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. <span data-ttu-id="20fd1-132">Umieść kod podobny do poniższego przykładu kodu w `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> można zarejestrować obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="20fd1-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="20fd1-133">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="20fd1-133">Compiling the Code</span></span>  
 <span data-ttu-id="20fd1-134">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="20fd1-134">This example requires:</span></span>  
  
-   <span data-ttu-id="20fd1-135">Dwa <xref:System.Windows.Forms.Form> formantów `Form1` i `Form2`.</span><span class="sxs-lookup"><span data-stu-id="20fd1-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="20fd1-136">A <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form1` o nazwie `menuStrip1`, a <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form2` o nazwie `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="20fd1-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="20fd1-137">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="20fd1-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20fd1-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20fd1-138">See Also</span></span>  
 [<span data-ttu-id="20fd1-139">Porady: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="20fd1-139">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="20fd1-140">Porady: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="20fd1-140">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="20fd1-141">Informacje o formancie MenuStrip</span><span class="sxs-lookup"><span data-stu-id="20fd1-141">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
