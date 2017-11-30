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
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Porady: odpowiadanie na kliknięcia elementu CheckBox formularzy systemu Windows
Zawsze, gdy użytkownik kliknie formularzy systemu Windows <xref:System.Windows.Forms.CheckBox> kontroli, <xref:System.Windows.Forms.Control.Click> zdarzenie. Można programowanie aplikacji w celu wykonania akcji w zależności od stanu pola wyboru.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Na odpowiadanie na kliknięcia elementu CheckBox  
  
1.  W <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń, użyj <xref:System.Windows.Forms.CheckBox.Checked%2A> właściwości, aby określić stan formantu i wykonać wszelkie niezbędne działania.  
  
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
    >  Jeśli użytkownik próbuje kliknij dwukrotnie <xref:System.Windows.Forms.CheckBox> formantu, kliknij każdy będą przetwarzane oddzielnie; która jest, <xref:System.Windows.Forms.CheckBox> formant nie obsługuje kliknij dwukrotnie zdarzenie.  
  
    > [!NOTE]
    >  Gdy <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> właściwość jest `true` (ustawienie domyślne), <xref:System.Windows.Forms.CheckBox> jest automatycznie wybrana lub wyczyszczona po kliknięciu. W przeciwnym razie należy ręcznie ustawić <xref:System.Windows.Forms.CheckBox.Checked%2A> właściwości podczas <xref:System.Windows.Forms.Control.Click> zdarzenie.  
  
     Można również użyć <xref:System.Windows.Forms.CheckBox> kontroli w celu ustalenia sposobu działania.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Aby określić plan działania, gdy pole wyboru zostanie kliknięty  
  
1.  Użyj instrukcji case się zapytanie o wartość <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości w celu określenia sposobu działania. Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości może trzy możliwe wartości zwracane, które reprezentują pole sprawdzany, pole jest niezaznaczone lub innego stanie nieokreślonym w którym zostanie wyświetlone okno z wygaszone wygląd, aby wskazać opcją jest niedostępny.  
  
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
    >  Gdy <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.Forms.CheckBox.Checked%2A> zwraca `true` dla obu <xref:System.Windows.Forms.CheckState.Checked> i <xref:System.Windows.Forms.CheckState.Indeterminate>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.CheckBox>  
 [Informacje o formancie CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Porady: Ustawianie opcji za pomocą formularzy systemu Windows formantów CheckBox](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [CheckBox — formant](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
