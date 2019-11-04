---
title: Style i szablony kalendarza
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Calendar
- templates [WPF], Calendar
- states [WPF], Calendar
- parts [WPF], Calendar
- Calendar [WPF], styles and templates
- ControlTemplate [WPF], Calendar
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
ms.openlocfilehash: 49d9ced42572ac06a4ff824ec41a59c14497d215
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460927"
---
# <a name="calendar-styles-and-templates"></a>Style i szablony kalendarza
W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Calendar>. Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="calendar-parts"></a>Części kalendarza  
 W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.Calendar>.  
  
|Części|Typ|Opis|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|Aktualnie wyświetlany miesiąc lub rok w <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|Panel, który zawiera <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>Stany kalendarza  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Calendar>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="calendaritem-parts"></a>CalendarItem części  
 W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.Primitives.CalendarItem>.  
  
|Części|Typ|Opis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|Katalog główny formantu.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|Przycisk wyświetlający poprzednią stronę kalendarza, gdy zostanie kliknięty.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|Przycisk, który wyświetla następną stronę kalendarza, gdy zostanie kliknięty.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|Przycisk, który umożliwia przełączanie między trybem miesiąc, trybem roku i trybem dekady.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Hostuje zawartość w trybie miesiąca.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Hostuje zawartość w trybie roku lub dekady.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|Nakładka dla wyłączonego stanu.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate>, który opisuje strukturę wizualizacji.|  
  
## <a name="calendaritem-states"></a>Stany CalendarItem  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Primitives.CalendarItem>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Stan normalny|CommonStates|Stan domyślny.|  
|Stan wyłączenia|CommonStates|Stan kalendarza, gdy właściwość <xref:System.Windows.UIElement.IsEnabled%2A> jest `false`.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="calendardaybutton-parts"></a>CalendarDayButton części  
 Formant <xref:System.Windows.Controls.Primitives.CalendarDayButton> nie zawiera żadnych nazwanych części.  
  
## <a name="calendardaybutton-states"></a>Stany CalendarDayButton  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Primitives.CalendarDayButton>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Typow|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Styczn|CommonStates|Zostanie naciśnięty <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Niezaznaczone|SelectionStates|Przycisk jest wybrany.|  
|Niezaznaczone|SelectionStates|Przycisk nie jest zaznaczony.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Przycisk ma fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Przycisk nie ma fokusu.|  
|Fokus|FocusStates|Przycisk ma fokus.|  
|Bez fokusu|FocusStates|Przycisk nie ma fokusu.|  
|Wyprzedzeni|ActiveStates|Przycisk jest aktywny.|  
|Nieaktywne|ActiveStates|Przycisk jest nieaktywny.|  
|RegularDay|DayStates|Przycisk nie reprezentuje <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Obecnych|DayStates|Przycisk reprezentuje <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|Przycisk reprezentuje dzień, który można wybrać.|  
|BlackoutDay|BlackoutDayStates|Przycisk reprezentuje dzień, którego nie można wybrać.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="calendarbutton-parts"></a>CalendarButton części  
 Formant <xref:System.Windows.Controls.Primitives.CalendarButton> nie zawiera żadnych nazwanych części.  
  
## <a name="calendarbutton-states"></a>Stany CalendarButton  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Primitives.CalendarButton>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Typow|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Styczn|CommonStates|Zostanie naciśnięty <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Niezaznaczone|SelectionStates|Przycisk jest wybrany.|  
|Niezaznaczone|SelectionStates|Przycisk nie jest zaznaczony.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Przycisk ma fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Przycisk nie ma fokusu.|  
|Fokus|FocusStates|Przycisk ma fokus.|  
|Bez fokusu|FocusStates|Przycisk nie ma fokusu.|  
|Wyprzedzeni|ActiveStates|Przycisk jest aktywny.|  
|Nieaktywne|ActiveStates|Przycisk jest nieaktywny.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="calendar-controltemplate-example"></a>Przykład ControlTemplate kalendarza  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Calendar> i skojarzonych typów.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
