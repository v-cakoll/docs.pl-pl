---
title: 'Instrukcje: Tworzenie pola tekstowego tylko do odczytu (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: be85eedf272e596ceb10e7510b8c99ce6aed0727
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130731"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Instrukcje: Tworzenie pola tekstowego tylko do odczytu (Windows Forms)
Można edytować pole tekstowe Windows Forms można przekształcić do kontrolki tylko do odczytu. Na przykład pola tekstowego może wyświetlić wartość, która zwykle jest edytowany, ale nie może być aktualnie, ze względu na stan aplikacji.  
  
### <a name="to-create-a-read-only-text-box"></a>Aby utworzyć pole tekstowe tylko do odczytu  
  
1.  Ustaw <xref:System.Windows.Forms.TextBox> kontrolki <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> właściwość `true`. Z właściwością ustawioną na `true`, użytkownicy nadal mogą przewijać i wyróżnianie tekstu w polu tekstowym bez możliwości zmiany. A **kopiowania** polecenie działa w polu tekstowym, ale **Wytnij** i **Wklej** polecenia nie są.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Właściwość ma wpływ tylko na interakcji z użytkownikiem w czasie wykonywania. Nadal można zmienić zawartości pola tekstowego programowo w czasie wykonywania, zmieniając <xref:System.Windows.Forms.TextBox.Text%2A> właściwości pola tekstowego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextBox>
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
- [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy systemu Windows](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy systemu Windows](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy systemu Windows](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy systemu Windows](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
