---
title: ComboBox — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- ComboBox [WPF], styles and templates
- states [WPF], ComboBox
- ControlTemplate [WPF], ComboBox
- styles [WPF], ComboBox
- templates [WPF], ComboBox
- parts [WPF], ComboBox
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
ms.openlocfilehash: af7f8a544af5e9892a8f3f059048bbfd113d2491
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865362"
---
# <a name="combobox-styles-and-templates"></a>ComboBox — Style i szablony
W tym temacie opisano style i szablony dla <xref:System.Windows.Controls.ComboBox> kontrolki. Można zmienić wartość domyślną, <xref:System.Windows.Controls.ControlTemplate> aby dać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="combobox-parts"></a>Elementy ComboBox  
 W poniższej tabeli wymieniono nazwane części <xref:System.Windows.Controls.ComboBox> formantu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_EditableTextBox|<xref:System.Windows.Controls.TextBox>|Zawiera tekst <xref:System.Windows.Controls.ComboBox> .|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Lista rozwijana zawierająca elementy w polu kombi.|  
  
 Podczas tworzenia <xref:System.Windows.Controls.ControlTemplate> dla elementu <xref:System.Windows.Controls.ComboBox> , szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w obrębie <xref:System.Windows.Controls.ScrollViewer> . ( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element w <xref:System.Windows.Controls.ComboBox> ; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym <xref:System.Windows.Controls.ScrollViewer> , należy podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter` .  
  
## <a name="combobox-states"></a>ComboBox — Stany  
 Poniższa tabela zawiera listę stanów <xref:System.Windows.Controls.ComboBox> formantu.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|Disabled|CommonStates|Kontrolka jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad <xref:System.Windows.Controls.ComboBox> kontrolką.|  
|Ustawiono fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|FocusedDropDown|FocusStates|Lista rozwijana dla <xref:System.Windows.Controls.ComboBox> ma fokus.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości to `false` .|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość jest `true` i ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość jest `true` i formant nie ma fokusu.|  
|Modyfikować|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A>Właściwość jest `true` .|  
|Umożliwia edycji|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A>Właściwość jest `false` .|  
  
## <a name="comboboxitem-parts"></a>ComboBoxItem części  
 <xref:System.Windows.Controls.ComboBoxItem>Kontrolka nie ma żadnych nazwanych części.  
  
## <a name="comboboxitem-states"></a>Stany ComboBoxItem  
 Poniższa tabela zawiera listę stanów <xref:System.Windows.Controls.ComboBoxItem> formantu.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|Disabled|CommonStates|Kontrolka jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad <xref:System.Windows.Controls.ComboBoxItem> kontrolką.|  
|Ustawiono fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Wybrano|SelectionStates|Element jest obecnie zaznaczony.|  
|Niezaznaczone|SelectionStates|Nie wybrano elementu.|  
|SelectedUnfocused|SelectionStates|Element jest zaznaczony, ale nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości to `false` .|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość jest `true` i ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość jest `true` i formant nie ma fokusu.|  
  
## <a name="combobox-controltemplate-example"></a>Przykład ControlTemplate ComboBox  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ComboBox> kontrolki i skojarzonych typów.  
  
 [!code-xaml[ControlTemplateExamples#ComboBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
 W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony formantu](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie formantu](control-customization.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md)
