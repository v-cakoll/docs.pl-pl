---
title: DatePicker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd5c7c796ee9d51a216368de3f3b04c10a5a3acd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker> Kontroli zezwala użytkownikowi na wybranie daty, wpisując albo go do pola tekstowego lub za pomocą listy rozwijanej <xref:System.Windows.Controls.Calendar> formantu.  
  
 Na poniższej ilustracji pokazano <xref:System.Windows.Controls.DatePicker>.  
  
 ![Formant selektora daty](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")  
Formant selektora daty  
  
 Duża liczba <xref:System.Windows.Controls.DatePicker> są właściwości formantu w zarządzaniu wbudowanych <xref:System.Windows.Controls.Calendar>i działają tak samo jak równoważne właściwości w <xref:System.Windows.Controls.Calendar>. W szczególności <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, i <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> właściwości działania tak samo do ich <xref:System.Windows.Controls.Calendar> odpowiedniki. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.Calendar>.  
  
 Użytkownicy mogą wpisywać daty bezpośrednio do pola tekstowego, który określa <xref:System.Windows.Controls.DatePicker.Text%2A> właściwości. Jeśli <xref:System.Windows.Controls.DatePicker> nie można przekonwertować ciągu wprowadzone na prawidłową datę <xref:System.Windows.Controls.DatePicker.DateValidationError> zdarzeń zostanie wygenerowany. Domyślnie powoduje to wyjątek, ale program obsługi zdarzeń dla <xref:System.Windows.Controls.DatePicker.DateValidationError> można ustawić <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> właściwości `false` i zapobiec zgłaszanych wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty](../../../../docs/framework/wpf/controls/index.md)  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
