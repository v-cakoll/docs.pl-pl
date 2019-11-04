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
ms.openlocfilehash: f0887f36990de483139a9fde1472a78737cb7b72
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460388"
---
# <a name="datagrid"></a>DataGrid
Formant <xref:System.Windows.Controls.DataGrid> umożliwia wyświetlanie i edytowanie danych z wielu różnych źródeł, takich jak baza danych SQL, zapytanie LINQ lub inne źródło danych możliwe do powiązania. Aby uzyskać więcej informacji, zobacz [Omówienie źródeł powiązań](../data/binding-sources-overview.md).  
  
 Kolumny mogą wyświetlać tekst, kontrolki, takie jak <xref:System.Windows.Controls.ComboBox>lub jakakolwiek inna zawartość WPF, taka jak obrazy, przyciski lub zawartość w szablonie. Możesz użyć <xref:System.Windows.Controls.DataGridTemplateColumn>, aby wyświetlić dane zdefiniowane w szablonie. Poniższa tabela zawiera listę typów kolumn, które są udostępniane domyślnie.  
  
|Wygenerowany typ kolumny|Typ danych|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> można dostosować w wyglądzie, takich jak czcionka komórki, kolor i rozmiar. <xref:System.Windows.Controls.DataGrid> obsługuje wszystkie funkcje stylów i tworzenia szablonów innych formantów WPF. <xref:System.Windows.Controls.DataGrid> obejmuje również domyślne i dostosowywalne zachowania do edycji, sortowania i walidacji.  
  
 W poniższej tabeli wymieniono niektóre typowe zadania dotyczące <xref:System.Windows.Controls.DataGrid> i sposobu ich wykonania. Wyświetlając powiązany interfejs API, można znaleźć więcej informacji i przykładowy kod.  
  
|Scenariusz|Wynosi|  
|--------------|--------------|  
|Przemienne kolory tła|Ustaw właściwość <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> na 2 lub więcej, a następnie przypisz <xref:System.Windows.Media.Brush> do właściwości <xref:System.Windows.Controls.DataGrid.RowBackground%2A> i <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A>.|  
|Zdefiniuj zachowanie wyboru komórki i wiersza|Ustaw właściwości <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> i <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>.|  
|Dostosuj wygląd nagłówków, komórek i wierszy wizualizacji|Zastosuj nową <xref:System.Windows.Style> do właściwości <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>lub <xref:System.Windows.Controls.DataGrid.RowStyle%2A>.|  
|Ustawianie opcji ustalania wielkości|Ustaw właściwości <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>lub <xref:System.Windows.FrameworkElement.MinWidth%2A>. Aby uzyskać więcej informacji, zobacz [Opcje ustalania rozmiarów w kontrolce DataGrid](sizing-options-in-the-datagrid-control.md).|  
|Dostęp do wybranych elementów|Sprawdź Właściwość <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>, aby pobrać zaznaczone komórki i Właściwość <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> w celu pobrania wybranych wierszy. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Dostosowywanie interakcji użytkowników końcowych|Ustaw właściwości <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>i <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A>.|  
|Anuluj lub Zmień automatycznie generowane kolumny|Obsłuż zdarzenie <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn>.|  
|Zablokuj kolumnę|Ustaw właściwość <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> na 1 i Przenieś kolumnę do lewej strony, ustawiając właściwość <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> na 0.|  
|Używanie danych XML jako źródła danych|Powiąż <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> na <xref:System.Windows.Controls.DataGrid> z kwerendą XPath, która reprezentuje kolekcję elementów. Utwórz każdą kolumnę w <xref:System.Windows.Controls.DataGrid>. Powiąż każdą kolumnę, ustawiając wyrażenie XPath dla powiązania z zapytaniem, które pobiera właściwość w źródle elementu. Aby zapoznać się z przykładem, zobacz <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: wyświetlanie danych z bazy danych programu SQL Server w kontrolce DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Opisuje sposób skonfigurowania nowego projektu WPF, dodania elementu Entity Framework, ustawienia źródła i wyświetlenia danych w <xref:System.Windows.Controls.DataGrid>.|  
|[Jak dodać szczegóły wiersza do kontrolki DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|Opisuje sposób tworzenia szczegółów wiersza dla <xref:System.Windows.Controls.DataGrid>.|  
|[Instrukcje: implementowanie walidacji za pomocą kontrolki DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|Opisuje sposób sprawdzania poprawności wartości w <xref:System.Windows.Controls.DataGrid> komórkach i wierszach oraz wyświetlanie opinii o walidacji.|  
|[Domyślne zachowanie myszy i klawiatury w kontrolce DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Opisuje sposób współdziałania z kontrolką <xref:System.Windows.Controls.DataGrid> przy użyciu klawiatury i myszy.|  
|[Jak grupować, sortować i filtrować dane w DataGrid kontrolce](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Opisuje sposób wyświetlania danych w <xref:System.Windows.Controls.DataGrid> na różne sposoby, grupując, sortując i filtrując dane.|  
|[Opcje ustalania rozmiaru w kontrolce DataGrid](sizing-options-in-the-datagrid-control.md)|Opisuje sposób kontrolowania bezwzględnego i automatycznego ustalania wielkości w <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DataGrid>
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
- [Kontrolki](index.md)
- [Model zawartości WPF](wpf-content-model.md)
