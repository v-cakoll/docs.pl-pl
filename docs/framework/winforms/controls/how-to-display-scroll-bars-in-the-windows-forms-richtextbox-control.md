---
title: 'Porady: wyświetlanie pasków przewijania w komórkach formantu RichTextBox formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 5588aad5b2e38716c628947c6e06365e7053eb5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532746"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Porady: wyświetlanie pasków przewijania w komórkach formantu RichTextBox formularzy systemu Windows
Domyślnie program Windows Forms <xref:System.Windows.Forms.RichTextBox> kontrolka Wyświetla pasków przewijania w poziomie i w pionie w razie potrzeby. Istnieje siedem możliwe wartości <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> właściwość <xref:System.Windows.Forms.RichTextBox> kontroli, które są opisane w poniższej tabeli.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Wyświetlanie pasków przewijania w formancie RichTextBox  
  
1.  Ustaw <xref:System.Windows.Forms.RichTextBox.Multiline%2A> właściwości `true`. Nie typu pasek, łącznie z przewijania poziomo, nie wyświetla w przypadku <xref:System.Windows.Forms.RichTextBox.Multiline%2A> właściwość jest ustawiona na `false`.  
  
2.  Ustaw <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> odpowiednie wartości dla właściwości <xref:System.Windows.Forms.RichTextBoxScrollBars> wyliczenia.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (ustawienie domyślne)|Wyświetla poziomy lub pionowy pasek przewijania i/lub tylko wtedy, gdy tekst przekracza szerokość lub długość kontrolki.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Nigdy nie wyświetla żadnego typu pasek przewijania.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Wyświetla przewijania poziomego paska tylko wtedy, gdy tekst przekracza szerokość formantu. (W tym celu włączone, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> musi mieć ustawioną właściwość `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Wyświetla przewijania pionowego paska tylko wtedy, gdy tekst przekracza wysokość formantu.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Wyświetla paska podczas przewijania poziomego <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwość jest ustawiona na `false`. Wygaszone paska przewijania, gdy tekst nie przekracza szerokość formantu.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Zawsze wyświetla pionowy pasek przewijania. Wygaszone paska przewijania, gdy tekst nie przekracza długość kontrolki.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Zawsze wyświetla pionowy pasek przewijania. Wyświetla paska podczas przewijania poziomego <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwość jest ustawiona na `false`. Paski przewijania pojawiają się wygaszone, gdy tekst nie przekracza szerokość lub długość kontrolki.|  
  
3.  Ustaw <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> właściwości odpowiednią wartość.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |`false`|Tekst w formancie nie zostanie automatycznie dopasowana do szerokość formantu, więc zostanie przewiń w prawo, aż do osiągnięcia końca wiersza. Użyj tej wartości w przypadku wybrania paski przewijania w poziomie i/lub powyżej.|  
    |`true` (ustawienie domyślne)|Tekst w formancie zostanie automatycznie dopasowana do szerokość formantu. Poziomy pasek przewijania nie będą wyświetlane. Użyj tej wartości, jeśli została wybrana opcja pionowe paski przewijania lub Brak, powyżej, aby wyświetlić jeden lub więcej akapitów.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox, kontrolka](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
