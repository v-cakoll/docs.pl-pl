---
title: Wyznacz przycisk jako przycisk Anuluj
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 123b3e275065efadd24815320ea7d855808e60b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743262"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj
Na dowolnym formularzu systemu Windows można wyznaczyć kontrolkę <xref:System.Windows.Forms.Button>, która będzie przyciskiem Anuluj. Przycisk Anuluj jest klikany za każdym razem, gdy użytkownik naciśnie klawisz ESC, niezależnie od tego, który inny formant w formularzu ma fokus. Taki przycisk jest zazwyczaj zaprogramowany, aby umożliwić użytkownikowi szybkie zakończenie operacji bez zatwierdzania żadnej akcji.  
  
### <a name="to-designate-the-cancel-button"></a>Aby wyznaczyć przycisk Anuluj  
  
1. Ustaw właściwość <xref:System.Windows.Forms.Form.CancelButton%2A> formularza na odpowiednią kontrolkę <xref:System.Windows.Forms.Button>.  
  
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
- [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Akceptuj](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Button, kontrolka](button-control-windows-forms.md)
