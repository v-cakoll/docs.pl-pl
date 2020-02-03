---
title: MonthCalendar, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: a9b56164339d03b380a564b21855f6d94ec06af5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734941"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar — Informacje o formancie [Formularze systemu Windows]
Formant Windows Forms <xref:System.Windows.Forms.MonthCalendar> przedstawia intuicyjny interfejs graficzny, aby użytkownicy mogli wyświetlać i ustawiać informacje o dacie. Kontrolka wyświetla kalendarz: siatkę zawierającą numerowane dni miesiąca, ułożone w kolumnach poniżej dni tygodnia, z zaznaczonym zakresem dat. Możesz wybrać inny miesiąc, klikając przyciski strzałek po każdej stronie napisu miesiąca. W przeciwieństwie do podobnej kontrolki <xref:System.Windows.Forms.DateTimePicker> można wybrać więcej niż jedną datę z tą kontrolką. Aby uzyskać więcej informacji na temat kontrolki <xref:System.Windows.Forms.DateTimePicker>, zobacz [kontrolka DateTimePicker](datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>Konfigurowanie formantu MonthCalendar  
 Wygląd formantu <xref:System.Windows.Forms.MonthCalendar> jest wysoce konfigurowalny. Domyślnie dzisiejsza data jest wyświetlana jako okrąg i jest również zapisywana w dolnej części siatki. Tę funkcję można zmienić, ustawiając właściwości <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> i <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> na `false`. Możesz również dodać numery tygodniowe do kalendarza, ustawiając właściwość <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> na `true`. Ustawiając właściwość <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>, można wyświetlić wiele miesięcy w poziomie i w pionie. Domyślnie niedziela jest wyświetlana jako pierwszy dzień tygodnia, ale dowolny dzień można wyznaczyć przy użyciu właściwości <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>.  
  
 Można również ustawić, aby niektóre daty były wyświetlane pogrubione na raz, co rok lub co miesiąc, przez dodanie <xref:System.DateTime> obiektów do właściwości <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>i <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić określone dni pogrubione przy użyciu formantu Windows Forms MonthCalendar](display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 Właściwość klucza formantu <xref:System.Windows.Forms.MonthCalendar> jest <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, zakres dat zaznaczonych w kontrolce. Wartość <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> nie może przekroczyć maksymalnej dozwolonej liczby dni ustawionej we właściwości <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A>. Najwcześniejsza i Najpóźniejsza data, którą użytkownik może wybrać, zależy od właściwości <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> i <xref:System.Windows.Forms.MonthCalendar.MinDate%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MonthCalendar>
- [MonthCalendar, kontrolka](monthcalendar-control-windows-forms.md)
