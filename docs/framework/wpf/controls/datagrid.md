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
ms.openlocfilehash: a8f267706c1ace02b091329360779711981d01e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid> Kontroli umożliwia wyświetlanie i edytowanie danych z różnych źródeł, takich jak z bazy danych SQL, zapytania LINQ lub dowolnego innego źródła danych może być powiązana. Aby uzyskać więcej informacji, zobacz [powiązanie Przegląd źródeł](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Kolumny można wyświetlić tekst, formanty, takie jak <xref:System.Windows.Controls.ComboBox>, lub dowolnej innej zawartości WPF, taką jak obrazy, przyciski lub zawartość w szablonie. Można użyć <xref:System.Windows.Controls.DataGridTemplateColumn> do wyświetlania danych zdefiniowanych w szablonie. W poniższej tabeli wymieniono typy kolumn, które znajdują się domyślnie.  
  
|Typ wygenerowanego kolumny|Typ danych|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> można dostosować wygląd, na przykład komórki czcionkę, kolor i rozmiar. <xref:System.Windows.Controls.DataGrid> obsługuje wszystkie funkcje stylami i tworzenia szablonów innych formantów WPF. <xref:System.Windows.Controls.DataGrid> zawiera także domyślne i dostosowania zachowania edycji, sortowanie i sprawdzania poprawności.  
  
 W poniższej tabeli przedstawiono niektóre typowe zadania <xref:System.Windows.Controls.DataGrid> i sposobu ich wykonywania. Wyświetlając pokrewne interfejsu API, można znaleźć więcej informacji oraz przykładowy kod.  
  
|Scenariusz|Podejście|  
|--------------|--------------|  
|Kolory tła przemiennych|Ustaw <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> właściwości 2 lub więcej, a następnie przypisz <xref:System.Windows.Media.Brush> do <xref:System.Windows.Controls.DataGrid.RowBackground%2A> i <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> właściwości.|  
|Zdefiniuj sposób zaznaczenia wierszy i komórek|Ustaw <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> i <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> właściwości.|  
|Dostosowywanie wyglądu nagłówków, komórek lub wierszy|Zastosuj nowy <xref:System.Windows.Style> do <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>, lub <xref:System.Windows.Controls.DataGrid.RowStyle%2A> właściwości.|  
|Ustaw opcje ustalania rozmiaru|Ustaw <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, lub <xref:System.Windows.FrameworkElement.MinWidth%2A> właściwości. Aby uzyskać więcej informacji, zobacz [opcje rozmiaru w formancie DataGrid](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md).|  
|Wybrane dostęp do elementów|Sprawdź <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> właściwości do pobrania zaznaczonych komórek i <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> właściwości do pobrania zaznaczone wiersze. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Dostosowywanie interakcje użytkownika końcowego|Ustaw <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, i <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> właściwości.|  
|Anuluj lub zmiana automatycznie generowanej kolumn|Obsługa <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> zdarzeń.|  
|Zablokuj kolumny|Ustaw <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> 1 i Przenieś kolumny do położenia w lewej, ustawiając dla właściwości <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> właściwości na 0.|  
|Użycie danych XML jako źródła danych|Powiąż <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> na <xref:System.Windows.Controls.DataGrid> do zapytania XPath, który reprezentuje kolekcję elementów. Utwórz każdej kolumny w <xref:System.Windows.Controls.DataGrid>. Powiązania każdej kolumny przez ustawienie języka XPath w powiązaniu kwerendę, która pobiera właściwości elementu źródłowego. Na przykład zobacz <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: wyświetlanie danych z bazy danych programu SQL Server w kontrolce DataGrid](../../../../docs/framework/wpf/controls/walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Opisuje sposób skonfigurować nowy projekt WPF, Dodaj Entity Framework Element, ustaw źródła i wyświetlić dane w <xref:System.Windows.Controls.DataGrid>.|  
|[Jak dodać szczegóły wiersza do kontrolki DataGrid](../../../../docs/framework/wpf/controls/how-to-add-row-details-to-a-datagrid-control.md)|Opisuje sposób tworzenia szczegóły wiersza <xref:System.Windows.Controls.DataGrid>.|  
|[Instrukcje: implementowanie walidacji za pomocą kontrolki DataGrid](../../../../docs/framework/wpf/controls/how-to-implement-validation-with-the-datagrid-control.md)|Opisuje sposób sprawdzania poprawności wartości w <xref:System.Windows.Controls.DataGrid> komórek i wierszy i wyświetlania weryfikacji opinii.|  
|[Domyślne zachowanie myszy i klawiatury w kontrolce DataGrid](../../../../docs/framework/wpf/controls/default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Opisuje sposób interakcji z <xref:System.Windows.Controls.DataGrid> formantu przy użyciu klawiatury i myszy.|  
|[Jak grupować, sortować i filtrować dane w DataGrid kontrolce](../../../../docs/framework/wpf/controls/how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Opisuje sposób wyświetlania danych w <xref:System.Windows.Controls.DataGrid> w różny sposób grupowania, sortowania i filtrowania danych.|  
|[Opcje ustalania rozmiaru w kontrolce DataGrid](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)|Zawiera opis sposobu kontrolowania bezwzględnych i automatycznej zmiany rozmiaru w <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.DataGrid>  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Szablonowanie danych — omówienie](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Kontrolki](../../../../docs/framework/wpf/controls/index.md)  
 [Model zawartości WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md)
