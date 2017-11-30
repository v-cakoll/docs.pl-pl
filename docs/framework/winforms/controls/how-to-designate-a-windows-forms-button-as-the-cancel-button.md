---
title: 'Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj'
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
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bbdf2ec4f2353662f1077b9d95966e0a2ebd316
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj
Na każdym formularzy systemu Windows, możesz wyznaczyć <xref:System.Windows.Forms.Button> formantu przycisku Anuluj. Kliknięto przycisk Anuluj przy każdym naciśnięciu klawisza ESC, niezależnie od tego, który inny formant w formularzu ma fokus. Aby umożliwić użytkownikowi szybkie zakończyć operację bez zatwierdzania jakiegokolwiek działania, zwykle zaplanowano taki przycisk.  
  
### <a name="to-designate-the-cancel-button"></a>Aby wyznaczyć przycisku Anuluj  
  
1.  Ustaw formularza <xref:System.Windows.Forms.Form.CancelButton%2A> właściwości do odpowiedniego <xref:System.Windows.Forms.Button> formantu.  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [Informacje o kontrolce przycisku](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Sposoby wyboru formantu przycisku formularzy systemu Windows](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [Button — formant](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
