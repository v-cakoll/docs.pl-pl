---
title: TextBox — Style i szablony
description: Dowiedz się więcej na temat stylów i szablonów dla kontrolki TextBox Windows Presentation Foundation. Zmodyfikuj ControlTemplate, aby nadać formantowi unikatowy wygląd.
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 0e15fd40f5590ee46da49cc6c0d5fb30e051f7e4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164726"
---
# <a name="textbox-styles-and-templates"></a>TextBox — Style i szablony
W tym temacie opisano style i szablony dla <xref:System.Windows.Controls.TextBox> kontrolki. Można zmienić wartość domyślną, <xref:System.Windows.Controls.ControlTemplate> aby dać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="textbox-parts"></a>Elementy TextBox  
 W poniższej tabeli wymieniono nazwane części <xref:System.Windows.Controls.TextBox> formantu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|Element wizualizacji, który może zawierać <xref:System.Windows.FrameworkElement> . Tekst <xref:System.Windows.Controls.TextBox> jest wyświetlany w tym elemencie.|  
  
## <a name="textbox-states"></a>Stany pól TextBox  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.TextBox> kontrolki.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką.|  
|Disabled|CommonStates|Kontrolka jest wyłączona.|  
|ReadOnly|CommonStates|Użytkownik nie może zmienić tekstu w <xref:System.Windows.Controls.TextBox> .|  
|Ustawiono fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości to `false` .|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość ma `true` fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość ma `true` kontrolkę, która nie ma fokusu.|  
  
## <a name="textbox-controltemplate-example"></a>ControlTemplate — przykład pola tekstowego  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.TextBox> kontrolki.  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony formantu](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie formantu](control-customization.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md)
