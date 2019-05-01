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
ms.openlocfilehash: 83d674e3fb7ff7e715b75c635b891cd4e9703a21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972058"
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown — Formant (Formularze systemu Windows)
Formularze Windows <xref:System.Windows.Forms.DomainUpDown> kontroli wygląda kombinacją pole tekstowe oraz parę przycisków przenoszenia w górę lub w dół na liście. Kontrolka Wyświetla i ustawia ciąg tekstowy z listy dostępnych opcji. Użytkownik może wybrać ciąg przez kliknięcie przycisków, aby przejść na liście w górę i w dół, przez naciśnięcie klawiszy strzałek w górę i w dół lub wpisując ciąg, który pasuje do elementu na liście. Jedno możliwe użycie tej kontrolki jest służąca do wybierania elementów z alfabetycznie posortowaną listę nazw. (Aby posortować listę, należy ustawić <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> właściwość `true`.) Funkcja ta kontrolka jest bardzo podobne do pola listy lub pola kombi, ale zajmuje on bardzo mało miejsca.  
  
 Kluczowe właściwości kontrolki są <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, i <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Właściwość zawiera listę obiektów, których wartości tekstowe są wyświetlane w formancie. Jeśli <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> ustawiono `false`, formant automatycznie wykonuje tekstu, że użytkownik wpisuje i dopasowuje je do wartości na liście. Jeśli <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> ustawiono `true`, przewijania po ostatnim elemencie spowoduje przejście do pierwszego elementu na liście i na odwrót. Metody klucza kontrolki są <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> i <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Ta kontrolka wyświetla tylko ciągi tekstowe. Jeśli chcesz, aby formant, który wyświetla wartości liczbowe, użyj <xref:System.Windows.Forms.NumericUpDown> kontroli. Aby uzyskać więcej informacji, zobacz [formant NumericUpDown](numericupdown-control-windows-forms.md) .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [DomainUpDown, kontrolka — omówienie](domainupdown-control-overview-windows-forms.md)  
 Ogólne pojęcia związane z <xref:System.Windows.Forms.DomainUpDown> formant, który umożliwia użytkownikom przeglądanie, a następnie wybierz z listy ciągów tekstowych.  
  
 [Instrukcje: Programowe Dodawanie elementów do kontrolki DomainUpDown formularzy Windows](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 Opisuje sposób określania ciągów tekstowych <xref:System.Windows.Forms.DomainUpDown> powinien być wyświetlany formantu.  
  
 [Instrukcje: Usuwanie elementów z kontrolki DomainUpDown formularzy Windows](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Opisuje sposób usuwania elementów z <xref:System.Windows.Forms.DomainUpDown> kontrolki w kodzie.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.DomainUpDown>  
 Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Ta klasa opisuje i zawiera linki do wszystkich swoich elementów członkowskich...  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Formanty, używane w formularzach Windows Forms](controls-to-use-on-windows-forms.md)  
 Zawiera listę wszystkich kontrolek Windows Forms, wraz z łączami do informacji na temat ich używania.
