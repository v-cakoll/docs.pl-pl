---
title: 'Instrukcje: Usuwanie elementu ToolStripMenuItem z Menu rozwijanego MDI (formularze Windows)'
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
ms.openlocfilehash: 378410977c31a446b34bf907dfd438a2a799c84a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662291"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="9f9ab-102">Instrukcje: Usuwanie elementu ToolStripMenuItem z Menu rozwijanego MDI (formularze Windows)</span><span class="sxs-lookup"><span data-stu-id="9f9ab-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="9f9ab-103">W niektórych aplikacjach rodzaj okna podrzędnego interfejsu wielu dokumentów (MDI) może różnić się od nadrzędnego okna MDI.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="9f9ab-104">Na przykład element nadrzędny MDI może być arkusza kalkulacyjnego i elementu podrzędnego MDI może być wykres.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="9f9ab-105">W takim przypadku chcesz zaktualizować zawartość menu nadrzędny MDI zawartość elementu podrzędnego MDI menu, zgodnie z oknami podrzędnymi MDI różnego rodzaju zostaną aktywowane.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="9f9ab-106">W poniższej procedurze użyto <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości, aby usunąć element menu z listy rozwijanej części menu nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="9f9ab-107">Zamyka okno podrzędne MDI przywraca elementy usunięte menu do menu nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="9f9ab-108">Aby usunąć elementu MenuStrip z menu rozwijanego MDI</span><span class="sxs-lookup"><span data-stu-id="9f9ab-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="9f9ab-109">Tworzenie formularza i ustaw jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="9f9ab-110">Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="9f9ab-111">Dodawanie pozycji menu najwyższego poziomu do `Form1` <xref:System.Windows.Forms.MenuStrip> i ustaw jego <xref:System.Windows.Forms.Control.Text%2A> właściwość `&File`.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="9f9ab-112">Dodaj trzy elementy podmenu do `&File` element menu i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Open`, `&Import from`, i `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="9f9ab-113">Dodaj dwa elementy podmenu do `&Import from` elementu podmenu i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Word` i `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="9f9ab-114">Dodawanie formularza do projektu, Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza, a następnie ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość `Form2` <xref:System.Windows.Forms.MenuStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="9f9ab-115">Dodawanie pozycji menu najwyższego poziomu do `Form2` <xref:System.Windows.Forms.MenuStrip> i ustaw jego <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwość `&File`.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="9f9ab-116">Dodaj `&Import from` elementu podmenu do `&File` menu `Form2`i Dodaj `&Word` elementu podmenu do `&File` menu.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="9f9ab-117">Ustaw <xref:System.Windows.Forms.MergeAction> i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości `Form2` elementy menu, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="9f9ab-118">Element menu formularz2</span><span class="sxs-lookup"><span data-stu-id="9f9ab-118">Form2 menu item</span></span>|<span data-ttu-id="9f9ab-119">Wartość MergeAction</span><span class="sxs-lookup"><span data-stu-id="9f9ab-119">MergeAction value</span></span>|<span data-ttu-id="9f9ab-120">Wartość MergeIndex</span><span class="sxs-lookup"><span data-stu-id="9f9ab-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="9f9ab-121">Plik</span><span class="sxs-lookup"><span data-stu-id="9f9ab-121">File</span></span>|<span data-ttu-id="9f9ab-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="9f9ab-122">MatchOnly</span></span>|<span data-ttu-id="9f9ab-123">-1</span><span class="sxs-lookup"><span data-stu-id="9f9ab-123">-1</span></span>|  
    |<span data-ttu-id="9f9ab-124">Importuj z</span><span class="sxs-lookup"><span data-stu-id="9f9ab-124">Import from</span></span>|<span data-ttu-id="9f9ab-125">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="9f9ab-125">MatchOnly</span></span>|<span data-ttu-id="9f9ab-126">-1</span><span class="sxs-lookup"><span data-stu-id="9f9ab-126">-1</span></span>|  
    |<span data-ttu-id="9f9ab-127">Word</span><span class="sxs-lookup"><span data-stu-id="9f9ab-127">Word</span></span>|<span data-ttu-id="9f9ab-128">Usuń</span><span class="sxs-lookup"><span data-stu-id="9f9ab-128">Remove</span></span>|<span data-ttu-id="9f9ab-129">-1</span><span class="sxs-lookup"><span data-stu-id="9f9ab-129">-1</span></span>|  
  
10. <span data-ttu-id="9f9ab-130">W `Form1`, Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="9f9ab-131">W ramach programu obsługi zdarzeń, Wstaw kod, podobnie jak poniższy przykład kodu, aby utworzyć i wyświetlić nowe wystąpienia `Form2` jako elementy podrzędne MDI `Form1`:</span><span class="sxs-lookup"><span data-stu-id="9f9ab-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
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
  
12. <span data-ttu-id="9f9ab-132">Umieść kod podobny do poniższego przykładu kodu w `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f9ab-133">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9f9ab-133">Compiling the Code</span></span>  
 <span data-ttu-id="9f9ab-134">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9f9ab-134">This example requires:</span></span>  
  
- <span data-ttu-id="9f9ab-135">Dwa <xref:System.Windows.Forms.Form> kontrolki o nazwie `Form1` i `Form2`.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="9f9ab-136">A <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form1` o nazwie `menuStrip1`, a <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form2` o nazwie `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="9f9ab-137">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="9f9ab-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f9ab-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f9ab-138">See also</span></span>

- [<span data-ttu-id="9f9ab-139">Instrukcje: Tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="9f9ab-139">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="9f9ab-140">Instrukcje: Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="9f9ab-140">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="9f9ab-141">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="9f9ab-141">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
