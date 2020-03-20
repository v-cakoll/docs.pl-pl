---
title: Ustawianie opcji za pomocą kontrolek CheckBox
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
ms.openlocfilehash: 00b467836d8e60aeee51a010a6384abf7dd73c56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141851"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Porady: ustawianie opcji za pomocą formantów CheckBox formularzy systemu Windows
Formant <xref:System.Windows.Forms.CheckBox> Formularze systemu Windows służy do nadawania użytkownikom opcji Prawda/Fałsz lub Tak/Nie. Formant wyświetla znacznik wyboru po jego wybraniu.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Aby ustawić opcje za pomocą kontrolek CheckBox  
  
1. Sprawdź wartość właściwości, <xref:System.Windows.Forms.CheckBox.Checked%2A> aby określić jej stan i użyj tej wartości, aby ustawić opcję.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.CheckBox> kodu, <xref:System.Windows.Forms.CheckBox.CheckedChanged> gdy zdarzenie formantu <xref:System.Windows.Forms.Control.AllowDrop%2A> jest wywoływane, właściwość formularza jest ustawiona na `false` jeśli pole wyboru jest zaznaczone. Jest to przydatne w sytuacjach, w których chcesz ograniczyć interakcję z użytkownikiem.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox, kontrolka — omówienie](checkbox-control-overview-windows-forms.md)
- [Instrukcje: odpowiadanie na kliknięcia kontrolki CheckBox formularzy Windows Forms](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Sterowanie polem wyboru](checkbox-control-windows-forms.md)
