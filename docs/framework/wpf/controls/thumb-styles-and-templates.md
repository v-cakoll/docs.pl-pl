---
title: Style i szablony miniatury
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: b7fc595f0c592d42f118c6b5542edf93716c2fca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790783"
---
# <a name="thumb-styles-and-templates"></a>Style i szablony miniatury

W tym temacie opisano, style i szablony <xref:System.Windows.Controls.Primitives.Thumb> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).

## <a name="thumb-parts"></a>Części Thumb

<xref:System.Windows.Controls.Primitives.Thumb> Formant nie ma żadnych części o nazwie.

## <a name="thumb-states"></a>Stany przycisku przewijania

Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.Thumb> kontroli.

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

## <a name="thumb-controltemplate-example"></a>Przykład ControlTemplate Thumb

Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Primitives.Thumb> kontroli.

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

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
