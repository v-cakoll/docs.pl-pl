---
title: DomainUpDown — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 6fda542204e2b41dd1d729d2b940c6f38a5812ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965300"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown — Informacje o formancie [Formularze systemu Windows]
Formant Windows Forms <xref:System.Windows.Forms.DomainUpDown> jest zasadniczo połączeniem pola tekstowego i pary przycisków do przesuwania w górę lub w dół na liście. Kontrolka wyświetla i ustawia ciąg tekstowy z listy wyborów. Użytkownik może wybrać ciąg, klikając przyciski w górę i w dół, aby przejść przez listę, naciskając klawisze strzałek w górę i w dół lub wpisując ciąg, który pasuje do elementu na liście. Jednym z możliwych użycia dla tej kontrolki jest wybranie elementów z listy alfabetycznie posortowanej.  
  
> [!NOTE]
> Aby posortować listę, ustaw <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> właściwość na. `true`  
  
 Funkcja tego formantu jest bardzo podobna do pola listy lub pola kombi, ale zajmuje bardzo mało miejsca.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwości klucza kontrolki to <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, i <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Właściwość zawiera listę obiektów, których wartości tekstowe są wyświetlane w kontrolce. Jeśli <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> jest ustawiona na `false`, formant automatycznie uzupełnia tekst, który jest typem użytkownika i dopasowuje go do wartości na liście. Jeśli <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> jest ustawiona na `true`, przewijanie do ostatniego elementu spowoduje przejście do pierwszego elementu na liście i na odwrót. Kluczowymi metodami formantu są <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> i. <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>  
  
 Ta kontrolka wyświetla tylko ciągi tekstowe. Jeśli chcesz, aby kontrolka, która wyświetla wartości liczbowe, <xref:System.Windows.Forms.NumericUpDown> używała kontrolki. Aby uzyskać więcej informacji, zobacz [NumericUpDown Control — Omówienie](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown, kontrolka](domainupdown-control-windows-forms.md)
