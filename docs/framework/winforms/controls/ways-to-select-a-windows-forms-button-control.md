---
title: Sposoby wyboru kontrolki przycisku formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: f2881646a05d257044c6461f822a4c35a225f8c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223293"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Sposoby wyboru kontrolki przycisku formularzy systemu Windows
Można wybrać przycisk Windows Forms w następujący sposób:  
  
-   Kliknij przycisk za pomocą myszy.  
  
-   Wywoływanie przycisku <xref:System.Windows.Forms.Control.Click> zdarzenia w kodzie.  
  
-   Przenieś fokus do przycisku, naciskając klawisz TAB, a następnie wybierz przycisk, naciskając klawisz spacji lub ENTER.  
  
-   Naciśnij klawisz dostępu (ALT + podkreślona litera) dla przycisku. Aby uzyskać więcej informacji na temat kluczy dostępu, zobacz [jak: Tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).  
  
-   Jeśli przycisk znajduje się przycisk "Zaakceptuj" formularza, naciskając klawisz ENTER wybierze przycisk, nawet wtedy, gdy inna kontrolka ma fokus, chyba że inne kontrola jest inny przycisk, pole tekstu wielowierszowego lub formant niestandardowy, który traps klawisz enter.  
  
-   Jeśli przycisk znajduje się przycisk "Anuluj" formularza, naciskając klawisz ESC wybierze przycisk, nawet wtedy, gdy inna kontrolka ma fokus.  
  
-   Wywołaj <xref:System.Windows.Forms.Button.PerformClick%2A> metodę, aby wybrać przycisk programowo.  
  
## <a name="see-also"></a>Zobacz także

- [Button, kontrolka — omówienie](button-control-overview-windows-forms.md)
- [Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows](how-to-respond-to-windows-forms-button-clicks.md)
- [Button, kontrolka](button-control-windows-forms.md)
