---
title: 'Porady: usuwanie elementu ToolStripMenuItem z menu rozwijanego MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 3198195cf0991734826508aa65818505bf2038c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735850"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="52eeb-102">Porady: usuwanie elementu ToolStripMenuItem z menu rozwijanego MDI (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="52eeb-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="52eeb-103">W niektórych aplikacjach rodzaj okna podrzędnego interfejsu wielu dokumentów (MDI) może różnić się od okna nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="52eeb-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="52eeb-104">Na przykład element nadrzędny MDI może być arkuszem kalkulacyjnym, a obiekt podrzędny MDI może być wykresem.</span><span class="sxs-lookup"><span data-stu-id="52eeb-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="52eeb-105">W takim przypadku należy zaktualizować zawartość menu elementu nadrzędnego MDI z zawartością menu elementu podrzędnego MDI, ponieważ aktywowane są okna podrzędne MDI różnych rodzajów.</span><span class="sxs-lookup"><span data-stu-id="52eeb-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="52eeb-106">Poniższa procedura używa właściwości <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>, aby usunąć element menu z rozwijanej części menu nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="52eeb-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="52eeb-107">Zamknięcie podrzędnego okna MDI przywraca usunięte elementy menu do menu nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="52eeb-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="52eeb-108">Aby usunąć element MenuStrip z menu rozwijanego MDI</span><span class="sxs-lookup"><span data-stu-id="52eeb-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="52eeb-109">Utwórz formularz i ustaw jego właściwość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="52eeb-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="52eeb-110">Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> <xref:System.Windows.Forms.MenuStrip> na `true`.</span><span class="sxs-lookup"><span data-stu-id="52eeb-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="52eeb-111">Dodaj element menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> `Form1`i ustaw jego właściwość <xref:System.Windows.Forms.Control.Text%2A> na `&File`.</span><span class="sxs-lookup"><span data-stu-id="52eeb-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="52eeb-112">Dodaj trzy elementy podmenu do elementu menu `&File` i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości na `&Open`, `&Import from`i `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="52eeb-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="52eeb-113">Dodaj dwa elementy podmenu do elementu podmenu `&Import from` i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości na `&Word` i `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="52eeb-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="52eeb-114">Dodaj formularz do projektu, Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> `Form2`<xref:System.Windows.Forms.MenuStrip> na `true`.</span><span class="sxs-lookup"><span data-stu-id="52eeb-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="52eeb-115">Dodaj element menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> `Form2`i ustaw jego właściwość <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&File`.</span><span class="sxs-lookup"><span data-stu-id="52eeb-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="52eeb-116">Dodaj element podmenu `&Import from` do menu `&File` `Form2`, a następnie Dodaj element podmenu `&Word` do menu `&File`.</span><span class="sxs-lookup"><span data-stu-id="52eeb-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="52eeb-117">Ustaw właściwości <xref:System.Windows.Forms.MergeAction> i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> elementów menu `Form2`, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="52eeb-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="52eeb-118">Element menu Form2</span><span class="sxs-lookup"><span data-stu-id="52eeb-118">Form2 menu item</span></span>|<span data-ttu-id="52eeb-119">MergeAction wartość</span><span class="sxs-lookup"><span data-stu-id="52eeb-119">MergeAction value</span></span>|<span data-ttu-id="52eeb-120">MergeIndex wartość</span><span class="sxs-lookup"><span data-stu-id="52eeb-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="52eeb-121">Plik</span><span class="sxs-lookup"><span data-stu-id="52eeb-121">File</span></span>|<span data-ttu-id="52eeb-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="52eeb-122">MatchOnly</span></span>|<span data-ttu-id="52eeb-123">-1</span><span class="sxs-lookup"><span data-stu-id="52eeb-123">-1</span></span>|  
    |<span data-ttu-id="52eeb-124">Importuj z</span><span class="sxs-lookup"><span data-stu-id="52eeb-124">Import from</span></span>|<span data-ttu-id="52eeb-125">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="52eeb-125">MatchOnly</span></span>|<span data-ttu-id="52eeb-126">-1</span><span class="sxs-lookup"><span data-stu-id="52eeb-126">-1</span></span>|  
    |<span data-ttu-id="52eeb-127">Word</span><span class="sxs-lookup"><span data-stu-id="52eeb-127">Word</span></span>|<span data-ttu-id="52eeb-128">Usuń</span><span class="sxs-lookup"><span data-stu-id="52eeb-128">Remove</span></span>|<span data-ttu-id="52eeb-129">-1</span><span class="sxs-lookup"><span data-stu-id="52eeb-129">-1</span></span>|  
  
10. <span data-ttu-id="52eeb-130">W `Form1`Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Click> `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="52eeb-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="52eeb-131">W ramach procedury obsługi zdarzeń Wstaw kod podobny do następującego przykładu kodu, aby utworzyć i wyświetlić nowe wystąpienia `Form2` jako elementy podrzędne MDI `Form1`:</span><span class="sxs-lookup"><span data-stu-id="52eeb-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
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
  
12. <span data-ttu-id="52eeb-132">Umieść kod podobny do następującego przykładu kodu w <xref:System.Windows.Forms.ToolStripMenuItem> `&Open`, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="52eeb-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="52eeb-133">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="52eeb-133">Compiling the Code</span></span>  
 <span data-ttu-id="52eeb-134">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="52eeb-134">This example requires:</span></span>  
  
- <span data-ttu-id="52eeb-135">Dwie <xref:System.Windows.Forms.Form> kontrolki o nazwach `Form1` i `Form2`.</span><span class="sxs-lookup"><span data-stu-id="52eeb-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="52eeb-136">Kontrolka <xref:System.Windows.Forms.MenuStrip> na `Form1` o nazwie `menuStrip1`oraz kontrolce <xref:System.Windows.Forms.MenuStrip> na `Form2` o nazwie `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="52eeb-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="52eeb-137">Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="52eeb-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52eeb-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52eeb-138">See also</span></span>

- [<span data-ttu-id="52eeb-139">Instrukcje: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="52eeb-139">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="52eeb-140">Instrukcje: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="52eeb-140">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="52eeb-141">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="52eeb-141">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
