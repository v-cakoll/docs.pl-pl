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
ms.openlocfilehash: 18bef548b11f1a680c1361027b86f6952bedaad0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912447"
---
# <a name="calendar-styles-and-templates"></a>Style i szablony kalendarza
W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Calendar> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="calendar-parts"></a>Elementy kalendarza  
 Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.Calendar> kontroli.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|Aktualnie wyświetlany miesiąc lub rok w <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|Panel, który zawiera <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>Stany kalendarza  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Calendar> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="calendaritem-parts"></a>Części CalendarItem  
 Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.Primitives.CalendarItem> kontroli.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|Katalog główny formantu.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|Przycisk, który wyświetla poprzedniej strony, kalendarza, po kliknięciu.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|Przycisk, który wyświetla następną stronę kalendarza, po kliknięciu.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|Przycisk, który pozwala na przełączanie się między trybem miesiąc, rok trybu a dekadę trybu.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Obsługuje zawartości w trybie miesiąca.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Obsługuje zawartości w trybie roku lub dekadę.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|Nakładce w stanie wyłączenia.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate> Opisujący struktury efektów wizualnych.|  
  
## <a name="calendaritem-states"></a>Stany CalendarItem  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.CalendarItem> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalny stan|CommonStates|Stan domyślny.|  
|Stan wyłączenia|CommonStates|Stan kalendarza podczas <xref:System.Windows.UIElement.IsEnabled%2A> właściwość `false`.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="calendardaybutton-parts"></a>Części CalendarDayButton  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton> Formant nie ma żadnych części o nazwie.  
  
## <a name="calendardaybutton-states"></a>Stany CalendarDayButton  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.CalendarDayButton> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Naciśnięto|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Naciśnięciu.|  
|Wybrane|SelectionStates|Ten przycisk jest zaznaczony.|  
|Niezaznaczone|SelectionStates|Nie wybrano przycisku.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Ten przycisk ma fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Ten przycisk ma fokus.|  
|Fokus|FocusStates|Ten przycisk ma fokus.|  
|Po przeniesieniu fokusu|FocusStates|Ten przycisk ma fokus.|  
|Aktywne|ActiveStates|Przycisk jest aktywny.|  
|Nieaktywne|ActiveStates|Przycisk będzie nieaktywny.|  
|RegularDay|DayStates|Ten przycisk nie reprezentuje <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Dzisiaj|DayStates|Reprezentuje przycisk <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|Przycisk reprezentuje dzień, w którym można wybrać.|  
|BlackoutDay|BlackoutDayStates|Przycisk reprezentuje dzień, w którym nie można go wybrać.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="calendarbutton-parts"></a>Części CalendarButton  
 <xref:System.Windows.Controls.Primitives.CalendarButton> Formant nie ma żadnych części o nazwie.  
  
## <a name="calendarbutton-states"></a>Stany CalendarButton  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.CalendarButton> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Naciśnięto|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Naciśnięciu.|  
|Wybrane|SelectionStates|Ten przycisk jest zaznaczony.|  
|Niezaznaczone|SelectionStates|Nie wybrano przycisku.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Ten przycisk ma fokus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Ten przycisk ma fokus.|  
|Fokus|FocusStates|Ten przycisk ma fokus.|  
|Po przeniesieniu fokusu|FocusStates|Ten przycisk ma fokus.|  
|Aktywne|ActiveStates|Przycisk jest aktywny.|  
|Nieaktywne|ActiveStates|Przycisk będzie nieaktywny.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="calendar-controltemplate-example"></a>Przykład ControlTemplate kalendarza  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Calendar> kontroli i typy skojarzonych.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
