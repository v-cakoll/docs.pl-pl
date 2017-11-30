---
title: 'Porady: wstawianie elementu MenuStrip do menu rozwijanego MDI (Formularze systemu Windows)'
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
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2befec35090cf69c6a12cfe24c3512ae9a9b1bfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="0d0f9-102">Porady: wstawianie elementu MenuStrip do menu rozwijanego MDI (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="0d0f9-102">How to: Insert a MenuStrip into an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="0d0f9-103">W niektórych aplikacjach rodzaj okno podrzędne interfejsu wielu dokumentów (MDI) może się różnić od nadrzędnego okna MDI.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="0d0f9-104">Na przykład element nadrzędny MDI może być arkusza kalkulacyjnego i podrzędnych MDI może być wykresu.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="0d0f9-105">W takim przypadku chcesz zaktualizować zawartość element nadrzędny MDI menu z zawartością menu podrzędnego MDI jako okien podrzędnych MDI różnego rodzaju są uaktywnione.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="0d0f9-106">W poniższej procedurze użyto <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości, aby wstawić grupy elementów menu z menu podrzędnego MDI do listy rozwijanej części menu nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to insert a group of menu items from the MDI child menu into the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="0d0f9-107">Zamknięcie okna podrzędnego MDI usuwa elementy menu wstawiony element nadrzędny MDI.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-107">Closing the MDI child window removes the inserted menu items from the MDI parent.</span></span>  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a><span data-ttu-id="0d0f9-108">Aby wstawić elementu MenuStrip do menu rozwijanego MDI</span><span class="sxs-lookup"><span data-stu-id="0d0f9-108">To insert a MenuStrip into an MDI drop-down menu</span></span>  
  
1.  <span data-ttu-id="0d0f9-109">Tworzenie formularza i ustawić jej <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="0d0f9-110">Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="0d0f9-111">Dodaj element menu najwyższego poziomu do `Form1` <xref:System.Windows.Forms.MenuStrip> i ustawić jej <xref:System.Windows.Forms.Control.Text%2A> właściwości `&File`.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4.  <span data-ttu-id="0d0f9-112">Dodaj trzy elementy podmenu do `&File` element menu i zestaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Open`, `&Import from`, i `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5.  <span data-ttu-id="0d0f9-113">Dodaj dwa elementy podmenu do `&Import from` elementu podmenu i zestaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Word` i `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6.  <span data-ttu-id="0d0f9-114">Dodawanie formularza do projektu, należy dodać <xref:System.Windows.Forms.MenuStrip> formularza i zestawu <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość `Form2` <xref:System.Windows.Forms.MenuStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="0d0f9-115">Dodaj element menu najwyższego poziomu do `Form2` <xref:System.Windows.Forms.MenuStrip> i ustawić jej <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&File`.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8.  <span data-ttu-id="0d0f9-116">Dodawanie elementów podmenu w celu `&File` menu `Form2` w następującej kolejności: <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `&Close``and Save`, a inny <xref:System.Windows.Forms.ToolStripSeparator>.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-116">Add submenu items to the `&File` menu of `Form2` in the following order: a <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `&Close``and Save`, and another <xref:System.Windows.Forms.ToolStripSeparator>.</span></span>  
  
9. <span data-ttu-id="0d0f9-117">Ustaw <xref:System.Windows.Forms.MergeAction> i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości `Form2` elementów menu, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="0d0f9-118">Element menu formularz2</span><span class="sxs-lookup"><span data-stu-id="0d0f9-118">Form2 menu item</span></span>|<span data-ttu-id="0d0f9-119">Wartość MergeAction</span><span class="sxs-lookup"><span data-stu-id="0d0f9-119">MergeAction value</span></span>|<span data-ttu-id="0d0f9-120">Wartość MergeIndex</span><span class="sxs-lookup"><span data-stu-id="0d0f9-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="0d0f9-121">Plik</span><span class="sxs-lookup"><span data-stu-id="0d0f9-121">File</span></span>|<span data-ttu-id="0d0f9-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="0d0f9-122">MatchOnly</span></span>|<span data-ttu-id="0d0f9-123">-1</span><span class="sxs-lookup"><span data-stu-id="0d0f9-123">-1</span></span>|  
    |<span data-ttu-id="0d0f9-124">Separator</span><span class="sxs-lookup"><span data-stu-id="0d0f9-124">Separator</span></span>|<span data-ttu-id="0d0f9-125">Insert</span><span class="sxs-lookup"><span data-stu-id="0d0f9-125">Insert</span></span>|<span data-ttu-id="0d0f9-126">2</span><span class="sxs-lookup"><span data-stu-id="0d0f9-126">2</span></span>|  
    |<span data-ttu-id="0d0f9-127">Zapisanie</span><span class="sxs-lookup"><span data-stu-id="0d0f9-127">Save</span></span>|<span data-ttu-id="0d0f9-128">Insert</span><span class="sxs-lookup"><span data-stu-id="0d0f9-128">Insert</span></span>|<span data-ttu-id="0d0f9-129">3</span><span class="sxs-lookup"><span data-stu-id="0d0f9-129">3</span></span>|  
    |<span data-ttu-id="0d0f9-130">Zapisz i zamknij</span><span class="sxs-lookup"><span data-stu-id="0d0f9-130">Save and Close</span></span>|<span data-ttu-id="0d0f9-131">Insert</span><span class="sxs-lookup"><span data-stu-id="0d0f9-131">Insert</span></span>|<span data-ttu-id="0d0f9-132">4</span><span class="sxs-lookup"><span data-stu-id="0d0f9-132">4</span></span>|  
    |<span data-ttu-id="0d0f9-133">Separator</span><span class="sxs-lookup"><span data-stu-id="0d0f9-133">Separator</span></span>|<span data-ttu-id="0d0f9-134">Insert</span><span class="sxs-lookup"><span data-stu-id="0d0f9-134">Insert</span></span>|<span data-ttu-id="0d0f9-135">5</span><span class="sxs-lookup"><span data-stu-id="0d0f9-135">5</span></span>|  
  
10. <span data-ttu-id="0d0f9-136">Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenie `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-136">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="0d0f9-137">W ramach programu obsługi zdarzeń, Wstaw kod podobny do poniższego przykładu kodu można tworzyć i wyświetlać nowych wystąpień `Form2` jako elementy podrzędne MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-137">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
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
  
12. <span data-ttu-id="0d0f9-138">Umieść kod podobny do poniższego przykładu kodu w `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> można zarejestrować obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-138">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0d0f9-139">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0d0f9-139">Compiling the Code</span></span>  
 <span data-ttu-id="0d0f9-140">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0d0f9-140">This example requires:</span></span>  
  
-   <span data-ttu-id="0d0f9-141">Dwa <xref:System.Windows.Forms.Form> formantów `Form1` i `Form2`.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-141">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="0d0f9-142">A <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form1` o nazwie `menuStrip1`, a <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form2` o nazwie `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-142">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="0d0f9-143">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="0d0f9-143">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d0f9-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d0f9-144">See Also</span></span>  
 [<span data-ttu-id="0d0f9-145">Porady: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="0d0f9-145">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="0d0f9-146">Porady: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="0d0f9-146">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="0d0f9-147">Informacje o formancie MenuStrip</span><span class="sxs-lookup"><span data-stu-id="0d0f9-147">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
