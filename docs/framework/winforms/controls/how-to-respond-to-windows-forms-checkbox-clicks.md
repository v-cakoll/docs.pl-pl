---
title: Reagowanie na kliknięcia kontrolki CheckBox
description: Dowiedz się, jak programować Windows Forms aplikację, aby wykonać jakąś akcję w zależności od stanu pola wyboru.
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
ms.openlocfilehash: 58944bc421f990343b6c58484aaab3d79c8bda5e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174500"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="ed90c-103">Porady: odpowiadanie na kliknięcia elementu CheckBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ed90c-103">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="ed90c-104">Za każdym razem, gdy użytkownik kliknie <xref:System.Windows.Forms.CheckBox> kontrolkę Windows Forms, <xref:System.Windows.Forms.Control.Click> wystąpi zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="ed90c-104">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="ed90c-105">Możesz zaprogramować aplikację, aby wykonać jakąś akcję w zależności od stanu pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="ed90c-105">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="ed90c-106">Aby odpowiedzieć na kliknięcia pola wyboru</span><span class="sxs-lookup"><span data-stu-id="ed90c-106">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="ed90c-107">W programie <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń Użyj właściwości, <xref:System.Windows.Forms.CheckBox.Checked%2A> Aby określić stan kontrolki i wykonać wszelkie niezbędne działania.</span><span class="sxs-lookup"><span data-stu-id="ed90c-107">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="ed90c-108">Jeśli użytkownik spróbuje dwukrotnie kliknąć <xref:System.Windows.Forms.CheckBox> kontrolkę, każde kliknięcie zostanie przetworzone oddzielnie. oznacza to, że formant nie <xref:System.Windows.Forms.CheckBox> obsługuje zdarzenia podwójnego kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="ed90c-108">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ed90c-109">Gdy <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> Właściwość jest `true` (domyślnie), <xref:System.Windows.Forms.CheckBox> jest automatycznie wybierana lub czyszczona po kliknięciu.</span><span class="sxs-lookup"><span data-stu-id="ed90c-109">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="ed90c-110">W przeciwnym razie należy ręcznie ustawić <xref:System.Windows.Forms.CheckBox.Checked%2A> Właściwość po <xref:System.Windows.Forms.Control.Click> wystąpieniu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ed90c-110">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="ed90c-111">Można również użyć <xref:System.Windows.Forms.CheckBox> kontrolki do określenia sposobu działania.</span><span class="sxs-lookup"><span data-stu-id="ed90c-111">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="ed90c-112">Aby określić kurs akcji po kliknięciu pola wyboru</span><span class="sxs-lookup"><span data-stu-id="ed90c-112">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="ed90c-113">Użyj instrukcji case, aby wysłać zapytanie do wartości <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości w celu określenia sposobu działania.</span><span class="sxs-lookup"><span data-stu-id="ed90c-113">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="ed90c-114">Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> Właściwość jest ustawiona na `true` , <xref:System.Windows.Forms.CheckBox.CheckState%2A> Właściwość może zwracać trzy możliwe wartości, które reprezentują zaznaczone pole, pole jest niezaznaczone lub trzeci nieokreślony stan, w którym pole jest wyświetlane z wygaszonym wyglądem, aby wskazać, że opcja jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="ed90c-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="ed90c-115">Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> Właściwość jest ustawiona na `true` , <xref:System.Windows.Forms.CheckBox.Checked%2A> Właściwość zwraca `true` dla obu <xref:System.Windows.Forms.CheckState.Checked> i <xref:System.Windows.Forms.CheckState.Indeterminate> .</span><span class="sxs-lookup"><span data-stu-id="ed90c-115">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed90c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed90c-116">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="ed90c-117">CheckBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="ed90c-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="ed90c-118">Instrukcje: ustawianie opcji za pomocą kontrolek CheckBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ed90c-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="ed90c-119">CheckBox — formant</span><span class="sxs-lookup"><span data-stu-id="ed90c-119">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
