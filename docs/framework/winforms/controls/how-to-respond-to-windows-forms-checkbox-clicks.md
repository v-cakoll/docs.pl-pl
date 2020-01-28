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
ms.openlocfilehash: ba2afb52939a6274978ce725dac19b5622419b99
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735662"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Porady: odpowiadanie na kliknięcia elementu CheckBox formularzy systemu Windows
Za każdym razem, gdy użytkownik kliknie kontrolkę <xref:System.Windows.Forms.CheckBox> Windows Forms, wystąpi zdarzenie <xref:System.Windows.Forms.Control.Click>. Możesz zaprogramować aplikację, aby wykonać jakąś akcję w zależności od stanu pola wyboru.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Aby odpowiedzieć na kliknięcia pola wyboru  
  
1. W obsłudze zdarzeń <xref:System.Windows.Forms.Control.Click> Użyj właściwości <xref:System.Windows.Forms.CheckBox.Checked%2A>, aby określić stan kontrolki i wykonać wszelkie niezbędne działania.  
  
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
    > Jeśli użytkownik spróbuje dwukrotnie kliknąć kontrolkę <xref:System.Windows.Forms.CheckBox>, każde kliknięcie zostanie przetworzone osobno; oznacza to, że formant <xref:System.Windows.Forms.CheckBox> nie obsługuje zdarzenia podwójnego kliknięcia.  
  
    > [!NOTE]
    > Gdy właściwość <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> jest `true` (wartość domyślna), <xref:System.Windows.Forms.CheckBox> jest automatycznie wybierana lub czyszczona po kliknięciu. W przeciwnym razie należy ręcznie ustawić właściwość <xref:System.Windows.Forms.CheckBox.Checked%2A>, gdy wystąpi zdarzenie <xref:System.Windows.Forms.Control.Click>.  
  
     Możesz również użyć formantu <xref:System.Windows.Forms.CheckBox>, aby określić sposób działania.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Aby określić kurs akcji po kliknięciu pola wyboru  
  
1. Użyj instrukcji case, aby wykonać zapytanie o wartość właściwości <xref:System.Windows.Forms.CheckBox.CheckState%2A> w celu określenia sposobu działania. Gdy właściwość <xref:System.Windows.Forms.CheckBox.ThreeState%2A> jest ustawiona na `true`, właściwość <xref:System.Windows.Forms.CheckBox.CheckState%2A> może zwracać trzy możliwe wartości, które reprezentują zaznaczone pole, zaznaczenie pola wyboru lub trzeci nieokreślony stan, w którym pole jest wyświetlane z wygaszonym wyglądem, aby wskazać, że opcja jest niedostępna.  
  
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
    > Gdy właściwość <xref:System.Windows.Forms.CheckBox.ThreeState%2A> jest ustawiona na `true`, właściwość <xref:System.Windows.Forms.CheckBox.Checked%2A> zwraca `true` zarówno dla <xref:System.Windows.Forms.CheckState.Checked>, jak i <xref:System.Windows.Forms.CheckState.Indeterminate>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox, kontrolka — omówienie](checkbox-control-overview-windows-forms.md)
- [Instrukcje: ustawianie opcji za pomocą kontrolek CheckBox formularzy Windows Forms](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox, kontrolka](checkbox-control-windows-forms.md)
