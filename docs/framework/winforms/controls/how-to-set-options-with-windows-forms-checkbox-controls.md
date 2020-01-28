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
ms.openlocfilehash: 84198eab42aa02b1bb37fa16a3c4247a37f58a10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746765"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Porady: ustawianie opcji za pomocą formantów CheckBox formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.CheckBox> Windows Forms służy do nadawania użytkownikom wartości PRAWDA/FAŁSZ lub tak/nie. Kontrolka Wyświetla znacznik wyboru, gdy jest zaznaczone.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Aby ustawić opcje z kontrolkami CheckBox  
  
1. Sprawdź wartość właściwości <xref:System.Windows.Forms.CheckBox.Checked%2A>, aby określić jej stan, i Użyj tej wartości, aby ustawić opcję.  
  
     W poniższym przykładzie kodu, gdy zostanie wywołane zdarzenie <xref:System.Windows.Forms.CheckBox.CheckedChanged> formantu <xref:System.Windows.Forms.CheckBox>, właściwość <xref:System.Windows.Forms.Control.AllowDrop%2A> formularza jest ustawiona na `false`, jeśli pole wyboru jest zaznaczone. Jest to przydatne w sytuacjach, w których chcesz ograniczyć interakcję z użytkownikiem.  
  
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
- [Instrukcje: odpowiadanie na kliknięcia kontrolki CheckBox formularzy Windows Forms](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox, kontrolka](checkbox-control-windows-forms.md)
