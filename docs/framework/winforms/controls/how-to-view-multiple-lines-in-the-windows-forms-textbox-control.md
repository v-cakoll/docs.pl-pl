---
title: 'Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: 47404f02a753fe143dd573bdf73143416872af9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012922"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy systemu Windows
Domyślnie w formularzach Windows <xref:System.Windows.Forms.TextBox> kontrolka Wyświetla pojedynczą linie tekstu i nie są wyświetlane paski przewijania. Jeśli tekst jest dłuższy niż dostępna ilość miejsca, tylko część tekstu jest widoczna. To zachowanie domyślne można zmienić, ustawiając <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, i <xref:System.Windows.Forms.TextBox.ScrollBars%2A> właściwości odpowiednie wartości.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Aby wyświetlić znak powrotu karetki w formancie TextBox  
  
- Aby wyświetlić znak powrotu karetki w wielowierszowym <xref:System.Windows.Forms.TextBox>, użyj <xref:System.Environment.NewLine%2A> właściwości.  
  
     Należy pamiętać, że interpretacji znaków ucieczki (\\) jest specyficzny dla języka. Visual Basic stosuje `Chr$(13) & Chr$(10)` przy użyciu kombinacji znak powrotu karetki, jak powrotu i wysuwu wiersza.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Aby wyświetlić wiele wierszy w formancie TextBox  
  
1. Ustaw <xref:System.Windows.Forms.TextBox.Multiline%2A> właściwość `true`. Jeśli <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> jest `true` (ustawienie domyślne), następnie pojawi się jako jeden lub więcej akapitów tekstu w kontrolce; w przeciwnym razie zostanie wyświetlony jako listy, w której niektóre linie mogą zostać obcięte na brzegu kontrolki.  
  
2. Ustaw <xref:System.Windows.Forms.TextBox.ScrollBars%2A> właściwość do odpowiedniej wartości.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Użyj tej wartości, jeśli tekst będzie akapitu, prawie zawsze pasuje do formantu. Użytkownik może użyć wskaźnika myszy, aby poruszać się wewnątrz formantu, jeśli tekst jest zbyt długa, aby wyświetlić wszystkie na raz.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Użyj tej wartości, jeśli chcesz wyświetlić listę wierszy, z których część może być dłuższy niż szerokość <xref:System.Windows.Forms.TextBox> kontroli.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Użyj tej wartości, jeśli lista może być dłuższa niż wysokość formantu.|  
  
3. Ustaw <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwość do odpowiedniej wartości.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |`false`|Tekst w kontrolce nie będzie automatycznie zawijany, dzięki czemu będzie ona przewiń w prawo aż do osiągnięcia końca wiersza. Użyj tej wartości, jeśli została wybrana opcja <xref:System.Windows.Forms.ScrollBars.Horizontal> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.Both>powyżej.|  
    |`true` (ustawienie domyślne)|Poziomy pasek przewijania nie będzie widoczna. Użyj tej wartości, jeśli została wybrana opcja <xref:System.Windows.Forms.ScrollBars.Vertical> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.None>powyżej, aby wyświetlić jeden lub więcej akapitów.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextBox>
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
- [Instrukcje: Kontrolowanie punktu wstawiania w formancie TextBox formularzy Windows](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: Tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: Tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: Umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: Zaznaczanie tekstu w formancie TextBox formularzy Windows](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
