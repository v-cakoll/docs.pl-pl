---
title: TreeView — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TreeView
- templates [WPF], TreeView
- parts [WPF], TreeView
- states [WPF], TreeView
- styles [WPF], TreeView
- TreeView [WPF], styles and templates
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
ms.openlocfilehash: 9f963e4b60193197ae56e2021d76d541ad6bfbef
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="treeview-styles-and-templates"></a>TreeView — Style i szablony
W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.TreeView> formantu. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="treeview-parts"></a>Części TreeView  
 <xref:System.Windows.Controls.TreeView> Formant nie ma żadnych części o nazwie.  
  
 Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.TreeView>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element <xref:System.Windows.Controls.TreeView>; <xref:System.Windows.Controls.ScrollViewer> włącza przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym elementu <xref:System.Windows.Controls.ScrollViewer>, musisz podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter`.  
  
## <a name="treeview-states"></a>Stany TreeView  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.TreeView> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="treeviewitem-parts"></a>Element TreeViewItem części  
 W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.TreeViewItem> formantu.  
  
|Część|Typ|Opis|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|Element wizualny, zawierające ten nagłówek zawartości <xref:System.Windows.Controls.TreeView> formantu.|  
  
## <a name="treeviewitem-states"></a>Stany TreeViewItem  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.TreeViewItem> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalny|CommonStates|Stan domyślny.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad <xref:System.Windows.Controls.TreeViewItem>.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.TreeViewItem> Jest wyłączona.|  
|Fokus|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Ma fokus.|  
|Bez fokusu|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Nie ma fokusa.|  
|Rozwinięty|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Kontroli jest rozwinięta.|  
|Zwinięte|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Kontroli jest zwinięty.|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Zawiera elementy.|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Nie ma elementów.|  
|Wybrane|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Jest zaznaczone.|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Jest wybrany, ale nie jest aktywny.|  
|Niezaznaczony|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Nie jest zaznaczone.|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="treeview-controltemplate-example"></a>Przykład ControlTemplate TreeView  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.TreeView> kontroli i jego związanych z nimi typów.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pełny przykład, zobacz [style próbki ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Style i szablony kontrolek](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Niestandardowe dostosowywanie kontrolki](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
