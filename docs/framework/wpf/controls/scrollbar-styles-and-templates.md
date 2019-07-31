---
title: ScrollBar — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 016556fb825ddf60af7dc572d6fda7323b9bb09d
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671982"
---
# <a name="scrollbar-styles-and-templates"></a>ScrollBar — Style i szablony
W tym temacie opisano style i szablony dla <xref:System.Windows.Controls.Primitives.ScrollBar> kontrolki. Można zmienić wartość domyślną <xref:System.Windows.Controls.ControlTemplate> , aby dać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="scrollbar-parts"></a>Składniki ScrollBar  
 W poniższej tabeli wymieniono nazwane części <xref:System.Windows.Controls.Primitives.ScrollBar> formantu.  
  
|Części|Typ|Opis|  
|-|-|-|  
|PART_Track|<xref:System.Windows.Controls.Primitives.Track>|Kontener dla elementu, który wskazuje pozycję <xref:System.Windows.Controls.Primitives.ScrollBar>.|  
  
## <a name="scrollbar-states"></a>Stany ScrollBar  
 Poniższa tabela zawiera listę stanów wizualnych <xref:System.Windows.Controls.Primitives.ScrollBar> dla kontrolki.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> i dołączonej właściwości to `false`.|  
|InvalidFocused|ValidationStates|Dołączona właściwość jest `true` i ma fokus. <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość jest `true` i formant nie ma fokusu. <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>|  
  
## <a name="scrollbar-controltemplate-example"></a>Przykład ControlTemplate ScrollBar  
 Poniższy przykład pokazuje, <xref:System.Windows.Controls.ControlTemplate> jak zdefiniować <xref:System.Windows.Controls.Primitives.ScrollBar> dla kontrolki.  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
