---
title: 'Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 8170190145e76a86f5343bc42b39be7fb9d61a0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344146"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj
W każdym formularzu Windows, można wyznaczyć <xref:System.Windows.Forms.Button> formantu przycisk Anuluj. Kliknięto przycisk Anuluj w każdym przypadku, gdy użytkownik naciśnie klawisz ESC, niezależnie od tego, którego fokus ma inne kontrolki na formularzu. Taki przycisk jest zwykle zaprogramowane umożliwia użytkownikowi szybkie zakończyć operację bez zobowiązania do dowolnej akcji.  
  
### <a name="to-designate-the-cancel-button"></a>Aby wyznaczyć przycisk Anuluj  
  
1. Ustaw dla formularza <xref:System.Windows.Forms.Form.CancelButton%2A> właściwości do odpowiednich <xref:System.Windows.Forms.Button> kontroli.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Button, kontrolka — omówienie](button-control-overview-windows-forms.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: Wyznaczanie przycisku Windows Forms na przycisk Akceptuj](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Button, kontrolka](button-control-windows-forms.md)
