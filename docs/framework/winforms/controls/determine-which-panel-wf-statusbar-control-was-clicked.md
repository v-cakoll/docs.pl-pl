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
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="31925-102">Porady: ustalanie, który panel został kliknięty w formancie StatusBar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="31925-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
> <span data-ttu-id="31925-103">I <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> elementów sterujących zastąpić <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> dodać funkcje do i formantów; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> formanty są zachowywane zarówno dla zgodności z powrotem i wykorzystania w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="31925-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="31925-104">Aby zaprogramować formant [StatusBar Control](statusbar-control-windows-forms.md) w celu reagowania <xref:System.Windows.Forms.StatusBar.PanelClick> na kliknięcia użytkownika, użyj case statement w ramach zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="31925-104">To program the [StatusBar Control](statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="31925-105">Zdarzenie zawiera argument (argument panelu), który zawiera odwołanie <xref:System.Windows.Forms.StatusBarPanel>do kliknięty .</span><span class="sxs-lookup"><span data-stu-id="31925-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="31925-106">Za pomocą tego odwołania można określić indeks kliknięty panel i odpowiednio zaprogramować.</span><span class="sxs-lookup"><span data-stu-id="31925-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31925-107">Upewnij się, że właściwość <xref:System.Windows.Forms.StatusBar> formantu jest ustawiona <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="31925-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="31925-108">Aby określić, który panel został kliknięty</span><span class="sxs-lookup"><span data-stu-id="31925-108">To determine which panel was clicked</span></span>  
  
1. <span data-ttu-id="31925-109">W <xref:System.Windows.Forms.StatusBar.PanelClick> programie obsługi zdarzeń `Select Case` użyj instrukcji (w języku Visual Basic) lub `switch case` (Visual C# lub Visual C++), aby określić, który panel został kliknięty, sprawdzając indeks kliknięty panel w argumentach zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="31925-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or Visual C++) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="31925-110">Poniższy przykład kodu wymaga obecności, w <xref:System.Windows.Forms.StatusBar> formularzu, `StatusBar1`formantu i dwóch <xref:System.Windows.Forms.StatusBarPanel> obiektów oraz `StatusBarPanel1` `StatusBarPanel2`.</span><span class="sxs-lookup"><span data-stu-id="31925-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
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
  
     <span data-ttu-id="31925-111">(Visual C#, Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="31925-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="31925-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31925-112">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="31925-113">Porady: ustawianie rozmiaru paneli paska stanu</span><span class="sxs-lookup"><span data-stu-id="31925-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="31925-114">Przewodnik: aktualizowanie informacji na pasku stanu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="31925-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="31925-115">StatusBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="31925-115">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
