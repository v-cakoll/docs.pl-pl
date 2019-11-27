---
title: TextBox — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 41e390c261836909240cc146a48729d48c4a410e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283701"
---
# <a name="textbox-styles-and-templates"></a>TextBox — Style i szablony
W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.TextBox>. Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="textbox-parts"></a>Elementy TextBox  
 W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.TextBox>.  
  
|Części|Type|Opis|  
|-|-|-|  
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|Element wizualizacji, który może zawierać <xref:System.Windows.FrameworkElement>. Tekst <xref:System.Windows.Controls.TextBox> zostanie wyświetlony w tym elemencie.|  
  
## <a name="textbox-states"></a>Stany pól TextBox  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.TextBox>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|ReadOnly|CommonStates|Użytkownik nie może zmienić tekstu w <xref:System.Windows.Controls.TextBox>.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="textbox-controltemplate-example"></a>ControlTemplate — przykład pola tekstowego  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
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
