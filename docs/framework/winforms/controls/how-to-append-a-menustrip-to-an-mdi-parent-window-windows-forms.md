---
title: 'Porady: dołączanie formantu MenuStrip do nadrzędnego okna MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 06e5c9daab8b7eb72024fff27d661c0eb3bf84c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747156"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Porady: dołączanie formantu MenuStrip do nadrzędnego okna MDI (Formularze systemu Windows)
W niektórych aplikacjach rodzaj okna podrzędnego interfejsu wielu dokumentów (MDI) może różnić się od okna nadrzędnego MDI. Na przykład element nadrzędny MDI może być arkuszem kalkulacyjnym, a obiekt podrzędny MDI może być wykresem. W takim przypadku należy zaktualizować zawartość menu elementu nadrzędnego MDI z zawartością menu elementu podrzędnego MDI, ponieważ aktywowane są okna podrzędne MDI różnych rodzajów.  
  
 Poniższa procedura używa właściwości <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>, aby dołączyć menu podrzędne MDI do menu nadrzędnego MDI. Zamknięcie podrzędnego okna MDI usuwa menu dołączone z elementu nadrzędnego MDI.  
  
 Zobacz również [aplikacje interfejsu wielu dokumentów (MDI)](../advanced/multiple-document-interface-mdi-applications.md).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Aby dołączyć element menu do elementu nadrzędnego MDI  
  
1. Utwórz formularz i ustaw jego właściwość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.  
  
2. Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> <xref:System.Windows.Forms.MenuStrip> na `true`.  
  
3. Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.Visible%2A> `Form1`<xref:System.Windows.Forms.MenuStrip> na `false`.  
  
4. Dodaj element menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> `Form1`i ustaw jego właściwość <xref:System.Windows.Forms.Control.Text%2A> na `&File`.  
  
5. Dodaj element podmenu do elementu menu `&File` i ustaw jego właściwość <xref:System.Windows.Forms.Form.Text%2A> na `&Open`.  
  
6. Dodaj formularz do projektu, Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> `Form2`<xref:System.Windows.Forms.MenuStrip> na `true`.  
  
7. Dodaj element menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> `Form2`i ustaw jego właściwość <xref:System.Windows.Forms.Form.Text%2A> na `&Special`.  
  
8. Dodaj dwa elementy podmenu do elementu menu `&Special` i ustaw ich <xref:System.Windows.Forms.Form.Text%2A> właściwości na odpowiednio `Command&1` i `Command&2`.  
  
9. Ustaw właściwość <xref:System.Windows.Forms.MergeAction> elementów menu `&Special`, `Command&1`i `Command&2` na <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.ToolStripMenuItem>`&Open`.  
  
11. W ramach procedury obsługi zdarzeń Wstaw kod podobny do następującego przykładu kodu, aby utworzyć i wyświetlić nowe wystąpienia `Form2` jako elementy podrzędne MDI `Form1`.  
  
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
  
12. Umieść kod podobny do następującego przykładu kodu w <xref:System.Windows.Forms.ToolStripMenuItem> `&Open`, aby zarejestrować procedurę obsługi zdarzeń.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Dwie <xref:System.Windows.Forms.Form> kontrolki o nazwach `Form1` i `Form2`.  
  
- Kontrolka <xref:System.Windows.Forms.MenuStrip> na `Form1` o nazwie `menuStrip1`oraz kontrolce <xref:System.Windows.Forms.MenuStrip> na `Form2` o nazwie `menuStrip2`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.
