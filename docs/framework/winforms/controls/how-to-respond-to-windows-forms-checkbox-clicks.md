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
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Porady: odpowiadanie na kliknięcia elementu CheckBox formularzy systemu Windows
Za każdym razem, gdy <xref:System.Windows.Forms.CheckBox> użytkownik kliknie formant Windows Forms, <xref:System.Windows.Forms.Control.Click> zdarzenie występuje. Aplikację można zaprogramować w celu wykonania pewnych akcji w zależności od stanu pola wyboru.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Aby odpowiedzieć na kliknięcia pola wyboru  
  
1. W <xref:System.Windows.Forms.Control.Click> programie obsługi zdarzeń <xref:System.Windows.Forms.CheckBox.Checked%2A> użyj właściwości, aby określić stan formantu i wykonać wszelkie niezbędne działania.  
  
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
    > Jeśli użytkownik spróbuje dwukrotnie <xref:System.Windows.Forms.CheckBox> kliknąć formant, każde kliknięcie zostanie przetworzone oddzielnie; oznacza to, <xref:System.Windows.Forms.CheckBox> że formant nie obsługuje zdarzenia dwukrotnego kliknięcia.  
  
    > [!NOTE]
    > Gdy <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> właściwość `true` jest (domyślnie), <xref:System.Windows.Forms.CheckBox> jest automatycznie zaznaczone lub wyczyszczone po kliknięciu. W przeciwnym razie należy <xref:System.Windows.Forms.CheckBox.Checked%2A> ręcznie ustawić <xref:System.Windows.Forms.Control.Click> właściwość, gdy wystąpi zdarzenie.  
  
     Można również użyć <xref:System.Windows.Forms.CheckBox> formantu, aby określić przebieg działania.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Aby określić kierunek działania po kliknięciu pola wyboru  
  
1. Użyj case instrukcji do kwerendy <xref:System.Windows.Forms.CheckBox.CheckState%2A> wartość właściwości, aby określić przebieg akcji. Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest `true`ustawiona na , <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwość może zwrócić trzy możliwe wartości, które reprezentują pole jest zaznaczone, pole jest niezaznaczone lub trzeci nieokreślony stan, w którym pole jest wyświetlane z wygaszonym wyglądem, aby wskazać, że opcja jest niedostępna.  
  
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
    > Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest `true`ustawiona <xref:System.Windows.Forms.CheckBox.Checked%2A> `true` na <xref:System.Windows.Forms.CheckState.Checked> , <xref:System.Windows.Forms.CheckState.Indeterminate>właściwość zwraca dla obu i .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox, kontrolka — omówienie](checkbox-control-overview-windows-forms.md)
- [Instrukcje: ustawianie opcji za pomocą kontrolek CheckBox formularzy Windows Forms](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Sterowanie polem wyboru](checkbox-control-windows-forms.md)
