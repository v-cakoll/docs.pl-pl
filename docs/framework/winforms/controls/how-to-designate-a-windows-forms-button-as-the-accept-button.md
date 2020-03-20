---
title: Wyznacz przycisk jako przycisk Zaakceptuj
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: ca5f691fb26db5c4adcb48405c9600b54827104c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142150"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj
W dowolnym formularzu systemu Windows <xref:System.Windows.Forms.Button> można wyznaczyć formant jako przycisk accept, znany również jako przycisk domyślny. Za każdym razem, gdy użytkownik naciśnie klawisz ENTER, przycisk domyślny jest klikany niezależnie od tego, który inny formant w formularzu ma fokus.  
  
> [!NOTE]
> Wyjątkami są to, gdy formant z fokusem jest inny przycisk — w tym przypadku przycisk z fokusem zostanie kliknięty — lub wielowierszowe pole tekstowe lub niestandardowy formant, który zalewkuje klawisz ENTER.  
  
### <a name="to-designate-the-accept-button"></a>Aby wyznaczyć przycisk akceptuję  
  
1. Ustaw <xref:System.Windows.Forms.Form.AcceptButton%2A> właściwość formularza na <xref:System.Windows.Forms.Button> odpowiednią formant.  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Button — Informacje o formancie](button-control-overview-windows-forms.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Anuluj](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button, kontrolka](button-control-windows-forms.md)
