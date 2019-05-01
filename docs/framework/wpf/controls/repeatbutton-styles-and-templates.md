---
title: RepeatButton — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
ms.openlocfilehash: 86f212326bc707e4b07b8cab8d9a95d4f6ef8920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053319"
---
# <a name="repeatbutton-styles-and-templates"></a>RepeatButton — Style i szablony

W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Primitives.RepeatButton> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).

## <a name="repeatbutton-parts"></a>RepeatButton części

<xref:System.Windows.Controls.Primitives.RepeatButton> Formant nie ma żadnych części o nazwie.

## <a name="repeatbutton-states"></a>RepeatButton stanów

Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.RepeatButton> kontroli.

|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|
|-|-|-|
|Normalne|CommonStates|Stan domyślny.|
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad kontrolką.|
|Naciśnięto|CommonStates|Użytkownik naciśnie kontrolkę.|
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|
|Fokus|FocusStates|Kontrolka ma fokus.|
|Po przeniesieniu fokusu|FocusStates|Kontrolka nie ma fokusu.|
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|

## <a name="repeatbutton-controltemplate-example"></a>Przykład ControlTemplate RepeatButton

Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.RepeatButton> kontroli.

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

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
