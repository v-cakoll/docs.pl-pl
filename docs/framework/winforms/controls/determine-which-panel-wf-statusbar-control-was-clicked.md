---
title: Określ, który panel został kliknięty w kontrolce StatusBar
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
ms.openlocfilehash: 94619f8bd426a42e5dafa0db99880e20d24f9963
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746013"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Porady: ustalanie, który panel został kliknięty w formancie StatusBar formularzy systemu Windows
> [!IMPORTANT]
> Kontrolki <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> zastępują i dodają funkcje do kontrolek <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel>; jednak kontrolki <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję.  
  
 Aby program [StatusBar Formant sterowania](statusbar-control-windows-forms.md) odpowiedzią na kliknięcia przez użytkownika, użyj instrukcji case w zdarzeniu <xref:System.Windows.Forms.StatusBar.PanelClick>. Zdarzenie zawiera argument (argument panelu), który zawiera odwołanie do klikniętej <xref:System.Windows.Forms.StatusBarPanel>. Korzystając z tego odwołania, można określić indeks klikniętego panelu i odpowiednio do programu.  
  
> [!NOTE]
> Upewnij się, że właściwość <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> kontrolki <xref:System.Windows.Forms.StatusBar> jest ustawiona na `true`.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Aby określić, który panel został kliknięty  
  
1. W obsłudze zdarzeń <xref:System.Windows.Forms.StatusBar.PanelClick> Użyj `Select Case` (w Visual Basic) lub `switch case` (wizualizacji C# lub wizualizacji C++), aby określić, który panel został kliknięty, sprawdzając indeks klikniętego panelu w argumentach zdarzeń.  
  
     Poniższy przykład kodu wymaga obecności, w formularzu, kontrolki <xref:System.Windows.Forms.StatusBar>, `StatusBar1`i dwóch <xref:System.Windows.Forms.StatusBarPanel> obiektów, `StatusBarPanel1` i `StatusBarPanel2`.  
  
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
  
     (Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Instrukcje: ustawianie rozmiaru paneli paska stanu](how-to-set-the-size-of-status-bar-panels.md)
- [Przewodnik: aktualizowanie informacji na pasku stanu w czasie wykonywania](walkthrough-updating-status-bar-information-at-run-time.md)
- [StatusBar, kontrolka — omówienie](statusbar-control-overview-windows-forms.md)
