---
title: 'Porady: tworzenie pola tekstowego tylko do odczytu'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 17ae9524009c687cd62fb315f842e188e120ac68
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731275"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Porady: tworzenie pola tekstowego tylko do odczytu (Formularze systemu Windows)

Możesz przekształcić edytowalne pole tekstowe Windows Forms na kontrolkę tylko do odczytu. Na przykład pole tekstowe może wyświetlać wartość, która jest zwykle edytowana, ale może nie być obecnie ze względu na stan aplikacji.

## <a name="to-create-a-read-only-text-box"></a>Aby utworzyć pole tekstowe tylko do odczytu

1. Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> kontrolki <xref:System.Windows.Forms.TextBox> na `true`. Mając właściwość o wartości `true`, użytkownicy mogą nadal przewijać i wyróżniać tekst w polu tekstowym bez zezwalania na wprowadzanie zmian. Polecenie **copy** działa w polu tekstowym, ale polecenia **wycinania** i **wklejania** nie są.

    > [!NOTE]
    > Właściwość <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> ma wpływ tylko na interakcję użytkownika w czasie wykonywania. Zawartość pola tekstowego można nadal zmieniać programowo w czasie wykonywania, zmieniając właściwość <xref:System.Windows.Forms.TextBox.Text%2A> pola tekstowego.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextBox>
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
- [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
