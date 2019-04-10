---
title: 'Instrukcje: wyświetlanie pasków przewijania w komórkach kontrolki RichTextBox formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 152706cee511e4bca1dd324a652e8077b1f8548a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312660"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Instrukcje: wyświetlanie pasków przewijania w komórkach kontrolki RichTextBox formularzy systemu Windows
Domyślnie w formularzach Windows <xref:System.Windows.Forms.RichTextBox> kontrolka Wyświetla poziome i pionowe paski przewijania, zgodnie z potrzebami. Istnieje siedem możliwych wartości dla <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> właściwość <xref:System.Windows.Forms.RichTextBox> kontrolki, które są opisane w poniższej tabeli.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Wyświetlanie pasków przewijania w formancie RichTextBox  
  
1. Ustaw <xref:System.Windows.Forms.RichTextBox.Multiline%2A> właściwość `true`. Nie typu paska, w tym przewijania poziomo, zostaną wyświetlone, jeśli <xref:System.Windows.Forms.RichTextBox.Multiline%2A> właściwość jest ustawiona na `false`.  
  
2. Ustaw <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> właściwość do odpowiedniej wartości <xref:System.Windows.Forms.RichTextBoxScrollBars> wyliczenia.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (ustawienie domyślne)|Wyświetla poziomy lub pionowy pasek przewijania i/lub tylko wtedy, gdy tekst przekracza szerokość i długość kontrolki.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Nigdy nie wyświetla dowolnego typu paska przewijania.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Wyświetla przewijania poziomego paska tylko wtedy, gdy tekst przekracza szerokość formantu. (W tym celu, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwość musi być równa `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Wyświetla przewijania pionowego paska tylko wtedy, gdy tekst przekracza wysokość formantu.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Wyświetla paska podczas przewijania w poziomie <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwość jest ustawiona na `false`. Pasek przewijania jest wyszarzony, gdy tekst nie przekracza szerokość formantu.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Zawsze wyświetla pionowy pasek przewijania. Pasek przewijania jest wyszarzony, gdy tekst nie przekracza długość kontrolki.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Zawsze wyświetla pionowy pasek przewijania. Wyświetla paska podczas przewijania w poziomie <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwość jest ustawiona na `false`. Paski przewijania są wyświetlane wygaszone, gdy tekst nie przekracza szerokość i długość kontrolki.|  
  
3. Ustaw <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwość do odpowiedniej wartości.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |`false`|Tekst w kontrolce nie jest automatycznie dopasowana do szerokość kontrolki, dzięki czemu będzie ona przewiń w prawo aż do osiągnięcia końca wiersza. Użyj tej wartości w przypadku wybrania poziomych pasków przewijania i/lub powyżej.|  
    |`true` (ustawienie domyślne)|Tekst w kontrolce zostanie automatycznie dopasowana do szerokość formantu. Poziomy pasek przewijania nie będzie widoczna. Użyj tej wartości, jeśli została wybrana opcja pionowe paski przewijania lub Brak, powyżej, aby wyświetlić jeden lub więcej akapitów.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
