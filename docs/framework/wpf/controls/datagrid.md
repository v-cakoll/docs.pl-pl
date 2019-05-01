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
ms.openlocfilehash: dda712d58a4ff956de074ecd416402ba0aece5f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912239"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid> Control umożliwia wyświetlania i edytowania danych z wielu różnych źródeł, takich jak z bazy danych SQL, zapytanie LINQ lub dowolnego innego źródła danych może być powiązana. Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie źródeł](../data/binding-sources-overview.md).  
  
 Kolumny można wyświetlić tekst, formanty, takie jak <xref:System.Windows.Controls.ComboBox>, lub inną zawartość WPF, takie jak obrazy, przycisków lub żadnej zawartości zawarte w szablonie. Możesz użyć <xref:System.Windows.Controls.DataGridTemplateColumn> do wyświetlania danych zdefiniowanych w szablonie. W poniższej tabeli wymieniono typy kolumn, które znajdują się domyślnie.  
  
|Typ kolumny wygenerowany|Typ danych|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> można dostosować wygląd, takich jak komórki czcionkę, kolor i rozmiar. <xref:System.Windows.Controls.DataGrid> obsługuje wszystkie funkcje szablonów i stylów innych kontrolek WPF. <xref:System.Windows.Controls.DataGrid> zawiera również domyślne i możliwe do dostosowania zachowania edycję, sortowanie i sprawdzania poprawności.  
  
 W poniższej tabeli wymieniono niektóre typowe zadania <xref:System.Windows.Controls.DataGrid> i sposobu ich wykonania. Wyświetlając powiązanych interfejsów API, można znaleźć więcej informacji i przykładowy kod.  
  
|Scenariusz|Podejście|  
|--------------|--------------|  
|Różne kolory tła|Ustaw <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> właściwość 2 lub więcej, a następnie przypisz <xref:System.Windows.Media.Brush> do <xref:System.Windows.Controls.DataGrid.RowBackground%2A> i <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> właściwości.|  
|Zdefiniuj zachowanie podczas zaznaczania wierszy i komórek|Ustaw <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> i <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> właściwości.|  
|Dostosowywanie wyglądu nagłówków, komórek i wierszy|Zastosuj nowy <xref:System.Windows.Style> do <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>, lub <xref:System.Windows.Controls.DataGrid.RowStyle%2A> właściwości.|  
|Ustaw opcje ustalania rozmiaru|Ustaw <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, lub <xref:System.Windows.FrameworkElement.MinWidth%2A> właściwości. Aby uzyskać więcej informacji, zobacz [opcje ustalania rozmiaru w formancie DataGrid](sizing-options-in-the-datagrid-control.md).|  
|Uzyskiwanie dostępu do wybrano elementów|Sprawdź <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> właściwości do pobrania zaznaczonych komórek i <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> właściwości do pobrania wybranych wierszy. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Dostosowywanie interakcje użytkownika końcowego|Ustaw <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, i <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> właściwości.|  
|Anulowanie lub zmienianie kolumn wygenerowany automatycznie|Obsługa <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> zdarzeń.|  
|Zablokuj kolumnę|Ustaw <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> 1 i Przenieś kolumnę pozycji skrajnie po lewej, ustawiając właściwość <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> właściwości na wartość 0.|  
|Użycie danych XML jako źródła danych|Powiąż <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> na <xref:System.Windows.Controls.DataGrid> zapytania XPath, który reprezentuje kolekcję elementów. Tworzenie każdej kolumny w <xref:System.Windows.Controls.DataGrid>. Powiąż każda kolumna przez ustawienie języka XPath dla powiązania do zapytania, które pobiera właściwość na element "source". Aby uzyskać przykład, zobacz <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: Wyświetlanie danych z bazy danych programu SQL Server w formancie DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Opisuje, jak skonfigurować nowy projekt WPF, Dodaj Entity Framework Element, ustaw źródło i wyświetlić dane w <xref:System.Windows.Controls.DataGrid>.|  
|[Instrukcje: Dodać szczegóły wiersza do formantu DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|Opisuje sposób tworzenia szczegóły wiersza dla <xref:System.Windows.Controls.DataGrid>.|  
|[Instrukcje: Implementuj walidację za pomocą formantu DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|W tym artykule opisano sposób sprawdzania poprawności wartości w <xref:System.Windows.Controls.DataGrid> komórek i wierszy i wyświetlania sprawdzania poprawności opinii.|  
|[Domyślne zachowanie myszy i klawiatury w kontrolce DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|W tym artykule opisano sposób interakcji z <xref:System.Windows.Controls.DataGrid> kontroli przy użyciu klawiatury i myszy.|  
|[Instrukcje: Grupować, sortować i filtrować dane w DataGrid kontrolce](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Opisuje sposób wyświetlania danych w <xref:System.Windows.Controls.DataGrid> na różne sposoby grupowania, sortowania i filtrowania danych.|  
|[Opcje ustalania rozmiaru w kontrolce DataGrid](sizing-options-in-the-datagrid-control.md)|W tym artykule opisano sposób kontrolowania bezwzględne i automatycznego ustalania rozmiaru w <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DataGrid>
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
- [Kontrolki](index.md)
- [Model zawartości WPF](wpf-content-model.md)
