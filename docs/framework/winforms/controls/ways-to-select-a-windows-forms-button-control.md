---
title: Sposoby zaznaczania kontrolki przycisku
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740007"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Sposoby wyboru kontrolki przycisku formularzy systemu Windows
Przycisk Windows Forms można wybrać w następujący sposób:  
  
- Za pomocą myszy kliknij przycisk.  
  
- Wywołaj zdarzenie <xref:System.Windows.Forms.Control.Click> przycisku w kodzie.  
  
- Przenieś fokus na przycisk, naciskając klawisz TAB, a następnie wybierz przycisk, naciskając klawisz spacji lub ENTER.  
  
- Naciśnij klawisz dostępu (ALT + podkreślona litera) dla przycisku. Aby uzyskać więcej informacji o kluczach dostępu, zobacz [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).  
  
- Jeśli przycisk jest przyciskiem "Akceptuj" formularza, naciśnięcie klawisza ENTER wybiera przycisk, nawet jeśli inny formant ma fokus — chyba że inny formant jest innym przyciskiem, wielowierszowym polem tekstowym lub kontrolką niestandardową, która Zalewka klawisza ENTER.  
  
- Jeśli przycisk jest przycisk "Anuluj" w formularzu, naciśnięcie klawisza ESC wybiera przycisk, nawet jeśli inny formant ma fokus.  
  
- Wywołaj metodę <xref:System.Windows.Forms.Button.PerformClick%2A>, aby wybrać przycisk programowo.  
  
## <a name="see-also"></a>Zobacz także

- [Button, kontrolka — omówienie](button-control-overview-windows-forms.md)
- [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Button, kontrolka](button-control-windows-forms.md)
