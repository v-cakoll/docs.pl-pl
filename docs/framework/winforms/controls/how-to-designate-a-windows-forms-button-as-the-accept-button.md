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
ms.openlocfilehash: e35dbc2b66f743f5af3c405228439268590e1a5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660206"
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
- [Button, kontrolka — omówienie](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)
- [Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: Wyznaczanie przycisku Windows Forms na przycisk Anuluj](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button, kontrolka](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
