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
ms.openlocfilehash: 45276d23380fe956fc3d59b90d5baae23ee8a7e2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283633"
---
# <a name="treeview-styles-and-templates"></a>TreeView — Style i szablony
W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.TreeView>. Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="treeview-parts"></a>Elementy TreeView  
 Formant <xref:System.Windows.Controls.TreeView> nie zawiera żadnych nazwanych części.  
  
 Podczas tworzenia <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.TreeView>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>. (<xref:System.Windows.Controls.ItemsPresenter> wyświetla każdy element w <xref:System.Windows.Controls.TreeView>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym <xref:System.Windows.Controls.ScrollViewer>, należy nadać <xref:System.Windows.Controls.ItemsPresenter> nazwę `ItemsPresenter`.  
  
## <a name="treeview-states"></a>Stany TreeView  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.TreeView>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="treeviewitem-parts"></a>TreeViewItem części  
 W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.TreeViewItem>.  
  
|Części|Typ|Opis|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|Element wizualizacji, który zawiera tę zawartość nagłówka kontrolki <xref:System.Windows.Controls.TreeView>.|  
  
## <a name="treeviewitem-states"></a>Stany TreeViewItem  
 Poniższa tabela zawiera listę stanów wizualnych dla formantu <xref:System.Windows.Controls.TreeViewItem>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad <xref:System.Windows.Controls.TreeViewItem>.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.TreeViewItem> jest wyłączona.|  
|Fokus|FocusStates|<xref:System.Windows.Controls.TreeViewItem> ma fokus.|  
|Bez fokusu|FocusStates|<xref:System.Windows.Controls.TreeViewItem> nie ma fokusu.|  
|Pakowane|ExpansionStates|Formant <xref:System.Windows.Controls.TreeViewItem> jest rozwinięty.|  
|Zwinięte|ExpansionStates|Formant <xref:System.Windows.Controls.TreeViewItem> jest zwinięty.|  
|Do odczytu HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> zawiera elementy.|  
|Noitems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> nie ma elementów.|  
|Wybrane|SelectionStates|Wybrano <xref:System.Windows.Controls.TreeViewItem>.|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> jest zaznaczone, ale nie jest aktywne.|  
|Niezaznaczone|SelectionStates|Nie wybrano <xref:System.Windows.Controls.TreeViewItem>.|  
|Prawidłowe|ValidationStates|Kontrolka używa klasy <xref:System.Windows.Controls.Validation> i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości jest `false`.|  
|InvalidFocused|ValidationStates|Właściwość dołączona <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true` ma fokus.|  
|InvalidUnfocused|ValidationStates|Dołączona właściwość <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest `true`, która nie ma fokusu.|  
  
## <a name="treeview-controltemplate-example"></a>Przykład ControlTemplate TreeView  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.TreeView> i skojarzonych z nią typów.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 W poprzednim przykładzie jest użyty co najmniej jeden z poniższych zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md)
