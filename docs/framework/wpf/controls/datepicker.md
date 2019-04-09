---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 555bf31b27ba233ffa54438077984b02b5e3084a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161344"
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker> Kontroli umożliwia użytkownikowi wybranie daty, wpisując ją do pola tekstowego lub za pomocą listy rozwijanej <xref:System.Windows.Controls.Calendar> kontroli.  
  
 Poniższa ilustracja przedstawia <xref:System.Windows.Controls.DatePicker>.  
  
 ![Kontrolki DatePicker](./media/ndp-datepicker.png "NDP_DatePicker")  
DatePicker Control  
  
 Wiele <xref:System.Windows.Controls.DatePicker> właściwości formantu związanych z zarządzaniem wbudowanej <xref:System.Windows.Controls.Calendar>i funkcji identycznie do równoważne właściwość <xref:System.Windows.Controls.Calendar>. W szczególności <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, i <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> właściwości działać identycznie do ich <xref:System.Windows.Controls.Calendar> odpowiedniki. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.Calendar>.  
  
 Użytkownicy mogą wpisać wartość typu date bezpośrednio do pola tekstowego, który ustawia <xref:System.Windows.Controls.DatePicker.Text%2A> właściwości. Jeśli <xref:System.Windows.Controls.DatePicker> nie można przekonwertować ciągu wprowadzone na prawidłową datę <xref:System.Windows.Controls.DatePicker.DateValidationError> zdarzenia zostaną podniesione. Domyślnie powoduje to, że wyjątek, ale program obsługi zdarzeń dla <xref:System.Windows.Controls.DatePicker.DateValidationError> można ustawić <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> właściwość `false` i zapobiec wyjątkowi z są zgłaszane.  
  
## <a name="see-also"></a>Zobacz także

- [Formanty](index.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
