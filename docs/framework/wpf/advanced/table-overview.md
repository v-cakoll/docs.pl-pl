---
title: Omówienie tabel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: 4bd747cea43755116c56b16f1de9a6ffb59935ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187271"
---
# <a name="table-overview"></a>Omówienie tabel
<xref:System.Windows.Documents.Table>jest elementem poziomu bloku, który obsługuje prezentację zawartości dokumentu flow opartą na siatce. Elastyczność tego elementu sprawia, że jest bardzo przydatny, ale także sprawia, że bardziej skomplikowane jest prawidłowe zrozumienie i użycie.  
  
 Ten temat zawiera poniższe sekcje.  
  
- [Podstawy tabeli](#table_basics)  
  
- [Jak tabela jest inna niż Grid?](#table_vs_Grid)  
  
- [Podstawowa struktura tabeli](#basic_table_structure)  
  
- [Hermetyzacja tabeli](#table_containment)  
  
- [Grupowanie wierszy](#row_groupings)  
  
- [Pierwszeństwo renderowania w tle](#rendering_precedence)  
  
- [Obejmujące wiersze lub kolumny](#spanning_rows_or_columns)  
  
- [Tworzenie tabeli z kodem](#building_a_table_with_code)  
  
- [Tematy pokrewne]
  
<a name="table_basics"></a>
## <a name="table-basics"></a>Podstawy tabeli  
  
<a name="table_vs_Grid"></a>
### <a name="how-is-table-different-then-grid"></a>Jak tabela jest inna niż Grid?  
 <xref:System.Windows.Documents.Table>i <xref:System.Windows.Controls.Grid> dzielić niektóre typowe funkcje, ale każdy jest najlepiej nadaje się do różnych scenariuszy. A <xref:System.Windows.Documents.Table> jest przeznaczony do użytku w ramach zawartości przepływu (zobacz [Omówienie dokumentu przepływu, aby](flow-document-overview.md) uzyskać więcej informacji na temat zawartości przepływu). Siatki są najlepiej używane wewnątrz formularzy (w zasadzie w dowolnym miejscu poza zawartością przepływu). W <xref:System.Windows.Documents.FlowDocument>obrębie <xref:System.Windows.Documents.Table> , obsługuje zachowania zawartości przepływu, takie jak podział na <xref:System.Windows.Controls.Grid> strony, ponowne wlanie kolumny i wybór zawartości, podczas gdy nie. A <xref:System.Windows.Controls.Grid> z drugiej strony najlepiej jest <xref:System.Windows.Documents.FlowDocument> używany poza <xref:System.Windows.Controls.Grid> a z wielu powodów, <xref:System.Windows.Documents.Table> w tym dodaje elementy oparte na indeksie wiersza i kolumny, nie. Element <xref:System.Windows.Controls.Grid> umożliwia nakładanie warstw zawartości podrzędnej, dzięki czemu więcej niż jeden element istnieje w pojedynczej "komórce". <xref:System.Windows.Documents.Table>nie obsługuje nakładania warstw. Elementy podrzędne <xref:System.Windows.Controls.Grid> a mogą być absolutnie umieszczone względem obszaru ich "komórki" granice. <xref:System.Windows.Documents.Table>nie obsługuje tej funkcji. Na koniec <xref:System.Windows.Controls.Grid> wymaga mniej zasobów, a następnie <xref:System.Windows.Documents.Table> należy rozważyć użycie a <xref:System.Windows.Controls.Grid> w celu zwiększenia wydajności.  
  
<a name="basic_table_structure"></a>
### <a name="basic-table-structure"></a>Podstawowa struktura tabeli  
 <xref:System.Windows.Documents.Table>zawiera prezentację opartą na siatce <xref:System.Windows.Documents.TableColumn> składającą się z kolumn <xref:System.Windows.Documents.TableRow> (reprezentowanych przez elementy) i wierszy (reprezentowanych przez elementy). <xref:System.Windows.Documents.TableColumn>elementy nie hostują zawartości; po prostu definiują kolumny i charakterystyki kolumn. <xref:System.Windows.Documents.TableRow>elementy muszą być hostowane w elemencie, <xref:System.Windows.Documents.TableRowGroup> który definiuje grupowanie wierszy dla tabeli. <xref:System.Windows.Documents.TableCell>elementy, które zawierają rzeczywistą zawartość, która ma być przedstawiona przez tabelę, muszą być hostowane w elemencie. <xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.TableCell>mogą zawierać tylko elementy, <xref:System.Windows.Documents.Block>które wynikają z .  Prawidłowe elementy <xref:System.Windows.Documents.TableCell> podrzędne dla include.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell>elementy nie mogą bezpośrednio hostować zawartości tekstowej. Aby uzyskać więcej informacji na temat reguł <xref:System.Windows.Documents.TableCell>zamknięcia dla elementów zawartości przepływu, takich jak , zobacz [Omówienie dokumentu przepływu](flow-document-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table>jest podobny <xref:System.Windows.Controls.Grid> do elementu, ale ma więcej możliwości i dlatego wymaga większego obciążenia zasobów.  
  
 Poniższy przykład definiuje prostą tabelę 2 x 3 z XAML.  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.  
  
 ![Zrzut ekranu przedstawiający sposób renderowania podstawowej tabeli.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>
### <a name="table-containment"></a>Hermetyzacja tabeli  
 <xref:System.Windows.Documents.Table>pochodzi z <xref:System.Windows.Documents.Block> elementu i przestrzega wspólnych zasad dla <xref:System.Windows.Documents.Block> elementów poziomu.  Element <xref:System.Windows.Documents.Table> może być zawarty przez którykolwiek z następujących elementów:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>
### <a name="row-groupings"></a>Grupowanie wierszy  
 Element <xref:System.Windows.Documents.TableRowGroup> umożliwia dowolne grupowanie wierszy w tabeli; każdy wiersz w tabeli musi należeć do grupowania wierszy.  Wiersze w grupie wierszy często mają wspólny zamiar i mogą być stylizowane jako grupa.  Typowym zastosowaniem grupowania wierszy jest oddzielenie wierszy specjalnego przeznaczenia, takich jak tytuł, nagłówek i wiersze stopki, od zawartości podstawowej zawartej w tabeli.  
  
 W poniższym przykładzie użyto xaml do zdefiniowania tabeli ze stylizowanymi wierszami nagłówka i stopki.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.  
  
 ![Zrzut ekranu: grupy wierszy tabeli](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>
### <a name="background-rendering-precedence"></a>Pierwszeństwo renderowania w tle  
 Elementy tabeli są renderowane w następującej kolejności (kolejność z od najniższej do najwyższej). Nie można zmienić tej kolejności. Na przykład nie ma właściwości "Z-order" dla tych elementów, które można użyć do zastąpienia tej ustalonej kolejności.  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 Rozważmy poniższy przykład, który definiuje kolory tła dla każdego z tych elementów w tabeli.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Na poniższym rysunku przedstawiono sposób renderowania w tym przykładzie (przedstawiający tylko kolory tła).  
  
 ![Zrzut ekranu: Tabela z&#45;kolejności](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>
### <a name="spanning-rows-or-columns"></a>Obejmujące wiersze lub kolumny  
 Komórki tabeli mogą być skonfigurowane tak, aby <xref:System.Windows.Documents.TableCell.RowSpan%2A> obejmowały <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> wiele wierszy lub kolumn, używając odpowiednio atrybutów lub.  
  
 Rozważmy poniższy przykład, w którym komórka obejmuje trzy kolumny.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.  
  
 ![Zrzut ekranu: komórka obejmująca wszystkie trzy kolumny](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>
## <a name="building-a-table-with-code"></a>Tworzenie tabeli z kodem  
 Poniższe przykłady pokazują, jak programowo utworzyć <xref:System.Windows.Documents.Table> i wypełnić go zawartością. Zawartość tabeli są podzielone na pięć wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> obiekty <xref:System.Windows.Documents.Table.RowGroups%2A> zawarte w obiekcie) i <xref:System.Windows.Documents.TableColumn> sześć kolumn (reprezentowane przez obiekty). Wiersze są używane do różnych celów prezentacji, w tym wiersza tytułu przeznaczonego do tytułu całej tabeli, wiersza nagłówka opisującego kolumny danych w tabeli oraz wiersza stopki z informacjami podsumowującymi.  Należy zauważyć, że pojęcie "tytuł", "nagłówek" i "stopka" wiersze nie są związane z tabeli; są to po prostu rzędy o różnych cechach. Komórki tabeli zawierają rzeczywistą zawartość, która może składać się [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] z tekstu, obrazów lub prawie każdego innego elementu.  
  
 Po pierwsze, <xref:System.Windows.Documents.FlowDocument> a jest <xref:System.Windows.Documents.Table>tworzony do <xref:System.Windows.Documents.Table> hosta , i nowy <xref:System.Windows.Documents.FlowDocument>jest tworzony i dodawany do zawartości .  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Następnie sześć <xref:System.Windows.Documents.TableColumn> obiektów są tworzone i dodawane do <xref:System.Windows.Documents.Table.Columns%2A> kolekcji tabeli, z niektórych formatowania stosowane.  
  
> [!NOTE]
> Należy zauważyć, że <xref:System.Windows.Documents.Table.Columns%2A> kolekcja tabeli używa standardowego indeksowania opartego na wartości zero.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Następnie tworzony jest wiersz tytułu i dodawany do tabeli z zastosowanym formatowaniem.  Wiersz tytułu zawiera pojedynczą komórkę, która obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Następnie tworzony jest i dodawany wiersz nagłówka do tabeli, a komórki w wierszu nagłówka są tworzone i wypełniane zawartością.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Następnie tworzony jest wiersz danych i dodawany do tabeli, a komórki w tym wierszu są tworzone i wypełniane zawartością.  Tworzenie tego wiersza jest podobne do tworzenia wiersza nagłówka z nieco innym formatowaniem.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Na koniec tworzony jest wiersz stopki, dodawany i sformatowany.  Podobnie jak wiersz tytułu, stopka zawiera pojedynczą komórkę, która obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd dokumentu przepływu](flow-document-overview.md)
- [Definiowanie tabeli przy użyciu XAML](how-to-define-a-table-with-xaml.md)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Używanie elementów zawartości przepływu](how-to-use-flow-content-elements.md)
