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
ms.openlocfilehash: 4ba0f7f02b548a5d9ea1a99605a668f449b3e4a9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923626"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>Instrukcje: ustawianie rozmiaru paneli paska stanu
> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.StatusBar> do <xref:System.Windows.Forms.StatusBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
 Każde wystąpienie <xref:System.Windows.Forms.StatusBarPanel> klasy w kontrolce [kontrolki StatusBar](statusbar-control-windows-forms.md) ma wiele właściwości dynamicznych, które określają jego szerokość i zachowanie w czasie wykonywania.  
  
### <a name="to-set-the-size-of-a-panel"></a>Aby ustawić rozmiar panelu  
  
1. <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>W procedurze należy ustawić właściwości, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, i <xref:System.Windows.Forms.StatusBarPanel.Width%2A> (lub dowolny podzestaw) dla paneli <xref:System.Windows.Forms.StatusBar.Panels%2A> paska stanu przy użyciu <xref:System.Windows.Forms.StatusBarPanel> ich indeksu przekazaną przez właściwość kolekcji.  
  
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
- [Przewodnik: Aktualizowanie informacji o pasku stanu w czasie wykonywania](walkthrough-updating-status-bar-information-at-run-time.md)
- [Instrukcje: Określ, który panel w Windows Forms kontrolce StatusBar został kliknięty](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar, kontrolka — omówienie](statusbar-control-overview-windows-forms.md)
