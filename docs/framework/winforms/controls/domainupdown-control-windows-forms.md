---
title: DomainUpDown — Formant (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: c23f374f1ec9cab6e43b12d32b97c40533ac36cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown — Formant (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.DomainUpDown> formant wygląda kombinację pole tekstowe i parę przyciski przenoszenia w górę lub w dół listy. Kontrolka Wyświetla i ustawia ciąg tekstowy, z listy dostępnych opcji. Użytkownik może wybrać ciąg, kilikając przyciski, aby przejść na liście, naciskając klawisze strzałek w górę i w dół lub wpisując ciąg zgodny element na liście. Jeden możliwości zastosowania dla tego formantu jest wybierania elementów z posortowane alfabetycznie listę nazw. (Aby posortować listę, należy ustawić <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> właściwości `true`.) Funkcja tego formantu jest bardzo podobny do pola listy lub pola kombi, ale zajmuje on bardzo mało miejsca.  
  
 Właściwości klucza formantu są <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, i <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Właściwość zawiera listę obiektów, których wartości tekstowe są wyświetlane w formancie. Jeśli <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> ma ustawioną wartość `false`, formantu automatycznie wykonuje tekstu, czy użytkownik, typy i dopasowuje je do wartości na liście. Jeśli <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> ma ustawioną wartość `true`, przewijanie poza ostatni element spowoduje przejście do pierwszego elementu na liście i na odwrót. Metody klucza formantu są <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> i <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Ten formant wyświetla tylko ciągi. Formant, który wyświetla wartości liczbowe, należy użyć <xref:System.Windows.Forms.NumericUpDown> formantu. Aby uzyskać więcej informacji, zobacz [formantu NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [DomainUpDown, kontrolka — omówienie](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 Ogólne pojęcia związane z <xref:System.Windows.Forms.DomainUpDown> kontroli, co umożliwi użytkownikom do przeglądania i wybrać z listy ciągów tekstowych.  
  
 [Instrukcje: dodawanie w sposób programowy elementów do kontrolki DomainUpDown formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 Opisuje sposób określenia ciągów tekstowych <xref:System.Windows.Forms.DomainUpDown> powinien być wyświetlany przez formant.  
  
 [Instrukcje: usuwanie elementów z kontrolki DomainUpDown formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Opisuje sposób usuwania pozycji z <xref:System.Windows.Forms.DomainUpDown> kontroli w kodzie.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.DomainUpDown>  
 Ta klasa opisuje i zawiera łącza do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Ta klasa opisuje i zawiera łącza do wszystkich jej członków.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Formanty, które można używać w formularzach systemu Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 Zawiera listę wszystkich formanty formularzy systemu Windows, linki do informacji na temat ich użycia.
