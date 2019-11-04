---
title: Style i szablony ekspandera
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
ms.openlocfilehash: 26989474f264161be12bcc14fed614fdc7f775b6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460327"
---
# <a name="expander-styles-and-templates"></a>Style i szablony ekspandera
W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.Expander>. Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="expander-parts"></a>Części ekspandera  
 Formant <xref:System.Windows.Controls.Expander> nie zawiera żadnych nazwanych części.  
  
## <a name="expander-states"></a>Stany ekspandera  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.Expander>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Typow|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Pakowane|ExpansionStates|Formant jest rozwinięty.|  
|Zwinięte|ExpansionStates|Formant nie jest rozwinięty.|  
|ExpandDown|ExpandDirectionStates|Kontrolka rozszerza się w dół.|  
|ExpandUp|ExpandDirectionStates|Kontrolka rozszerza się w górę.|  
|ExpandLeft|ExpandDirectionStates|Kontrolka rozwija się w lewo.|  
|ExpandRight|ExpandDirectionStates|Kontrolka rozwija się w prawo.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="expander-controltemplate-example"></a>Przykład rozwinięcia ControlTemplate  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.Expander>.  
  
 [!code-xaml[ControlTemplateExamples#Expander](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
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
