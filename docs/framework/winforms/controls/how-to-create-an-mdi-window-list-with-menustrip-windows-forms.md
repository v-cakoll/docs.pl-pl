---
title: 'Instrukcje: Tworzenie List okien MDI za pomocą elementu MenuStrip (formularze Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: 00f35fe872fc5702595108646e2605ed419823f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585315"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Instrukcje: Tworzenie List okien MDI za pomocą elementu MenuStrip (formularze Windows)
Umożliwia tworzenie aplikacji, które można otworzyć kilku dokumentów, w tym samym czasie i kopiowania i wklejania zawartości z jednego dokumentu do innego interfejsu wielu dokumentów (MDI).  
  
 Ta procedura pokazuje, jak utworzyć listę wszystkie formularze podrzędne aktywne menu okna nadrzędnego.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>Do tworzenie list okien MDI w formancie MenuStrip  
  
1.  Tworzenie formularza i ustaw jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwość `true`.  
  
2.  Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza.  
  
3.  Dodaj dwa elementy menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> i ustaw ich <xref:System.Windows.Forms.Control.Text%2A> właściwości `&File` i `&Window`.  
  
4.  Dodaj element podmenu do `&File` element menu i ustaw jego <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwość `&Open`.  
  
5.  Ustaw <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6.  Dodawanie formularza do projektu i kontrolka ma do niej dodać, takich jak innego <xref:System.Windows.Forms.MenuStrip>.  
  
7.  Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
8.  W ramach programu obsługi zdarzeń, Wstaw kod podobne do następujących czynności, aby utworzyć i wyświetlić nowe wystąpienia `Form2` jako elementy podrzędne MDI `Form1`.  
  
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
  
9. Umieść kod następujący w `&New` <xref:System.Windows.Forms.ToolStripMenuItem> zarejestrować program obsługi zdarzeń.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Dwa <xref:System.Windows.Forms.Form> kontrolki o nazwie `Form1` i `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form1` o nazwie `menuStrip1`, a <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form2` o nazwie `menuStrip2`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [Instrukcje: Tworzenie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip, kontrolka](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
