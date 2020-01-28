---
title: Wyznaczanie przycisku jako przycisku Akceptuj przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27a5de51f8c5b2c84cc205e09ac1a2179c315752
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746062"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj przy użyciu narzędzia Projektant
Na dowolnym formularzu systemu Windows można wyznaczyć kontrolkę <xref:System.Windows.Forms.Button> na przycisk Akceptuj, znaną również jako przycisk domyślny. Za każdym razem, gdy użytkownik naciśnie klawisz ENTER, przycisk domyślny zostanie kliknięty niezależnie od tego, który inny formant w formularzu ma fokus. Wyjątkami jest to, gdy kontrolka z fokusem jest innym przyciskiem. w takim przypadku zostanie kliknięty przycisk z fokusem — lub wielowierszowe pole tekstowe lub kontrolka niestandardowa, która Zalewka klawisza ENTER.

## <a name="to-designate-the-accept-button"></a>Aby wyznaczyć przycisk Akceptuj

1. Wybierz formularz, w którym znajduje się przycisk.

2. W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.Form.AcceptButton%2A> formularza na nazwę kontrolki <xref:System.Windows.Forms.Button>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Button, kontrolka — omówienie](button-control-overview-windows-forms.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Anuluj przy użyciu narzędzia Projektant](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button, kontrolka](button-control-windows-forms.md)
