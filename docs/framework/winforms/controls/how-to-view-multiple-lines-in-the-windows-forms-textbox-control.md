---
title: 'Porady: wyświetlanie wielu wierszy w formancie TextBox formularzy systemu Windows'
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
ms.openlocfilehash: c826a519d8be05430eb6e2434209424514347b5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Porady: wyświetlanie wielu wierszy w formancie TextBox formularzy systemu Windows
Domyślnie program Windows Forms <xref:System.Windows.Forms.TextBox> kontroli Wyświetla pojedynczą linie tekstu i nie są wyświetlane paski przewijania. Jeśli tekst jest dłuższy niż dostępne miejsce, widoczna jest tylko część tekstu. To zachowanie domyślne można zmienić, ustawiając <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, i <xref:System.Windows.Forms.TextBox.ScrollBars%2A> właściwości, aby odpowiednie wartości.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Aby wyświetlić karetki w formancie TextBox  
  
-   Aby wyświetlić karetki w wielu wierszach <xref:System.Windows.Forms.TextBox>, użyj <xref:System.Environment.NewLine%2A> właściwości.  
  
     Należy pamiętać, że interpretacji znaki specjalne (\\) jest specyficzny dla języka. Używa języka Visual Basic `Chr$(13) & Chr$(10)` karetki kombinacji znak powrotu i wysuwu wiersza.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Aby wyświetlić wiele wierszy w formancie TextBox  
  
1.  Ustaw <xref:System.Windows.Forms.TextBox.Multiline%2A> właściwości `true`. Jeśli <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> jest `true` (ustawienie domyślne), to tekst w formancie pojawi się jako jeden lub więcej akapitów; w przeciwnym razie zostanie wyświetlony jako listy, w której niektóre wiersze mogą przycinana na granicy formantu.  
  
2.  Ustaw <xref:System.Windows.Forms.TextBox.ScrollBars%2A> właściwości odpowiednią wartość.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Użyj tej wartości, czy tekst będzie akapitu który prawie zawsze pasuje do formantu. Użytkownik może użyć wskaźnik myszy do przenoszenia wewnątrz formantu, jeśli tekst jest zbyt długi, aby wyświetlić wszystkie naraz.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Użyj tej wartości, jeśli chcesz wyświetlić listę wierszy, z których część może być dłuższy niż szerokość <xref:System.Windows.Forms.TextBox> formantu.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Użyj tej wartości, jeśli lista może być dłuższa niż wysokość formantu.|  
  
3.  Ustaw <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwości odpowiednią wartość.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |`false`|Tekst w formancie nie będzie automatycznie zawijany, więc zostanie przewiń w prawo, aż do osiągnięcia końca wiersza. Użyj tej wartości, jeśli została wybrana opcja <xref:System.Windows.Forms.ScrollBars.Horizontal> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.Both>powyżej.|  
    |`true` (ustawienie domyślne)|Poziomy pasek przewijania nie będą wyświetlane. Użyj tej wartości, jeśli została wybrana opcja <xref:System.Windows.Forms.ScrollBars.Vertical> paski przewijania lub <xref:System.Windows.Forms.ScrollBars.None>powyżej, aby wyświetlić jeden lub więcej akapitów.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Instrukcje: tworzenie pola tekstowego tylko do odczytu](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Instrukcje: umieszczanie cudzysłowu w ciągu](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [TextBox, kontrolka](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
