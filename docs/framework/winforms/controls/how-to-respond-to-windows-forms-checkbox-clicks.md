---
title: 'Instrukcje: odpowiadanie na kliknięcia elementu CheckBox formularzy systemu Windows'
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
ms.openlocfilehash: 7ff6b2aad9ef0775547af57f11af28839e69637c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914980"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="f2232-102">Instrukcje: odpowiadanie na kliknięcia elementu CheckBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f2232-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="f2232-103">Za każdym razem <xref:System.Windows.Forms.Control.Click> , gdy użytkownik <xref:System.Windows.Forms.CheckBox> kliknie kontrolkę Windows Forms, wystąpi zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="f2232-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="f2232-104">Możesz zaprogramować aplikację, aby wykonać jakąś akcję w zależności od stanu pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="f2232-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="f2232-105">Aby odpowiedzieć na kliknięcia pola wyboru</span><span class="sxs-lookup"><span data-stu-id="f2232-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="f2232-106">W programie obsługi <xref:System.Windows.Forms.CheckBox.Checked%2A>zdarzeńUżyj właściwości, aby określić stan kontrolki i wykonać wszelkie niezbędne działania. <xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="f2232-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="f2232-107">Jeśli użytkownik spróbuje dwukrotnie kliknąć <xref:System.Windows.Forms.CheckBox> kontrolkę, każde kliknięcie zostanie przetworzone oddzielnie. oznacza to <xref:System.Windows.Forms.CheckBox> , że formant nie obsługuje zdarzenia podwójnego kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="f2232-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f2232-108">Gdy właściwość jest `true` (domyślnie), <xref:System.Windows.Forms.CheckBox> jest automatycznie wybierana lub czyszczona po kliknięciu. <xref:System.Windows.Forms.CheckBox.AutoCheck%2A></span><span class="sxs-lookup"><span data-stu-id="f2232-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="f2232-109">W przeciwnym razie należy ręcznie ustawić <xref:System.Windows.Forms.CheckBox.Checked%2A> Właściwość <xref:System.Windows.Forms.Control.Click> po wystąpieniu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f2232-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="f2232-110">Można również użyć <xref:System.Windows.Forms.CheckBox> kontrolki do określenia sposobu działania.</span><span class="sxs-lookup"><span data-stu-id="f2232-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="f2232-111">Aby określić kurs akcji po kliknięciu pola wyboru</span><span class="sxs-lookup"><span data-stu-id="f2232-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="f2232-112">Użyj instrukcji case, aby wysłać zapytanie do wartości <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości w celu określenia sposobu działania.</span><span class="sxs-lookup"><span data-stu-id="f2232-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="f2232-113">Gdy właściwość jest ustawiona na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwość może zwracać trzy możliwe wartości, które reprezentują zaznaczone pole, pole niezaznaczone lub trzeci nieokreślony stan, w którym pole jest wyświetlane z wygaszoną <xref:System.Windows.Forms.CheckBox.ThreeState%2A> wygląd wskazujący, że opcja jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="f2232-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="f2232-114">`true` <xref:System.Windows.Forms.CheckBox.Checked%2A> <xref:System.Windows.Forms.CheckState.Checked> Gdy właściwość jest ustawiona na, właściwość zwraca `true` dla obu i <xref:System.Windows.Forms.CheckState.Indeterminate>. <xref:System.Windows.Forms.CheckBox.ThreeState%2A></span><span class="sxs-lookup"><span data-stu-id="f2232-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2232-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2232-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="f2232-116">CheckBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="f2232-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="f2232-117">Instrukcje: Ustawianie opcji za pomocą kontrolek CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f2232-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="f2232-118">CheckBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="f2232-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
