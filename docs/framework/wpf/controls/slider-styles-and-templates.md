---
title: Style i szablony suwaka
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
ms.openlocfilehash: 8ec1f436ac0134ccdb19e63592c4181951814cb1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375678"
---
# <a name="slider-styles-and-templates"></a>Style i szablony suwaka
W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Slider> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="slider-parts"></a>Części suwaka  
 Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.Slider> kontroli.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_Track|<xref:System.Windows.Controls.Primitives.Track>|Kontener dla elementu, który wskazuje pozycję <xref:System.Windows.Controls.Slider>.|  
|PART_SelectionRange|<xref:System.Windows.FrameworkElement>|Element, który wyświetla zaznaczony zakres wzdłuż <xref:System.Windows.Controls.Slider>.  Wybranego zakresu jest widoczny tylko wtedy, gdy <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> właściwość `true`.|  
  
## <a name="slider-states"></a>Stany suwaka  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Slider> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad kontrolką.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Po przeniesieniu fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="slider-controltemplate-example"></a>Przykład ControlTemplate suwaka  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Slider> kontroli.  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
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
