---
title: 'Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: cc352f15fb1e8b531cd0f9b298b2db4ce649d3cf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039645"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Instrukcje: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant
Na dowolnym formularzu systemu Windows można wyznaczyć <xref:System.Windows.Forms.Button> kontrolkę jako przycisk Anuluj. Przycisk Anuluj jest klikany za każdym razem, gdy użytkownik naciśnie klawisz ESC, niezależnie od tego, który inny formant w formularzu ma fokus. Taki przycisk jest zazwyczaj zaprogramowany, aby umożliwić użytkownikowi szybkie zakończenie operacji bez zatwierdzania żadnej akcji.

## <a name="to-designate-the-cancel-button"></a>Aby wyznaczyć przycisk Anuluj

1. Wybierz formularz, w którym znajduje się przycisk.

2. W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.Form.CancelButton%2A> właściwość formularza na <xref:System.Windows.Forms.Button> nazwę formantu.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Button, kontrolka — omówienie](button-control-overview-windows-forms.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Instrukcje: Odpowiadanie na kliknięcia przycisku Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: Wyznacz przycisk Windows Forms jako przycisk Akceptuj przy użyciu narzędzia Projektant](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Button, kontrolka](button-control-windows-forms.md)
