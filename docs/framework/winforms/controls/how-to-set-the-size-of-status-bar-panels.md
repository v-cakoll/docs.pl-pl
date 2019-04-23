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
# <a name="how-to-set-the-size-of-status-bar-panels"></a><span data-ttu-id="ab1f7-102">Instrukcje: ustawianie rozmiaru paneli paska stanu</span><span class="sxs-lookup"><span data-stu-id="ab1f7-102">How to: Set the Size of Status-Bar Panels</span></span>
> [!NOTE]
>  <span data-ttu-id="ab1f7-103"><xref:System.Windows.Forms.ToolStripStatusLabel> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.StatusBar> kontrolować; jednak <xref:System.Windows.Forms.StatusBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="ab1f7-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="ab1f7-104">Każde wystąpienie <xref:System.Windows.Forms.StatusBarPanel> klas w obrębie [StatusBar, kontrolka](statusbar-control-windows-forms.md) kontrolka ma szereg właściwości dynamicznych, które określają jej szerokość i zachowanie przy zmianie rozmiaru w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ab1f7-104">Each instance of the <xref:System.Windows.Forms.StatusBarPanel> class within a [StatusBar Control](statusbar-control-windows-forms.md) control has a number of dynamic properties that determine its width and resize behavior at run time.</span></span>  
  
### <a name="to-set-the-size-of-a-panel"></a><span data-ttu-id="ab1f7-105">Aby ustawić rozmiar panelu</span><span class="sxs-lookup"><span data-stu-id="ab1f7-105">To set the size of a panel</span></span>  
  
1. <span data-ttu-id="ab1f7-106">W procedurze, należy ustawić <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, i <xref:System.Windows.Forms.StatusBarPanel.Width%2A> właściwości (lub dowolnego podzbioru tam) na pasku stanu paneli przy użyciu jej indeksu przekazany przez <xref:System.Windows.Forms.StatusBar.Panels%2A> właściwość <xref:System.Windows.Forms.StatusBarPanel> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ab1f7-106">In a procedure, set the <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, and <xref:System.Windows.Forms.StatusBarPanel.Width%2A> properties (or any subset therein) for the status-bar panels using their index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property of the <xref:System.Windows.Forms.StatusBarPanel> collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ab1f7-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab1f7-107">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="ab1f7-108">Przewodnik: Aktualizowanie informacji na pasku stanu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="ab1f7-108">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="ab1f7-109">Instrukcje: Określanie, które panelu w formancie StatusBar formularzy Windows został kliknięty</span><span class="sxs-lookup"><span data-stu-id="ab1f7-109">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="ab1f7-110">StatusBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="ab1f7-110">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
