---
title: "Porady: tworzenie list okien MDI za pomocą elementu MenuStrip (Formularze systemu Windows)"
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
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea2b3f41e6e40b589589db99bb2a5a0ba474c8cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a><span data-ttu-id="098ea-102">Porady: tworzenie list okien MDI za pomocą elementu MenuStrip (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="098ea-102">How to: Create an MDI Window List with MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="098ea-103">Interfejs dokumentu wielokrotnego (MDI) umożliwia tworzenie aplikacji, które można otworzyć kilka dokumentów, w tym samym czasie i kopiowania i wklejania zawartości z jednego dokumentu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="098ea-103">Use the multiple-document interface (MDI) to create applications that can open several documents at the same time and copy and paste content from one document to the other.</span></span>  
  
 <span data-ttu-id="098ea-104">Ta procedura przedstawia sposób tworzenia listy wszystkich formularzy podrzędnych aktywne menu okna nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="098ea-104">This procedure shows you how to create a list of all the active child forms on the parent's Window menu.</span></span>  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a><span data-ttu-id="098ea-105">Aby tworzenie list okien MDI w formancie MenuStrip</span><span class="sxs-lookup"><span data-stu-id="098ea-105">To create an MDI Window list on a MenuStrip</span></span>  
  
1.  <span data-ttu-id="098ea-106">Tworzenie formularza i ustawić jej <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="098ea-106">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="098ea-107">Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza.</span><span class="sxs-lookup"><span data-stu-id="098ea-107">Add a <xref:System.Windows.Forms.MenuStrip> to the form.</span></span>  
  
3.  <span data-ttu-id="098ea-108">Dodaj dwa elementy menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> i ustawić ich <xref:System.Windows.Forms.Control.Text%2A> właściwości `&File` i `&Window`.</span><span class="sxs-lookup"><span data-stu-id="098ea-108">Add two top-level menu items to the <xref:System.Windows.Forms.MenuStrip> and set their <xref:System.Windows.Forms.Control.Text%2A> properties to `&File` and `&Window`.</span></span>  
  
4.  <span data-ttu-id="098ea-109">Dodawanie elementu podmenu `&File` element menu i zestaw jej <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Open`.</span><span class="sxs-lookup"><span data-stu-id="098ea-109">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&Open`.</span></span>  
  
5.  <span data-ttu-id="098ea-110">Ustaw <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="098ea-110">Set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property of the <xref:System.Windows.Forms.MenuStrip> to the `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
6.  <span data-ttu-id="098ea-111">Dodawanie formularza do projektu i Dodaj formant ma do niego, takie jak inny <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="098ea-111">Add a form to the project and add the control you want to it, such as another <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
7.  <span data-ttu-id="098ea-112">Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenie `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="098ea-112">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
8.  <span data-ttu-id="098ea-113">W ramach programu obsługi zdarzeń Wstawianie kodu podobne do następujących czynności, aby utworzyć i wyświetlić nowe wystąpienia klasy `Form2` jako elementy podrzędne MDI `Form1`.</span><span class="sxs-lookup"><span data-stu-id="098ea-113">Within the event handler, insert code similar to the following to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. <span data-ttu-id="098ea-114">Umieść kod podobnie do następującej w `&New` <xref:System.Windows.Forms.ToolStripMenuItem> można zarejestrować obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="098ea-114">Place code like the following in the `&New`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="098ea-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="098ea-115">Compiling the Code</span></span>  
 <span data-ttu-id="098ea-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="098ea-116">This example requires:</span></span>  
  
-   <span data-ttu-id="098ea-117">Dwa <xref:System.Windows.Forms.Form> formantów `Form1` i `Form2`.</span><span class="sxs-lookup"><span data-stu-id="098ea-117">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="098ea-118">A <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form1` o nazwie `menuStrip1`, a <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form2` o nazwie `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="098ea-118">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="098ea-119">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="098ea-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098ea-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="098ea-120">See Also</span></span>  
 [<span data-ttu-id="098ea-121">Porady: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="098ea-121">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="098ea-122">Porady: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="098ea-122">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="098ea-123">MenuStrip — formant</span><span class="sxs-lookup"><span data-stu-id="098ea-123">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
