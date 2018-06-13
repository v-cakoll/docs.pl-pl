---
title: 'Porady: tworzenie przycisków przełączania w formantach ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: a04d531433273328c2d8eb0c5ef614f08c33952a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530384"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Porady: tworzenie przycisków przełączania w formantach ToolStrip
Gdy użytkownik kliknie przycisk przełącznika, pojawi się zapadnięta i zachowuje zapadnięta wygląd, dopóki użytkownik kliknie przycisk ponownie.  
  
### <a name="to-create-a-toggling-toolstripbutton"></a>Aby utworzyć toggling element ToolStripButton  
  
-   Użyj kodu, takie jak w poniższym przykładzie kodu. Ten kod przyjęto założenie, że formularz zawiera <xref:System.Windows.Forms.ToolStrip> kontroli, a jego <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekcja zawiera <xref:System.Windows.Forms.ToolStripButton> o nazwie `toolStripButton1`. Założono również, że masz wywołuje program obsługi zdarzeń `toolStripButton1_CheckedChanged`.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStripButton>  
 [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
