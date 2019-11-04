---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 3e66b2306c11c54db14eb05cc6860257635cc653
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460359"
---
# <a name="datepicker"></a>DatePicker
Kontrolka <xref:System.Windows.Controls.DatePicker> umożliwia użytkownikowi wybranie daty przez wpisanie jej do pola tekstowego lub przy użyciu kontrolki <xref:System.Windows.Controls.Calendar> listy rozwijanej.  
  
 Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.DatePicker>.  
  
 ![DatePicker — formant](./media/ndp-datepicker.png "NDP_DatePicker")  
DatePicker — formant  
  
 Wiele właściwości kontrolki <xref:System.Windows.Controls.DatePicker> jest przeznaczonych do zarządzania jego wbudowaną <xref:System.Windows.Controls.Calendar>i działa identycznie z równoważną właściwością w <xref:System.Windows.Controls.Calendar>. W szczególności <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>i <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> właściwości działają identycznie z ich <xref:System.Windows.Controls.Calendar>nymi odpowiednikami. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.Calendar>.  
  
 Użytkownicy mogą wpisać datę bezpośrednio w polu tekstowym, które ustawia właściwość <xref:System.Windows.Controls.DatePicker.Text%2A>. Jeśli <xref:System.Windows.Controls.DatePicker> nie może skonwertować wprowadzonego ciągu na prawidłową datę, zostanie zgłoszone zdarzenie <xref:System.Windows.Controls.DatePicker.DateValidationError>. Domyślnie powoduje to wyjątek, ale program obsługi zdarzeń dla <xref:System.Windows.Controls.DatePicker.DateValidationError> może ustawić właściwość <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> na `false` i zapobiegać wywoływaniu wyjątku.  
  
## <a name="see-also"></a>Zobacz także

- [Kontrolki](index.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
