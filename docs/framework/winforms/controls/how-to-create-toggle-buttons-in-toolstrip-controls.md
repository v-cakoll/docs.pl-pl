---
title: 'Instrukcje: Tworzenie przycisków przełączania w formantach ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: 723916eb0c1e242df301c49bf0716e0262a3ba42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614981"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Instrukcje: Tworzenie przycisków przełączania w formantach ToolStrip
Gdy użytkownik kliknie przycisk przełączania, pojawi się wklęsłą i zachowuje wklęsłą wygląd, dopóki użytkownik kliknie przycisk ponownie.  
  
### <a name="to-create-a-toggling-toolstripbutton"></a>Aby utworzyć toggling element ToolStripButton  
  
-   Należy użyć kodu takiego jak w poniższym przykładzie kodu. Ten kod zakłada, że formularz zawiera <xref:System.Windows.Forms.ToolStrip> kontroli, a jego <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekcja zawiera <xref:System.Windows.Forms.ToolStripButton> o nazwie `toolStripButton1`. Zakłada również, że masz program obsługi zdarzeń wywołuje `toolStripButton1_CheckedChanged`.  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ToolStripButton>
- [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
