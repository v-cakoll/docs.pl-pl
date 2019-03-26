---
title: Przegląd Tabela
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: 4abb6368946f9dac5fdefd6ca44f3adeed55f78f
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410826"
---
# <a name="table-overview"></a>Przegląd Tabela
<xref:System.Windows.Documents.Table> jest element poziomu bloku, który obsługuje oparte na siatce prezentacji zawartości dokumentu przepływu. Elastyczność tego elementu sprawia, że bardzo przydatne, ale także stanowi bardziej skomplikowane, aby zrozumieć i zastosować poprawnie.  
  
 Ten temat zawiera następujące sekcje.  
  
-   [Podstawowe informacje dotyczące tabeli](#table_basics)  
  
-   [W jaki sposób innej tabeli, a następnie siatki?](#table_vs_Grid)  
  
-   [Struktura tabeli podstawowej](#basic_table_structure)  
  
-   [Tabela zawierania](#table_containment)  
  
-   [Grupowań wierszy](#row_groupings)  
  
-   [Pierwszeństwo renderowania w tle](#rendering_precedence)  
  
-   [Łączenie wierszy lub kolumn](#spanning_rows_or_columns)  
  
-   [Tworzenie tabeli przy użyciu kodu](#building_a_table_with_code)  
  
-   [Tematy pokrewne] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Podstawowe informacje dotyczące tabeli  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>W jaki sposób innej tabeli, a następnie siatki?  
 <xref:System.Windows.Documents.Table> i <xref:System.Windows.Controls.Grid> udostępnianie niektóre typowe funkcje, ale każdy jest najbardziej odpowiednie dla różnych scenariuszy. A <xref:System.Windows.Documents.Table> jest przeznaczony do użytku w ramach dowolnej zawartości (zobacz [Przegląd dokumentu przepływu](flow-document-overview.md) więcej informacji na temat zawartości przepływu). Siatki najlepiej sprawdzają się wewnątrz formularzy (zasadniczo dowolne miejsce poza przepływ zawartości). W ramach <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> obsługuje przepływ zawartości zachowań, takich jak podział na strony, ze zmianą ułożenia kolumny i zawartości zaznaczenia podczas <xref:System.Windows.Controls.Grid> nie. A <xref:System.Windows.Controls.Grid> z drugiej strony najlepiej nadaje się poza <xref:System.Windows.Documents.FlowDocument> wiele powodów, takich jak <xref:System.Windows.Controls.Grid> dodaje elementy w oparciu o indeks wierszy i kolumn <xref:System.Windows.Documents.Table> nie. <xref:System.Windows.Controls.Grid> Elementu umożliwia warstwowe zawartość elementu podrzędnego, dzięki czemu więcej niż jeden element istnieje w jednej "komórki." <xref:System.Windows.Documents.Table> nie obsługują warstw. Elementy podrzędne <xref:System.Windows.Controls.Grid> można pozycjonowane absolutnie względem pola ich granice "komórki". <xref:System.Windows.Documents.Table> nie obsługuje tej funkcji. Na koniec <xref:System.Windows.Controls.Grid> wymaga mniej zasobów, a następnie <xref:System.Windows.Documents.Table> zatem należy wziąć pod uwagę przy użyciu <xref:System.Windows.Controls.Grid> poprawić wydajność.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Struktura tabeli podstawowej  
 <xref:System.Windows.Documents.Table> zapewnia prezentację na podstawie siatki składający się z kolumn (reprezentowane przez <xref:System.Windows.Documents.TableColumn> elementy) i wiersze (reprezentowane przez <xref:System.Windows.Documents.TableRow> elementów). <xref:System.Windows.Documents.TableColumn> elementy nie jest hostem zawartości; określają one po prostu, kolumn i właściwości kolumn. <xref:System.Windows.Documents.TableRow> elementy muszą być hostowane w <xref:System.Windows.Documents.TableRowGroup> element, który definiuje grupowanie wierszy w tabeli. <xref:System.Windows.Documents.TableCell> elementy, które zawierają rzeczywistej zawartości, które mają zostać wyświetlone w tabeli, musi być hostowany w <xref:System.Windows.Documents.TableRow> elementu. <xref:System.Windows.Documents.TableCell> może zawierać tylko elementy, które wynikają z <xref:System.Windows.Documents.Block>.  Elementy prawidłowy element podrzędny dla <xref:System.Windows.Documents.TableCell> obejmują.  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell> elementy nie mogą bezpośrednio hostem zawartości tekstowej. Aby uzyskać więcej informacji o regułach zawierania dla przepływu, takich jak elementy zawartości <xref:System.Windows.Documents.TableCell>, zobacz [Przegląd dokumentu przepływu](flow-document-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> jest podobny do <xref:System.Windows.Controls.Grid> element ale ma więcej możliwości i, w związku z tym, wymaga większe obciążenie zasobów.  
  
 W poniższym przykładzie zdefiniowano prostej tabeli 2 x 3 z [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![Zrzut ekranu pokazujący, jak renderuje tabeli podstawowej.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Tabela zawierania  
 <xref:System.Windows.Documents.Table> pochodzi od klasy <xref:System.Windows.Documents.Block> element i stosuje reguły wspólnej <xref:System.Windows.Documents.Block> na poziomie elementów.  Element <xref:System.Windows.Documents.Table> elementu mogą znajdować się według dowolnej z następujących elementów:  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Grupowań wierszy  
 <xref:System.Windows.Documents.TableRowGroup> Element zapewnia sposób arbitralnie grupowanie wierszy w tabeli; każdy wiersz w tabeli musi należeć do grupowań wierszy.  Często wierszy w obrębie grupy wierszy udostępniać typowe opcje i może być wstawiony jako grupa.  Typowym zastosowaniem dla grupowań wierszy jest do rozdzielania wierszy specjalnych, takich jak tytuł, nagłówek i stopka wierszy z podstawowego zawartości, zawartych w tabeli.  
  
 W poniższym przykładzie użyto [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] do definiowania tabeli ze stylem wierszy w nagłówku i stopce.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![Zrzut ekranu: Grupami wierszy tabeli](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Pierwszeństwo renderowania w tle  
 Elementy tabeli renderowane w następującej kolejności (porządek od najniższej do najwyższej). Nie można zmienić tej kolejności. Na przykład nie ma żadnej właściwości "Kolejności Z" dla tych elementów, których można zmienić tę kolejność ustalonych.  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 Rozważmy następujący przykład, który definiuje kolory tła dla każdego z tych elementów w tabeli.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Na poniższej ilustracji przedstawiono, jak w tym przykładzie powoduje wyświetlenie (tylko kolory tła przedstawiający).  
  
 ![Zrzut ekranu: Tabela z&#45;kolejności](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Łączenie wierszy lub kolumn  
 Komórki tabeli może być skonfigurowany na wiele wierszy lub kolumn przy użyciu <xref:System.Windows.Documents.TableCell.RowSpan%2A> lub <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> , odpowiednio, atrybutów.  
  
 Rozważmy następujący przykład, w którym komórki obejmuje trzy kolumny.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![Zrzut ekranu: Komórka obejmująca wszystkie trzy kolumny](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Tworzenie tabeli przy użyciu kodu  
 W poniższych przykładach pokazano, jak programowo utworzyć <xref:System.Windows.Documents.Table> i wypełnianie jej zawartości. Zawartość tej tabeli są rozdzielone na pięć wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> obiektów zawartych w <xref:System.Windows.Documents.Table.RowGroups%2A> obiekt) i 6 kolumn (reprezentowane przez <xref:System.Windows.Documents.TableColumn> obiektów). Wiersze są używane do celów innej prezentacji, w tym wiersz tytułu przeznaczone do tytułu całą tabelę, wiersz nagłówka do opisania kolumn danych w tabeli i wiersz stopki z podsumowaniem.  Należy pamiętać, że pojęcie "title", "header" i "stopka" wierszy nie są wbudowane w tabeli; są to po prostu wiersze o różnej charakterystyce. Komórki tabeli zawierają rzeczywistej zawartości może składać się z tekstu, obrazów lub niemal każdy inny [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.  
  
 Najpierw <xref:System.Windows.Documents.FlowDocument> jest tworzona na hoście <xref:System.Windows.Documents.Table>, nowy <xref:System.Windows.Documents.Table> zostanie utworzony i dodany do zawartości <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Następnie sześciu <xref:System.Windows.Documents.TableColumn> obiekty są tworzone i dodawane do tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcji z niektórych zastosowanym formatowaniem.  
  
> [!NOTE]
>  Należy pamiętać, że tabela <xref:System.Windows.Documents.Table.Columns%2A> kolekcja używa standardowych indeksowania zaczynającego się od zera.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Następnie wiersz tytułu jest tworzone i dodawane do tabeli za pomocą niektórych zastosowanym formatowaniem.  Wiersz tytułu odbywa się zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Następnie wiersz nagłówka zostanie utworzony i dodany do tabeli i komórki w wierszu nagłówka są tworzone i wypełniane zawartością.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Następnie wiersz danych zostanie utworzony i dodany do tabeli i komórek w tym wierszu są tworzone i wypełniane zawartością.  Tworzenie tego wiersza jest podobne do tworzenia wiersz nagłówka z zastosowanym formatowaniem nieco inne.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Na koniec wiersza stopki utworzone, dodać i sformatowany.  Podobnie jak wiersz tytułu stopki zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd dokumentu przepływu](flow-document-overview.md)
- [Definiowanie tabeli przy użyciu XAML](how-to-define-a-table-with-xaml.md)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Używanie elementów zawartości przepływu](how-to-use-flow-content-elements.md)
