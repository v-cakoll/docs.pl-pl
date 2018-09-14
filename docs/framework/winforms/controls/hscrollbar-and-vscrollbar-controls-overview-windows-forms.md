---
title: HScrollBar i VScrollBar — Informacje o formantach (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
ms.openlocfilehash: 2c6436e77753322733580acba5a20d6bb220f29c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45588114"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar i VScrollBar — Informacje o formantach (Formularze systemu Windows)
Windows Forms <xref:System.Windows.Forms.ScrollBar> kontrolki jest używana do udostępniania prostą nawigację w za pośrednictwem długą listę elementów lub dużych ilości informacji, przewijając albo w poziomie lub w pionie w obrębie aplikacja lub formant. Paski przewijania są typowe element interfejsu Windows więc <xref:System.Windows.Forms.ScrollBar> kontroli jest często używana z kontrolkami, które nie pochodzą z <xref:System.Windows.Forms.ScrollableControl> klasy. Podobnie wielu programistów chce zastosować <xref:System.Windows.Forms.ScrollBar> sterowania podczas tworzenia własnej kontrolki użytkownika.  
  
 <xref:System.Windows.Forms.HScrollBar> (Poziomy) i <xref:System.Windows.Forms.VScrollBar> formantów (w pionie) działają niezależnie od innych formantów i mieć własny zestaw zdarzeń, właściwości i metod. <xref:System.Windows.Forms.ScrollBar> formanty nie są takie same jak paski przewijania wbudowanych, które są dołączone do pola tekstowe, pola listy, pola kombi lub formularze MDI ( <xref:System.Windows.Forms.TextBox> kontrolkę <xref:System.Windows.Forms.TextBox.ScrollBars%2A> właściwości, aby pokazać lub ukryć paski przewijania, które są dołączone do formantu).  
  
 <xref:System.Windows.Forms.ScrollBar> Steruje użyciem <xref:System.Windows.Forms.ScrollBar.Scroll> zdarzenia do monitorowania przepływu (czasami określane jako przycisku przewijania) suwaka wzdłuż paska przewijania. Za pomocą <xref:System.Windows.Forms.ScrollBar.Scroll> zdarzeń zapewnia dostęp do wartości paska przewijania, ponieważ przeciągania.  
  
## <a name="value-property"></a>Wartość właściwości  
 <xref:System.Windows.Forms.ScrollBar.Value%2A> Właściwości (która domyślnie wynosi 0) jest `integer` wartość odpowiadającą położenie suwaka na pasku przewijania. Pozycja pola przewijania znajduje się na wartość minimalna, przemieszczał się najdalej po lewej stronie położenie (poziomych pasków przewijania) lub górną pozycję (w przypadku pionowe paski przewijania). Gdy pole przewijania znajduje się na wartość maksymalna, przenosi pole przewijania najdalej z prawej strony lub dolną pozycję. Podobnie wartość w połowie między dolnej i górnej części zakresu umieszcza wiodących krawędzią pola przewijania w połowie paska przewijania.  
  
 Oprócz używania kliknięć myszą, aby zmienić wartość paska przewijania, użytkownika można również przeciągać do dowolnego punktu przy pasku suwaka. Wartość wynikowa zależy od położenia pola przewijania, ale jest zawsze w zakresie <xref:System.Windows.Forms.ScrollBar.Minimum%2A> do <xref:System.Windows.Forms.ScrollBar.Maximum%2A> właściwości ustawione przez użytkownika.  
  
## <a name="largechange-and-smallchange-properties"></a>Właściwości SmallChange i LargeChange  
 Gdy użytkownik naciśnie klawisz PAGE UP lub PAGE DOWN lub klika w ścieżce paska przewijania po obu stronach pole przewijania <xref:System.Windows.Forms.ScrollBar.Value%2A> zmiany właściwości zgodnie z wartością <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> właściwości.  
  
 Gdy użytkownik naciśnie jeden strzałki kluczy lub kliknie jeden z przycisków paska przewijania, <xref:System.Windows.Forms.ScrollBar.Value%2A> zmiany właściwości zgodnie z wartością <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [Dodatki do formularzy Windows Forms dla programu .NET Framework 2.0](https://msdn.microsoft.com/library/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
