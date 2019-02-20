---
title: 'Instrukcje: Dołączanie formantu MenuStrip do nadrzędnego okna MDI (formularze Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 9c39b80c06cae91c43c7a79390cef71ae781489e
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442750"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Instrukcje: Dołączanie formantu MenuStrip do nadrzędnego okna MDI (formularze Windows)
W niektórych aplikacjach rodzaj okna podrzędnego interfejsu wielu dokumentów (MDI) może różnić się od nadrzędnego okna MDI. Na przykład element nadrzędny MDI może być arkusza kalkulacyjnego i elementu podrzędnego MDI może być wykres. W takim przypadku chcesz zaktualizować zawartość menu nadrzędny MDI zawartość elementu podrzędnego MDI menu, zgodnie z oknami podrzędnymi MDI różnego rodzaju zostaną aktywowane.  
  
 W poniższej procedurze użyto <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości, aby dołączyć menu podrzędne MDI do menu nadrzędnego MDI. Zamyka okno podrzędne MDI usuwa dołączonym menu z elementu nadrzędnego MDI.  
  
 Zobacz też [aplikacje interfejsu wielu dokumentów (MDI)](../advanced/multiple-document-interface-mdi-applications.md).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Aby dołączyć element menu do elementu nadrzędnego MDI  
  
1.  Tworzenie formularza i ustaw jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwość `true`.  
  
2.  Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `true`.  
  
3.  Ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość `Form1` <xref:System.Windows.Forms.MenuStrip> do `false`.  
  
4.  Dodawanie pozycji menu najwyższego poziomu do `Form1` <xref:System.Windows.Forms.MenuStrip> i ustaw jego <xref:System.Windows.Forms.Control.Text%2A> właściwość `&File`.  
  
5.  Dodaj element podmenu do `&File` element menu i ustaw jego <xref:System.Windows.Forms.Form.Text%2A> właściwość `&Open`.  
  
6.  Dodawanie formularza do projektu, Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza, a następnie ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość `Form2` <xref:System.Windows.Forms.MenuStrip> do `true`.  
  
7.  Dodawanie pozycji menu najwyższego poziomu do `Form2` <xref:System.Windows.Forms.MenuStrip> i ustaw jego <xref:System.Windows.Forms.Form.Text%2A> właściwość `&Special`.  
  
8.  Dodaj dwa elementy podmenu do `&Special` element menu i ustaw ich <xref:System.Windows.Forms.Form.Text%2A> właściwości `Command&1` i `Command&2`odpowiednio.  
  
9. Ustaw <xref:System.Windows.Forms.MergeAction> właściwość `&Special`, `Command&1`, i `Command&2` elementy menu do <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. W ramach programu obsługi zdarzeń, Wstaw kod, podobnie jak poniższy przykład kodu, aby utworzyć i wyświetlić nowe wystąpienia `Form2` jako elementy podrzędne MDI `Form1`.  
  
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
  
12. Umieść kod podobny do poniższego przykładu kodu w `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> zarejestrować program obsługi zdarzeń.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Dwa <xref:System.Windows.Forms.Form> kontrolki o nazwie `Form1` i `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form1` o nazwie `menuStrip1`, a <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form2` o nazwie `menuStrip2`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.
