---
title: MonthCalendar — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: 9e243ef17425384d7eb7690aa121b58a6bf9354c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554234"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.MonthCalendar> kontroli przedstawia intuicyjny interfejs graficzny służący do wyświetlania i ustawiania informacji o dacie. Kontrolka ma wyświetlać kalendarz: siatki zawierający numerowane dni miesiąca, uporządkowane według kolumn poniżej dni tygodnia, za pomocą wybranego zakresu dat wyróżnione. Za pomocą przycisków strzałek po obu stronach podpis miesiąca możesz wybrać innego miesiąca. W odróżnieniu od podobny <xref:System.Windows.Forms.DateTimePicker> kontrolki, można wybrać więcej niż jednej daty za pomocą tej kontrolki. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.DateTimePicker> sterowania, zobacz [kontrolki DateTimePicker](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>Konfigurowanie MonthCalendar — formant  
 <xref:System.Windows.Forms.MonthCalendar> Wygląd formantu jest w wysokim stopniu konfigurowalne. Domyślnie dzisiejsza data jest wyświetlana w kółkach, a także zauważyć w dolnej części siatki. Tę funkcję można zmienić, określając <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> i <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> właściwości `false`. Można również dodać numery tygodni w kalendarzu, ustawiając <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> właściwość `true`. Ustawiając <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> właściwość może mieć wiele miesięcy wyświetlany poziomo i pionowo. Domyślnie, niedziela jest wyświetlany jako pierwszy dzień tygodnia, ale w jednym dniu może być wyznaczony przy użyciu <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A> właściwości.  
  
 Można również ustawić określone daty do wyświetlenia w pogrubioną czcionką jednorazowo, co roku lub co miesiąc, dodając <xref:System.DateTime> obiekty do <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>, i <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> właściwości. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie określonych dni pogrubioną czcionką za pomocą Windows formantu MonthCalendar formularzy](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 Właściwość klucza <xref:System.Windows.Forms.MonthCalendar> formant jest <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, zakres dat, wybrana w kontrolce. <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> Wartość nie może przekraczać maksymalną liczbę dni, które można wybrać, ustaw w <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> właściwości. Użytkownik może wybrać daty najwcześniejszej i najnowszych są określane przez <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> i <xref:System.Windows.Forms.MonthCalendar.MinDate%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.MonthCalendar>
- [MonthCalendar, kontrolka](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
