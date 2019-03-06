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
ms.openlocfilehash: 582179d8469cabc3551e1bed53c87e045f26e7cf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366078"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid — Style i szablony
W tym temacie opisano, style i szablony <xref:System.Windows.Controls.DataGrid> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datagrid-parts"></a>Części DataGrid  
 Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.DataGrid> kontroli.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Wiersz, który zawiera nagłówki kolumn.|  
  
 Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.DataGrid>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w ramach <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element na <xref:System.Windows.Controls.DataGrid>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednie podrzędne <xref:System.Windows.Controls.ScrollViewer>, należy podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter`.  
  
 Domyślny szablon dla <xref:System.Windows.Controls.DataGrid> zawiera <xref:System.Windows.Controls.ScrollViewer> kontroli. Aby uzyskać więcej informacji na temat częściami zdefiniowanymi przez <xref:System.Windows.Controls.ScrollViewer>, zobacz [scrollviewer — style i szablony](scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>Stany DataGrid  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.DataGrid> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|InvalidFocused|ValidationStates|Kontrolka nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Kontrolka jest nieprawidłowy i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka jest nieprawidłowy.|  
  
## <a name="datagridcell-parts"></a>Części DataGridCell  
 <xref:System.Windows.Controls.DataGridCell> Element nie ma żadnych części o nazwie.  
  
## <a name="datagridcell-states"></a>Stany DataGridCell  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.DataGridCell> elementu.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad komórką.|  
|Fokus|FocusStates|Komórka jest ustawiony fokus.|  
|Po przeniesieniu fokusu|FocusStates|Komórka nie ma fokusa|  
|bieżący|CurrentStates|Komórka jest bieżącej komórki.|  
|Regularne|CurrentStates|Komórka nie jest bieżącej komórki.|  
|Monitor|InteractionStates|Komórka jest w trybie wyświetlania.|  
|Edytowanie|InteractionStates|Komórka jest w trybie edycji.|  
|Wybrane|SelectionStates|Komórka jest zaznaczone.|  
|Niezaznaczone|SelectionStates|Komórka nie jest zaznaczone.|  
|InvalidFocused|ValidationStates|Komórka nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Komórka jest nieprawidłowy i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Komórka jest nieprawidłowy.|  
  
## <a name="datagridrow-parts"></a>Części DataGridRow  
 <xref:System.Windows.Controls.DataGridRow> Element nie ma żadnych części o nazwie.  
  
## <a name="datagridrow-states"></a>Stany DataGridRow  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.DataGridRow> elementu.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad odpowiednim wierszem.|  
|MouseOver_Editing|CommonStates|Wskaźnik myszy jest umieszczony nad wiersz i wiersz jest w trybie edycji.|  
|MouseOver_Selected|CommonStates|Wskaźnik myszy jest umieszczony nad odpowiednim wierszem i zostanie wybrany wiersz.|  
|MouseOver_Unfocused_Editing|CommonStates|Wskaźnik myszy jest umieszczony nad odpowiednim wierszem, wiersza znajduje się w trybie edycji i nie ma fokusu.|  
|MouseOver_Unfocused_Selected|CommonStates|Wskaźnik myszy jest umieszczony nad odpowiednim wierszem, wiersz jest zaznaczone, a nie ma fokusu.|  
|Normal_AlternatingRow|CommonStates|Wiersz jest wierszem przemienne.|  
|Normal_Editing|CommonStates|Wiersz jest w trybie edycji.|  
|Normal_Selected|CommonStates|Wiersz jest zaznaczone.|  
|Unfocused_Editing|CommonStates|Wiersz jest w trybie edycji i nie ma fokusu.|  
|Unfocused_Selected|CommonStates|Wiersz jest zaznaczone i nie ma fokusu.|  
|InvalidFocused|ValidationStates|Kontrolka nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Kontrolka jest nieprawidłowy i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka jest nieprawidłowy.|  
  
## <a name="datagridrowheader-parts"></a>Części DataGridRowHeader  
 Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.Primitives.DataGridRowHeader> elementu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który służy do zmiany rozmiaru nagłówka z góry.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który służy do zmiany rozmiaru nagłówka z dołu.|  
  
## <a name="datagridrowheader-states"></a>Stany DataGridRowHeader  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.DataGridRowHeader> elementu.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad odpowiednim wierszem.|  
|MouseOver_CurrentRow|CommonStates|Wskaźnik myszy jest umieszczony nad wiersz i wiersz jest bieżący wiersz.|  
|MouseOver_CurrentRow_Selected|CommonStates|Wskaźnik myszy jest umieszczony nad odpowiednim wierszem, a wiersz jest bieżące i wybrane.|  
|MouseOver_EditingRow|CommonStates|Wskaźnik myszy jest umieszczony nad wiersz i wiersz jest w trybie edycji.|  
|MouseOver_Selected|CommonStates|Wskaźnik myszy jest umieszczony nad odpowiednim wierszem i zostanie wybrany wiersz.|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|Umieść wskaźnik myszy nad odpowiednim wierszem, są aktualne i wybrany wiersz, a nie ma fokusu.|  
|MouseOver_Unfocused_EditingRow|CommonStates|Wskaźnik myszy jest umieszczony nad odpowiednim wierszem, wiersza znajduje się w trybie edycji i nie ma fokusu.|  
|MouseOver_Unfocused_Selected|CommonStates|Wskaźnik myszy jest umieszczony nad odpowiednim wierszem, wiersz jest zaznaczone, a nie ma fokusu.|  
|Normal_CurrentRow|CommonStates|Wiersz jest bieżący wiersz.|  
|Normal_CurrentRow_Selected|CommonStates|Wiersz jest bieżący wiersz i jest zaznaczone.|  
|Normal_EditingRow|CommonStates|Wiersz jest w trybie edycji.|  
|Normal_Selected|CommonStates|Wiersz jest zaznaczone.|  
|Unfocused_CurrentRow_Selected|CommonStates|Wiersz jest bieżący wiersz, jest zaznaczone, a nie ma fokusu.|  
|Unfocused_EditingRow|CommonStates|Wiersz jest w trybie edycji i nie ma fokusu.|  
|Unfocused_Selected|CommonStates|Wiersz jest zaznaczone i nie ma fokusu.|  
|InvalidFocused|ValidationStates|Kontrolka nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Kontrolka jest nieprawidłowy i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka jest nieprawidłowy.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>Części DataGridColumnHeadersPresenter  
 Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> elementu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Symbol zastępczy dla nagłówków kolumn.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>Stany DataGridColumnHeadersPresenter  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> elementu.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|InvalidFocused|ValidationStates|Komórka nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Komórka jest nieprawidłowy i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Komórka jest nieprawidłowy.|  
  
## <a name="datagridcolumnheader-parts"></a>Części DataGridColumnHeader  
 Poniższa tabela zawiera listę nazwanych części do <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> elementu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który służy do zmiany rozmiaru nagłówka kolumny z lewej strony.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Element, który służy do zmiany rozmiaru nagłówka kolumny z prawej strony.|  
  
## <a name="datagridcolumnheader-states"></a>Stany DataGridColumnHeader  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> elementu.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad kontrolką.|  
|Naciśnięto|CommonStates|Użytkownik naciśnie kontrolkę.|  
|SortAscending|SortStates|Kolumna jest sortowany w kolejności rosnącej.|  
|SortDescending|SortStates|Kolumna jest sortowany w kolejności malejącej.|  
|Nieposortowane|SortStates|Kolumna nie jest posortowana.|  
|InvalidFocused|ValidationStates|Kontrolka nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Kontrolka jest nieprawidłowy i nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka jest nieprawidłowy.|  
  
## <a name="datagrid-controltemplate-example"></a>Przykład ControlTemplate DataGrid  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.DataGrid> kontrolki i ich skojarzone typy.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
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
