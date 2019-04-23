---
title: DateTimePicker — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: 451172b51427e4932470c53737c7bc276920271c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173601"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.DateTimePicker> kontrolka zezwala użytkownikowi na wybranie jednego elementu z listy daty lub godziny. Gdy jest używana do reprezentowania daty, pojawi się z dwóch części: listy rozwijanej, za pomocą Data jest reprezentowana w tekst i siatki, która pojawia się po kliknięciu strzałki w dół obok listy. Siatka wygląda <xref:System.Windows.Forms.MonthCalendar> formant, który może służyć do wybierania wielu daty. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.MonthCalendar> sterowania, zobacz [— informacje o formancie MonthCalendar](monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Właściwości klucza  
 Jeśli chcesz, aby <xref:System.Windows.Forms.DateTimePicker> do wyświetlania jako kontrolkę do pobrania lub edytowanie czasów zamiast daty, ustaw <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> właściwości `true` i <xref:System.Windows.Forms.DateTimePicker.Format%2A> właściwość <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie godziny za pomocą formantu DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
 Gdy <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> właściwość jest ustawiona na `true`, pole wyboru jest wyświetlane obok wybranej daty w formancie. Gdy pole wyboru jest zaznaczone, można zaktualizować wybranej wartości daty / godziny. Gdy pole wyboru jest pusta, wartość pojawia się niedostępne.  
  
 Kontrolki <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> i <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> właściwości określają zakres dat i godzin. <xref:System.Windows.Forms.DateTimePicker.Value%2A> Właściwość zawiera bieżącą datę i czas kontrolki jest ustawiona na. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie i zwracanie dat za pomocą Windows formantu DateTimePicker formularzy](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Wartości mogą być wyświetlane w czterech formatach, które są ustawiane przez <xref:System.Windows.Forms.DateTimePicker.Format%2A> właściwości: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>, lub <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Jeśli wybrano opcję formatu niestandardowego, musisz ustawić <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> właściwość odpowiedni ciąg. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie daty w niestandardowym formacie za pomocą formantu DateTimePicker formularzy Windows](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wyświetlanie daty w niestandardowym formacie za pomocą formantu DateTimePicker formularzy Windows](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
- [Instrukcje: Ustaw i zwracają dat za pomocą formantu DateTimePicker formularzy Windows](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
