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
ms.openlocfilehash: 300fd8d6c6bc8a73257d71280bbb0b5565c275ec
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375561"
---
# <a name="treeview-styles-and-templates"></a>TreeView — Style i szablony
W tym temacie opisano, style i szablony <xref:System.Windows.Controls.TreeView> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="treeview-parts"></a>Części widoku drzewa  
 <xref:System.Windows.Controls.TreeView> Formant nie ma żadnych części o nazwie.  
  
 Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.TreeView>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w ramach <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element na <xref:System.Windows.Controls.TreeView>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednie podrzędne <xref:System.Windows.Controls.ScrollViewer>, należy podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter`.  
  
## <a name="treeview-states"></a>Stany TreeView  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.TreeView> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="treeviewitem-parts"></a>Części TreeViewItem  
 Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.TreeViewItem> kontroli.  
  
|Część|Typ|Opis|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|Element wizualny, który zawiera zawartość nagłówka <xref:System.Windows.Controls.TreeView> kontroli.|  
  
## <a name="treeviewitem-states"></a>Stany TreeViewItem  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.TreeViewItem> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad <xref:System.Windows.Controls.TreeViewItem>.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.TreeViewItem> Jest wyłączona.|  
|Fokus|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Jest ustawiony fokus.|  
|Po przeniesieniu fokusu|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Nie ma fokusu.|  
|Rozwinięte|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Kontroli jest rozwinięty.|  
|Zwinięty|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Kontroli jest zwinięta.|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Ma elementy.|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Nie ma elementów.|  
|Wybrane|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Jest zaznaczone.|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Jest wybrany, ale nie jest aktywny.|  
|Niezaznaczone|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Nie jest zaznaczone.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="treeview-controltemplate-example"></a>Przykład ControlTemplate TreeView  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.TreeView> kontrolki i ich skojarzone typy.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
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
