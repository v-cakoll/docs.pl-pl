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
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Instrukcje: odpowiadanie na kliknięcia elementu CheckBox formularzy systemu Windows
Za każdym razem <xref:System.Windows.Forms.Control.Click> , gdy użytkownik <xref:System.Windows.Forms.CheckBox> kliknie kontrolkę Windows Forms, wystąpi zdarzenie. Możesz zaprogramować aplikację, aby wykonać jakąś akcję w zależności od stanu pola wyboru.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Aby odpowiedzieć na kliknięcia pola wyboru  
  
1. W programie obsługi <xref:System.Windows.Forms.CheckBox.Checked%2A>zdarzeńUżyj właściwości, aby określić stan kontrolki i wykonać wszelkie niezbędne działania. <xref:System.Windows.Forms.Control.Click>  
  
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
    > Jeśli użytkownik spróbuje dwukrotnie kliknąć <xref:System.Windows.Forms.CheckBox> kontrolkę, każde kliknięcie zostanie przetworzone oddzielnie. oznacza to <xref:System.Windows.Forms.CheckBox> , że formant nie obsługuje zdarzenia podwójnego kliknięcia.  
  
    > [!NOTE]
    > Gdy właściwość jest `true` (domyślnie), <xref:System.Windows.Forms.CheckBox> jest automatycznie wybierana lub czyszczona po kliknięciu. <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> W przeciwnym razie należy ręcznie ustawić <xref:System.Windows.Forms.CheckBox.Checked%2A> Właściwość <xref:System.Windows.Forms.Control.Click> po wystąpieniu zdarzenia.  
  
     Można również użyć <xref:System.Windows.Forms.CheckBox> kontrolki do określenia sposobu działania.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Aby określić kurs akcji po kliknięciu pola wyboru  
  
1. Użyj instrukcji case, aby wysłać zapytanie do wartości <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości w celu określenia sposobu działania. Gdy właściwość jest ustawiona na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwość może zwracać trzy możliwe wartości, które reprezentują zaznaczone pole, pole niezaznaczone lub trzeci nieokreślony stan, w którym pole jest wyświetlane z wygaszoną <xref:System.Windows.Forms.CheckBox.ThreeState%2A> wygląd wskazujący, że opcja jest niedostępna.  
  
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
    > `true` <xref:System.Windows.Forms.CheckBox.Checked%2A> <xref:System.Windows.Forms.CheckState.Checked> Gdy właściwość jest ustawiona na, właściwość zwraca `true` dla obu i <xref:System.Windows.Forms.CheckState.Indeterminate>. <xref:System.Windows.Forms.CheckBox.ThreeState%2A>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox, kontrolka — omówienie](checkbox-control-overview-windows-forms.md)
- [Instrukcje: Ustawianie opcji za pomocą kontrolek CheckBox Windows Forms](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox, kontrolka](checkbox-control-windows-forms.md)
