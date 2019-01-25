---
title: 'Instrukcje: Ustawianie rozmiaru paneli paska stanu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- StatusBar control [Windows Forms], panel size
- status bars [Windows Forms], setting panel size
- panels [Windows Forms], setting size in status bars
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
ms.openlocfilehash: be1f216af61c1e7b77e84c584dc9d965a97c56b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539665"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>Instrukcje: Ustawianie rozmiaru paneli paska stanu
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripStatusLabel> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.StatusBar> kontrolować; jednak <xref:System.Windows.Forms.StatusBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.  
  
 Każde wystąpienie <xref:System.Windows.Forms.StatusBarPanel> klas w obrębie [StatusBar, kontrolka](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) kontrolka ma szereg właściwości dynamicznych, które określają jej szerokość i zachowanie przy zmianie rozmiaru w czasie wykonywania.  
  
### <a name="to-set-the-size-of-a-panel"></a>Aby ustawić rozmiar panelu  
  
1.  W procedurze, należy ustawić <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, i <xref:System.Windows.Forms.StatusBarPanel.Width%2A> właściwości (lub dowolnego podzbioru tam) na pasku stanu paneli przy użyciu jej indeksu przekazany przez <xref:System.Windows.Forms.StatusBar.Panels%2A> właściwość <xref:System.Windows.Forms.StatusBarPanel> kolekcji.  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Przewodnik: Aktualizowanie informacji na pasku stanu w czasie wykonywania](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)
- [Instrukcje: Określanie, które panelu w formancie StatusBar formularzy Windows został kliknięty](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar, kontrolka — omówienie](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
