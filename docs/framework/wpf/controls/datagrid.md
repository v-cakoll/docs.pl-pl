---
title: DataGrid
description: Dowiedz się, w jaki sposób formant DataGrid umożliwia wyświetlanie i edytowanie danych z różnych źródeł, takich jak baza danych, zapytanie LINQ lub inne źródło danych możliwe do powiązania.
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid column types [WPF]
- DataGrid scenarios [WPF]
- DataGrid control [WPF]
- controls [WPF], DataGrid
- DataGrid [WPF], common tasks for
- DataGrid [WPF], customizing the appearance of
- DataGrid columns [WPF], using
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
ms.openlocfilehash: 3db49c12fcb363ef7f99e5c69beae09ab05addcf
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168324"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid>Kontrolka umożliwia wyświetlanie i edytowanie danych z wielu różnych źródeł, takich jak z bazy danych SQL, programu LINQ Query lub dowolnego innego źródła danych możliwego do powiązania. Aby uzyskać więcej informacji, zobacz [Omówienie źródeł powiązań](../data/binding-sources-overview.md).  
  
 Kolumny mogą wyświetlać tekst, kontrolki, takie jak <xref:System.Windows.Controls.ComboBox> , lub inne zawartość WPF, takie jak obrazy, przyciski lub zawartość w szablonie. Możesz użyć, <xref:System.Windows.Controls.DataGridTemplateColumn> Aby wyświetlić dane zdefiniowane w szablonie. Poniższa tabela zawiera listę typów kolumn, które są udostępniane domyślnie.  
  
|Wygenerowany typ kolumny|Typ danych|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>można dostosować w wyglądzie, np. czcionkę komórki, kolor i rozmiar. <xref:System.Windows.Controls.DataGrid>obsługuje wszystkie funkcje stylów i tworzenia szablonów innych formantów WPF. <xref:System.Windows.Controls.DataGrid>zawiera również domyślne i dostosowywalne zachowania do edycji, sortowania i walidacji.  
  
 W poniższej tabeli wymieniono niektóre typowe zadania <xref:System.Windows.Controls.DataGrid> i sposoby ich wykonania. Wyświetlając powiązany interfejs API, można znaleźć więcej informacji i przykładowy kod.  
  
|Scenariusz|Podejście|  
|--------------|--------------|  
|Przemienne kolory tła|Ustaw <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> Właściwość na wartość 2 lub więcej, a następnie przypisz <xref:System.Windows.Media.Brush> do <xref:System.Windows.Controls.DataGrid.RowBackground%2A> <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> właściwości i.|  
|Zdefiniuj zachowanie wyboru komórki i wiersza|Ustaw <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> właściwości i <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> .|  
|Dostosuj wygląd nagłówków, komórek i wierszy wizualizacji|Zastosuj nową <xref:System.Windows.Style> do <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A> <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A> właściwości,, <xref:System.Windows.Controls.DataGrid.CellStyle%2A> lub <xref:System.Windows.Controls.DataGrid.RowStyle%2A> .|  
|Ustawianie opcji ustalania wielkości|Ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwości, <xref:System.Windows.FrameworkElement.MaxHeight%2A> , <xref:System.Windows.FrameworkElement.MinHeight%2A> , <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.FrameworkElement.MaxWidth%2A> lub <xref:System.Windows.FrameworkElement.MinWidth%2A> . Aby uzyskać więcej informacji, zobacz [Opcje ustalania rozmiarów w kontrolce DataGrid](sizing-options-in-the-datagrid-control.md).|  
|Dostęp do wybranych elementów|Sprawdź <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> Właściwość, aby pobrać zaznaczone komórki i <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> Właściwość w celu pobrania wybranych wierszy. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Dostosowywanie interakcji użytkowników końcowych|Ustaw <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A> właściwości, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A> , <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A> , <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A> , <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A> i <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> .|  
|Anuluj lub Zmień automatycznie generowane kolumny|Obsłuż <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> zdarzenie.|  
|Zablokuj kolumnę|Ustaw <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> Właściwość na 1 i Przenieś kolumnę do lewej strony, ustawiając <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> Właściwość na 0.|  
|Używanie danych XML jako źródła danych|Powiąż <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> na <xref:System.Windows.Controls.DataGrid> zapytanie XPath, które reprezentuje kolekcję elementów. Utwórz każdą kolumnę w <xref:System.Windows.Controls.DataGrid> . Powiąż każdą kolumnę, ustawiając wyrażenie XPath dla powiązania z zapytaniem, które pobiera właściwość w źródle elementu. Aby zapoznać się z przykładem, zobacz <xref:System.Windows.Controls.DataGridTextColumn> .|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: wyświetlanie danych z serwera bazy danych SQL w kontrolce DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Opisuje sposób skonfigurowania nowego projektu WPF, dodania elementu Entity Framework, ustawienia źródła i wyświetlenia danych w <xref:System.Windows.Controls.DataGrid> .|  
|[Instrukcje: dodawanie szczegółów wiersza do kontrolki DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|Opisuje sposób tworzenia szczegółowych informacji o wierszach dla <xref:System.Windows.Controls.DataGrid> .|  
|[Instrukcje: implementowanie weryfikowania za pomocą kontrolki DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|Opisuje sposób sprawdzania poprawności wartości w <xref:System.Windows.Controls.DataGrid> komórkach i wierszach oraz wyświetlanie informacji zwrotnych.|  
|[Domyślne zachowanie myszy i klawiatury w formancie DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Opisuje sposób korzystania z formantu przy <xref:System.Windows.Controls.DataGrid> użyciu klawiatury i myszy.|  
|[Instrukcje: grupowanie, sortowanie i filtrowanie danych w kontrolce DataGrid](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Opisuje sposób wyświetlania danych na <xref:System.Windows.Controls.DataGrid> różne sposoby poprzez grupowanie, sortowanie i filtrowanie danych.|  
|[Opcje ustalania rozmiaru w formancie DataGrid](sizing-options-in-the-datagrid-control.md)|Opisuje sposób kontrolowania bezwzględnego i automatycznego ustalania rozmiarów w <xref:System.Windows.Controls.DataGrid> .|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DataGrid>
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Przegląd powiązań danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
- [Formanty](index.md)
- [Model zawartości WPF](wpf-content-model.md)
