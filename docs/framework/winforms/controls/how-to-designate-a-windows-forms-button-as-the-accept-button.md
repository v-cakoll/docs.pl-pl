---
title: 'Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj'
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
ms.openlocfilehash: 1e24e410681b03a92c8c48b187dde569eccdc1c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222149"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj
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
- [Sposoby wyboru kontrolki przycisku formularzy systemu Windows](ways-to-select-a-windows-forms-button-control.md)
- [Instrukcje: odpowiadanie na kliknięcia przycisków formularzy systemu Windows](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button, kontrolka](button-control-windows-forms.md)
