---
title: Wyznacz przycisk jako przycisk Akceptuj
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
ms.openlocfilehash: 1063f649768cac2c866390718b261a21e18ec4d3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743266"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj
Na dowolnym formularzu systemu Windows można wyznaczyć kontrolkę <xref:System.Windows.Forms.Button> na przycisk Akceptuj, znaną również jako przycisk domyślny. Za każdym razem, gdy użytkownik naciśnie klawisz ENTER, przycisk domyślny zostanie kliknięty niezależnie od tego, który inny formant w formularzu ma fokus.  
  
> [!NOTE]
> Wyjątkami jest to, gdy kontrolka z fokusem jest innym przyciskiem. w takim przypadku zostanie kliknięty przycisk z fokusem — lub wielowierszowe pole tekstowe lub kontrolka niestandardowa, która Zalewka klawisza ENTER.  
  
### <a name="to-designate-the-accept-button"></a>Aby wyznaczyć przycisk Akceptuj  
  
1. Ustaw właściwość <xref:System.Windows.Forms.Form.AcceptButton%2A> formularza na odpowiednią kontrolkę <xref:System.Windows.Forms.Button>.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Button, kontrolka — omówienie](button-control-overview-windows-forms.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Anuluj](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button, kontrolka](button-control-windows-forms.md)
