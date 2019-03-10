---
title: 'Instrukcje: Ustawianie opcji za pomocą formantów CheckBox formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
ms.openlocfilehash: 3eb68d76d936f13e78d13629455c6ac7fb537b40
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714791"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Instrukcje: Ustawianie opcji za pomocą formantów CheckBox formularzy Windows
Formularze Windows <xref:System.Windows.Forms.CheckBox> formantu umożliwia użytkownikom True/False lub opcji Yes/No. Kontrolka wyświetla znacznik wyboru, gdy jest wybrana.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Aby ustawić opcje za pomocą formantów CheckBox  
  
1.  Sprawdź wartość <xref:System.Windows.Forms.CheckBox.Checked%2A> właściwości, aby ustalić jego stan, a następnie użyj tej wartości, aby ustawić opcję.  
  
     W przykładowym kodzie poniżej, kiedy <xref:System.Windows.Forms.CheckBox> kontrolki <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenie jest zgłaszane, formularza <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwość jest ustawiona na `false` Jeśli zaznaczono pole wyboru. Jest to przydatne w sytuacjach, w której chcesz ograniczyć interakcji z użytkownikiem.  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.CheckBox>
- [CheckBox, kontrolka — omówienie](checkbox-control-overview-windows-forms.md)
- [Instrukcje: Odpowiadanie do formularzy Windows Forms kliknięcia kontrolki CheckBox](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox, kontrolka](checkbox-control-windows-forms.md)
