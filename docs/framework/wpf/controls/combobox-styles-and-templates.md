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
ms.openlocfilehash: 887698bdaebf7bc5ddac8997167589d9fbd3dd4d
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960379"
---
# <a name="combobox-styles-and-templates"></a>ComboBox — Style i szablony
W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.ComboBox>. Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="combobox-parts"></a>Elementy ComboBox  
 W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.ComboBox>.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_EditableTextBox|<xref:System.Windows.Controls.TextBox>|Zawiera tekst <xref:System.Windows.Controls.ComboBox>.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Lista rozwijana zawierająca elementy w polu kombi.|  
  
 Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ComboBox>szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>. (<xref:System.Windows.Controls.ItemsPresenter> wyświetla każdy element w <xref:System.Windows.Controls.ComboBox>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym <xref:System.Windows.Controls.ScrollViewer>, należy nadać <xref:System.Windows.Controls.ItemsPresenter> nazwę `ItemsPresenter`.  
  
## <a name="combobox-states"></a>ComboBox — Stany  
 W poniższej tabeli wymieniono Stany formantu <xref:System.Windows.Controls.ComboBox>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Wyłączono|CommonStates|Kontrolka jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką <xref:System.Windows.Controls.ComboBox>.|  
|Ustawiono fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|FocusedDropDown|FocusStates|Lista rozwijana dla <xref:System.Windows.Controls.ComboBox> ma fokus.|  
|Prawidłowy|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
|Modyfikować|EditStates|Właściwość <xref:System.Windows.Controls.ComboBox.IsEditable%2A> jest `true`.|  
|Umożliwia edycji|EditStates|Właściwość <xref:System.Windows.Controls.ComboBox.IsEditable%2A> jest `false`.|  
  
## <a name="comboboxitem-parts"></a>ComboBoxItem części  
 Formant <xref:System.Windows.Controls.ComboBoxItem> nie zawiera żadnych nazwanych części.  
  
## <a name="comboboxitem-states"></a>Stany ComboBoxItem  
 W poniższej tabeli wymieniono Stany formantu <xref:System.Windows.Controls.ComboBoxItem>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Wyłączono|CommonStates|Kontrolka jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką <xref:System.Windows.Controls.ComboBoxItem>.|  
|Ustawiono fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Wybrane|SelectionStates|Element jest obecnie zaznaczony.|  
|Niezaznaczone|SelectionStates|Nie wybrano elementu.|  
|SelectedUnfocused|SelectionStates|Element jest zaznaczony, ale nie ma fokusu.|  
|Prawidłowy|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="combobox-controltemplate-example"></a>Przykład ControlTemplate ComboBox  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.ComboBox> i skojarzonych typów.  
  
 [!code-xaml[ControlTemplateExamples#ComboBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
 W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md)
