---
title: Wyświetl wiele wierszy w kontrolce TextBox
description: Dowiedz się, jak wyświetlić wiele wierszy w kontrolce TextBox Windows Forms, ustawiając właściwości wielowierszowe, WordWrap i ScrollBar.
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
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174474"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Porady: wyświetlanie wielu wierszy w formancie TextBox formularzy systemu Windows
Domyślnie <xref:System.Windows.Forms.TextBox> formant Windows Forms wyświetla pojedynczy wiersz tekstu i nie wyświetla pasków przewijania. Jeśli tekst jest dłuższy niż dostępne miejsce, widoczna jest tylko część tekstu. To zachowanie domyślne można zmienić <xref:System.Windows.Forms.TextBox.Multiline%2A> , ustawiając <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwości, i <xref:System.Windows.Forms.TextBox.ScrollBars%2A> na odpowiednie wartości.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Aby wyświetlić znak powrotu karetki w kontrolce TextBox  
  
- Aby wyświetlić znak powrotu karetki w wielowierszowym <xref:System.Windows.Forms.TextBox> , należy użyć <xref:System.Environment.NewLine%2A> właściwości.  
  
     Należy pamiętać, że interpretacja znaków ucieczki ( \\ ) jest specyficzna dla języka. Visual Basic używa `Chr$(13) & Chr$(10)` do kombinacji znaków powrotu karetki i znaku wysuwu wiersza.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Aby wyświetlić wiele wierszy w kontrolce TextBox  
  
1. Ustaw <xref:System.Windows.Forms.TextBox.Multiline%2A> Właściwość na wartość `true` . Jeśli <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> jest `true` (domyślnie), tekst w kontrolce będzie wyświetlany jako jeden lub więcej akapitów; w przeciwnym razie pojawi się jako lista, w której niektóre wiersze mogą być przycinane na krawędzi formantu.  
  
2. Ustaw <xref:System.Windows.Forms.TextBox.ScrollBars%2A> Właściwość na odpowiednią wartość.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Użyj tej wartości, jeśli tekst będzie akapitem, który prawie zawsze pasuje do formantu. Użytkownik może użyć wskaźnika myszy, aby poruszać się wewnątrz kontrolki, jeśli tekst jest zbyt długi, aby wyświetlić go jednocześnie.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Użyj tej wartości, jeśli chcesz wyświetlić listę linii, a niektóre z nich mogą być dłuższe niż szerokość <xref:System.Windows.Forms.TextBox> kontrolki.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Użyj tej wartości, jeśli lista może być dłuższa niż wysokość formantu.|  
  
3. Ustaw <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> Właściwość na odpowiednią wartość.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |`false`|Tekst w kontrolce nie zostanie automatycznie opakowany, więc przewinięcie w prawo do momentu osiągnięcia końca wiersza. Użyj tej wartości, jeśli wybrano <xref:System.Windows.Forms.ScrollBars.Horizontal> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.Both> powyżej.|  
    |`true`wartooć|Poziomy pasek przewijania nie zostanie wyświetlony. Użyj tej wartości, jeśli wybrano <xref:System.Windows.Forms.ScrollBars.Vertical> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.None> powyżej, aby wyświetlić jeden lub więcej akapitów.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.TextBox>
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
- [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Porady: zaznaczanie tekstu w formancie TextBox formularzy systemu Windows](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [TextBox — Formant](textbox-control-windows-forms.md)
