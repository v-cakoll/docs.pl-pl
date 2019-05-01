---
title: DatePicker — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
ms.openlocfilehash: 5c8e199dd7123e1490c8a836a62ffea158797eb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912252"
---
# <a name="datepicker-styles-and-templates"></a>DatePicker — Style i szablony
W tym temacie opisano, style i szablony <xref:System.Windows.Controls.DatePicker> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datepicker-parts"></a>Części DatePicker  
 Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.DatePicker> kontroli.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|Katalog główny formantu.|  
|PART_Button|<xref:System.Windows.Controls.Button>|Przycisk, który otwiera i zamyka <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Pole tekstowe, która pozwala na dane wejściowe daty.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Menu podręczne dla <xref:System.Windows.Controls.DatePicker> kontroli.|  
  
## <a name="datepicker-states"></a>Stany DatePicker  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.DatePicker> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.DatePicker> Jest wyłączona.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="datepickertextbox-parts"></a>Części DatePickerTextBox  
 Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.Primitives.DatePickerTextBox> kontroli.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|Element, który zawiera początkowy tekst w <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Element wizualny, który może zawierać <xref:System.Windows.FrameworkElement>. Tekst <xref:System.Windows.Controls.TextBox> jest wyświetlana w tym elemencie.|  
  
## <a name="datepickertextbox-states"></a>Stany DatePickerTextBox  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.DatePickerTextBox> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> Jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|Użytkownik nie może zmieniać tekst w <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Po przeniesieniu fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Znakiem wodnym|WatermarkStates|Kontrolka wyświetla jego początkowego tekstu.  <xref:System.Windows.Controls.Primitives.DatePickerTextBox> Jest w stanie, gdy użytkownik został wprowadzony tekst lub nie wybrano daty.|  
|Unwatermarked|WatermarkStates|Użytkownik wpisze tekst do <xref:System.Windows.Controls.Primitives.DatePickerTextBox> lub wybrać datę w <xref:System.Windows.Controls.DatePicker>.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="datepicker-controltemplate-example"></a>Przykład ControlTemplate DatePicker  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.DatePicker> kontroli.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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
