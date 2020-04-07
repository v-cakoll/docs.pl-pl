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
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805910"
---
# <a name="togglebutton-styles-and-templates"></a>ToggleButton — Style i szablony

W tym temacie opisano style <xref:System.Windows.Controls.Primitives.ToggleButton> i szablony formantu. Można zmodyfikować <xref:System.Windows.Controls.ControlTemplate> wartość domyślną, aby nadać formancie unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu formantu](../../../desktop-wpf/themes/how-to-create-apply-template.md).

## <a name="togglebutton-parts"></a>Część przycisku togglebutton

Formant <xref:System.Windows.Controls.Primitives.ToggleButton> nie ma żadnych nazwanych części.

## <a name="togglebutton-states"></a>Stany przycisku

W poniższej tabeli wymieniono stany wizualne formantu. <xref:System.Windows.Controls.Primitives.ToggleButton>

|Nazwa visualstate|Nazwa grupy programu VisualStateGroup|Opis|
|-|-|-|
|Normalne|CommonStates (CommonStates)|Stan domyślny.|
|Mouseover|CommonStates (CommonStates)|Wskaźnik myszy jest umieszczony nad formantem.|
|Naciśnięte|CommonStates (CommonStates)|Formant jest wciśnięty.|
|Disabled (Wyłączony)|CommonStates (CommonStates)|Formant jest wyłączony.|
|Ustawiono fokus|FocusStates (Stan ostrości)|Formant ma fokus.|
|Unfocused|FocusStates (Stan ostrości)|Formant nie ma fokusu.|
|Zaznaczone|Sprawdź Państwa|Parametr <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> ma wartość `true`.|
|Niezaznaczone|Sprawdź Państwa|Parametr <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> ma wartość `false`.|
|Nieokreślony|Sprawdź Państwa|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>jest `true`i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`jest .|
|Prawidłowe|Stan sprawdzania poprawności|Formant używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej `false`właściwości jest .|
|Nieprawidłowo skupiony|Stan sprawdzania poprawności|Dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> właściwość `true` jest i formant ma fokus.|
|Nieprawidłowy Nieskoncentrowany|Stan sprawdzania poprawności|Dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> właściwość `true` jest i formant nie ma fokusu.|

> [!NOTE]
> Jeśli nieokreślony stan wizualny nie istnieje w szablonie formantu, stan wizualizacji niezaznaczone będzie używany jako domyślny stan wizualny.

## <a name="togglebutton-controltemplate-example"></a>Przykład panelu sterowania przyciskiem przełączania

W poniższym <xref:System.Windows.Controls.ControlTemplate> przykładzie pokazano, <xref:System.Windows.Controls.Primitives.ToggleButton> jak zdefiniować formantu.

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

W poprzednim przykładzie użyto co najmniej jednego z następujących zasobów.

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

Aby uzyskać pełną próbkę, zobacz [Stylowanie za pomocą próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Tworzenie szablonu formantu](../../../desktop-wpf/themes/how-to-create-apply-template.md)
