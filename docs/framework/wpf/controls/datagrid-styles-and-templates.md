---
title: DataGrid — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
ms.openlocfilehash: 066e8c9ce1112399be8128d0821498f0d56a3dc3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283803"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid — Style i szablony
W tym temacie opisano style i szablony dla kontrolki <xref:System.Windows.Controls.DataGrid>. Możesz zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate>, aby nadać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="datagrid-parts"></a>DataGrid — części  
 W poniższej tabeli wymieniono nazwane części formantu <xref:System.Windows.Controls.DataGrid>.  
  
|Części|Typ|Opis|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Wiersz zawierający nagłówki kolumn.|  
  
 Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.DataGrid>szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>. (<xref:System.Windows.Controls.ItemsPresenter> wyświetla każdy element w <xref:System.Windows.Controls.DataGrid>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym <xref:System.Windows.Controls.ScrollViewer>, należy nadać <xref:System.Windows.Controls.ItemsPresenter> nazwę `ItemsPresenter`.  
  
 Szablon domyślny <xref:System.Windows.Controls.DataGrid> zawiera kontrolkę <xref:System.Windows.Controls.ScrollViewer>. Aby uzyskać więcej informacji na temat części zdefiniowanych przez <xref:System.Windows.Controls.ScrollViewer>, zobacz [Style i szablony ScrollViewer](scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>Stany DataGrid  
 Poniższa tabela zawiera listę stanów wizualnych dla kontrolki <xref:System.Windows.Controls.DataGrid>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|InvalidFocused|ValidationStates|Formant jest nieprawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Formant jest nieprawidłowy i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Formant jest prawidłowy.|  
  
## <a name="datagridcell-parts"></a>DataGridCell części  
 Element <xref:System.Windows.Controls.DataGridCell> nie zawiera żadnych nazwanych części.  
  
## <a name="datagridcell-states"></a>Stany DataGridCell  
 Poniższa tabela zawiera listę stanów wizualnych elementu <xref:System.Windows.Controls.DataGridCell>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad komórką.|  
|Fokus|FocusStates|Komórka ma fokus.|  
|Bez fokusu|FocusStates|Komórka nie ma fokusu.|  
|Obecne|CurrentStates|Komórka jest bieżącą komórką.|  
|Ustalon|CurrentStates|Komórka nie jest bieżącą komórką.|  
|Monitor|InteractionStates|Komórka jest w trybie wyświetlania.|  
|Edytowanie|InteractionStates|Komórka jest w trybie edycji.|  
|Wybrane|SelectionStates|Komórka jest zaznaczona.|  
|Niezaznaczone|SelectionStates|Komórka nie jest zaznaczona.|  
|InvalidFocused|ValidationStates|Komórka jest nieprawidłowa i ma fokus.|  
|InvalidUnfocused|ValidationStates|Komórka jest nieprawidłowa i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Komórka jest prawidłowa.|  
  
## <a name="datagridrow-parts"></a>DataGridRow części  
 Element <xref:System.Windows.Controls.DataGridRow> nie zawiera żadnych nazwanych części.  
  
## <a name="datagridrow-states"></a>Stany DataGridRow  
 Poniższa tabela zawiera listę stanów wizualnych elementu <xref:System.Windows.Controls.DataGridRow>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad wierszem.|  
|MouseOver_Editing|CommonStates|Wskaźnik myszy znajduje się nad wierszem, a wiersz jest w trybie edycji.|  
|MouseOver_Selected|CommonStates|Wskaźnik myszy znajduje się nad wierszem, a wiersz jest zaznaczony.|  
|MouseOver_Unfocused_Editing|CommonStates|Wskaźnik myszy znajduje się nad wierszem, wiersz jest w trybie edycji i nie ma fokusu.|  
|MouseOver_Unfocused_Selected|CommonStates|Wskaźnik myszy znajduje się nad wierszem, wiersz jest zaznaczony i nie ma fokusu.|  
|Normal_AlternatingRow|CommonStates|Wiersz jest przemiennym wierszem.|  
|Normal_Editing|CommonStates|Wiersz jest w trybie edycji.|  
|Normal_Selected|CommonStates|Wiersz jest zaznaczony.|  
|Unfocused_Editing|CommonStates|Wiersz jest w trybie edycji i nie ma fokusu.|  
|Unfocused_Selected|CommonStates|Wiersz jest zaznaczony i nie ma fokusu.|  
|InvalidFocused|ValidationStates|Formant jest nieprawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Formant jest nieprawidłowy i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Formant jest prawidłowy.|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader części  
 Poniższa tabela zawiera listę nazwanych elementów dla elementu <xref:System.Windows.Controls.Primitives.DataGridRowHeader>.  
  
|Części|Typ|Opis|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który jest używany do zmiany rozmiaru nagłówka wiersza od góry.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który jest używany do zmiany rozmiaru nagłówka wiersza od dołu.|  
  
## <a name="datagridrowheader-states"></a>Stany DataGridRowHeader  
 Poniższa tabela zawiera listę stanów wizualnych elementu <xref:System.Windows.Controls.Primitives.DataGridRowHeader>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad wierszem.|  
|MouseOver_CurrentRow|CommonStates|Wskaźnik myszy znajduje się nad wierszem, a wiersz jest bieżącym wierszem.|  
|MouseOver_CurrentRow_Selected|CommonStates|Wskaźnik myszy znajduje się nad wierszem, a wiersz jest bieżący i wybrany.|  
|MouseOver_EditingRow|CommonStates|Wskaźnik myszy znajduje się nad wierszem, a wiersz jest w trybie edycji.|  
|MouseOver_Selected|CommonStates|Wskaźnik myszy znajduje się nad wierszem, a wiersz jest zaznaczony.|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|Wskaźnik myszy znajduje się nad wierszem, wiersz jest bieżący i zaznaczony i nie ma fokusu.|  
|MouseOver_Unfocused_EditingRow|CommonStates|Wskaźnik myszy znajduje się nad wierszem, wiersz jest w trybie edycji i nie ma fokusu.|  
|MouseOver_Unfocused_Selected|CommonStates|Wskaźnik myszy znajduje się nad wierszem, wiersz jest zaznaczony i nie ma fokusu.|  
|Normal_CurrentRow|CommonStates|Wiersz jest bieżącym wierszem.|  
|Normal_CurrentRow_Selected|CommonStates|Wiersz jest bieżącym wierszem i jest wybrany.|  
|Normal_EditingRow|CommonStates|Wiersz jest w trybie edycji.|  
|Normal_Selected|CommonStates|Wiersz jest zaznaczony.|  
|Unfocused_CurrentRow_Selected|CommonStates|Wiersz jest bieżącym wierszem, jest zaznaczony i nie ma fokusu.|  
|Unfocused_EditingRow|CommonStates|Wiersz jest w trybie edycji i nie ma fokusu.|  
|Unfocused_Selected|CommonStates|Wiersz jest zaznaczony i nie ma fokusu.|  
|InvalidFocused|ValidationStates|Formant jest nieprawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Formant jest nieprawidłowy i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Formant jest prawidłowy.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter części  
 Poniższa tabela zawiera listę nazwanych elementów dla elementu <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>.  
  
|Części|Typ|Opis|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Symbol zastępczy nagłówków kolumn.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>Stany DataGridColumnHeadersPresenter  
 Poniższa tabela zawiera listę stanów wizualnych elementu <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|InvalidFocused|ValidationStates|Komórka jest nieprawidłowa i ma fokus.|  
|InvalidUnfocused|ValidationStates|Komórka jest nieprawidłowa i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Komórka jest prawidłowa.|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader części  
 Poniższa tabela zawiera listę nazwanych elementów dla elementu <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.  
  
|Części|Typ|Opis|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który jest używany do zmiany rozmiaru nagłówka kolumny z lewej strony.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który jest używany do zmiany rozmiaru nagłówka kolumny z prawej strony.|  
  
## <a name="datagridcolumnheader-states"></a>Stany DataGridColumnHeader  
 Poniższa tabela zawiera listę stanów wizualnych elementu <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką.|  
|Naciśnięto|CommonStates|Kontrolka zostanie naciśnięty.|  
|SortAscending|SortStates|Kolumna jest sortowana w kolejności rosnącej.|  
|SortDescending|SortStates|Kolumna jest sortowana w kolejności malejącej.|  
|Nieposortowane|SortStates|Kolumna nie jest posortowana.|  
|InvalidFocused|ValidationStates|Formant jest nieprawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Formant jest nieprawidłowy i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Formant jest prawidłowy.|  
  
## <a name="datagrid-controltemplate-example"></a>Przykład ControlTemplate DataGrid  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla kontrolki <xref:System.Windows.Controls.DataGrid> i skojarzonych z nią typów.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
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
