---
title: 'Instrukcje: ustawianie rozmiaru paneli paska stanu'
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
ms.openlocfilehash: efd3074aaf018e7226c484061cbacb2eac0be820
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311906"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>Instrukcje: ustawianie rozmiaru paneli paska stanu
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripStatusLabel> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.StatusBar> kontrolować; jednak <xref:System.Windows.Forms.StatusBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.  
  
 Każde wystąpienie <xref:System.Windows.Forms.StatusBarPanel> klas w obrębie [StatusBar, kontrolka](statusbar-control-windows-forms.md) kontrolka ma szereg właściwości dynamicznych, które określają jej szerokość i zachowanie przy zmianie rozmiaru w czasie wykonywania.  
  
### <a name="to-set-the-size-of-a-panel"></a>Aby ustawić rozmiar panelu  
  
1. W procedurze, należy ustawić <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, i <xref:System.Windows.Forms.StatusBarPanel.Width%2A> właściwości (lub dowolnego podzbioru tam) na pasku stanu paneli przy użyciu jej indeksu przekazany przez <xref:System.Windows.Forms.StatusBar.Panels%2A> właściwość <xref:System.Windows.Forms.StatusBarPanel> kolekcji.  
  
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
- [Przewodnik: Aktualizowanie informacji na pasku stanu w czasie wykonywania](walkthrough-updating-status-bar-information-at-run-time.md)
- [Instrukcje: Określanie, które panelu w formancie StatusBar formularzy Windows został kliknięty](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar, kontrolka — omówienie](statusbar-control-overview-windows-forms.md)
