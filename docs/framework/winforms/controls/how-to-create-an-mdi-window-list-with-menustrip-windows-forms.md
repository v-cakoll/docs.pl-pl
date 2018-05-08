---
title: 'Porady: tworzenie list okien MDI za pomocą elementu MenuStrip (Formularze systemu Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: c87ffadaef2842f10d40f6fd84eb1c70c6dfe37e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Porady: tworzenie list okien MDI za pomocą elementu MenuStrip (Formularze systemu Windows)
Interfejs dokumentu wielokrotnego (MDI) umożliwia tworzenie aplikacji, które można otworzyć kilka dokumentów, w tym samym czasie i kopiowania i wklejania zawartości z jednego dokumentu do drugiego.  
  
 Ta procedura przedstawia sposób tworzenia listy wszystkich formularzy podrzędnych aktywne menu okna nadrzędnego.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>Aby tworzenie list okien MDI w formancie MenuStrip  
  
1.  Tworzenie formularza i ustawić jej <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`.  
  
2.  Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza.  
  
3.  Dodaj dwa elementy menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> i ustawić ich <xref:System.Windows.Forms.Control.Text%2A> właściwości `&File` i `&Window`.  
  
4.  Dodawanie elementu podmenu `&File` element menu i zestaw jej <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Open`.  
  
5.  Ustaw <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6.  Dodawanie formularza do projektu i Dodaj formant ma do niego, takie jak inny <xref:System.Windows.Forms.MenuStrip>.  
  
7.  Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenie `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
8.  W ramach programu obsługi zdarzeń Wstawianie kodu podobne do następujących czynności, aby utworzyć i wyświetlić nowe wystąpienia klasy `Form2` jako elementy podrzędne MDI `Form1`.  
  
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
  
9. Umieść kod podobnie do następującej w `&New` <xref:System.Windows.Forms.ToolStripMenuItem> można zarejestrować obsługi zdarzeń.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Dwa <xref:System.Windows.Forms.Form> formantów `Form1` i `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form1` o nazwie `menuStrip1`, a <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form2` o nazwie `menuStrip2`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Instrukcje: tworzenie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [MenuStrip, kontrolka](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
