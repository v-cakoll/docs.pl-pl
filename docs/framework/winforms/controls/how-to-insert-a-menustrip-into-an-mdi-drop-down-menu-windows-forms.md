---
title: 'Instrukcje: Wstawianie elementu MenuStrip do Menu rozwijanego MDI (formularze Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: c06304e012867030936dfeffd129bb8301d31c8e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718743"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="ccb51-102">Instrukcje: Wstawianie elementu MenuStrip do Menu rozwijanego MDI (formularze Windows)</span><span class="sxs-lookup"><span data-stu-id="ccb51-102">How to: Insert a MenuStrip into an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="ccb51-103">W niektórych aplikacjach rodzaj okna podrzędnego interfejsu wielu dokumentów (MDI) może różnić się od nadrzędnego okna MDI.</span><span class="sxs-lookup"><span data-stu-id="ccb51-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="ccb51-104">Na przykład element nadrzędny MDI może być arkusza kalkulacyjnego i elementu podrzędnego MDI może być wykres.</span><span class="sxs-lookup"><span data-stu-id="ccb51-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="ccb51-105">W takim przypadku chcesz zaktualizować zawartość menu nadrzędny MDI zawartość elementu podrzędnego MDI menu, zgodnie z oknami podrzędnymi MDI różnego rodzaju zostaną aktywowane.</span><span class="sxs-lookup"><span data-stu-id="ccb51-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="ccb51-106">W poniższej procedurze użyto <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości można wstawić grupy elementów menu w menu podrzędne MDI do części rozwijanego menu nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="ccb51-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to insert a group of menu items from the MDI child menu into the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="ccb51-107">Zamyka okno podrzędne MDI usuwa elementy menu wstawiony z nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="ccb51-107">Closing the MDI child window removes the inserted menu items from the MDI parent.</span></span>  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a><span data-ttu-id="ccb51-108">Aby Wstawianie elementu MenuStrip do menu rozwijanego MDI</span><span class="sxs-lookup"><span data-stu-id="ccb51-108">To insert a MenuStrip into an MDI drop-down menu</span></span>  
  
1.  <span data-ttu-id="ccb51-109">Tworzenie formularza i ustaw jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="ccb51-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="ccb51-110">Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="ccb51-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="ccb51-111">Dodawanie pozycji menu najwyższego poziomu do `Form1` <xref:System.Windows.Forms.MenuStrip> i ustaw jego <xref:System.Windows.Forms.Control.Text%2A> właściwość `&File`.</span><span class="sxs-lookup"><span data-stu-id="ccb51-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4.  <span data-ttu-id="ccb51-112">Dodaj trzy elementy podmenu do `&File` element menu i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Open`, `&Import from`, i `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="ccb51-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5.  <span data-ttu-id="ccb51-113">Dodaj dwa elementy podmenu do `&Import from` elementu podmenu i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Word` i `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="ccb51-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6.  <span data-ttu-id="ccb51-114">Dodawanie formularza do projektu, Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza, a następnie ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość `Form2` <xref:System.Windows.Forms.MenuStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="ccb51-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="ccb51-115">Dodawanie pozycji menu najwyższego poziomu do `Form2` <xref:System.Windows.Forms.MenuStrip> i ustaw jego <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwość `&File`.</span><span class="sxs-lookup"><span data-stu-id="ccb51-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8.  <span data-ttu-id="ccb51-116">Dodawanie podmenu do `&File` menu `Form2` w następującej kolejności: <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`, a inny <xref:System.Windows.Forms.ToolStripSeparator>.</span><span class="sxs-lookup"><span data-stu-id="ccb51-116">Add submenu items to the `&File` menu of `Form2` in the following order: a <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`, and another <xref:System.Windows.Forms.ToolStripSeparator>.</span></span>  
  
9. <span data-ttu-id="ccb51-117">Ustaw <xref:System.Windows.Forms.MergeAction> i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości `Form2` elementy menu, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ccb51-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="ccb51-118">Element menu formularz2</span><span class="sxs-lookup"><span data-stu-id="ccb51-118">Form2 menu item</span></span>|<span data-ttu-id="ccb51-119">Wartość MergeAction</span><span class="sxs-lookup"><span data-stu-id="ccb51-119">MergeAction value</span></span>|<span data-ttu-id="ccb51-120">Wartość MergeIndex</span><span class="sxs-lookup"><span data-stu-id="ccb51-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="ccb51-121">Plik</span><span class="sxs-lookup"><span data-stu-id="ccb51-121">File</span></span>|<span data-ttu-id="ccb51-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="ccb51-122">MatchOnly</span></span>|<span data-ttu-id="ccb51-123">-1</span><span class="sxs-lookup"><span data-stu-id="ccb51-123">-1</span></span>|  
    |<span data-ttu-id="ccb51-124">Separator</span><span class="sxs-lookup"><span data-stu-id="ccb51-124">Separator</span></span>|<span data-ttu-id="ccb51-125">Insert</span><span class="sxs-lookup"><span data-stu-id="ccb51-125">Insert</span></span>|<span data-ttu-id="ccb51-126">2</span><span class="sxs-lookup"><span data-stu-id="ccb51-126">2</span></span>|  
    |<span data-ttu-id="ccb51-127">Zapisanie</span><span class="sxs-lookup"><span data-stu-id="ccb51-127">Save</span></span>|<span data-ttu-id="ccb51-128">Insert</span><span class="sxs-lookup"><span data-stu-id="ccb51-128">Insert</span></span>|<span data-ttu-id="ccb51-129">3</span><span class="sxs-lookup"><span data-stu-id="ccb51-129">3</span></span>|  
    |<span data-ttu-id="ccb51-130">Zapisz i zamknij</span><span class="sxs-lookup"><span data-stu-id="ccb51-130">Save and Close</span></span>|<span data-ttu-id="ccb51-131">Insert</span><span class="sxs-lookup"><span data-stu-id="ccb51-131">Insert</span></span>|<span data-ttu-id="ccb51-132">4</span><span class="sxs-lookup"><span data-stu-id="ccb51-132">4</span></span>|  
    |<span data-ttu-id="ccb51-133">Separator</span><span class="sxs-lookup"><span data-stu-id="ccb51-133">Separator</span></span>|<span data-ttu-id="ccb51-134">Insert</span><span class="sxs-lookup"><span data-stu-id="ccb51-134">Insert</span></span>|<span data-ttu-id="ccb51-135">5</span><span class="sxs-lookup"><span data-stu-id="ccb51-135">5</span></span>|  
  
10. <span data-ttu-id="ccb51-136">Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="ccb51-136">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="ccb51-137">W ramach programu obsługi zdarzeń, Wstaw kod, podobnie jak poniższy przykład kodu, aby utworzyć i wyświetlić nowe wystąpienia `Form2` jako elementy podrzędne MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="ccb51-137">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="ccb51-138">Umieść kod podobny do poniższego przykładu kodu w `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ccb51-138">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ccb51-139">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ccb51-139">Compiling the Code</span></span>  
 <span data-ttu-id="ccb51-140">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ccb51-140">This example requires:</span></span>  
  
-   <span data-ttu-id="ccb51-141">Dwa <xref:System.Windows.Forms.Form> kontrolki o nazwie `Form1` i `Form2`.</span><span class="sxs-lookup"><span data-stu-id="ccb51-141">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="ccb51-142">A <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form1` o nazwie `menuStrip1`, a <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form2` o nazwie `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="ccb51-142">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="ccb51-143">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="ccb51-143">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb51-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccb51-144">See also</span></span>
- [<span data-ttu-id="ccb51-145">Instrukcje: Tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="ccb51-145">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="ccb51-146">Instrukcje: Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="ccb51-146">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="ccb51-147">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="ccb51-147">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
