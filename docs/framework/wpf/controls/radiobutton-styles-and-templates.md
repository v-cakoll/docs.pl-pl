---
title: RadioButton — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], RadioButton
- RadioButton [WPF], styles and templates
- ControlTemplate [WPF], RadioButton
- states [WPF], RadioButton
- templates [WPF], RadioButton
- parts [WPF], RadioButton
ms.assetid: 9acf93f7-dd2f-4010-8ce0-1edd81c52ae2
ms.openlocfilehash: 892b4bead6ef6db3a6c007e34fb333ebf1e39850
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459864"
---
# <a name="radiobutton-styles-and-templates"></a>RadioButton — Style i szablony
W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.RadioButton>. Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="radiobutton-parts"></a>Składniki RadioButton  
 Formant <xref:System.Windows.Controls.RadioButton> nie zawiera żadnych nazwanych części.  
  
## <a name="radiobutton-states"></a>Stany RadioButton  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.RadioButton>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Typow|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką.|  
|Styczn|CommonStates|Kontrolka zostanie naciśnięty.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Dane|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `true`.|  
|Unchecked|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `false`.|  
|Określona|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> jest `true`, a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="radiobutton-controltemplate-example"></a>ControlTemplate — przykład  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.RadioButton>.  
  
 [!code-xaml[ControlTemplateExamples#RadioButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/radiobutton.xaml#radiobutton)]  
  
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
