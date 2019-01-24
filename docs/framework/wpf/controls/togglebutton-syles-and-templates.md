---
title: ToggleButton — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: 76b6cb370829da7dd7a8ee6c2dc2fd07c3478080
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731234"
---
# <a name="togglebutton-syles-and-templates"></a>ToggleButton — Style i szablony
W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Primitives.ToggleButton> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="togglebutton-parts"></a>ToggleButton części  
 <xref:System.Windows.Controls.Primitives.ToggleButton> Formant nie ma żadnych części o nazwie.  
  
## <a name="togglebutton-states"></a>Stany ToggleButton  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.ToggleButton> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad kontrolką.|  
|Naciśnięto|CommonStates|Użytkownik naciśnie kontrolkę.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Po przeniesieniu fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Zaznaczone|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `true`.|  
|Niezaznaczone|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `false`.|  
|Nieokreślony|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> jest `true`, i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `null`.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
> [!NOTE]
>  Jeśli nieokreślony stan wizualny nie istnieje w szablonie kontrolki, następnie nieoznaczonego stanu wizualnego będzie służyć jako domyślnego stanu wizualnego.  
  
## <a name="togglebutton-controltemplate-example"></a>Przykład ControlTemplate ToggleButton  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.ToggleButton> kontroli.  
  
 [!code-xaml[ControlTemplateExamples#ToggleButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
 W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](../../../../docs/framework/wpf/controls/control-customization.md)
- [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
