---
title: DateTimePicker, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: 63271dd91116c1f68d426f3ed5aa710644ded928
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746938"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker — Informacje o formancie [Formularze systemu Windows]
Kontrolka <xref:System.Windows.Forms.DateTimePicker> Windows Forms umożliwia użytkownikowi wybranie jednego elementu z listy dat lub godzin. Gdy jest używany do reprezentowania daty, pojawia się w dwóch częściach: Lista rozwijana z datą reprezentowaną w tekście i siatką wyświetlaną po kliknięciu strzałki w dół obok listy. Siatka wygląda jak kontrolka <xref:System.Windows.Forms.MonthCalendar>, która może być używana do wybierania wielu dat. Aby uzyskać więcej informacji na temat formantu <xref:System.Windows.Forms.MonthCalendar>, zobacz [MonthCalendar Control — Omówienie](monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Właściwości klucza  
 Jeśli chcesz, aby <xref:System.Windows.Forms.DateTimePicker> pojawił się jako kontrolka do pobrania lub edycji razy zamiast dat, ustaw właściwość <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> na `true` i Właściwość <xref:System.Windows.Forms.DateTimePicker.Format%2A> na <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Aby uzyskać więcej informacji [, zobacz How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).  
  
 Gdy właściwość <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> jest ustawiona na `true`, obok wybranej daty w kontrolce zostanie wyświetlone pole wyboru. Gdy to pole wyboru jest zaznaczone, można zaktualizować wybraną wartość daty i godziny. Gdy pole wyboru jest puste, wartość jest niedostępna.  
  
 Właściwości <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> i <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> kontrolki określają zakres dat i godzin. Właściwość <xref:System.Windows.Forms.DateTimePicker.Value%2A> zawiera bieżącą datę i godzinę ustawioną dla kontrolki. Aby uzyskać szczegółowe informacje, zobacz [How to: Set and Return Data with the Windows Forms DateTimePicker Control](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Wartości mogą być wyświetlane w czterech formatach, które są ustawiane przez właściwość <xref:System.Windows.Forms.DateTimePicker.Format%2A>: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>lub <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Jeśli wybrano format niestandardowy, należy ustawić właściwość <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> na odpowiedni ciąg. Aby uzyskać szczegółowe informacje, zobacz [jak: wyświetlić datę w formacie niestandardowym za pomocą formantu Windows Forms DateTimePicker](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: wyświetlanie daty w niestandardowym formacie za pomocą kontrolki DateTimePicker formularzy Windows Forms](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
- [Instrukcje: ustawianie i zwracanie dat za pomocą kontrolki DateTimePicker formularzy Windows Forms](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
