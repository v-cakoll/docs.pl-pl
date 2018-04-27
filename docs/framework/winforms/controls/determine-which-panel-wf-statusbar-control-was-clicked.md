---
title: 'Porady: ustalanie, który panel został kliknięty w formancie StatusBar formularzy systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
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
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 35dc392ed95a5dbe8182b1adbd05affea55d0baa
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="494f3-102">Porady: ustalanie, który panel został kliknięty w formancie StatusBar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="494f3-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="494f3-103"><xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> formanty Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> steruje; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> formanty są zachowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli możesz Wybierz.</span><span class="sxs-lookup"><span data-stu-id="494f3-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="494f3-104">Program [formantu StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) kontroli odpowiadanie na kliknięcia użytkownika, należy użyć instrukcji case w <xref:System.Windows.Forms.StatusBar.PanelClick> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="494f3-104">To program the [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="494f3-105">Zdarzenie zawiera argumentu (argument panelu), który zawiera odwołanie do klikniętej <xref:System.Windows.Forms.StatusBarPanel>.</span><span class="sxs-lookup"><span data-stu-id="494f3-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="494f3-106">Za pomocą tego odwołania, można określić indeksu kliknięty panel i odpowiednio programu.</span><span class="sxs-lookup"><span data-stu-id="494f3-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="494f3-107">Upewnij się, że <xref:System.Windows.Forms.StatusBar> formantu <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="494f3-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="494f3-108">Aby ustalić, który panel został kliknięty</span><span class="sxs-lookup"><span data-stu-id="494f3-108">To determine which panel was clicked</span></span>  
  
1.  <span data-ttu-id="494f3-109">W <xref:System.Windows.Forms.StatusBar.PanelClick> program obsługi zdarzeń, użyj `Select Case` (w języku Visual Basic) lub `switch case` (Visual C# lub [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) instrukcji, aby ustalić, który panel został kliknięty, sprawdzając indeks kliknięty panel w argumentach zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="494f3-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="494f3-110">Poniższy przykład kodu wymaga obecności, w formularzu z <xref:System.Windows.Forms.StatusBar> kontroli, `StatusBar1`i dwa <xref:System.Windows.Forms.StatusBarPanel> obiektów, `StatusBarPanel1` i `StatusBarPanel2`.</span><span class="sxs-lookup"><span data-stu-id="494f3-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
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
  
     <span data-ttu-id="494f3-111">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="494f3-111">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="494f3-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="494f3-112">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="494f3-113">Instrukcje: ustawianie rozmiaru paneli paska stanu</span><span class="sxs-lookup"><span data-stu-id="494f3-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [<span data-ttu-id="494f3-114">Przewodnik: aktualizowanie informacji na pasku stanu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="494f3-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [<span data-ttu-id="494f3-115">StatusBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="494f3-115">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
