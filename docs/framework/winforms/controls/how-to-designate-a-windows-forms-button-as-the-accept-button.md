---
title: 'Instrukcje: Wyznaczanie przycisku Windows Forms na przycisk Akceptuj'
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
ms.openlocfilehash: 00d9f4acffb88b5047b40df91799cea1caaf2cf2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714700"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Instrukcje: Wyznaczanie przycisku Windows Forms na przycisk Akceptuj
W każdym formularzu Windows, można wyznaczyć <xref:System.Windows.Forms.Button> formantu na przycisk Akceptuj, znany także jako przycisk domyślny. Zawsze wtedy, gdy użytkownik naciśnie klawisz ENTER, jest kliknięty przycisk domyślny, niezależnie od tego, którego fokus ma inne kontrolki na formularzu.  
  
> [!NOTE]
>  Wyjątki, aby się to w przypadku kontrolki z fokusem inny przycisk — w takim przypadku zostanie kliknięty przycisk z fokusem — lub wielowierszowego pola tekstowego lub formant niestandardowy, który traps klawisz ENTER.  
  
### <a name="to-designate-the-accept-button"></a>Aby wyznaczyć na przycisk Akceptuj  
  
1.  Ustaw dla formularza <xref:System.Windows.Forms.Form.AcceptButton%2A> właściwości do odpowiednich <xref:System.Windows.Forms.Button> kontroli.  
  
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
- [Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: Wyznaczanie przycisku Windows Forms na przycisk Anuluj](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button, kontrolka](button-control-windows-forms.md)
