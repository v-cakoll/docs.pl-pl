---
title: "Porady: odpowiadanie na kliknięcia elementu CheckBox formularzy systemu Windows"
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
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f15adb84f92c9434d6835e80f08bf1d9bd500ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="85c4f-102">Porady: odpowiadanie na kliknięcia elementu CheckBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="85c4f-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="85c4f-103">Zawsze, gdy użytkownik kliknie formularzy systemu Windows <xref:System.Windows.Forms.CheckBox> kontroli, <xref:System.Windows.Forms.Control.Click> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="85c4f-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="85c4f-104">Można programowanie aplikacji w celu wykonania akcji w zależności od stanu pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="85c4f-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="85c4f-105">Na odpowiadanie na kliknięcia elementu CheckBox</span><span class="sxs-lookup"><span data-stu-id="85c4f-105">To respond to CheckBox clicks</span></span>  
  
1.  <span data-ttu-id="85c4f-106">W <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń, użyj <xref:System.Windows.Forms.CheckBox.Checked%2A> właściwości, aby określić stan formantu i wykonać wszelkie niezbędne działania.</span><span class="sxs-lookup"><span data-stu-id="85c4f-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the   
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the   
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="85c4f-107">Jeśli użytkownik próbuje kliknij dwukrotnie <xref:System.Windows.Forms.CheckBox> formantu, kliknij każdy będą przetwarzane oddzielnie; która jest, <xref:System.Windows.Forms.CheckBox> formant nie obsługuje kliknij dwukrotnie zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="85c4f-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85c4f-108">Gdy <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> właściwość jest `true` (ustawienie domyślne), <xref:System.Windows.Forms.CheckBox> jest automatycznie wybrana lub wyczyszczona po kliknięciu.</span><span class="sxs-lookup"><span data-stu-id="85c4f-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="85c4f-109">W przeciwnym razie należy ręcznie ustawić <xref:System.Windows.Forms.CheckBox.Checked%2A> właściwości podczas <xref:System.Windows.Forms.Control.Click> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="85c4f-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="85c4f-110">Można również użyć <xref:System.Windows.Forms.CheckBox> kontroli w celu ustalenia sposobu działania.</span><span class="sxs-lookup"><span data-stu-id="85c4f-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="85c4f-111">Aby określić plan działania, gdy pole wyboru zostanie kliknięty</span><span class="sxs-lookup"><span data-stu-id="85c4f-111">To determine a course of action when a check box is clicked</span></span>  
  
1.  <span data-ttu-id="85c4f-112">Użyj instrukcji case się zapytanie o wartość <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości w celu określenia sposobu działania.</span><span class="sxs-lookup"><span data-stu-id="85c4f-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="85c4f-113">Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości może trzy możliwe wartości zwracane, które reprezentują pole sprawdzany, pole jest niezaznaczone lub innego stanie nieokreślonym w którym zostanie wyświetlone okno z wygaszone wygląd, aby wskazać opcją jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="85c4f-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select   
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="85c4f-114">Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.Forms.CheckBox.Checked%2A> zwraca `true` dla obu <xref:System.Windows.Forms.CheckState.Checked> i <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="85c4f-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c4f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85c4f-115">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="85c4f-116">Informacje o formancie CheckBox</span><span class="sxs-lookup"><span data-stu-id="85c4f-116">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="85c4f-117">Porady: Ustawianie opcji za pomocą formularzy systemu Windows formantów CheckBox</span><span class="sxs-lookup"><span data-stu-id="85c4f-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="85c4f-118">CheckBox — formant</span><span class="sxs-lookup"><span data-stu-id="85c4f-118">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
