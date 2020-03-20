---
title: Reagowanie na kliknięcia kontrolki CheckBox
ms.date: 03/30/2017
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
ms.openlocfilehash: 6ff20c443519446d3804b325924cb3c5cbedea97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141929"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="5b2d0-102">Porady: odpowiadanie na kliknięcia elementu CheckBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5b2d0-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="5b2d0-103">Za każdym razem, gdy <xref:System.Windows.Forms.CheckBox> użytkownik kliknie formant Windows Forms, <xref:System.Windows.Forms.Control.Click> zdarzenie występuje.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="5b2d0-104">Aplikację można zaprogramować w celu wykonania pewnych akcji w zależności od stanu pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="5b2d0-105">Aby odpowiedzieć na kliknięcia pola wyboru</span><span class="sxs-lookup"><span data-stu-id="5b2d0-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="5b2d0-106">W <xref:System.Windows.Forms.Control.Click> programie obsługi zdarzeń <xref:System.Windows.Forms.CheckBox.Checked%2A> użyj właściwości, aby określić stan formantu i wykonać wszelkie niezbędne działania.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="5b2d0-107">Jeśli użytkownik spróbuje dwukrotnie <xref:System.Windows.Forms.CheckBox> kliknąć formant, każde kliknięcie zostanie przetworzone oddzielnie; oznacza to, <xref:System.Windows.Forms.CheckBox> że formant nie obsługuje zdarzenia dwukrotnego kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5b2d0-108">Gdy <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> właściwość `true` jest (domyślnie), <xref:System.Windows.Forms.CheckBox> jest automatycznie zaznaczone lub wyczyszczone po kliknięciu.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="5b2d0-109">W przeciwnym razie należy <xref:System.Windows.Forms.CheckBox.Checked%2A> ręcznie ustawić <xref:System.Windows.Forms.Control.Click> właściwość, gdy wystąpi zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="5b2d0-110">Można również użyć <xref:System.Windows.Forms.CheckBox> formantu, aby określić przebieg działania.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="5b2d0-111">Aby określić kierunek działania po kliknięciu pola wyboru</span><span class="sxs-lookup"><span data-stu-id="5b2d0-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="5b2d0-112">Użyj case instrukcji do kwerendy <xref:System.Windows.Forms.CheckBox.CheckState%2A> wartość właściwości, aby określić przebieg akcji.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="5b2d0-113">Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest `true`ustawiona na , <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwość może zwrócić trzy możliwe wartości, które reprezentują pole jest zaznaczone, pole jest niezaznaczone lub trzeci nieokreślony stan, w którym pole jest wyświetlane z wygaszonym wyglądem, aby wskazać, że opcja jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="5b2d0-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="5b2d0-114">Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest `true`ustawiona <xref:System.Windows.Forms.CheckBox.Checked%2A> `true` na <xref:System.Windows.Forms.CheckState.Checked> , <xref:System.Windows.Forms.CheckState.Indeterminate>właściwość zwraca dla obu i .</span><span class="sxs-lookup"><span data-stu-id="5b2d0-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b2d0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b2d0-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="5b2d0-116">CheckBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="5b2d0-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="5b2d0-117">Instrukcje: ustawianie opcji za pomocą kontrolek CheckBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5b2d0-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="5b2d0-118">Sterowanie polem wyboru</span><span class="sxs-lookup"><span data-stu-id="5b2d0-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
