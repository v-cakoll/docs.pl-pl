---
title: DomainUpDown — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 1849e1bab440d779eaebfc7d2cd12e817c31bf79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605422"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.DomainUpDown> formant jest zasadniczo kombinacji pola tekstowego, a parę przycisków przenoszenia w górę lub w dół na liście. Kontrolka Wyświetla i ustawia ciąg tekstowy z listy dostępnych opcji. Użytkownik może wybrać ciąg przez kliknięcie przycisków, aby przejść na liście w górę i w dół, przez naciśnięcie klawiszy strzałek w górę i w dół lub wpisując ciąg, który pasuje do elementu na liście. Jedno możliwe użycie tej kontrolki jest służąca do wybierania elementów z alfabetycznie posortowaną listę nazw.  
  
> [!NOTE]
>  Aby posortować listę, należy ustawić <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> właściwość `true`.  
  
 Funkcja ta kontrolka jest bardzo podobne do pola listy lub pola kombi, ale zajmuje on bardzo mało miejsca.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Kluczowe właściwości kontrolki są <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, i <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Właściwość zawiera listę obiektów, których wartości tekstowe są wyświetlane w formancie. Jeśli <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> ustawiono `false`, formant automatycznie wykonuje tekstu, że użytkownik wpisuje i dopasowuje je do wartości na liście. Jeśli <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> ustawiono `true`, przewijania po ostatnim elemencie spowoduje przejście do pierwszego elementu na liście i na odwrót. Metody klucza kontrolki są <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> i <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Ta kontrolka wyświetla tylko ciągi tekstowe. Jeśli chcesz, aby formant, który wyświetla wartości liczbowe, użyj <xref:System.Windows.Forms.NumericUpDown> kontroli. Aby uzyskać więcej informacji, zobacz [— informacje o formancie NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown, kontrolka](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)
