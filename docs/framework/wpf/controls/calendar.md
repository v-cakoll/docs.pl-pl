---
title: Kalendarz
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: e99a716e7ca8f7b2c9ed11543f37e0b8cb7422a6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460806"
---
# <a name="calendar"></a>Kalendarz
Kalendarz umożliwia użytkownikowi wybranie daty przy użyciu wyświetlania kalendarza wizualnego.  
  
 Kontrolka <xref:System.Windows.Controls.Calendar> może być używana samodzielnie lub jako część rozwijana kontrolki <xref:System.Windows.Controls.DatePicker>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.DatePicker>.  
  
 Na poniższej ilustracji przedstawiono dwie <xref:System.Windows.Controls.Calendar> kontrolki, jeden z opcjami i Data niedostępności oraz jeden bez.  
  
 ![Kontrolki kalendarza](./media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Kontrolki kalendarza  
  
 Poniższa tabela zawiera informacje o zadaniach, które są zwykle skojarzone z <xref:System.Windows.Controls.Calendar>.  
  
|Zadanie|Implementacja|  
|----------|--------------------|  
|Określ daty, których nie można wybrać.|Użyj właściwości <xref:System.Windows.Controls.Calendar.BlackoutDates%2A>.|  
|<xref:System.Windows.Controls.Calendar> wyświetlać miesiąc, cały rok lub dekadę.|Ustaw właściwość <xref:System.Windows.Controls.Calendar.DisplayMode%2A> na miesiąc, rok lub dekadę.|  
|Określ, czy użytkownik może wybrać datę, zakres dat lub wiele zakresów dat.|Użyj <xref:System.Windows.Controls.Calendar.SelectionMode%2A>.|  
|Określ zakres dat wyświetlanych w <xref:System.Windows.Controls.Calendar>.|Użyj właściwości <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> i <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A>.|  
|Określ, czy bieżąca data jest wyróżniona.|Użyj właściwości <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A>. Domyślnie <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> jest `true`.|  
|Zmień rozmiar <xref:System.Windows.Controls.Calendar>.|Użyj <xref:System.Windows.Controls.Viewbox> lub ustaw właściwość <xref:System.Windows.FrameworkElement.LayoutTransform%2A> na <xref:System.Windows.Media.ScaleTransform>. Należy pamiętać, że jeśli ustawisz <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości <xref:System.Windows.Controls.Calendar>, rzeczywisty kalendarz nie zmieni jego rozmiaru.|  
  
 Formant <xref:System.Windows.Controls.Calendar> zapewnia podstawową nawigację przy użyciu myszy lub klawiatury. Poniższa tabela zawiera podsumowanie nawigacji klawiaturowej.  
  
|Kombinacja klawiszy|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Akcja|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|ZNAJDUJĄC|<xref:System.Windows.Controls.CalendarMode.Month>|Zmienia właściwość <xref:System.Windows.Controls.Calendar.SelectedDate%2A>, jeśli właściwość <xref:System.Windows.Controls.Calendar.SelectionMode%2A> nie jest ustawiona na <xref:System.Windows.Controls.CalendarSelectionMode.None>.|  
|ZNAJDUJĄC|<xref:System.Windows.Controls.CalendarMode.Year>|Zmienia miesiąc właściwości <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Należy zauważyć, że <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nie zmienia się.|  
|ZNAJDUJĄC|<xref:System.Windows.Controls.CalendarMode.Decade>|Zmienia rok <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Należy zauważyć, że <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nie zmienia się.|  
|SHIFT + Strzałka|<xref:System.Windows.Controls.CalendarMode.Month>|Jeśli <xref:System.Windows.Controls.Calendar.SelectionMode%2A> nie jest ustawiona na <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> lub <xref:System.Windows.Controls.CalendarSelectionMode.None>, rozszerza zakres wybranych dat.|  
|MOWA|<xref:System.Windows.Controls.CalendarMode.Month>|Zmienia <xref:System.Windows.Controls.Calendar.SelectedDate%2A> na pierwszy dzień bieżącego miesiąca.|  
|MOWA|<xref:System.Windows.Controls.CalendarMode.Year>|Zmienia miesiąc <xref:System.Windows.Controls.Calendar.DisplayDate%2A> na pierwszy miesiąc roku. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nie zmieni się.|  
|MOWA|<xref:System.Windows.Controls.CalendarMode.Decade>|Zmienia rok <xref:System.Windows.Controls.Calendar.DisplayDate%2A> na pierwszy rok dekady. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nie zmieni się.|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|Zmienia <xref:System.Windows.Controls.Calendar.SelectedDate%2A> na ostatni dzień bieżącego miesiąca.|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|Zmienia miesiąc <xref:System.Windows.Controls.Calendar.DisplayDate%2A> w ostatni miesiąc roku. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nie zmieni się.|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|Zmienia rok <xref:System.Windows.Controls.Calendar.DisplayDate%2A> w ostatni rok dekady. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nie zmieni się.|  
|CTRL + STRZAŁKA W GÓRĘ|Ile|Przełącza do następnego większego <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Jeśli <xref:System.Windows.Controls.Calendar.DisplayMode%2A> jest już <xref:System.Windows.Controls.CalendarMode.Decade>, nie ma żadnej akcji.|  
|CTRL + STRZAŁKA W DÓŁ|Ile|Przełącza do następnej mniejszej <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Jeśli <xref:System.Windows.Controls.Calendar.DisplayMode%2A> jest już <xref:System.Windows.Controls.CalendarMode.Month>, nie ma żadnej akcji.|  
|SPACJa lub ENTER|<xref:System.Windows.Controls.CalendarMode.Year> lub <xref:System.Windows.Controls.CalendarMode.Decade>|Przełącza <xref:System.Windows.Controls.Calendar.DisplayMode%2A> do <xref:System.Windows.Controls.CalendarMode.Month> lub <xref:System.Windows.Controls.CalendarMode.Year> reprezentowane przez element z fokusem.|  
  
## <a name="see-also"></a>Zobacz także

- [Kontrolki](index.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
