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
ms.openlocfilehash: 002d1c3271827239dcd3a319621f66fb5bc68d4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283773"
---
# <a name="datepicker-styles-and-templates"></a>DatePicker — Style i szablony
W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.DatePicker>. Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="datepicker-parts"></a>DatePicker części  
 W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.DatePicker>.  
  
|Części|Typ|Opis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|Katalog główny formantu.|  
|PART_Button|<xref:System.Windows.Controls.Button>|Przycisk, który otwiera i zamyka <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Pole tekstowe, które umożliwia wprowadzanie daty.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Okno podręczne dla kontrolki <xref:System.Windows.Controls.DatePicker>.|  
  
## <a name="datepicker-states"></a>Stany DatePicker  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.DatePicker>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.DatePicker> jest wyłączona.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox części  
 W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.  
  
|Części|Typ|Opis|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|Element, który zawiera początkowy tekst w <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Element wizualizacji, który może zawierać <xref:System.Windows.FrameworkElement>. Tekst <xref:System.Windows.Controls.TextBox> zostanie wyświetlony w tym elemencie.|  
  
## <a name="datepickertextbox-states"></a>Stany DatePickerTextBox  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|Użytkownik nie może zmienić tekstu w <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Znak wodny|WatermarkStates|Kontrolka wyświetla początkowy tekst.  <xref:System.Windows.Controls.Primitives.DatePickerTextBox> jest w stanie, gdy użytkownik nie wprowadził tekstu lub nie wybrano daty.|  
|Nie ma znaku wodnego|WatermarkStates|Użytkownik wprowadził tekst do <xref:System.Windows.Controls.Primitives.DatePickerTextBox> lub wybrano datę z <xref:System.Windows.Controls.DatePicker>.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, a kontrolka ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` i formant nie ma fokusu.|  
  
## <a name="datepicker-controltemplate-example"></a>Przykład DatePicker ControlTemplate  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.DatePicker>.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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
