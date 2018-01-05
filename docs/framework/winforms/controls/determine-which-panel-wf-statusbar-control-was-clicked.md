---
title: "Porady: ustalanie, który panel został kliknięty w formancie StatusBar formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a91ad8c28bae7d517a9e13937d5de340b1b6a605
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Porady: ustalanie, który panel został kliknięty w formancie StatusBar formularzy systemu Windows
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> formanty Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> steruje; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> formanty są zachowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli możesz Wybierz.  
  
 Program [formantu StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) kontroli odpowiadanie na kliknięcia użytkownika, należy użyć instrukcji case w <xref:System.Windows.Forms.StatusBar.PanelClick> zdarzeń. Zdarzenie zawiera argumentu (argument panelu), który zawiera odwołanie do klikniętej <xref:System.Windows.Forms.StatusBarPanel>. Za pomocą tego odwołania, można określić indeksu kliknięty panel i odpowiednio programu.  
  
> [!NOTE]
>  Upewnij się, że <xref:System.Windows.Forms.StatusBar> formantu <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwość jest ustawiona na `true`.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Aby ustalić, który panel został kliknięty  
  
1.  W <xref:System.Windows.Forms.StatusBar.PanelClick> program obsługi zdarzeń, użyj `Select Case` (w [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) lub `switch case` ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] lub [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) instrukcji, aby ustalić, który panel został kliknięty, sprawdzając indeks kliknięty panel w argumentach zdarzenia.  
  
     Poniższy przykład kodu wymaga obecności, w formularzu z <xref:System.Windows.Forms.StatusBar> kontroli, `StatusBar1`i dwa <xref:System.Windows.Forms.StatusBarPanel> obiektów, `StatusBarPanel1` i `StatusBarPanel2`.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Instrukcje: ustawianie rozmiaru paneli paska stanu](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [Przewodnik: aktualizowanie informacji na pasku stanu w czasie wykonywania](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [StatusBar, kontrolka — omówienie](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
