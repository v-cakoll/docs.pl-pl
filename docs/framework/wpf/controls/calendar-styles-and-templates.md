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
ms.openlocfilehash: 5398828d1526436ab5abbbd2e87515018b0cd8bf
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457527"
---
# <a name="calendar-styles-and-templates"></a>Style i szablony kalendarza
W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Calendar> formantu. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="calendar-parts"></a>Elementy kalendarza  
 W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Calendar> formantu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|Aktualnie wyświetlany miesiąc lub rok w <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|Panel, która zawiera <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>Stany kalendarza  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Calendar> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="calendaritem-parts"></a>Części CalendarItem  
 W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Primitives.CalendarItem> formantu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|Katalog główny formantu.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|Przycisk, który wyświetla poprzedniej strony kalendarza, po kliknięciu.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|Przycisk, który wyświetla następnej strony kalendarza, po kliknięciu.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|Przycisk, który pozwala na przełączanie się między trybem miesiąca, tryb roku a dekadę tryb.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Z zawartością w trybie miesiąca.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Z zawartością w trybie rok lub dekadę.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|Nakładce stanie wyłączenia.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate> Opisujący struktury visual.|  
  
## <a name="calendaritem-states"></a>Stany CalendarItem  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.CalendarItem> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Stan Normalny|CommonStates|Stan domyślny.|  
|Stan wyłączone|CommonStates|Stan kalendarza podczas <xref:System.Windows.UIElement.IsEnabled%2A> jest właściwość `false`.|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="calendardaybutton-parts"></a>Części CalendarDayButton  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton> Formant nie ma żadnych części o nazwie.  
  
## <a name="calendardaybutton-states"></a>Stany CalendarDayButton  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.CalendarDayButton> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Jest wyłączona.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Naciśnięto|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Zostanie naciśnięty.|  
|Wybrane|SelectionStates|Ten przycisk jest zaznaczony.|  
|Niezaznaczony|SelectionStates|Nie wybrano przycisku.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Przycisk ma fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Przycisk ma fokus.|  
|Fokus|FocusStates|Przycisk ma fokus.|  
|Bez fokusu|FocusStates|Przycisk ma fokus.|  
|Aktywne|ActiveStates|Przycisk jest aktywny.|  
|Nieaktywne|ActiveStates|Przycisk jest nieaktywny.|  
|RegularDay|DayStates|Reprezentuje przycisk <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Dzisiaj|DayStates|Reprezentuje przycisk <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|Przycisk reprezentuje dzień, w którym można wybrać.|  
|BlackoutDay|BlackoutDayStates|Przycisk reprezentuje dzień, w którym nie można wybrać.|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="calendarbutton-parts"></a>Części CalendarButton  
 <xref:System.Windows.Controls.Primitives.CalendarButton> Formant nie ma żadnych części o nazwie.  
  
## <a name="calendarbutton-states"></a>Stany CalendarButton  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.CalendarButton> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Jest wyłączona.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Naciśnięto|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Zostanie naciśnięty.|  
|Wybrane|SelectionStates|Ten przycisk jest zaznaczony.|  
|Niezaznaczony|SelectionStates|Nie wybrano przycisku.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Przycisk ma fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Przycisk ma fokus.|  
|Fokus|FocusStates|Przycisk ma fokus.|  
|Bez fokusu|FocusStates|Przycisk ma fokus.|  
|Aktywne|ActiveStates|Przycisk jest aktywny.|  
|Nieaktywne|ActiveStates|Przycisk jest nieaktywny.|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="calendar-controltemplate-example"></a>Przykład ControlTemplate kalendarza  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Calendar> kontroli i związanych z nimi typów.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pełny przykład, zobacz [style próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Style i szablony kontrolek](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Niestandardowe dostosowywanie kontrolki](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
