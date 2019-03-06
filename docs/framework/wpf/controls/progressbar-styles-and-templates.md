---
title: ProgressBar — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 7041a5497355a806894b0a0e0363fffde134aadb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377254"
---
# <a name="progressbar-styles-and-templates"></a>ProgressBar — Style i szablony
W tym temacie opisano, style i szablony <xref:System.Windows.Controls.ProgressBar> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="progressbar-parts"></a>Części ProgressBar  
 Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.ProgressBar> kontroli.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_Indicator|<xref:System.Windows.FrameworkElement>|Obiekt, który wskazuje postęp.|  
|PART_Track|<xref:System.Windows.FrameworkElement>|Obiekt, który określa ścieżkę wskaźnik postępu.|  
|PART_GlowRect|<xref:System.Windows.FrameworkElement>|Obiekt, który embellishes pasek postępu.|  
  
## <a name="progressbar-states"></a>Stany ProgressBar  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.ProgressBar> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Określony|CommonStates|<xref:System.Windows.Controls.ProgressBar> Raporty postępu na podstawie <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> właściwości.|  
|Nieokreślony|CommonStates|<xref:System.Windows.Controls.ProgressBar> zgłasza ogólny postęp za pomocą wzorca powtarzania.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="progressbar-controltemplate-example"></a>Przykład ControlTemplate elementu ProgressBar  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ProgressBar> kontroli.  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
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
