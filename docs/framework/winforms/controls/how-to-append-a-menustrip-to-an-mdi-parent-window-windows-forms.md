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
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Porady: dołączanie formantu MenuStrip do nadrzędnego okna MDI (Formularze systemu Windows)
W niektórych aplikacjach rodzaj okno podrzędne interfejsu wielu dokumentów (MDI) może się różnić od nadrzędnego okna MDI. Na przykład element nadrzędny MDI może być arkusza kalkulacyjnego i podrzędnych MDI może być wykresu. W takim przypadku chcesz zaktualizować zawartość element nadrzędny MDI menu z zawartością menu podrzędnego MDI jako okien podrzędnych MDI różnego rodzaju są uaktywnione.  
  
 W poniższej procedurze użyto <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości do dołączenia do menu nadrzędnego MDI menu podrzędnego MDI. Zamknięcie okna podrzędnego MDI Usuwa menu dołączany element nadrzędny MDI.  
  
 Zobacz też [aplikacje interfejsu wielu dokumentów (MDI)](http://msdn.microsoft.com/library/xyhh2e7e\(v=vs.110\)).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Aby dołączyć elementu menu. element nadrzędny MDI  
  
1.  Tworzenie formularza i ustawić jej <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`.  
  
2.  Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `true`.  
  
3.  Ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość `Form1` <xref:System.Windows.Forms.MenuStrip> do `false`.  
  
4.  Dodaj element menu najwyższego poziomu do `Form1` <xref:System.Windows.Forms.MenuStrip> i ustawić jej <xref:System.Windows.Forms.Control.Text%2A> właściwości `&File`.  
  
5.  Dodawanie elementu podmenu `&File` element menu i zestaw jej <xref:System.Windows.Forms.Form.Text%2A> właściwości `&Open`.  
  
6.  Dodawanie formularza do projektu, należy dodać <xref:System.Windows.Forms.MenuStrip> formularza i zestawu <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość `Form2` <xref:System.Windows.Forms.MenuStrip> do `true`.  
  
7.  Dodaj element menu najwyższego poziomu do `Form2` <xref:System.Windows.Forms.MenuStrip> i ustawić jej <xref:System.Windows.Forms.Form.Text%2A> właściwości `&Special`.  
  
8.  Dodaj dwa elementy podmenu do `&Special` element menu i zestaw ich <xref:System.Windows.Forms.Form.Text%2A> właściwości `Command&1` i `Command&2`odpowiednio.  
  
9. Ustaw <xref:System.Windows.Forms.MergeAction> właściwość `&Special`, `Command&1`, i `Command&2` elementy menu <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenie `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. W ramach programu obsługi zdarzeń, Wstaw kod podobny do poniższego przykładu kodu można tworzyć i wyświetlać nowych wystąpień `Form2` jako elementy podrzędne MDI `Form1`.  
  
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
  
12. Umieść kod podobny do poniższego przykładu kodu w `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> można zarejestrować obsługi zdarzeń.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Dwa <xref:System.Windows.Forms.Form> formantów `Form1` i `Form2`.  
  
-   A <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form1` o nazwie `menuStrip1`, a <xref:System.Windows.Forms.MenuStrip> kontrolować na `Form2` o nazwie `menuStrip2`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.
