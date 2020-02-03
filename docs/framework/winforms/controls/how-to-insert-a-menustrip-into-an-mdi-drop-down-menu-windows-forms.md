---
title: 'Porady: wstawianie elementu MenuStrip do menu rozwijanego MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 6e189dd159c48b5779679d0563fab85e9b848992
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736406"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="a6a81-102">Porady: wstawianie elementu MenuStrip do menu rozwijanego MDI (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="a6a81-102">How to: Insert a MenuStrip into an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="a6a81-103">W niektórych aplikacjach rodzaj okna podrzędnego interfejsu wielu dokumentów (MDI) może różnić się od okna nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="a6a81-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="a6a81-104">Na przykład element nadrzędny MDI może być arkuszem kalkulacyjnym, a obiekt podrzędny MDI może być wykresem.</span><span class="sxs-lookup"><span data-stu-id="a6a81-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="a6a81-105">W takim przypadku należy zaktualizować zawartość menu elementu nadrzędnego MDI z zawartością menu elementu podrzędnego MDI, ponieważ aktywowane są okna podrzędne MDI różnych rodzajów.</span><span class="sxs-lookup"><span data-stu-id="a6a81-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="a6a81-106">Poniższa procedura używa właściwości <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>, aby wstawić grupę elementów menu z menu podrzędnego MDI do części listy rozwijanej menu nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="a6a81-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to insert a group of menu items from the MDI child menu into the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="a6a81-107">Zamknięcie okna podrzędnego MDI usuwa wstawione elementy menu z elementu nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="a6a81-107">Closing the MDI child window removes the inserted menu items from the MDI parent.</span></span>  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a><span data-ttu-id="a6a81-108">Aby wstawić element MenuStrip do menu rozwijanego MDI</span><span class="sxs-lookup"><span data-stu-id="a6a81-108">To insert a MenuStrip into an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="a6a81-109">Utwórz formularz i ustaw jego właściwość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="a6a81-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="a6a81-110">Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> <xref:System.Windows.Forms.MenuStrip> na `true`.</span><span class="sxs-lookup"><span data-stu-id="a6a81-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="a6a81-111">Dodaj element menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> `Form1`i ustaw jego właściwość <xref:System.Windows.Forms.Control.Text%2A> na `&File`.</span><span class="sxs-lookup"><span data-stu-id="a6a81-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="a6a81-112">Dodaj trzy elementy podmenu do elementu menu `&File` i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości na `&Open`, `&Import from`i `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="a6a81-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="a6a81-113">Dodaj dwa elementy podmenu do elementu podmenu `&Import from` i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości na `&Word` i `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="a6a81-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="a6a81-114">Dodaj formularz do projektu, Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> `Form2`<xref:System.Windows.Forms.MenuStrip> na `true`.</span><span class="sxs-lookup"><span data-stu-id="a6a81-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="a6a81-115">Dodaj element menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> `Form2`i ustaw jego właściwość <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&File`.</span><span class="sxs-lookup"><span data-stu-id="a6a81-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="a6a81-116">Dodaj elementy podmenu do `&File` menu `Form2` w następującej kolejności: <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`i innych <xref:System.Windows.Forms.ToolStripSeparator>.</span><span class="sxs-lookup"><span data-stu-id="a6a81-116">Add submenu items to the `&File` menu of `Form2` in the following order: a <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`, and another <xref:System.Windows.Forms.ToolStripSeparator>.</span></span>  
  
9. <span data-ttu-id="a6a81-117">Ustaw właściwości <xref:System.Windows.Forms.MergeAction> i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> elementów menu `Form2`, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a6a81-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="a6a81-118">Element menu Form2</span><span class="sxs-lookup"><span data-stu-id="a6a81-118">Form2 menu item</span></span>|<span data-ttu-id="a6a81-119">MergeAction wartość</span><span class="sxs-lookup"><span data-stu-id="a6a81-119">MergeAction value</span></span>|<span data-ttu-id="a6a81-120">MergeIndex wartość</span><span class="sxs-lookup"><span data-stu-id="a6a81-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="a6a81-121">Plik</span><span class="sxs-lookup"><span data-stu-id="a6a81-121">File</span></span>|<span data-ttu-id="a6a81-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="a6a81-122">MatchOnly</span></span>|<span data-ttu-id="a6a81-123">-1</span><span class="sxs-lookup"><span data-stu-id="a6a81-123">-1</span></span>|  
    |<span data-ttu-id="a6a81-124">Separator</span><span class="sxs-lookup"><span data-stu-id="a6a81-124">Separator</span></span>|<span data-ttu-id="a6a81-125">Insert</span><span class="sxs-lookup"><span data-stu-id="a6a81-125">Insert</span></span>|<span data-ttu-id="a6a81-126">2</span><span class="sxs-lookup"><span data-stu-id="a6a81-126">2</span></span>|  
    |<span data-ttu-id="a6a81-127">Zapisanie</span><span class="sxs-lookup"><span data-stu-id="a6a81-127">Save</span></span>|<span data-ttu-id="a6a81-128">Insert</span><span class="sxs-lookup"><span data-stu-id="a6a81-128">Insert</span></span>|<span data-ttu-id="a6a81-129">3</span><span class="sxs-lookup"><span data-stu-id="a6a81-129">3</span></span>|  
    |<span data-ttu-id="a6a81-130">Zapisz i Zamknij</span><span class="sxs-lookup"><span data-stu-id="a6a81-130">Save and Close</span></span>|<span data-ttu-id="a6a81-131">Insert</span><span class="sxs-lookup"><span data-stu-id="a6a81-131">Insert</span></span>|<span data-ttu-id="a6a81-132">4</span><span class="sxs-lookup"><span data-stu-id="a6a81-132">4</span></span>|  
    |<span data-ttu-id="a6a81-133">Separator</span><span class="sxs-lookup"><span data-stu-id="a6a81-133">Separator</span></span>|<span data-ttu-id="a6a81-134">Insert</span><span class="sxs-lookup"><span data-stu-id="a6a81-134">Insert</span></span>|<span data-ttu-id="a6a81-135">5</span><span class="sxs-lookup"><span data-stu-id="a6a81-135">5</span></span>|  
  
10. <span data-ttu-id="a6a81-136">Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.ToolStripMenuItem>`&Open`.</span><span class="sxs-lookup"><span data-stu-id="a6a81-136">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="a6a81-137">W ramach procedury obsługi zdarzeń Wstaw kod podobny do następującego przykładu kodu, aby utworzyć i wyświetlić nowe wystąpienia `Form2` jako elementy podrzędne MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a6a81-137">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="a6a81-138">Umieść kod podobny do następującego przykładu kodu w <xref:System.Windows.Forms.ToolStripMenuItem> `&Open`, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a6a81-138">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a6a81-139">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a6a81-139">Compiling the Code</span></span>  
 <span data-ttu-id="a6a81-140">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a6a81-140">This example requires:</span></span>  
  
- <span data-ttu-id="a6a81-141">Dwie <xref:System.Windows.Forms.Form> kontrolki o nazwach `Form1` i `Form2`.</span><span class="sxs-lookup"><span data-stu-id="a6a81-141">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="a6a81-142">Kontrolka <xref:System.Windows.Forms.MenuStrip> na `Form1` o nazwie `menuStrip1`oraz kontrolce <xref:System.Windows.Forms.MenuStrip> na `Form2` o nazwie `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="a6a81-142">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="a6a81-143">Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6a81-143">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a81-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6a81-144">See also</span></span>

- [<span data-ttu-id="a6a81-145">Instrukcje: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="a6a81-145">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="a6a81-146">Instrukcje: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="a6a81-146">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="a6a81-147">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a6a81-147">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
