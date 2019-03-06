---
title: Kalendarz
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: d2332f5d11e60a45e4da5d62ef7beed7aa14dfa7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359409"
---
# <a name="calendar"></a>Kalendarz
Kalendarz umożliwia użytkownikowi wybranie daty przy użyciu wyświetlanego kalendarza wizualnego.  
  
 A <xref:System.Windows.Controls.Calendar> formantu można używać oddzielnie lub w ramach listy rozwijanej <xref:System.Windows.Controls.DatePicker> kontroli. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.DatePicker>.  
  
 Na poniższej ilustracji przedstawiono dwie <xref:System.Windows.Controls.Calendar> kontroluje jednej z opcji i niedostępności dat i jedna bez.  
  
 ![Calendar controls](./media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Formanty kalendarza  
  
 Poniższa tabela zawiera informacje o zadaniach, które są zwykle skojarzone z <xref:System.Windows.Controls.Calendar>.  
  
|Zadanie|Implementacja|  
|----------|--------------------|  
|Określ daty nie można go wybrać.|Użyj <xref:System.Windows.Controls.Calendar.BlackoutDates%2A> właściwości.|  
|Masz <xref:System.Windows.Controls.Calendar> wyświetlana przez miesiąc, cały rok lub dekadę.|Ustaw <xref:System.Windows.Controls.Calendar.DisplayMode%2A> właściwość miesiąc, rok lub dekadę.|  
|Określ, czy użytkownik może wybrać datę, zakres dat lub wiele zakresów dat.|Użyj <xref:System.Windows.Controls.Calendar.SelectionMode%2A>.|  
|Określ zakres dat, <xref:System.Windows.Controls.Calendar> Wyświetla.|Użyj <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> i <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> właściwości.|  
|Określ, czy bieżąca data jest wyróżniona.|Użyj <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> właściwości. Domyślnie <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> jest `true`.|  
|Zmiana rozmiaru <xref:System.Windows.Controls.Calendar>.|Użyj <xref:System.Windows.Controls.Viewbox> lub ustaw <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwość <xref:System.Windows.Media.ScaleTransform>. Należy pamiętać, że jeśli ustawisz <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości <xref:System.Windows.Controls.Calendar>, rzeczywiste kalendarz nie zmienia jego rozmiar.|  
  
 <xref:System.Windows.Controls.Calendar> Control oferuje podstawowe nawigacji za pomocą myszy lub klawiatury. Poniższa tabela zawiera podsumowanie nawigacji za pomocą klawiatury.  
  
|Kombinacja klawiszy|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Akcja|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|STRZAŁKA|<xref:System.Windows.Controls.CalendarMode.Month>|Zmiany <xref:System.Windows.Controls.Calendar.SelectedDate%2A> właściwość Jeśli <xref:System.Windows.Controls.Calendar.SelectionMode%2A> nie ustawiono właściwości <xref:System.Windows.Controls.CalendarSelectionMode.None>.|  
|STRZAŁKA|<xref:System.Windows.Controls.CalendarMode.Year>|Zmiany w miesiącu <xref:System.Windows.Controls.Calendar.DisplayDate%2A> właściwości. Należy pamiętać, że <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nie zmienia się.|  
|STRZAŁKA|<xref:System.Windows.Controls.CalendarMode.Decade>|Zmienia roku <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Należy pamiętać, że <xref:System.Windows.Controls.Calendar.SelectedDate%2A> nie zmienia się.|  
|SHIFT + STRZAŁKA|<xref:System.Windows.Controls.CalendarMode.Month>|Jeśli <xref:System.Windows.Controls.Calendar.SelectionMode%2A> nie jest ustawiony na <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> lub <xref:System.Windows.Controls.CalendarSelectionMode.None>, rozszerza zakres dat wybrany.|  
|STRONA GŁÓWNA|<xref:System.Windows.Controls.CalendarMode.Month>|Zmiany <xref:System.Windows.Controls.Calendar.SelectedDate%2A> pierwszy dzień bieżącego miesiąca.|  
|STRONA GŁÓWNA|<xref:System.Windows.Controls.CalendarMode.Year>|Zmiany w miesiącu <xref:System.Windows.Controls.Calendar.DisplayDate%2A> do pierwszego miesiąca w roku. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nie zmienia się.|  
|STRONA GŁÓWNA|<xref:System.Windows.Controls.CalendarMode.Decade>|Zmienia roku <xref:System.Windows.Controls.Calendar.DisplayDate%2A> do pierwszego roku dekadę. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nie zmienia się.|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|Zmiany <xref:System.Windows.Controls.Calendar.SelectedDate%2A> ostatni dzień bieżącego miesiąca.|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|Zmiany w miesiącu <xref:System.Windows.Controls.Calendar.DisplayDate%2A> do ostatniego miesiąca roku. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nie zmienia się.|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|Zmienia roku <xref:System.Windows.Controls.Calendar.DisplayDate%2A> do ostatniego roku dekadę. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Nie zmienia się.|  
|CTRL + STRZAŁKA W GÓRĘ|Dowolne|Przełącza do następnego większych <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Jeśli <xref:System.Windows.Controls.Calendar.DisplayMode%2A> jest już <xref:System.Windows.Controls.CalendarMode.Decade>, żadna akcja.|  
|CTRL+DOWN ARROW|Dowolne|Przełącza do następnego mniejszych <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Jeśli <xref:System.Windows.Controls.Calendar.DisplayMode%2A> jest już <xref:System.Windows.Controls.CalendarMode.Month>, żadna akcja.|  
|SPACJI lub ENTER|<xref:System.Windows.Controls.CalendarMode.Year> lub <xref:System.Windows.Controls.CalendarMode.Decade>|Przełączniki <xref:System.Windows.Controls.Calendar.DisplayMode%2A> do <xref:System.Windows.Controls.CalendarMode.Month> lub <xref:System.Windows.Controls.CalendarMode.Year> reprezentowanego przez element z fokusem.|  
  
## <a name="see-also"></a>Zobacz także
- [Kontrolki](index.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
