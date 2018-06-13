---
title: 'Porady: ustawianie rozmiaru paneli paska stanu'
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
ms.openlocfilehash: d708b94d02b4f1c1e2f00101e6e394043a6057ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533783"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>Porady: ustawianie rozmiaru paneli paska stanu
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripStatusLabel> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.StatusBar> kontrolować; jednak <xref:System.Windows.Forms.StatusBar> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.  
  
 Każde wystąpienie <xref:System.Windows.Forms.StatusBarPanel> klas w ramach [formantu StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) formant ma wiele właściwości dynamiczne, które określają jego szerokość, a następnie zmień rozmiar zachowania w czasie wykonywania.  
  
### <a name="to-set-the-size-of-a-panel"></a>Aby określić rozmiar panelu  
  
1.  W procedurze, ustaw <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, i <xref:System.Windows.Forms.StatusBarPanel.Width%2A> właściwości (lub dowolnego podzbioru tam) na pasku stanu paneli przy użyciu jej indeksu przekazywane <xref:System.Windows.Forms.StatusBar.Panels%2A> właściwość <xref:System.Windows.Forms.StatusBarPanel> kolekcji.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Przewodnik: aktualizowanie informacji na pasku stanu w czasie wykonywania](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [Instrukcje: ustalanie, który panel został kliknięty w kontrolce StatusBar formularzy Windows Forms](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [StatusBar, kontrolka — omówienie](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
