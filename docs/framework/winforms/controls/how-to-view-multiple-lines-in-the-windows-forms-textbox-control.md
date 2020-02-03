---
title: Wyświetl wiele wierszy w kontrolce TextBox
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
ms.openlocfilehash: 61ea671c1e86fa8254bfc1b043a46f3b7aa6af1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728283"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Porady: wyświetlanie wielu wierszy w formancie TextBox formularzy systemu Windows
Domyślnie formant Windows Forms <xref:System.Windows.Forms.TextBox> wyświetla pojedynczy wiersz tekstu i nie wyświetla pasków przewijania. Jeśli tekst jest dłuższy niż dostępne miejsce, widoczna jest tylko część tekstu. To zachowanie domyślne można zmienić, ustawiając właściwości <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>i <xref:System.Windows.Forms.TextBox.ScrollBars%2A> na odpowiednie wartości.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Aby wyświetlić znak powrotu karetki w kontrolce TextBox  
  
- Aby wyświetlić znak powrotu karetki w <xref:System.Windows.Forms.TextBox>wielowierszowym, należy użyć właściwości <xref:System.Environment.NewLine%2A>.  
  
     Należy pamiętać, że interpretacja znaków ucieczki (\\) jest specyficzna dla języka. Visual Basic używa `Chr$(13) & Chr$(10)` kombinacji znaków powrotu karetki i znaku wysuwu wiersza.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Aby wyświetlić wiele wierszy w kontrolce TextBox  
  
1. Ustaw właściwość <xref:System.Windows.Forms.TextBox.Multiline%2A> na `true`. Jeśli <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> jest `true` (domyślnie), tekst w kontrolce będzie wyświetlany jako jeden lub więcej akapitów; w przeciwnym razie pojawi się jako lista, w której niektóre wiersze mogą być przycinane na krawędzi formantu.  
  
2. Ustaw właściwość <xref:System.Windows.Forms.TextBox.ScrollBars%2A> na odpowiednią wartość.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Użyj tej wartości, jeśli tekst będzie akapitem, który prawie zawsze pasuje do formantu. Użytkownik może użyć wskaźnika myszy, aby poruszać się wewnątrz kontrolki, jeśli tekst jest zbyt długi, aby wyświetlić go jednocześnie.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Użyj tej wartości, jeśli chcesz wyświetlić listę linii, a niektóre z nich mogą być dłuższe niż szerokość kontrolki <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Użyj tej wartości, jeśli lista może być dłuższa niż wysokość formantu.|  
  
3. Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> na odpowiednią wartość.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |`false`|Tekst w kontrolce nie zostanie automatycznie opakowany, więc przewinięcie w prawo do momentu osiągnięcia końca wiersza. Użyj tej wartości, jeśli wybrano <xref:System.Windows.Forms.ScrollBars.Horizontal> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.Both>, powyżej.|  
    |`true` (wartość domyślna)|Poziomy pasek przewijania nie zostanie wyświetlony. Użyj tej wartości, jeśli wybrano <xref:System.Windows.Forms.ScrollBars.Vertical> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.None>, aby wyświetlić jeden lub więcej akapitów.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextBox>
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
- [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
