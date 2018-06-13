---
title: 'Porady: dołączanie formantu MenuStrip do nadrzędnego okna MDI (Formularze systemu Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 048add340a81856cd30482c52c93c76bbf6181f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529558"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a><span data-ttu-id="ff19b-102">Porady: dołączanie formantu MenuStrip do nadrzędnego okna MDI (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="ff19b-102">How to: Append a MenuStrip to an MDI Parent Window (Windows Forms)</span></span>
<span data-ttu-id="ff19b-103">W niektórych aplikacjach rodzaj okno podrzędne interfejsu wielu dokumentów (MDI) może się różnić od nadrzędnego okna MDI.</span><span class="sxs-lookup"><span data-stu-id="ff19b-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="ff19b-104">Na przykład element nadrzędny MDI może być arkusza kalkulacyjnego i podrzędnych MDI może być wykresu.</span><span class="sxs-lookup"><span data-stu-id="ff19b-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="ff19b-105">W takim przypadku chcesz zaktualizować zawartość element nadrzędny MDI menu z zawartością menu podrzędnego MDI jako okien podrzędnych MDI różnego rodzaju są uaktywnione.</span><span class="sxs-lookup"><span data-stu-id="ff19b-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="ff19b-106">W poniższej procedurze użyto <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości do dołączenia do menu nadrzędnego MDI menu podrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="ff19b-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to append the MDI child menu to the MDI parent menu.</span></span> <span data-ttu-id="ff19b-107">Zamknięcie okna podrzędnego MDI Usuwa menu dołączany element nadrzędny MDI.</span><span class="sxs-lookup"><span data-stu-id="ff19b-107">Closing the MDI child window removes the appended menu from the MDI parent.</span></span>  
  
 <span data-ttu-id="ff19b-108">Zobacz też [aplikacje interfejsu wielu dokumentów (MDI)](http://msdn.microsoft.com/library/xyhh2e7e\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ff19b-108">Also see [Multiple-Document Interface (MDI) Applications](http://msdn.microsoft.com/library/xyhh2e7e\(v=vs.110\)).</span></span>  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a><span data-ttu-id="ff19b-109">Aby dołączyć elementu menu. element nadrzędny MDI</span><span class="sxs-lookup"><span data-stu-id="ff19b-109">To append a menu item to an MDI parent</span></span>  
  
1.  <span data-ttu-id="ff19b-110">Tworzenie formularza i ustawić jej <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="ff19b-110">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="ff19b-111">Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="ff19b-111">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="ff19b-112">Ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość `Form1` <xref:System.Windows.Forms.MenuStrip> do `false`.</span><span class="sxs-lookup"><span data-stu-id="ff19b-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the `Form1`<xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
4.  <span data-ttu-id="ff19b-113">Dodaj element menu najwyższego poziomu do `Form1` <xref:System.Windows.Forms.MenuStrip> i ustawić jej <xref:System.Windows.Forms.Control.Text%2A> właściwości `&File`.</span><span class="sxs-lookup"><span data-stu-id="ff19b-113">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
5.  <span data-ttu-id="ff19b-114">Dodawanie elementu podmenu `&File` element menu i zestaw jej <xref:System.Windows.Forms.Form.Text%2A> właściwości `&Open`.</span><span class="sxs-lookup"><span data-stu-id="ff19b-114">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Open`.</span></span>  
  
6.  <span data-ttu-id="ff19b-115">Dodawanie formularza do projektu, należy dodać <xref:System.Windows.Forms.MenuStrip> formularza i zestawu <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość `Form2` <xref:System.Windows.Forms.MenuStrip> do `true`.</span><span class="sxs-lookup"><span data-stu-id="ff19b-115">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="ff19b-116">Dodaj element menu najwyższego poziomu do `Form2` <xref:System.Windows.Forms.MenuStrip> i ustawić jej <xref:System.Windows.Forms.Form.Text%2A> właściwości `&Special`.</span><span class="sxs-lookup"><span data-stu-id="ff19b-116">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Form.Text%2A> property to `&Special`.</span></span>  
  
8.  <span data-ttu-id="ff19b-117">Dodaj dwa elementy podmenu do `&Special` element menu i zestaw ich <xref:System.Windows.Forms.Form.Text%2A> właściwości `Command&1` i `Command&2`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="ff19b-117">Add two submenu items to the `&Special` menu item and set their <xref:System.Windows.Forms.Form.Text%2A> properties to `Command&1` and `Command&2`, respectively.</span></span>  
  
9. <span data-ttu-id="ff19b-118">Ustaw <xref:System.Windows.Forms.MergeAction> właściwość `&Special`, `Command&1`, i `Command&2` elementy menu <xref:System.Windows.Forms.MergeAction.Append>.</span><span class="sxs-lookup"><span data-stu-id="ff19b-118">Set the <xref:System.Windows.Forms.MergeAction> property of the `&Special`, `Command&1`, and `Command&2` menu items to <xref:System.Windows.Forms.MergeAction.Append>.</span></span>  
  
10. <span data-ttu-id="ff19b-119">Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenie `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="ff19b-119">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="ff19b-120">W ramach programu obsługi zdarzeń, Wstaw kod podobny do poniższego przykładu kodu można tworzyć i wyświetlać nowych wystąpień `Form2` jako elementy podrzędne MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="ff19b-120">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
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
  
12. <span data-ttu-id="ff19b-121">Umieść kod podobny do poniższego przykładu kodu w `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> można zarejestrować obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ff19b-121">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff19b-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ff19b-122">Compiling the Code</span></span>  
 <span data-ttu-id="ff19b-123">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ff19b-123">This example requires:</span></span>  
  
-   <span data-ttu-id="ff19b-124">Dwa <xref:System.Windows.Forms.Form> formantów `Form1` i `Form2`.</span><span class="sxs-lookup"><span data-stu-id="ff19b-124">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="ff19b-125">A <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form1` o nazwie `menuStrip1`, a <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form2` o nazwie `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="ff19b-125">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="ff19b-126">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="ff19b-126">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>
