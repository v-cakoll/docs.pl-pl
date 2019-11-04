---
title: ListView — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ListView
- states [WPF], ListView
- ControlTemplate [WPF], ListView
- styles [WPF], ListView
- ListView [WPF], styles and templates
- templates [WPF], ListView
ms.assetid: d2387356-2171-4785-822a-7247e024b4ee
ms.openlocfilehash: 5f5a9d9f747246ee9b72b42a45291a42bb04cb88
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459380"
---
# <a name="listview-styles-and-templates"></a>ListView — Style i szablony
W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.ListView>. Możesz zmodyfikować wartość domyślną <xref:System.Windows.Controls.ControlTemplate>, aby dać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="listview-parts"></a>Elementy ListView  
 Formant <xref:System.Windows.Controls.ListView> nie zawiera żadnych nazwanych części.  
  
 Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ListView>szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>. (<xref:System.Windows.Controls.ItemsPresenter> wyświetla każdy element w <xref:System.Windows.Controls.ListView>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym <xref:System.Windows.Controls.ScrollViewer>, należy nadać <xref:System.Windows.Controls.ItemsPresenter> nazwę `ItemsPresenter`.  
  
## <a name="listview-states"></a>Stany elementu ListView  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.ListView>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="listviewitem-parts"></a>Elementy ListViewItem  
 Formant <xref:System.Windows.Controls.ListViewItem> nie zawiera żadnych nazwanych części.  
  
## <a name="listviewitem-states"></a>Stany ListViewItem  
 W poniższej tabeli wymieniono Stany formantu <xref:System.Windows.Controls.ListViewItem>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Typow|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką <xref:System.Windows.Controls.ComboBox>.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Niezaznaczone|SelectionStates|Element jest obecnie zaznaczony.|  
|Niezaznaczone|SelectionStates|Nie wybrano elementu.|  
|SelectedUnfocused|SelectionStates|Element jest zaznaczony, ale nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="listview-controltemplate-examples"></a>Przykłady elementu ListView ControlTemplate  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.ListView> i skojarzonych z nią typów.  
  
 [!code-xaml[ControlTemplateExamples#ListView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listview.xaml#listview)]  
  
 W <xref:System.Windows.Controls.ControlTemplate> przykładach użyto co najmniej jednego z poniższych zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
