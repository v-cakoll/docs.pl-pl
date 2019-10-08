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
ms.openlocfilehash: fa7106207c69f19b647ba80ab7e724e9aad174c1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005077"
---
# <a name="table-overview"></a>Przegląd Tabela
<xref:System.Windows.Documents.Table> to element poziomu bloku, który obsługuje prezentację zawartości dokumentu przepływu na podstawie siatki. Elastyczność tego elementu sprawia, że jest to bardzo przydatne, ale również bardziej skomplikowane do zrozumienia i użycia.  
  
 Ten temat zawiera następujące sekcje.  
  
- [Podstawowe informacje dotyczące tabeli](#table_basics)  
  
- [Czym różni się tabela w tabeli?](#table_vs_Grid)  
  
- [Podstawowa struktura tabeli](#basic_table_structure)  
  
- [Zawieranie tabeli](#table_containment)  
  
- [Grupowanie wierszy](#row_groupings)  
  
- [Pierwszeństwo renderowania w tle](#rendering_precedence)  
  
- [Łączenie wierszy lub kolumn](#spanning_rows_or_columns)  
  
- [Kompilowanie tabeli przy użyciu kodu](#building_a_table_with_code)  
  
- [Tematy pokrewne] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Podstawowe informacje dotyczące tabeli  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>Czym różni się tabela w tabeli?  
 <xref:System.Windows.Documents.Table> i <xref:System.Windows.Controls.Grid> udostępniają niektóre typowe funkcje, ale każdy z nich jest najlepiej dostosowany do różnych scenariuszy. @No__t-0 jest zaprojektowana do użycia w obrębie zawartości przepływu (zobacz temat [Omówienie dokumentu Flow](flow-document-overview.md) , aby uzyskać więcej informacji na temat przepływu zawartości). Siatki najlepiej używać wewnątrz formularzy (zasadniczo poza zawartością przepływu). W <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Documents.Table> obsługuje zachowania zawartości przepływu, takie jak stronicowanie, Ponowne wlewanie kolumn i wybór zawartości, podczas gdy <xref:System.Windows.Controls.Grid>. @No__t-0 z drugiej strony najlepiej jest używać poza <xref:System.Windows.Documents.FlowDocument> z wielu powodów, w tym <xref:System.Windows.Controls.Grid> dodaje elementy na podstawie indeksu wierszy i kolumn, <xref:System.Windows.Documents.Table> nie. Element <xref:System.Windows.Controls.Grid> umożliwia warstwową zawartość elementu podrzędnego, co pozwala na istnienie więcej niż jednego elementu w jednej komórce. <xref:System.Windows.Documents.Table> nie obsługuje warstw. Elementy podrzędne <xref:System.Windows.Controls.Grid> mogą być absolutnie pozycjonowane względem obszaru ich granic "komórki". <xref:System.Windows.Documents.Table> nie obsługuje tej funkcji. Na koniec <xref:System.Windows.Controls.Grid> wymaga mniejszej ilości zasobów, a następnie <xref:System.Windows.Documents.Table>, aby zwiększyć wydajność przy użyciu <xref:System.Windows.Controls.Grid>.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Podstawowa struktura tabeli  
 <xref:System.Windows.Documents.Table> zawiera prezentację opartą na siatce składającą się z kolumn (reprezentowane przez elementy <xref:System.Windows.Documents.TableColumn>) i wierszy (reprezentowanych przez elementy <xref:System.Windows.Documents.TableRow>). elementy <xref:System.Windows.Documents.TableColumn> nie obsługują zawartości; po prostu definiują kolumny i właściwości kolumn. elementy <xref:System.Windows.Documents.TableRow> muszą być hostowane w elemencie <xref:System.Windows.Documents.TableRowGroup>, który definiuje Grupowanie wierszy dla tabeli. elementy <xref:System.Windows.Documents.TableCell>, które zawierają rzeczywistą zawartość, która ma być prezentowana przez tabelę, muszą być hostowane w elemencie <xref:System.Windows.Documents.TableRow>. <xref:System.Windows.Documents.TableCell> może zawierać tylko elementy pochodne od <xref:System.Windows.Documents.Block>.  Prawidłowymi elementami podrzędnymi dla <xref:System.Windows.Documents.TableCell> include.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> elementy <xref:System.Windows.Documents.TableCell> nie mogą bezpośrednio hostować zawartości tekstowej. Aby uzyskać więcej informacji na temat reguł zawierania dla elementów zawartości przepływu, takich jak <xref:System.Windows.Documents.TableCell>, zobacz [Omówienie dokumentu przepływu](flow-document-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table> jest podobna do elementu <xref:System.Windows.Controls.Grid>, ale ma więcej możliwości i w związku z tym wymaga większego obciążenia zasobów.  
  
 W poniższym przykładzie zdefiniowano prostą tabelę 2 x 3 z XAML.  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu.  
  
 ![Zrzut ekranu pokazujący sposób renderowania podstawowej tabeli.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Zawieranie tabeli  
 <xref:System.Windows.Documents.Table> pochodzi z elementu <xref:System.Windows.Documents.Block> i stosuje się do wspólnych reguł dla elementów poziomu <xref:System.Windows.Documents.Block>.  Element <xref:System.Windows.Documents.Table> może być zawarty w jednym z następujących elementów:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Grupowanie wierszy  
 Element <xref:System.Windows.Documents.TableRowGroup> umożliwia arbitralne Grupowanie wierszy w tabeli. Każdy wiersz w tabeli musi należeć do grupowania wierszy.  Wiersze w grupie wierszy często korzystają ze wspólnego zamiaru i mogą być wzorowane jako Grupa.  Typowym zastosowaniem grupowania wierszy jest oddzielenie wierszy specjalnego przeznaczenia, takich jak tytuł, nagłówek i stopka, z zawartości głównej zawartej w tabeli.  
  
 Poniższy przykład używa języka XAML do definiowania tabeli z stylem nagłówek i stopka.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu.  
  
 ![Zrzut ekranu: grupy wierszy tabeli](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Pierwszeństwo renderowania w tle  
 Elementy tabeli są renderowane w następującej kolejności (porządek osi z od najniższego do najwyższego). Nie można zmienić tej kolejności. Na przykład nie istnieje właściwość "Z-Order" dla tych elementów, których można użyć do przesłonięcia ustalonej kolejności.  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 Rozważmy poniższy przykład, który definiuje kolory tła dla każdego z tych elementów w tabeli.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu (wyświetlane są tylko kolory tła).  
  
 ![Zrzut ekranu: tabela&#45;z kolejnością](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Łączenie wierszy lub kolumn  
 Komórki tabeli można skonfigurować tak, aby obejmowały wiele wierszy lub kolumn przy użyciu odpowiednio atrybutów <xref:System.Windows.Documents.TableCell.RowSpan%2A> lub <xref:System.Windows.Documents.TableCell.ColumnSpan%2A>.  
  
 Rozważmy poniższy przykład, w którym komórka obejmuje trzy kolumny.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu.  
  
 ![Zrzut ekranu: komórka obejmująca wszystkie trzy kolumny](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Kompilowanie tabeli przy użyciu kodu  
 W poniższych przykładach pokazano, jak programowo utworzyć <xref:System.Windows.Documents.Table> i wypełnić go zawartością. Zawartość tabeli jest przydzielona do pięciu wierszy (reprezentowanych przez <xref:System.Windows.Documents.TableRow> obiektów zawartych w obiekcie <xref:System.Windows.Documents.Table.RowGroups%2A>) i sześciu kolumn (reprezentowanych przez <xref:System.Windows.Documents.TableColumn> obiektów). Wiersze są używane do różnych celów prezentacji, łącznie z wierszem tytułu, który ma tytuł całej tabeli, wiersz nagłówka opisujący kolumny danych w tabeli oraz wiersz stopki z informacjami podsumowującymi.  Należy zauważyć, że pojęcie wierszy "title", "Header" i "Stopka" nie jest związane z tabelą; są to po prostu wiersze o różnej charakterystyce. Komórki tabeli zawierają rzeczywistą zawartość, która może składać się z tekstu, obrazów lub niemal dowolnego innego elementu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Najpierw jest tworzony <xref:System.Windows.Documents.FlowDocument>, aby hostować <xref:System.Windows.Documents.Table>, a nowy <xref:System.Windows.Documents.Table> zostanie utworzony i dodany do zawartości <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Następnie sześć <xref:System.Windows.Documents.TableColumn> obiektów są tworzone i dodawane do kolekcji <xref:System.Windows.Documents.Table.Columns%2A> tabeli, z zastosowaniem formatowania.  
  
> [!NOTE]
> Należy zauważyć, że kolekcja <xref:System.Windows.Documents.Table.Columns%2A> tabeli używa standardowego indeksowania opartego na zero.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Następnie wiersz tytułu zostanie utworzony i dodany do tabeli z zastosowaniem formatowania.  Wiersz tytułu ma zawierać pojedynczą komórkę obejmującą wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Następnie wiersz nagłówka jest tworzony i dodawany do tabeli, a komórki w wierszu nagłówka są tworzone i wypełniane zawartością.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Następnie wiersz danych jest tworzony i dodawany do tabeli, a komórki w tym wierszu są tworzone i wypełniane zawartością.  Kompilowanie tego wiersza jest podobne do tworzenia wiersza nagłówka z niewielkim innym formatowaniem.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Na koniec wiersz stopki jest tworzony, dodawany i sformatowany.  Podobnie jak w przypadku wiersza tytułu, stopka zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd dokumentu przepływu](flow-document-overview.md)
- [Definiowanie tabeli przy użyciu XAML](how-to-define-a-table-with-xaml.md)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Używanie elementów zawartości przepływu](how-to-use-flow-content-elements.md)
