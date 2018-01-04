---
title: "DataGrid — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fd9b374f9e2c367daa9869862ab717828049887
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="datagrid-styles-and-templates"></a>DataGrid — Style i szablony
W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.DataGrid> formantu. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datagrid-parts"></a>Części DataGrid  
 W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.DataGrid> formantu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Wiersz, który zawiera nagłówki kolumn.|  
  
 Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.DataGrid>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element <xref:System.Windows.Controls.DataGrid>; <xref:System.Windows.Controls.ScrollViewer> włącza przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym elementu <xref:System.Windows.Controls.ScrollViewer>, musisz podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter`.  
  
 Szablon domyślny <xref:System.Windows.Controls.DataGrid> zawiera <xref:System.Windows.Controls.ScrollViewer> formantu. Aby uzyskać więcej informacji o części zdefiniowanych przez <xref:System.Windows.Controls.ScrollViewer>, zobacz [ScrollViewer style i szablony](../../../../docs/framework/wpf/controls/scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>Stany DataGrid  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.DataGrid> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|InvalidFocused|ValidationStates|Formant nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Formant jest nieprawidłowy i nie ma fokusa.|  
|Prawidłowe|ValidationStates|Formant jest nieprawidłowy.|  
  
## <a name="datagridcell-parts"></a>Części DataGridCell  
 <xref:System.Windows.Controls.DataGridCell> Element nie ma żadnych części o nazwie.  
  
## <a name="datagridcell-states"></a>Stany DataGridCell  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.DataGridCell> elementu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad komórką.|  
|Fokus|FocusStates|Komórki ma fokus.|  
|Bez fokusu|FocusStates|Komórka nie ma fokusu|  
|Bieżący|CurrentStates|Komórka jest bieżącej komórki.|  
|Regularne|CurrentStates|Komórka nie jest bieżącą komórką.|  
|Monitor|InteractionStates|Komórka jest w trybie wyświetlania.|  
|Edytowanie|InteractionStates|Komórka jest w trybie edycji.|  
|Wybrane|SelectionStates|Wybrano komórki.|  
|Niezaznaczony|SelectionStates|Nie wybrano komórki.|  
|InvalidFocused|ValidationStates|Komórki nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Komórka jest nieprawidłowa i nie ma fokusa.|  
|Prawidłowe|ValidationStates|Komórka jest nieprawidłowy.|  
  
## <a name="datagridrow-parts"></a>Element DataGridRow części  
 <xref:System.Windows.Controls.DataGridRow> Element nie ma żadnych części o nazwie.  
  
## <a name="datagridrow-states"></a>Element DataGridRow stanów  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.DataGridRow> elementu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad wiersza.|  
|MouseOver_Editing|CommonStates|Wskaźnik myszy znajduje się nad wiersz i wiersz jest w trybie edycji.|  
|MouseOver_Selected|CommonStates|Wskaźnik myszy znajduje się nad wiersz i wiersz jest zaznaczone.|  
|MouseOver_Unfocused_Editing|CommonStates|Wskaźnik myszy znajduje się nad wiersza, wiersz jest w trybie edycji i nie ma fokusa.|  
|MouseOver_Unfocused_Selected|CommonStates|Wskaźnik myszy znajduje się nad wiersza, wiersz jest zaznaczone, a nie ma fokusa.|  
|Normal_AlternatingRow|CommonStates|Wiersz jest przemiennych wierszy.|  
|Normal_Editing|CommonStates|Wiersz jest w trybie edycji.|  
|Normal_Selected|CommonStates|Wiersz jest zaznaczone.|  
|Unfocused_Editing|CommonStates|Wiersz jest w trybie edycji i nie ma fokusa.|  
|Unfocused_Selected|CommonStates|Wiersz jest zaznaczona i nie ma fokusa.|  
|InvalidFocused|ValidationStates|Formant nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Formant jest nieprawidłowy i nie ma fokusa.|  
|Prawidłowe|ValidationStates|Formant jest nieprawidłowy.|  
  
## <a name="datagridrowheader-parts"></a>Części DataGridRowHeader  
 W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Primitives.DataGridRowHeader> elementu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który służy do zmiany rozmiaru nagłówka wiersza od góry.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który służy do zmiany rozmiaru nagłówka wiersza w dolnej.|  
  
## <a name="datagridrowheader-states"></a>Stany DataGridRowHeader  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.DataGridRowHeader> elementu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad wiersza.|  
|MouseOver_CurrentRow|CommonStates|Wskaźnik myszy znajduje się nad wiersz i wiersz jest bieżącego wiersza.|  
|MouseOver_CurrentRow_Selected|CommonStates|Wskaźnik myszy znajduje się nad wiersz i wiersz jest bieżącego i wybranych.|  
|MouseOver_EditingRow|CommonStates|Wskaźnik myszy znajduje się nad wiersz i wiersz jest w trybie edycji.|  
|MouseOver_Selected|CommonStates|Wskaźnik myszy znajduje się nad wiersz i wiersz jest zaznaczone.|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|Wskaźnik myszy znajduje się na wiersza, są aktualne i wybranego wiersza, a nie ma fokusa.|  
|MouseOver_Unfocused_EditingRow|CommonStates|Wskaźnik myszy znajduje się nad wiersza, wiersz jest w trybie edycji i nie ma fokusa.|  
|MouseOver_Unfocused_Selected|CommonStates|Wskaźnik myszy znajduje się nad wiersza, wiersz jest zaznaczone, a nie ma fokusa.|  
|Normal_CurrentRow|CommonStates|Wiersz jest bieżącego wiersza.|  
|Normal_CurrentRow_Selected|CommonStates|Wiersz jest bieżący wiersz i jest zaznaczone.|  
|Normal_EditingRow|CommonStates|Wiersz jest w trybie edycji.|  
|Normal_Selected|CommonStates|Wiersz jest zaznaczone.|  
|Unfocused_CurrentRow_Selected|CommonStates|Wiersz jest bieżący wiersz, jest zaznaczone, a nie ma fokusa.|  
|Unfocused_EditingRow|CommonStates|Wiersz jest w trybie edycji i nie ma fokusa.|  
|Unfocused_Selected|CommonStates|Wiersz jest zaznaczona i nie ma fokusa.|  
|InvalidFocused|ValidationStates|Formant nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Formant jest nieprawidłowy i nie ma fokusa.|  
|Prawidłowe|ValidationStates|Formant jest nieprawidłowy.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>Części DataGridColumnHeadersPresenter  
 W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> elementu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Symbol zastępczy dla nagłówków kolumn.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>Stany DataGridColumnHeadersPresenter  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> elementu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|InvalidFocused|ValidationStates|Komórki nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Komórka jest nieprawidłowa i nie ma fokusa.|  
|Prawidłowe|ValidationStates|Komórka jest nieprawidłowy.|  
  
## <a name="datagridcolumnheader-parts"></a>Elementy nagłówka DataGridColumnHeader  
 W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> elementu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który służy do zmiany rozmiaru nagłówka kolumny z lewej strony.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który służy do zmiany rozmiaru nagłówka kolumny z prawej strony.|  
  
## <a name="datagridcolumnheader-states"></a>Stany nagłówka DataGridColumnHeader  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> elementu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad formantem.|  
|Naciśnięto|CommonStates|Formant zostanie naciśnięty.|  
|SortAscending|SortStates|Kolumna jest sortowany w kolejności rosnącej.|  
|SortDescending|SortStates|Kolumna jest sortowany w kolejności malejącej.|  
|Nieposortowane|SortStates|Kolumna nie jest posortowana.|  
|InvalidFocused|ValidationStates|Formant nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Formant jest nieprawidłowy i nie ma fokusa.|  
|Prawidłowe|ValidationStates|Formant jest nieprawidłowy.|  
  
## <a name="datagrid-controltemplate-example"></a>Przykład ControlTemplate DataGrid  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.DataGrid> kontroli i jego związanych z nimi typów.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Style i szablony kontrolek](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Niestandardowe dostosowywanie kontrolki](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
