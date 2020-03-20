---
title: GroupBox — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187481"
---
# <a name="groupbox-styles-and-templates"></a>GroupBox — Style i szablony
<a name="introduction"></a>W tym temacie opisano style <xref:System.Windows.Controls.GroupBox> i szablony formantu. Można zmodyfikować <xref:System.Windows.Controls.ControlTemplate> wartość domyślną, aby nadać formancie unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu formantu](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a>Części GroupBox  
 Formant <xref:System.Windows.Controls.GroupBox> nie ma żadnych nazwanych części.  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a>Stany GroupBox  
 W poniższej tabeli wymieniono stany wizualne formantu. <xref:System.Windows.Controls.GroupBox>  
  
|Nazwa visualstate|Nazwa grupy programu VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|Stan sprawdzania poprawności|Formant używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej `false`właściwości jest .|  
|Nieprawidłowo skupiony|Stan sprawdzania poprawności|Dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> właściwość `true` ma formant ma fokus.|  
|Nieprawidłowy Nieskoncentrowany|Stan sprawdzania poprawności|Dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> właściwość `true` ma formant nie ma fokusu.|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a>Przykład controltemplate skrzynki grupowej  
 W poniższym <xref:System.Windows.Controls.ControlTemplate> przykładzie pokazano, <xref:System.Windows.Controls.GroupBox> jak zdefiniować formantu.  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 Używa <xref:System.Windows.Controls.ControlTemplate> co najmniej jednego z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełną próbkę, zobacz [Stylowanie za pomocą próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Tworzenie szablonu formantu](../../../desktop-wpf/themes/how-to-create-apply-template.md)
