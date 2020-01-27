---
title: Wyświetlanie pasków przewijania w kontrolce RichTextBox
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 2185b572ef20765043d3df3dbfd8bf5b21cfac28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745563"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Porady: wyświetlanie pasków przewijania w komórkach formantu RichTextBox formularzy systemu Windows
Domyślnie formant Windows Forms <xref:System.Windows.Forms.RichTextBox> Wyświetla poziomy i pionowy pasek przewijania odpowiednio do potrzeb. Istnieje siedem możliwych wartości właściwości <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> kontrolki <xref:System.Windows.Forms.RichTextBox>, które opisano w poniższej tabeli.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Aby wyświetlić paski przewijania w kontrolce RichTextBox  
  
1. Ustaw <xref:System.Windows.Forms.RichTextBox.Multiline%2A> właściwość `true`. Jeśli właściwość <xref:System.Windows.Forms.RichTextBox.Multiline%2A> jest ustawiona na `false`, nie ma żadnego typu paska przewijania, w tym w poziomie.  
  
2. Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> na odpowiednią wartość wyliczenia <xref:System.Windows.Forms.RichTextBoxScrollBars>.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (wartość domyślna)|Wyświetla poziomy lub pionowy pasek przewijania lub oba, tylko wtedy, gdy tekst przekracza szerokość lub długość kontrolki.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Nigdy nie wyświetla żadnego typu paska przewijania.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Wyświetla poziomy pasek przewijania tylko wtedy, gdy tekst przekracza szerokość kontrolki. (W takim przypadku Właściwość <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> musi być ustawiona na `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Wyświetla pionowy pasek przewijania tylko wtedy, gdy tekst przekracza wysokość kontrolki.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Wyświetla poziomy pasek przewijania, gdy właściwość <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> jest ustawiona na `false`. Pasek przewijania jest wyszarzony, gdy tekst nie przekracza szerokości kontrolki.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Zawsze wyświetla pionowy pasek przewijania. Pasek przewijania jest wyszarzony, gdy tekst nie przekracza długości kontrolki.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Zawsze wyświetla pionowy pasek przewijania. Wyświetla poziomy pasek przewijania, gdy właściwość <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> jest ustawiona na `false`. Paski przewijania są wyświetlane jako wygaszone, gdy tekst nie przekracza szerokości lub długości kontrolki.|  
  
3. Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> na odpowiednią wartość.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |`false`|Tekst w kontrolce nie jest automatycznie dostosowywany, aby dopasować szerokość kontrolki, aby przewinąć ją w prawo do momentu osiągnięcia końca wiersza. Użyj tej wartości, jeśli wybrano poziome paski przewijania lub oba powyższe elementy.|  
    |`true` (wartość domyślna)|Tekst w kontrolce jest automatycznie dopasowywany do szerokości kontrolki. Poziomy pasek przewijania nie zostanie wyświetlony. Użyj tej wartości, jeśli wybrano opcję paski przewijania w pionie lub brak, powyżej, aby wyświetlić jeden lub więcej akapitów.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
