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
ms.openlocfilehash: 77f93dae2a91f282c6746c3fec3fb5f567cae2e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211988"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Instrukcje: odpowiadanie na kliknięcia elementu CheckBox formularzy systemu Windows
Zawsze, gdy użytkownik kliknie formularze Windows <xref:System.Windows.Forms.CheckBox> kontroli <xref:System.Windows.Forms.Control.Click> wystąpi zdarzenie. Można programować aplikację, aby wykonywać niektórych akcji, w zależności od stanu pola wyboru.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Aby reagować na kliknięcia kontrolki CheckBox  
  
1.  W <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń, użyj <xref:System.Windows.Forms.CheckBox.Checked%2A> właściwość, aby określić stan formantu i wykonać wszelkie niezbędne działania.  
  
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
    >  Jeśli użytkownik próbuje kliknij dwukrotnie <xref:System.Windows.Forms.CheckBox> kontrolki, każde kliknięcie będą przetwarzane oddzielnie; czyli, <xref:System.Windows.Forms.CheckBox> formant nie obsługuje zdarzeń kliknij dwukrotnie plik.  
  
    > [!NOTE]
    >  Gdy <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> właściwość `true` (ustawienie domyślne), <xref:System.Windows.Forms.CheckBox> automatycznie lub odznaczane, po kliknięciu. W przeciwnym razie należy ręcznie ustawić <xref:System.Windows.Forms.CheckBox.Checked%2A> właściwości podczas <xref:System.Windows.Forms.Control.Click> wystąpi zdarzenie.  
  
     Można również użyć <xref:System.Windows.Forms.CheckBox> kontroli w celu określenia sposobu działania.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Aby określić zadanie, gdy pole wyboru zostanie kliknięty  
  
1.  Tworzenie zapytania wartość przy użyciu instrukcji case <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości w celu określenia sposobu działania. Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości może zwracać trzema możliwymi wartościami reprezentujących pola sprawdzany pole jest nie zaznaczone, lub na nieokreślony stan w którym pojawia się okno dialogowe z wygaszone wygląd, aby wskazać, opcja jest niedostępna.  
  
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
    >  Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.Forms.CheckBox.Checked%2A> właściwość zwraca `true` dla obu <xref:System.Windows.Forms.CheckState.Checked> i <xref:System.Windows.Forms.CheckState.Indeterminate>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox, kontrolka — omówienie](checkbox-control-overview-windows-forms.md)
- [Instrukcje: ustawianie opcji za pomocą kontrolek CheckBox formularzy systemu Windows](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox, kontrolka](checkbox-control-windows-forms.md)
