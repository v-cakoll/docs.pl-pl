---
title: 'Porady: tworzenie list okien MDI za pomocą elementu MenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: f013c3df2ab5783a22fe2c34402dc53a328cafa2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731012"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Porady: tworzenie list okien MDI za pomocą elementu MenuStrip (Formularze systemu Windows)
Użyj interfejsu wielu dokumentów (MDI) do tworzenia aplikacji, które mogą otwierać kilka dokumentów w tym samym czasie i kopiować i wklejać zawartość z jednego dokumentu do drugiego.  
  
 Ta procedura pokazuje, jak utworzyć listę wszystkich aktywnych formularzy podrzędnych w menu okna nadrzędnego.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>Aby utworzyć listę okien MDI dla elementu MenuStrip  
  
1. Utwórz formularz i ustaw jego właściwość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.  
  
2. Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza.  
  
3. Dodaj dwa elementy menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> i ustaw ich <xref:System.Windows.Forms.Control.Text%2A> właściwości na `&File` i `&Window`.  
  
4. Dodaj element podmenu do elementu menu `&File` i ustaw jego właściwość <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&Open`.  
  
5. Ustaw właściwość <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> <xref:System.Windows.Forms.MenuStrip> na `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6. Dodaj formularz do projektu i Dodaj do niego formant, taki jak inny <xref:System.Windows.Forms.MenuStrip>.  
  
7. Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.ToolStripMenuItem>`&New`.  
  
8. W ramach procedury obsługi zdarzeń Wstaw kod podobny do poniższego, aby utworzyć i wyświetlić nowe wystąpienia `Form2` jako elementy podrzędne MDI `Form1`.  
  
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
  
9. Umieść kod podobny do poniższego w <xref:System.Windows.Forms.ToolStripMenuItem> `&New`, aby zarejestrować procedurę obsługi zdarzeń.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Dwie <xref:System.Windows.Forms.Form> kontrolki o nazwach `Form1` i `Form2`.  
  
- Kontrolka <xref:System.Windows.Forms.MenuStrip> na `Form1` o nazwie `menuStrip1`oraz kontrolce <xref:System.Windows.Forms.MenuStrip> na `Form2` o nazwie `menuStrip2`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie formularzy nadrzędnych MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Instrukcje: tworzenie formularzy podrzędnych MDI](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip, kontrolka](menustrip-control-windows-forms.md)
