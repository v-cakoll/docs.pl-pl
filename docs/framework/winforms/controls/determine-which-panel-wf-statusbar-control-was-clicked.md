---
title: 'Instrukcje: ustalanie, który panel został kliknięty w kontrolce StatusBar formularzy systemu Windows'
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
ms.openlocfilehash: 6229d8965949641105cd0e9708474c3249d52d1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965723"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Instrukcje: ustalanie, który panel został kliknięty w kontrolce StatusBar formularzy systemu Windows
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> Formanty i zastępują i dodają funkcje do kontrolek i, natomiast kontrolki i są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości. <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> następnie.  
  
 Aby program [StatusBar Formant sterowania](statusbar-control-windows-forms.md) , aby odpowiadał na kliknięcia przez użytkownika, użyj instrukcji case w <xref:System.Windows.Forms.StatusBar.PanelClick> zdarzeniu. Zdarzenie zawiera argument (argument panelu), który zawiera odwołanie do klikniętego <xref:System.Windows.Forms.StatusBarPanel>elementu. Korzystając z tego odwołania, można określić indeks klikniętego panelu i odpowiednio do programu.  
  
> [!NOTE]
> Upewnij się, <xref:System.Windows.Forms.StatusBar> że <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwość kontrolki jest ustawiona `true`na.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Aby określić, który panel został kliknięty  
  
1. `switch case` `Select Case` W procedurze obsługi C# C++zdarzeń Użyj instrukcji (w Visual Basic) lub (wizualizacji lub wizualizacji), aby określić, który panel został kliknięty, sprawdzając indeks klikniętego panelu w argumentach zdarzeń <xref:System.Windows.Forms.StatusBar.PanelClick> .  
  
     Poniższy przykład kodu wymaga obecności, w <xref:System.Windows.Forms.StatusBar> formularzu, `StatusBar1`kontrolki, i dwóch <xref:System.Windows.Forms.StatusBarPanel> obiektów, `StatusBarPanel1` i `StatusBarPanel2`.  
  
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
- [Instrukcje: Ustawianie rozmiaru paneli paska stanu](how-to-set-the-size-of-status-bar-panels.md)
- [Przewodnik: Aktualizowanie informacji o pasku stanu w czasie wykonywania](walkthrough-updating-status-bar-information-at-run-time.md)
- [StatusBar, kontrolka — omówienie](statusbar-control-overview-windows-forms.md)
