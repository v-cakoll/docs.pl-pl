---
title: 'Porady: usuwanie elementu ToolStripMenuItem z menu rozwijanego MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 3198195cf0991734826508aa65818505bf2038c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735850"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>Porady: usuwanie elementu ToolStripMenuItem z menu rozwijanego MDI (Formularze systemu Windows)
W niektórych aplikacjach rodzaj okna podrzędnego interfejsu wielu dokumentów (MDI) może różnić się od okna nadrzędnego MDI. Na przykład element nadrzędny MDI może być arkuszem kalkulacyjnym, a obiekt podrzędny MDI może być wykresem. W takim przypadku należy zaktualizować zawartość menu elementu nadrzędnego MDI z zawartością menu elementu podrzędnego MDI, ponieważ aktywowane są okna podrzędne MDI różnych rodzajów.  
  
 Poniższa procedura używa właściwości <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>, aby usunąć element menu z rozwijanej części menu nadrzędnego MDI. Zamknięcie podrzędnego okna MDI przywraca usunięte elementy menu do menu nadrzędnego MDI.  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>Aby usunąć element MenuStrip z menu rozwijanego MDI  
  
1. Utwórz formularz i ustaw jego właściwość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.  
  
2. Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> <xref:System.Windows.Forms.MenuStrip> na `true`.  
  
3. Dodaj element menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> `Form1`i ustaw jego właściwość <xref:System.Windows.Forms.Control.Text%2A> na `&File`.  
  
4. Dodaj trzy elementy podmenu do elementu menu `&File` i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości na `&Open`, `&Import from`i `E&xit`.  
  
5. Dodaj dwa elementy podmenu do elementu podmenu `&Import from` i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości na `&Word` i `&Excel`.  
  
6. Dodaj formularz do projektu, Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> `Form2`<xref:System.Windows.Forms.MenuStrip> na `true`.  
  
7. Dodaj element menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> `Form2`i ustaw jego właściwość <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&File`.  
  
8. Dodaj element podmenu `&Import from` do menu `&File` `Form2`, a następnie Dodaj element podmenu `&Word` do menu `&File`.  
  
9. Ustaw właściwości <xref:System.Windows.Forms.MergeAction> i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> elementów menu `Form2`, jak pokazano w poniższej tabeli.  
  
    |Element menu Form2|MergeAction wartość|MergeIndex wartość|  
    |---------------------|-----------------------|----------------------|  
    |Plik|MatchOnly|-1|  
    |Importuj z|MatchOnly|-1|  
    |Word|Usuń|-1|  
  
10. W `Form1`Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Click> `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. W ramach procedury obsługi zdarzeń Wstaw kod podobny do następującego przykładu kodu, aby utworzyć i wyświetlić nowe wystąpienia `Form2` jako elementy podrzędne MDI `Form1`:  
  
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
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Dwie <xref:System.Windows.Forms.Form> kontrolki o nazwach `Form1` i `Form2`.  
  
- Kontrolka <xref:System.Windows.Forms.MenuStrip> na `Form1` o nazwie `menuStrip1`oraz kontrolce <xref:System.Windows.Forms.MenuStrip> na `Form2` o nazwie `menuStrip2`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie formularzy nadrzędnych MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Instrukcje: tworzenie formularzy podrzędnych MDI](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
