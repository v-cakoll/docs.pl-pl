---
title: Określanie, który panel w formancie paska stanu został kliknięty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
ms.openlocfilehash: eb3b10d515ba5b62236594e063ca7f060b34b73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182361"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Porady: ustalanie, który panel został kliknięty w formancie StatusBar formularzy systemu Windows
> [!IMPORTANT]
> I <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> elementów sterujących zastąpić <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> dodać funkcje do i formantów; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> formanty są zachowywane zarówno dla zgodności z powrotem i wykorzystania w przyszłości, jeśli wybierzesz.  
  
 Aby zaprogramować formant [StatusBar Control](statusbar-control-windows-forms.md) w celu reagowania <xref:System.Windows.Forms.StatusBar.PanelClick> na kliknięcia użytkownika, użyj case statement w ramach zdarzenia. Zdarzenie zawiera argument (argument panelu), który zawiera odwołanie <xref:System.Windows.Forms.StatusBarPanel>do kliknięty . Za pomocą tego odwołania można określić indeks kliknięty panel i odpowiednio zaprogramować.  
  
> [!NOTE]
> Upewnij się, że właściwość <xref:System.Windows.Forms.StatusBar> formantu jest ustawiona <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `true`.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Aby określić, który panel został kliknięty  
  
1. W <xref:System.Windows.Forms.StatusBar.PanelClick> programie obsługi zdarzeń `Select Case` użyj instrukcji (w języku Visual Basic) lub `switch case` (Visual C# lub Visual C++), aby określić, który panel został kliknięty, sprawdzając indeks kliknięty panel w argumentach zdarzenia.  
  
     Poniższy przykład kodu wymaga obecności, w <xref:System.Windows.Forms.StatusBar> formularzu, `StatusBar1`formantu i dwóch <xref:System.Windows.Forms.StatusBarPanel> obiektów oraz `StatusBarPanel1` `StatusBarPanel2`.  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     (Visual C#, Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.statusBar1.PanelClick += new
       System.Windows.Forms.StatusBarPanelClickEventHandler
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Porady: ustawianie rozmiaru paneli paska stanu](how-to-set-the-size-of-status-bar-panels.md)
- [Przewodnik: aktualizowanie informacji na pasku stanu w czasie wykonywania](walkthrough-updating-status-bar-information-at-run-time.md)
- [StatusBar, kontrolka — omówienie](statusbar-control-overview-windows-forms.md)
