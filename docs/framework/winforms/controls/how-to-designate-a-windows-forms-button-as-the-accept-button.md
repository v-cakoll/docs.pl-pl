---
title: 'Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj'
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
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80503cd6fc2fc1c624cdd2aeb1ca3f699ffd9832
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj
Na każdym formularzy systemu Windows, możesz wyznaczyć <xref:System.Windows.Forms.Button> formantu na przycisk Akceptuj, znanej także jako przycisk domyślny. Przy każdym naciśnięciu klawisza ENTER zostanie kliknięty przycisk domyślny, niezależnie od tego, który inny formant w formularzu ma fokus.  
  
> [!NOTE]
>  Wyjątki, aby się to, gdy formant fokus jest inny przycisk — w takim przypadku zostanie kliknięty przycisk z fokusem — lub wielowierszowego pola tekstowego lub kontrolki niestandardowej, która traps klawisz ENTER.  
  
### <a name="to-designate-the-accept-button"></a>Aby wyznaczyć na przycisk Akceptuj  
  
1.  Ustaw formularza <xref:System.Windows.Forms.Form.AcceptButton%2A> właściwości do odpowiedniego <xref:System.Windows.Forms.Button> formantu.  
  
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
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Button, kontrolka — omówienie](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Sposoby wyboru kontrolki przycisku Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Anuluj](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 [Button, kontrolka](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
