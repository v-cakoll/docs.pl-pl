---
title: "Porady: ustawianie opcji za pomocą formantów CheckBox formularzy systemu Windows"
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
f1_keywords: checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b7d3ddb090488f6503c0765f6054308c28d4ab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Porady: ustawianie opcji za pomocą formantów CheckBox formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.CheckBox> formantu służy do zapewniają użytkownikom True/False lub opcje tak/nie. Gdy jest wybrana kontrolka ma wyświetlać znacznik wyboru.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Aby ustawić opcje za pomocą formantów CheckBox  
  
1.  Sprawdź wartość <xref:System.Windows.Forms.CheckBox.Checked%2A> właściwości, aby określić jego stan i użycie tej wartości można ustawić opcję.  
  
     W przykładowym kodzie poniżej, kiedy <xref:System.Windows.Forms.CheckBox> formantu <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenie jest zgłaszane, formularza <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwość jest ustawiona na `false` Jeśli zaznaczono pole wyboru. Jest to przydatne w sytuacjach, w której chcesz ograniczyć interakcji z użytkownikiem.  
  
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
 <xref:System.Windows.Forms.CheckBox>  
 [Informacje o formancie CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Porady: odpowiadanie na formularzach systemu Windows kliknięcia elementu CheckBox](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [CheckBox — formant](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
