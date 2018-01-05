---
title: "DateTimePicker — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0db5e532a2688d7f213fd42772234b9600192390
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.DateTimePicker> formant umożliwia użytkownikowi wybranie pojedynczego elementu z listy daty i godziny. Gdy jest używany do reprezentowania datę, pojawi się z dwóch części: listy rozwijanej z przedstawiany w tekst i siatki, które pojawia się po kliknięciu Strzałka w dół obok listy. Siatka wygląda <xref:System.Windows.Forms.MonthCalendar> formantu, który może służyć do wybierania wielu daty. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.MonthCalendar> sterowania, zobacz [informacje o formancie MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Właściwości klucza  
 W razie potrzeby <xref:System.Windows.Forms.DateTimePicker> były wyświetlane jako formant do pobrania lub edytowanie czasów zamiast dat, należy ustawić <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> właściwości `true` i <xref:System.Windows.Forms.DateTimePicker.Format%2A> właściwości <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie czasu za pomocą formantu DateTimePicker](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).  
  
 Gdy <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> właściwość jest ustawiona na `true`, pole wyboru jest wyświetlany obok wybranej daty w formancie. Gdy pole wyboru jest zaznaczone, może zostać zaktualizowana wybranej wartości daty i godziny. Jeśli zaznaczenie jest puste, wartość znajduje się niedostępne.  
  
 Kontrolki <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> i <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> właściwości określają zakres dat i godzin. <xref:System.Windows.Forms.DateTimePicker.Value%2A> Właściwość zawiera bieżącą datę i godzinę, o których ma ustawioną wartość formantu. Aby uzyskać więcej informacji, zobacz [jak: zestaw i zwraca dat za pomocą formantu DateTimePicker formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Wartości mogą być wyświetlane w czterech formatów, które są ustawiane przez <xref:System.Windows.Forms.DateTimePicker.Format%2A> właściwości: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>, lub <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Jeśli wybrano opcję formatu niestandardowego, należy ustawić <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> odpowiedni ciąg dla właściwości. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie daty w formacie niestandardowych za pomocą formantu DateTimePicker formularzy systemu Windows](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: wyświetlanie daty w niestandardowym formacie za pomocą kontrolki DateTimePicker formularzy Windows Forms](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)  
 [Instrukcje: ustawianie i zwracanie dat za pomocą kontrolki DateTimePicker formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
