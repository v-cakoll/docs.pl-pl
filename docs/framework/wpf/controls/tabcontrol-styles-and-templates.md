---
title: TabControl — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TabControl
- TabControl [WPF], styles and templates [WPF]
- parts [WPF], TabControl
- styles [WPF], TabControl
- states [WPF], TabControl
- templates [WPF], TabControl
ms.assetid: f6b19a30-f10e-4fa1-96ce-f17a54092ab6
ms.openlocfilehash: 32ee86e2388808739a2c2ff5a02bb40fc641129b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460535"
---
# <a name="tabcontrol-styles-and-templates"></a>TabControl — Style i szablony
W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.TabControl>. Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="tabcontrol-parts"></a>Elementy TabControl  
 W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.TabControl>.  
  
|Części|Typ|Opis|  
|-|-|-|  
|PART_SelectedContentHost|<xref:System.Windows.Controls.ContentPresenter>|Obiekt, który pokazuje zawartość aktualnie wybranego <xref:System.Windows.Controls.TabItem>.|  
  
 Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.TabControl>szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>. (<xref:System.Windows.Controls.ItemsPresenter> wyświetla każdy element w <xref:System.Windows.Controls.TabControl>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym <xref:System.Windows.Controls.ScrollViewer>, należy nadać <xref:System.Windows.Controls.ItemsPresenter> nazwę `ItemsPresenter`.  
  
## <a name="tabcontrol-states"></a>Stany TabControl  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.TabControl>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Typow|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="tabitem-parts"></a>TabItem części  
 Formant <xref:System.Windows.Controls.TabItem> nie zawiera żadnych nazwanych części.  
  
## <a name="tabitem-states"></a>Stany TabItem  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.TabItem>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Typow|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Niezaznaczone|SelectionStates|Kontrolka jest zaznaczona.|  
|Niezaznaczone|SelectionStates|Kontrolka nie jest zaznaczona.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="tabcontrol-controltemplate-example"></a>Przykład ControlTemplate TabControl  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolek <xref:System.Windows.Controls.TabControl> i <xref:System.Windows.Controls.TabItem>.  
  
 [!code-xaml[ControlTemplateExamples#TabControl](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tabcontrol.xaml#tabcontrol)]  
  
 W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
