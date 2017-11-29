---
title: "Porady: wyświetlanie pasków przewijania w komórkach formantu RichTextBox formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3b20c526b27eb185bf79eaf0ace47e5a9fded42a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Porady: wyświetlanie pasków przewijania w komórkach formantu RichTextBox formularzy systemu Windows
Domyślnie program Windows Forms <xref:System.Windows.Forms.RichTextBox> kontrolka Wyświetla pasków przewijania w poziomie i w pionie w razie potrzeby. Istnieje siedem możliwe wartości <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> właściwość <xref:System.Windows.Forms.RichTextBox> kontroli, które są opisane w poniższej tabeli.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Wyświetlanie pasków przewijania w formancie RichTextBox  
  
1.  Ustaw <xref:System.Windows.Forms.RichTextBox.Multiline%2A> właściwości `true`. Nie typu pasek, łącznie z przewijania poziomo, nie wyświetla w przypadku <xref:System.Windows.Forms.RichTextBox.Multiline%2A> właściwość jest ustawiona na `false`.  
  
2.  Ustaw <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> odpowiednie wartości dla właściwości <xref:System.Windows.Forms.RichTextBoxScrollBars> wyliczenia.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both>(ustawienie domyślne)|Wyświetla poziomy lub pionowy pasek przewijania i/lub tylko wtedy, gdy tekst przekracza szerokość lub długość kontrolki.|  
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
    |`true`(ustawienie domyślne)|Tekst w formancie zostanie automatycznie dopasowana do szerokość formantu. Poziomy pasek przewijania nie będą wyświetlane. Użyj tej wartości, jeśli została wybrana opcja pionowe paski przewijania lub Brak, powyżej, aby wyświetlić jeden lub więcej akapitów.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox — formant](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Formanty do użycia w formularzach systemu Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
