---
title: DomainUpDown — Formant
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: b538350a84e341d6b2759a7db28f8799f3777a86
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745827"
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown — Formant (Formularze systemu Windows)
Formant Windows Forms <xref:System.Windows.Forms.DomainUpDown> wygląda jak kombinacja pól tekstowych i pary przycisków do przesunięcia w górę lub w dół na liście. Kontrolka wyświetla i ustawia ciąg tekstowy z listy wyborów. Użytkownik może wybrać ciąg, klikając przyciski w górę i w dół, aby przejść przez listę, naciskając klawisze strzałek w górę i w dół lub wpisując ciąg, który pasuje do elementu na liście. Jednym z możliwych użycia dla tej kontrolki jest wybranie elementów z listy alfabetycznie posortowanej. (Aby posortować listę, ustaw właściwość <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> na `true`). Funkcja tego formantu jest bardzo podobna do pola listy lub pola kombi, ale zajmuje bardzo mało miejsca.  
  
 Właściwości klucza kontrolki to <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>i <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. Właściwość <xref:System.Windows.Forms.DomainUpDown.Items%2A> zawiera listę obiektów, których wartości tekstowe są wyświetlane w formancie. Jeśli <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> jest ustawiona na `false`, formant automatycznie uzupełnia tekst, który jest typem użytkownika i dopasowuje go do wartości na liście. Jeśli <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> jest ustawiona na `true`, przewijanie do ostatniego elementu spowoduje przejście do pierwszego elementu na liście i na odwrót. Kluczowe metody kontrolki są <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> i <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Ta kontrolka wyświetla tylko ciągi tekstowe. Jeśli chcesz, aby kontrolka wyświetlająca wartości liczbowe, użyj kontrolki <xref:System.Windows.Forms.NumericUpDown>. Aby uzyskać więcej informacji, zobacz [NumericUpDown Control](numericupdown-control-windows-forms.md) .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [DomainUpDown, kontrolka — omówienie](domainupdown-control-overview-windows-forms.md)  
 Wprowadza ogólne koncepcje <xref:System.Windows.Forms.DomainUpDown> formantu, który umożliwia użytkownikom przeglądanie i wybieranie z listy ciągów tekstowych.  
  
 [Instrukcje: dodawanie w sposób programowy elementów do kontrolki DomainUpDown formularzy Windows Forms](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 Opisuje sposób określania ciągów tekstowych, które powinny być wyświetlane w kontrolce <xref:System.Windows.Forms.DomainUpDown>.  
  
 [Instrukcje: usuwanie elementów z kontrolki DomainUpDown formularzy Windows Forms](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Opisuje sposób usuwania elementów z formantu <xref:System.Windows.Forms.DomainUpDown> w kodzie.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.DomainUpDown>  
 Opisuje tę klasę i zawiera linki do wszystkich jej elementów członkowskich.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Opisuje tę klasę i zawiera linki do wszystkich jej elementów członkowskich.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontrolki, których można użyć na Windows Forms](controls-to-use-on-windows-forms.md)  
 Zawiera pełną listę kontrolek Windows Forms, z łączami do informacji o ich użyciu.
