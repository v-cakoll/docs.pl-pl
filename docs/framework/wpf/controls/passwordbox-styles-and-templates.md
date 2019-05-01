---
title: PasswordBox — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 7783330dd56ec5b2759e783a6935761eb3587978
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770646"
---
# <a name="passwordbox-styles-and-templates"></a>PasswordBox — Style i szablony

W tym temacie opisano, style i szablony <xref:System.Windows.Controls.PasswordBox> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).

## <a name="passwordbox-parts"></a>Części PasswordBox

Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.PasswordBox> kontroli.

|Część|Typ|Opis|
|-|-|-|
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|Element wizualny, który może zawierać <xref:System.Windows.FrameworkElement>. Tekst <xref:System.Windows.Controls.PasswordBox> jest wyświetlana w tym elemencie.|

## <a name="passwordbox-states"></a>Stany PasswordBox

Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.PasswordBox> kontroli.

|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|
|-|-|-|
|Normalne|CommonStates|Stan domyślny.|
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad kontrolką.|
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|
|Fokus|FocusStates|Kontrolka ma fokus.|
|Po przeniesieniu fokusu|FocusStates|Kontrolka nie ma fokusu.|
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|

## <a name="passwordbox-controltemplate-example"></a>Przykład ControlTemplate PasswordBox

Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.PasswordBox> kontroli.

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

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
