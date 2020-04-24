---
title: DataGrid
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
ms.openlocfilehash: cdf4bfff8182b62d55f56b823c7ff129de4f9f1c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646118"
---
# <a name="datagrid"></a>DataGrid
Formant <xref:System.Windows.Controls.DataGrid> umożliwia wyświetlanie i edytowanie danych z wielu różnych źródeł, takich jak baza danych SQL, kwerenda LINQ lub inne źródło danych, które można powiązać. Aby uzyskać więcej informacji, zobacz [Omówienie źródeł wiązania](../data/binding-sources-overview.md).  
  
 Kolumny mogą wyświetlać tekst, formanty, takie jak <xref:System.Windows.Controls.ComboBox>zawartość WPF lub inne, takie jak obrazy, przyciski lub dowolna zawartość zawarta w szablonie. Można użyć <xref:System.Windows.Controls.DataGridTemplateColumn> a do wyświetlania danych zdefiniowanych w szablonie. W poniższej tabeli wymieniono typy kolumn, które są domyślnie dostarczane.  
  
|Wygenerowany typ kolumny|Typ danych|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>można dostosować pod względem wyglądu, takiego jak czcionka komórki, kolor i rozmiar. <xref:System.Windows.Controls.DataGrid>obsługuje wszystkie funkcje stylizacji i szablonów innych formantów WPF. <xref:System.Windows.Controls.DataGrid>obejmuje również domyślne i konfigurowalne zachowania do edycji, sortowania i sprawdzania poprawności.  
  
 W poniższej tabeli wymieniono <xref:System.Windows.Controls.DataGrid> niektóre typowe zadania i sposób ich wykonania. Przeglądając powiązany interfejs API, można znaleźć więcej informacji i przykładowy kod.  
  
|Scenariusz|Podejście|  
|--------------|--------------|  
|Naprzemienne kolory tła|Ustaw <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> właściwość na 2 lub więcej, <xref:System.Windows.Controls.DataGrid.RowBackground%2A> a <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> następnie przypisz do <xref:System.Windows.Media.Brush> i właściwości.|  
|Definiowanie zachowania zaznaczania komórek i wierszy|Ustaw <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> właściwości <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> i.|  
|Dostosowywanie wyglądu nagłówków, komórek i wierszy|Zastosuj nowy <xref:System.Windows.Style> do <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A> <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>właściwości <xref:System.Windows.Controls.DataGrid.CellStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowStyle%2A> , lub.|  
|Ustawianie opcji zmiany rozmiaru|Ustaw <xref:System.Windows.FrameworkElement.Height%2A>właściwości <xref:System.Windows.FrameworkElement.MaxHeight%2A> <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A> , lub. Aby uzyskać więcej informacji, zobacz [Opcje rozmiaru w formancie DataGrid](sizing-options-in-the-datagrid-control.md).|  
|Dostęp do wybranych elementów|Sprawdź <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> właściwość, aby uzyskać <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> wybrane komórki i właściwość, aby uzyskać wybrane wiersze. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Dostosowywanie interakcji z użytkownikiem końcowym|Ustaw <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>właściwości <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A> <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> , i .|  
|Anulowanie lub zmiana automatycznie generowanych kolumn|Obsługa <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> zdarzenia.|  
|Blokowanie kolumny|Ustaw <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> właściwość na 1 i przenieś kolumnę do <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> pozycji najbardziej lewej, ustawiając właściwość na 0.|  
|Używanie danych XML jako źródła danych|<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Powiąż <xref:System.Windows.Controls.DataGrid> na xpath kwerendy, która reprezentuje kolekcję elementów. Utwórz każdą <xref:System.Windows.Controls.DataGrid>kolumnę w pliku . Powiąż każdą kolumnę, ustawiając XPath na powiązanie do kwerendy, która pobiera właściwości w źródle elementu. Na przykład zobacz <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: wyświetlanie danych z bazy danych programu SQL Server w kontrolce DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Opisuje sposób konfigurowania nowego projektu WPF, dodawania elementu struktury encji, ustawiania źródła i wyświetlania danych w programie <xref:System.Windows.Controls.DataGrid>.|  
|[Jak dodać szczegóły wiersza do formantu DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|W tym artykule opisano <xref:System.Windows.Controls.DataGrid>sposób tworzenia szczegółów wiersza dla pliku .|  
|[Instrukcje: implementowanie walidacji za pomocą kontrolki DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|W tym artykule <xref:System.Windows.Controls.DataGrid> opisano sposób sprawdzania poprawności wartości w komórkach i wierszach oraz wyświetlania opinii dotyczących sprawdzania poprawności.|  
|[Domyślne zachowanie myszy i klawiatury w kontrolce DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|W tym artykule <xref:System.Windows.Controls.DataGrid> opisano sposób interakcji z formantem za pomocą klawiatury i myszy.|  
|[Jak grupować, sortować i filtrować dane w DataGrid kontrolce](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|W tym artykule <xref:System.Windows.Controls.DataGrid> opisano sposób wyświetlania danych na różne sposoby przez grupowanie, sortowanie i filtrowanie danych.|  
|[Opcje ustalania rozmiaru w kontrolce DataGrid](sizing-options-in-the-datagrid-control.md)|W tym artykule opisano sposób <xref:System.Windows.Controls.DataGrid>sterowania bezwzględnym i automatycznym doszłach w pliku .|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.DataGrid>
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
- [Formanty](index.md)
- [Model zawartości WPF](wpf-content-model.md)
