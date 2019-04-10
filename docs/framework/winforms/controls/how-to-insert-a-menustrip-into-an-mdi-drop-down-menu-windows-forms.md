---
title: 'Instrukcje: Wstawianie elementu MenuStrip do Menu rozwijanego MDI (formularze Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 1b41699d8da1c99705f6796105dab6f3ab1d727d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341637"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a>Instrukcje: Wstawianie elementu MenuStrip do Menu rozwijanego MDI (formularze Windows)
W niektórych aplikacjach rodzaj okna podrzędnego interfejsu wielu dokumentów (MDI) może różnić się od nadrzędnego okna MDI. Na przykład element nadrzędny MDI może być arkusza kalkulacyjnego i elementu podrzędnego MDI może być wykres. W takim przypadku chcesz zaktualizować zawartość menu nadrzędny MDI zawartość elementu podrzędnego MDI menu, zgodnie z oknami podrzędnymi MDI różnego rodzaju zostaną aktywowane.  
  
 W poniższej procedurze użyto <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości można wstawić grupy elementów menu w menu podrzędne MDI do części rozwijanego menu nadrzędnego MDI. Zamyka okno podrzędne MDI usuwa elementy menu wstawiony z nadrzędnego MDI.  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a>Aby Wstawianie elementu MenuStrip do menu rozwijanego MDI  
  
1. Tworzenie formularza i ustaw jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwość `true`.  
  
2. Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość <xref:System.Windows.Forms.MenuStrip> do `true`.  
  
3. Dodawanie pozycji menu najwyższego poziomu do `Form1`<xref:System.Windows.Forms.MenuStrip> i ustaw jego <xref:System.Windows.Forms.Control.Text%2A> właściwość `&File`.  
  
4. Dodaj trzy elementy podmenu do `&File` element menu i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Open`, `&Import from`, i `E&xit`.  
  
5. Dodaj dwa elementy podmenu do `&Import from` elementu podmenu i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości `&Word` i `&Excel`.  
  
6. Dodawanie formularza do projektu, Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza, a następnie ustaw <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwość `Form2`<xref:System.Windows.Forms.MenuStrip> do `true`.  
  
7. Dodawanie pozycji menu najwyższego poziomu do `Form2`<xref:System.Windows.Forms.MenuStrip> i ustaw jego <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwość `&File`.  
  
8. Dodawanie podmenu do `&File` menu `Form2` w następującej kolejności: <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`, a inny <xref:System.Windows.Forms.ToolStripSeparator>.  
  
9. Ustaw <xref:System.Windows.Forms.MergeAction> i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwości `Form2` elementy menu, jak pokazano w poniższej tabeli.  
  
    |Element menu formularz2|Wartość MergeAction|Wartość MergeIndex|  
    |---------------------|-----------------------|----------------------|  
    |Plik|MatchOnly|-1|  
    |Separator|Insert|2|  
    |Zapisanie|Insert|3|  
    |Zapisz i zamknij|Insert|4|  
    |Separator|Insert|5|  
  
10. Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. W ramach programu obsługi zdarzeń, Wstaw kod, podobnie jak poniższy przykład kodu, aby utworzyć i wyświetlić nowe wystąpienia `Form2` jako elementy podrzędne MDI `Form1`.  
  
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
  
12. Umieść kod podobny do poniższego przykładu kodu w `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> zarejestrować program obsługi zdarzeń.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie formularzy nadrzędnych MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Instrukcje: Tworzenie formularzy podrzędnych MDI](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
