---
title: Sposoby wyboru kontrolki przycisku formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 39696be1286efa68fa70b698ba9623911c90e352
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Sposoby wyboru kontrolki przycisku formularzy systemu Windows
Przycisku formularzy systemu Windows można wybrać w następujący sposób:  
  
-   Kliknij przycisk za pomocą myszy.  
  
-   Wywołanie przycisku <xref:System.Windows.Forms.Control.Click> zdarzeń w kodzie.  
  
-   Przenieś fokus przycisku, naciskając klawisz TAB, a następnie wybierz przycisk, naciskając klawisz spacji lub ENTER.  
  
-   Naciśnij klawisz dostępu (ALT + podkreślona litera) dla przycisku. Aby uzyskać więcej informacji na temat kluczy dostępu, zobacz [porady: tworzenie dostępu do kluczy dla formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).  
  
-   Jeśli przycisk jest przycisk "Zaakceptuj" formularza, naciskając klawisz ENTER wybierze przycisk, nawet jeśli inny formant ma fokus, chyba że inne kontrola jest inny przycisk, wielowierszowego pola tekstowego lub kontrolki niestandardowej, która traps klawisz enter.  
  
-   Jeśli przycisk jest przycisk "Anuluj" formularza, naciskając klawisz ESC wybierze przycisk, nawet jeśli inny formant ma fokus.  
  
-   Wywołanie <xref:System.Windows.Forms.Button.PerformClick%2A> metodę, aby wybrać przycisk programowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Button, kontrolka — omówienie](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Button, kontrolka](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
