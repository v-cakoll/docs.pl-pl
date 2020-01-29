---
title: 'Porady: wstawianie elementu MenuStrip do menu rozwijanego MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 6e189dd159c48b5779679d0563fab85e9b848992
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736406"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a>Porady: wstawianie elementu MenuStrip do menu rozwijanego MDI (Formularze systemu Windows)
W niektórych aplikacjach rodzaj okna podrzędnego interfejsu wielu dokumentów (MDI) może różnić się od okna nadrzędnego MDI. Na przykład element nadrzędny MDI może być arkuszem kalkulacyjnym, a obiekt podrzędny MDI może być wykresem. W takim przypadku należy zaktualizować zawartość menu elementu nadrzędnego MDI z zawartością menu elementu podrzędnego MDI, ponieważ aktywowane są okna podrzędne MDI różnych rodzajów.  
  
 Poniższa procedura używa właściwości <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>, aby wstawić grupę elementów menu z menu podrzędnego MDI do części listy rozwijanej menu nadrzędnego MDI. Zamknięcie okna podrzędnego MDI usuwa wstawione elementy menu z elementu nadrzędnego MDI.  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a>Aby wstawić element MenuStrip do menu rozwijanego MDI  
  
1. Utwórz formularz i ustaw jego właściwość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.  
  
2. Dodaj <xref:System.Windows.Forms.MenuStrip> do `Form1` i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> <xref:System.Windows.Forms.MenuStrip> na `true`.  
  
3. Dodaj element menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> `Form1`i ustaw jego właściwość <xref:System.Windows.Forms.Control.Text%2A> na `&File`.  
  
4. Dodaj trzy elementy podmenu do elementu menu `&File` i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości na `&Open`, `&Import from`i `E&xit`.  
  
5. Dodaj dwa elementy podmenu do elementu podmenu `&Import from` i ustaw ich <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości na `&Word` i `&Excel`.  
  
6. Dodaj formularz do projektu, Dodaj <xref:System.Windows.Forms.MenuStrip> do formularza i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> `Form2`<xref:System.Windows.Forms.MenuStrip> na `true`.  
  
7. Dodaj element menu najwyższego poziomu do <xref:System.Windows.Forms.MenuStrip> `Form2`i ustaw jego właściwość <xref:System.Windows.Forms.ToolStripItem.Text%2A> na `&File`.  
  
8. Dodaj elementy podmenu do `&File` menu `Form2` w następującej kolejności: <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`i innych <xref:System.Windows.Forms.ToolStripSeparator>.  
  
9. Ustaw właściwości <xref:System.Windows.Forms.MergeAction> i <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> elementów menu `Form2`, jak pokazano w poniższej tabeli.  
  
    |Element menu Form2|MergeAction wartość|MergeIndex wartość|  
    |---------------------|-----------------------|----------------------|  
    |Plik|MatchOnly|-1|  
    |Separator|Wstaw|2|  
    |Zapisz|Wstaw|3|  
    |Zapisz i Zamknij|Wstaw|4|  
    |Separator|Wstaw|5|  
  
10. Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.ToolStripMenuItem>`&Open`.  
  
11. W ramach procedury obsługi zdarzeń Wstaw kod podobny do następującego przykładu kodu, aby utworzyć i wyświetlić nowe wystąpienia `Form2` jako elementy podrzędne MDI `Form1`.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie formularzy nadrzędnych MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Instrukcje: tworzenie formularzy podrzędnych MDI](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
