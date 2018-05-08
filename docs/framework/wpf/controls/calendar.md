---
title: Kalendarz
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: b706ec6236b7e3e10865eee9fd32c2eb5a5e7db2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="calendar"></a>Kalendarz
Kalendarza umożliwia użytkownikowi wybranie daty przy użyciu wyświetlanego kalendarza wizualnego.  
  
 A <xref:System.Windows.Controls.Calendar> formantu można używać samodzielnie lub w ramach listy rozwijanej <xref:System.Windows.Controls.DatePicker> formantu. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.DatePicker>.  
  
 Na poniższej ilustracji przedstawiono dwie <xref:System.Windows.Controls.Calendar> określa jeden z opcji i dat niedostępności i jeden bez.  
  
 ![Formanty kalendarza](../../../../docs/framework/wpf/controls/media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Formanty kalendarza  
  
 Poniższa tabela zawiera informacje o zadaniach, które są zwykle skojarzone z <xref:System.Windows.Controls.Calendar>.  
  
|Zadanie|Implementacja|  
|----------|--------------------|  
|Określ daty nie można wybrać.|Użyj <xref:System.Windows.Controls.Calendar.BlackoutDates%2A> właściwości.|  
|Ma <xref:System.Windows.Controls.Calendar> wyświetlanie miesiąca, cały rok lub dekadę.|Ustaw <xref:System.Windows.Controls.Calendar.DisplayMode%2A> właściwości miesiąc, rok lub dekadę.|  
|Określ, czy użytkownik może wybrać datę, zakres dat lub wiele zakresów dat.|Użyj <xref:System.Windows.Controls.Calendar.SelectionMode%2A>.|  
|Określ zakres dat który <xref:System.Windows.Controls.Calendar> Wyświetla.|Użyj <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> i <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> właściwości.|  
|Określ, czy zostanie wyróżniona bieżącą datę.|Użyj <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> właściwości. Domyślnie <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> jest `true`.|  
|Zmień rozmiar <xref:System.Windows.Controls.Calendar>.|Użyj <xref:System.Windows.Controls.Viewbox> lub ustaw <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości <xref:System.Windows.Media.ScaleTransform>. Należy pamiętać, że jeśli ustawisz <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości <xref:System.Windows.Controls.Calendar>, rzeczywista kalendarza nie zmienia jego rozmiar.|  
  
 <xref:System.Windows.Controls.Calendar> Kontrola zapewnia podstawowe nawigacji za pomocą myszy lub klawiatury. Poniższa tabela zawiera podsumowanie nawigacji klawiatury.  
  
|Kombinacja klawiszy|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Akcja|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|STRZAŁKA|<xref:System.Windows.Controls.CalendarMode.Month>|Zmiany <xref:System.Windows.Controls.Calendar.SelectedDate%2A> właściwości Jeśli <xref:System.Windows.Controls.Calendar.SelectionMode%2A> nie ustawiono właściwości <xref:System.Windows.Controls.CalendarSelectionMode.None>.|  
|STRZAŁKA|<xref:System.Windows.Controls.CalendarMode.Year>|Zmiany w miesiącu <xref:System.Windows.Controls.Calendar.DisplayDate%2A> właściwości. Należy pamiętać, że <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nie ulega zmianie.|  
|STRZAŁKA|<xref:System.Windows.Controls.CalendarMode.Decade>|Zmienia roku <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Należy pamiętać, że <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nie ulega zmianie.|  
|SHIFT + STRZAŁKA|<xref:System.Windows.Controls.CalendarMode.Month>|Jeśli <xref:System.Windows.Controls.Calendar.SelectionMode%2A> nie jest ustawiony na <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> lub <xref:System.Windows.Controls.CalendarSelectionMode.None>, rozszerza zakresu dat zaznaczonego.|  
|STRONA GŁÓWNA|<xref:System.Windows.Controls.CalendarMode.Month>|Zmiany <xref:System.Windows.Controls.Calendar.SelectedDate%2A> pierwszy dzień miesiąca.|  
|STRONA GŁÓWNA|<xref:System.Windows.Controls.CalendarMode.Year>|Zmiany w miesiącu <xref:System.Windows.Controls.Calendar.DisplayDate%2A> na pierwszy miesiąc w roku. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nie ulega zmianie.|  
|STRONA GŁÓWNA|<xref:System.Windows.Controls.CalendarMode.Decade>|Zmienia roku <xref:System.Windows.Controls.Calendar.DisplayDate%2A> do pierwszego roku dekadę. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nie ulega zmianie.|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|Zmiany <xref:System.Windows.Controls.Calendar.SelectedDate%2A> do ostatniego dnia miesiąca.|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|Zmiany w miesiącu <xref:System.Windows.Controls.Calendar.DisplayDate%2A> ostatni miesiąc roku. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nie ulega zmianie.|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|Zmienia roku <xref:System.Windows.Controls.Calendar.DisplayDate%2A> do ostatniego roku dekadę. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nie ulega zmianie.|  
|CTRL + STRZAŁKA W GÓRĘ|wszystkie|Przełącza do następnego większych <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Jeśli <xref:System.Windows.Controls.Calendar.DisplayMode%2A> jest już <xref:System.Windows.Controls.CalendarMode.Decade>, żadna akcja.|  
|CTRL + STRZAŁKA W DÓŁ|wszystkie|Przełącza do następnego mniejsze <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Jeśli <xref:System.Windows.Controls.Calendar.DisplayMode%2A> jest już <xref:System.Windows.Controls.CalendarMode.Month>, żadna akcja.|  
|SPACJA lub ENTER|<xref:System.Windows.Controls.CalendarMode.Year> lub <xref:System.Windows.Controls.CalendarMode.Decade>|Przełączniki <xref:System.Windows.Controls.Calendar.DisplayMode%2A> do <xref:System.Windows.Controls.CalendarMode.Month> lub <xref:System.Windows.Controls.CalendarMode.Year> reprezentowany przez element z fokusem.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki](../../../../docs/framework/wpf/controls/index.md)  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
