---
title: Wyznacz przycisk jako przycisk Anuluj przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: 95d1139b6e339055f944ad0b0967a6d91283d49e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746053"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant
Na dowolnym formularzu systemu Windows można wyznaczyć kontrolkę <xref:System.Windows.Forms.Button>, która będzie przyciskiem Anuluj. Przycisk Anuluj jest klikany za każdym razem, gdy użytkownik naciśnie klawisz ESC, niezależnie od tego, który inny formant w formularzu ma fokus. Taki przycisk jest zazwyczaj zaprogramowany, aby umożliwić użytkownikowi szybkie zakończenie operacji bez zatwierdzania żadnej akcji.

## <a name="to-designate-the-cancel-button"></a>Aby wyznaczyć przycisk Anuluj

1. Wybierz formularz, w którym znajduje się przycisk.

2. W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.Form.CancelButton%2A> formularza na nazwę kontrolki <xref:System.Windows.Forms.Button>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Button, kontrolka — omówienie](button-control-overview-windows-forms.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Akceptuj przy użyciu narzędzia Projektant](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Button, kontrolka](button-control-windows-forms.md)
