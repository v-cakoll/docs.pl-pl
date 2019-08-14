---
title: 'Instrukcje: Tworzenie pola tekstowego tylko do odczytu (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 18d2f5ed2530957487ac25c3eb6240f8bc50a938
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971941"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Instrukcje: Tworzenie pola tekstowego tylko do odczytu (Windows Forms)

Możesz przekształcić edytowalne pole tekstowe Windows Forms na kontrolkę tylko do odczytu. Na przykład pole tekstowe może wyświetlać wartość, która jest zwykle edytowana, ale może nie być obecnie ze względu na stan aplikacji.

## <a name="to-create-a-read-only-text-box"></a>Aby utworzyć pole tekstowe tylko do odczytu

1. <xref:System.Windows.Forms.TextBox> Ustaw Właściwość<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> kontrolki na `true`wartość. Po ustawieniu właściwości na `true`, użytkownicy mogą nadal przewijać i wyróżniać tekst w polu tekstowym bez zezwalania na wprowadzanie zmian. Polecenie **copy** działa w polu tekstowym, ale polecenia wycinania i **wklejania** nie są.

    > [!NOTE]
    > <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Właściwość ma wpływ tylko na interakcję użytkownika w czasie wykonywania. Zawartość pola tekstowego można nadal zmieniać programowo w czasie wykonywania, zmieniając <xref:System.Windows.Forms.TextBox.Text%2A> właściwość pola tekstowego.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextBox>
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
- [Instrukcje: Kontrolowanie punktu wstawiania w kontrolce TextBox Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: Tworzenie pola tekstowego hasła za pomocą kontrolki TextBox Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: Umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: Zaznacz tekst w kontrolce TextBox Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Instrukcje: Wyświetl wiele wierszy w kontrolce TextBox Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
