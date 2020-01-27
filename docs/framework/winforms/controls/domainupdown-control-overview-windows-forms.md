---
title: DomainUpDown — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 86703a96d4845414d043161e0efa67bfde9278db
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745857"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown — Informacje o formancie [Formularze systemu Windows]
Kontrolka <xref:System.Windows.Forms.DomainUpDown> Windows Forms jest zasadniczo połączeniem pola tekstowego i pary przycisków do przesuwania w górę lub w dół na liście. Kontrolka wyświetla i ustawia ciąg tekstowy z listy wyborów. Użytkownik może wybrać ciąg, klikając przyciski w górę i w dół, aby przejść przez listę, naciskając klawisze strzałek w górę i w dół lub wpisując ciąg, który pasuje do elementu na liście. Jednym z możliwych użycia dla tej kontrolki jest wybranie elementów z listy alfabetycznie posortowanej.  
  
> [!NOTE]
> Aby posortować listę, ustaw właściwość <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> na `true`.  
  
 Funkcja tego formantu jest bardzo podobna do pola listy lub pola kombi, ale zajmuje bardzo mało miejsca.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwości klucza kontrolki to <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>i <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. Właściwość <xref:System.Windows.Forms.DomainUpDown.Items%2A> zawiera listę obiektów, których wartości tekstowe są wyświetlane w formancie. Jeśli <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> jest ustawiona na `false`, formant automatycznie uzupełnia tekst, który jest typem użytkownika i dopasowuje go do wartości na liście. Jeśli <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> jest ustawiona na `true`, przewijanie do ostatniego elementu spowoduje przejście do pierwszego elementu na liście i na odwrót. Kluczowe metody kontrolki są <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> i <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Ta kontrolka wyświetla tylko ciągi tekstowe. Jeśli chcesz, aby kontrolka wyświetlająca wartości liczbowe, użyj kontrolki <xref:System.Windows.Forms.NumericUpDown>. Aby uzyskać więcej informacji, zobacz [NumericUpDown Control — Omówienie](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown, kontrolka](domainupdown-control-windows-forms.md)
