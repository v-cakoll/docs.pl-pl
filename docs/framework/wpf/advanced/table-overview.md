---
title: "Przegląd Tabela"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 922faa06456a1aa86ffd0c805ab33577280ccf4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="table-overview"></a>Przegląd Tabela
<xref:System.Windows.Documents.Table>jest elementem poziomu bloku, który obsługuje oparte na siatce prezentacji zawartości dokumentu przepływu. Elastyczność tego elementu ułatwia bardzo przydatne, ale również umożliwia bardziej skomplikowane zrozumieniu i użytkowaniu poprawnie.  
  
 Ten temat zawiera następujące sekcje.  
  
-   [Podstawowe informacje dotyczące tabeli](#table_basics)  
  
-   [W jaki sposób innej tabeli, a następnie siatki?](#table_vs_Grid)  
  
-   [Struktura tabeli podstawowej](#basic_table_structure)  
  
-   [Zawieranie tabeli](#table_containment)  
  
-   [Grupowań wierszy](#row_groupings)  
  
-   [Pierwszeństwo renderowania tła](#rendering_precedence)  
  
-   [Łączenie węzłów wierszy lub kolumn](#spanning_rows_or_columns)  
  
-   [Tworzenie tabeli z kodem](#building_a_table_with_code)  
  
-   [Tematy pokrewne] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Podstawowe informacje dotyczące tabeli  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>W jaki sposób innej tabeli, a następnie siatki?  
 <xref:System.Windows.Documents.Table>i <xref:System.Windows.Controls.Grid> udostępnianie niektóre typowe funkcje, ale każda jest najbardziej odpowiednie dla różnych scenariuszy. A <xref:System.Windows.Documents.Table> jest przeznaczony do użytku w dowolnej zawartości (zobacz [przepływu dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md) uzyskać więcej informacji o dowolnej zawartości). Najlepiej sprawdzają siatki wewnątrz formularzy (zasadniczo dowolnym poza przepływ zawartości). W ramach <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> obsługuje przepływ zachowania zawartości, takie jak podział na strony, ze zmianą ułożenia kolumn i wybór zawartości podczas <xref:System.Windows.Controls.Grid> nie. A <xref:System.Windows.Controls.Grid> z drugiej strony najlepiej jest używana poza <xref:System.Windows.Documents.FlowDocument> wielu powodów, takich jak <xref:System.Windows.Controls.Grid> dodaje elementy oparte na indeks wierszy i kolumn <xref:System.Windows.Documents.Table> nie. <xref:System.Windows.Controls.Grid> Element umożliwia warstwy zawartość elementu podrzędnego, dzięki czemu więcej niż jeden element istnieje w jednym "komórki." <xref:System.Windows.Documents.Table>nie obsługuje tworzenie warstw. Elementy podrzędne <xref:System.Windows.Controls.Grid> można bezwzględnego względem obszaru ich granice "komórki". <xref:System.Windows.Documents.Table>nie obsługuje tej funkcji. Na koniec <xref:System.Windows.Controls.Grid> wymaga mniej zasobów, a następnie <xref:System.Windows.Documents.Table> tak, rozważ użycie <xref:System.Windows.Controls.Grid> do zwiększenia wydajności.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Struktura tabeli podstawowej  
 <xref:System.Windows.Documents.Table>zapewnia oparte na siatce prezentacji składający się z kolumn (reprezentowane przez <xref:System.Windows.Documents.TableColumn> elementy), jak i wiersze (reprezentowane przez <xref:System.Windows.Documents.TableRow> elementów). <xref:System.Windows.Documents.TableColumn>elementy nie obsługują zawartość; po prostu definiują, kolumny i właściwości kolumn. <xref:System.Windows.Documents.TableRow>elementy muszą być hostowane w <xref:System.Windows.Documents.TableRowGroup> element, który definiuje grupowania wierszy dla tabeli. <xref:System.Windows.Documents.TableCell>elementów, które zawierają rzeczywiste zawartości będą widoczne w tabeli, musi być obsługiwana przez <xref:System.Windows.Documents.TableRow> elementu. <xref:System.Windows.Documents.TableCell>może zawierać tylko elementy, które pochodzą z <xref:System.Windows.Documents.Block>.  Elementy podrzędne prawidłowy dla <xref:System.Windows.Documents.TableCell> obejmują.  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell>elementy nie mogą bezpośrednio hostem zawartości tekstowej. Aby uzyskać więcej informacji o regułach zawierania dla przepływu elementów zawartości, takich jak <xref:System.Windows.Documents.TableCell>, zobacz [przepływu dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table>przypomina <xref:System.Windows.Controls.Grid> element a ma więcej możliwości i, w związku z tym wymaga większe obciążenie zasobów.  
  
 W poniższym przykładzie zdefiniowano prostą tabelę 2 x 3 z [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.  
  
 ![Zrzut ekranu: Renderowanie podstawowej tabeli](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Zawieranie tabeli  
 <xref:System.Windows.Documents.Table>pochodną <xref:System.Windows.Documents.Block> element i stosuje wspólne zasady dla <xref:System.Windows.Documents.Block> poziomu elementów.  A <xref:System.Windows.Documents.Table> elementu mogą znajdować się za pomocą dowolnej z następujących elementów:  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Grupowań wierszy  
 <xref:System.Windows.Documents.TableRowGroup> Element umożliwia arbitralnie grupy wierszy w tabeli; każdego wiersza w tabeli muszą należeć do grupowania wierszy.  Często wierszy w obrębie grupy wierszy udostępniać typowe opcje i może zostać wstawiony jako grupa.  Użycia grupowań wierszy ma oddzielić wierszy specjalnych, takich jak tytuł, nagłówku i stopce wierszy, od podstawowego zawartość w tabeli.  
  
 W poniższym przykładzie użyto [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] do definiowania tabeli z styl nagłówków i stopek wierszy.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.  
  
 ![Zrzut ekranu: Tabela grupy wierszy](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Pierwszeństwo renderowania tła  
 Renderowanie elementów tabeli w następującej kolejności (porządek osi z najniższą najwyższe). Nie można zmienić tego zamówienia. Na przykład nie ma właściwości "Porządek osi", dla tych elementów, które służą do przesłonięcia tego zamówienia ustalonych.  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 Rozważmy poniższy przykład, który definiuje kolory tła dla każdego z tych elementów w tabeli.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Na poniższej ilustracji przedstawiono, jak w tym przykładzie powoduje (tylko kolory tła przedstawiający).  
  
 ![Zrzut ekranu: Tabela z &#45; kolejność](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Łączenie węzłów wierszy lub kolumn  
 Komórek tabeli może być skonfigurowany tak, aby obejmować wiele wierszy lub kolumn za pomocą <xref:System.Windows.Documents.TableCell.RowSpan%2A> lub <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> atrybuty odpowiednio.  
  
 Rozważmy poniższy przykład, w którym komórki obejmuje trzy kolumny.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.  
  
 ![Zrzut ekranu: Komórka obejmująca wszystkie trzy kolumny](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Tworzenie tabeli z kodem  
 W poniższych przykładach pokazano, jak utworzyć programowo <xref:System.Windows.Documents.Table> i wypełnianie jej zawartości. Zawartość tabeli są rozdzielone do pięciu wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> obiektów zawartych w <xref:System.Windows.Documents.Table.RowGroups%2A> obiektu) i sześć kolumn (reprezentowane przez <xref:System.Windows.Documents.TableColumn> obiektów). Wiersze są używane do przedstawienia różnych celów, w tym tytuł wiersz przeznaczony do title całą tabelę, wiersz nagłówka do opisywania kolumn danych w tabeli i wiersz stopki z podsumowaniem.  Należy pamiętać, że pojęcie "title", "header" i "stopka" wierszy nie są włączone do tabeli; są to po prostu wierszy o różnej charakterystyce. Komórki tabeli zawierają rzeczywistej zawartości, może składać się z tekstu, obrazów lub niemal każdy inny [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.  
  
 Najpierw <xref:System.Windows.Documents.FlowDocument> jest tworzony na hoście <xref:System.Windows.Documents.Table>i nowy <xref:System.Windows.Documents.Table> jest tworzony i dodawany do zawartości <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Następnie sześciu <xref:System.Windows.Documents.TableColumn> obiekty są tworzone i dodawane do tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcji z niektórych formatowanie zastosowane.  
  
> [!NOTE]
>  Należy pamiętać, że tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcja używa standardowych indeksowania liczony od zera.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Następnie wiersz tytuł jest utworzony i dodane do tabeli z niektórych formatowanie zastosowane.  Wiersz tytułu odbywa się zawiera jedną komórkę, które obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Następnie wiersz nagłówka jest tworzony i dodawany do tabeli i komórek w wierszu nagłówka są tworzone i wypełniane przy użyciu zawartości.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Następnie wiersz danych jest tworzony i dodawany do tabeli i komórek w tym wierszu są tworzone i wypełniane przy użyciu zawartości.  Tworzenie tego wiersza jest podobny do budowania wiersz nagłówka z zastosowanym formatowaniem nieco inne.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Na koniec wiersza stopki jest utworzony, dodane i sformatowany.  Podobnie jak wiersz tytuł stopki zawiera jedną komórkę, które obejmuje wszystkie sześć kolumn w tabeli.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd dokumentu przepływu](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Definiowanie tabeli przy użyciu XAML](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Używanie elementów zawartości przepływu](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)
