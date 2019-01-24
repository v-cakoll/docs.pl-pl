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
ms.openlocfilehash: 66e9f5d45a4c9b3a04291a8ebbf054ebc055b5a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643640"
---
# <a name="listview-styles-and-templates"></a>ListView — Style i szablony
W tym temacie opisano, style i szablony <xref:System.Windows.Controls.ListView> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="listview-parts"></a>Elementy w ListView  
 <xref:System.Windows.Controls.ListView> Formant nie ma żadnych części o nazwie.  
  
 Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ListView>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w ramach <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element na <xref:System.Windows.Controls.ListView>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednie podrzędne <xref:System.Windows.Controls.ScrollViewer>, należy podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter`.  
  
## <a name="listview-states"></a>Stany ListView  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.ListView> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="listviewitem-parts"></a>Części ListViewItem  
 <xref:System.Windows.Controls.ListViewItem> Formant nie ma żadnych części o nazwie.  
  
## <a name="listviewitem-states"></a>Stany ListViewItem  
 W poniższej tabeli wymieniono stany <xref:System.Windows.Controls.ListViewItem> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad <xref:System.Windows.Controls.ComboBox> kontroli.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Po przeniesieniu fokusu|FocusStates|Kontrolka nie ma fokusu.|  
|Wybrane|SelectionStates|Element jest aktualnie wybrany.|  
|Niezaznaczone|SelectionStates|Nie wybrano elementu.|  
|SelectedUnfocused|SelectionStates|Element jest wybrany, ale nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="listview-controltemplate-examples"></a>Przykłady ListView ControlTemplate  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ListView> kontrolki i ich skojarzone typy.  
  
 [!code-xaml[ControlTemplateExamples#ListView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listview.xaml#listview)]  
  
 <xref:System.Windows.Controls.ControlTemplate> Przykładach użyto co najmniej jeden z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](../../../../docs/framework/wpf/controls/control-customization.md)
- [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
