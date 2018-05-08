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
ms.openlocfilehash: 7ed917afe2640fe2ffef4904a3795c5f0e84ded9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.MonthCalendar> formant przedstawia intuicyjnego interfejsu graficznego dla użytkowników wyświetlić i ustawić informacje o dacie. Wyświetla formant Kalendarz: siatka zawierająca numerowane dni miesiąca, rozmieszczone w kolumnach poniżej dni tygodnia, z wybranego zakresu dat wyróżnione. Możesz wybrać inny miesiąc, klikając przycisk strzałki po obu stronach podpis miesiąca. W przeciwieństwie do podobnych <xref:System.Windows.Forms.DateTimePicker> sterowania, można wybrać więcej niż jednej daty z tym formantem. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.DateTimePicker> sterowania, zobacz [DateTimePicker — formant](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>Konfigurowanie MonthCalendar — formant  
 <xref:System.Windows.Forms.MonthCalendar> Wysokiej konfiguruje się wygląd formantu. Domyślnie dzisiaj jest wyświetlane w postaci kółku, a także zauważyć w dolnej części siatki. Tej funkcji można zmienić, określając <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> i <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> właściwości `false`. Numery tygodni można dodać do kalendarza, ustawiając <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> właściwości `true`. Przez ustawienie <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> właściwości, może mieć wiele miesięcy wyświetlane w poziomie i w pionie. Domyślnie niedziela jest wyświetlany jako pierwszy dzień tygodnia, ale może zostać wyznaczony każdego dnia przy użyciu <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A> właściwości.  
  
 Można również ustawić niektórych terminów, które mają być wyświetlane w pogrubioną czcionką jednorazowo, co roku lub co miesiąc, dodając <xref:System.DateTime> obiekty do <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>, i <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> właściwości. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie określonych dni pogrubioną Bold za pomocą formantu MonthCalendar formularzy systemu Windows](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 Właściwość klucza <xref:System.Windows.Forms.MonthCalendar> formant jest <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, zakresu dat zaznaczonego w formancie. <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> Wartość nie może przekraczać maksymalną liczbę dni, które można wybrać, ustaw <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> właściwości. Najwcześniejsza i najnowszej daty, użytkownik może wybrać są określane przez <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> i <xref:System.Windows.Forms.MonthCalendar.MinDate%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MonthCalendar>  
 [MonthCalendar, kontrolka](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
