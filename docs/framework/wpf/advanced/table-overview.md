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
# <a name="table-overview"></a><span data-ttu-id="ade73-102">Omówienie tabel</span><span class="sxs-lookup"><span data-stu-id="ade73-102">Table Overview</span></span>
<span data-ttu-id="ade73-103"><xref:System.Windows.Documents.Table>jest elementem poziomu bloku, który obsługuje prezentację zawartości dokumentu flow opartą na siatce.</span><span class="sxs-lookup"><span data-stu-id="ade73-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="ade73-104">Elastyczność tego elementu sprawia, że jest bardzo przydatny, ale także sprawia, że bardziej skomplikowane jest prawidłowe zrozumienie i użycie.</span><span class="sxs-lookup"><span data-stu-id="ade73-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="ade73-105">Ten temat zawiera poniższe sekcje.</span><span class="sxs-lookup"><span data-stu-id="ade73-105">This topic contains the following sections.</span></span>  
  
- [<span data-ttu-id="ade73-106">Podstawy tabeli</span><span class="sxs-lookup"><span data-stu-id="ade73-106">Table Basics</span></span>](#table_basics)  
  
- [<span data-ttu-id="ade73-107">Jak tabela jest inna niż Grid?</span><span class="sxs-lookup"><span data-stu-id="ade73-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
- [<span data-ttu-id="ade73-108">Podstawowa struktura tabeli</span><span class="sxs-lookup"><span data-stu-id="ade73-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
- [<span data-ttu-id="ade73-109">Hermetyzacja tabeli</span><span class="sxs-lookup"><span data-stu-id="ade73-109">Table Containment</span></span>](#table_containment)  
  
- [<span data-ttu-id="ade73-110">Grupowanie wierszy</span><span class="sxs-lookup"><span data-stu-id="ade73-110">Row Groupings</span></span>](#row_groupings)  
  
- [<span data-ttu-id="ade73-111">Pierwszeństwo renderowania w tle</span><span class="sxs-lookup"><span data-stu-id="ade73-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
- [<span data-ttu-id="ade73-112">Obejmujące wiersze lub kolumny</span><span class="sxs-lookup"><span data-stu-id="ade73-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
- [<span data-ttu-id="ade73-113">Tworzenie tabeli z kodem</span><span class="sxs-lookup"><span data-stu-id="ade73-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
- <span data-ttu-id="ade73-114">[Tematy pokrewne]</span><span class="sxs-lookup"><span data-stu-id="ade73-114">[Related Topics]</span></span>
  
<a name="table_basics"></a>
## <a name="table-basics"></a><span data-ttu-id="ade73-115">Podstawy tabeli</span><span class="sxs-lookup"><span data-stu-id="ade73-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="ade73-116">Jak tabela jest inna niż Grid?</span><span class="sxs-lookup"><span data-stu-id="ade73-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="ade73-117"><xref:System.Windows.Documents.Table>i <xref:System.Windows.Controls.Grid> dzielić niektóre typowe funkcje, ale każdy jest najlepiej nadaje się do różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="ade73-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="ade73-118">A <xref:System.Windows.Documents.Table> jest przeznaczony do użytku w ramach zawartości przepływu (zobacz [Omówienie dokumentu przepływu, aby](flow-document-overview.md) uzyskać więcej informacji na temat zawartości przepływu).</span><span class="sxs-lookup"><span data-stu-id="ade73-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="ade73-119">Siatki są najlepiej używane wewnątrz formularzy (w zasadzie w dowolnym miejscu poza zawartością przepływu).</span><span class="sxs-lookup"><span data-stu-id="ade73-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="ade73-120">W <xref:System.Windows.Documents.FlowDocument>obrębie <xref:System.Windows.Documents.Table> , obsługuje zachowania zawartości przepływu, takie jak podział na <xref:System.Windows.Controls.Grid> strony, ponowne wlanie kolumny i wybór zawartości, podczas gdy nie.</span><span class="sxs-lookup"><span data-stu-id="ade73-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="ade73-121">A <xref:System.Windows.Controls.Grid> z drugiej strony najlepiej jest <xref:System.Windows.Documents.FlowDocument> używany poza <xref:System.Windows.Controls.Grid> a z wielu powodów, <xref:System.Windows.Documents.Table> w tym dodaje elementy oparte na indeksie wiersza i kolumny, nie.</span><span class="sxs-lookup"><span data-stu-id="ade73-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="ade73-122">Element <xref:System.Windows.Controls.Grid> umożliwia nakładanie warstw zawartości podrzędnej, dzięki czemu więcej niż jeden element istnieje w pojedynczej "komórce".</span><span class="sxs-lookup"><span data-stu-id="ade73-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="ade73-123"><xref:System.Windows.Documents.Table>nie obsługuje nakładania warstw.</span><span class="sxs-lookup"><span data-stu-id="ade73-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="ade73-124">Elementy podrzędne <xref:System.Windows.Controls.Grid> a mogą być absolutnie umieszczone względem obszaru ich "komórki" granice.</span><span class="sxs-lookup"><span data-stu-id="ade73-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="ade73-125"><xref:System.Windows.Documents.Table>nie obsługuje tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ade73-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="ade73-126">Na koniec <xref:System.Windows.Controls.Grid> wymaga mniej zasobów, a następnie <xref:System.Windows.Documents.Table> należy rozważyć użycie a <xref:System.Windows.Controls.Grid> w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="ade73-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>
### <a name="basic-table-structure"></a><span data-ttu-id="ade73-127">Podstawowa struktura tabeli</span><span class="sxs-lookup"><span data-stu-id="ade73-127">Basic Table Structure</span></span>  
 <span data-ttu-id="ade73-128"><xref:System.Windows.Documents.Table>zawiera prezentację opartą na siatce <xref:System.Windows.Documents.TableColumn> składającą się z kolumn <xref:System.Windows.Documents.TableRow> (reprezentowanych przez elementy) i wierszy (reprezentowanych przez elementy).</span><span class="sxs-lookup"><span data-stu-id="ade73-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="ade73-129"><xref:System.Windows.Documents.TableColumn>elementy nie hostują zawartości; po prostu definiują kolumny i charakterystyki kolumn.</span><span class="sxs-lookup"><span data-stu-id="ade73-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="ade73-130"><xref:System.Windows.Documents.TableRow>elementy muszą być hostowane w elemencie, <xref:System.Windows.Documents.TableRowGroup> który definiuje grupowanie wierszy dla tabeli.</span><span class="sxs-lookup"><span data-stu-id="ade73-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="ade73-131"><xref:System.Windows.Documents.TableCell>elementy, które zawierają rzeczywistą zawartość, która ma być przedstawiona przez tabelę, muszą być hostowane w elemencie. <xref:System.Windows.Documents.TableRow></span><span class="sxs-lookup"><span data-stu-id="ade73-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="ade73-132"><xref:System.Windows.Documents.TableCell>mogą zawierać tylko elementy, <xref:System.Windows.Documents.Block>które wynikają z .</span><span class="sxs-lookup"><span data-stu-id="ade73-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="ade73-133">Prawidłowe elementy <xref:System.Windows.Documents.TableCell> podrzędne dla include.</span><span class="sxs-lookup"><span data-stu-id="ade73-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <span data-ttu-id="ade73-134"><xref:System.Windows.Documents.TableCell>elementy nie mogą bezpośrednio hostować zawartości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="ade73-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="ade73-135">Aby uzyskać więcej informacji na temat reguł <xref:System.Windows.Documents.TableCell>zamknięcia dla elementów zawartości przepływu, takich jak , zobacz [Omówienie dokumentu przepływu](flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ade73-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ade73-136"><xref:System.Windows.Documents.Table>jest podobny <xref:System.Windows.Controls.Grid> do elementu, ale ma więcej możliwości i dlatego wymaga większego obciążenia zasobów.</span><span class="sxs-lookup"><span data-stu-id="ade73-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="ade73-137">Poniższy przykład definiuje prostą tabelę 2 x 3 z XAML.</span><span class="sxs-lookup"><span data-stu-id="ade73-137">The following example defines a simple 2 x 3 table with XAML.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="ade73-138">Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ade73-138">The following figure shows how this example renders.</span></span>  
  
 ![Zrzut ekranu przedstawiający sposób renderowania podstawowej tabeli.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>
### <a name="table-containment"></a><span data-ttu-id="ade73-140">Hermetyzacja tabeli</span><span class="sxs-lookup"><span data-stu-id="ade73-140">Table Containment</span></span>  
 <span data-ttu-id="ade73-141"><xref:System.Windows.Documents.Table>pochodzi z <xref:System.Windows.Documents.Block> elementu i przestrzega wspólnych zasad dla <xref:System.Windows.Documents.Block> elementów poziomu.</span><span class="sxs-lookup"><span data-stu-id="ade73-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="ade73-142">Element <xref:System.Windows.Documents.Table> może być zawarty przez którykolwiek z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="ade73-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>
### <a name="row-groupings"></a><span data-ttu-id="ade73-143">Grupowanie wierszy</span><span class="sxs-lookup"><span data-stu-id="ade73-143">Row Groupings</span></span>  
 <span data-ttu-id="ade73-144">Element <xref:System.Windows.Documents.TableRowGroup> umożliwia dowolne grupowanie wierszy w tabeli; każdy wiersz w tabeli musi należeć do grupowania wierszy.</span><span class="sxs-lookup"><span data-stu-id="ade73-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="ade73-145">Wiersze w grupie wierszy często mają wspólny zamiar i mogą być stylizowane jako grupa.</span><span class="sxs-lookup"><span data-stu-id="ade73-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="ade73-146">Typowym zastosowaniem grupowania wierszy jest oddzielenie wierszy specjalnego przeznaczenia, takich jak tytuł, nagłówek i wiersze stopki, od zawartości podstawowej zawartej w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ade73-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="ade73-147">W poniższym przykładzie użyto xaml do zdefiniowania tabeli ze stylizowanymi wierszami nagłówka i stopki.</span><span class="sxs-lookup"><span data-stu-id="ade73-147">The following example uses XAML to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="ade73-148">Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ade73-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="ade73-149">![Zrzut ekranu: grupy wierszy tabeli](./media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="ade73-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>
### <a name="background-rendering-precedence"></a><span data-ttu-id="ade73-150">Pierwszeństwo renderowania w tle</span><span class="sxs-lookup"><span data-stu-id="ade73-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="ade73-151">Elementy tabeli są renderowane w następującej kolejności (kolejność z od najniższej do najwyższej).</span><span class="sxs-lookup"><span data-stu-id="ade73-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="ade73-152">Nie można zmienić tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="ade73-152">This order cannot be changed.</span></span> <span data-ttu-id="ade73-153">Na przykład nie ma właściwości "Z-order" dla tych elementów, które można użyć do zastąpienia tej ustalonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="ade73-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="ade73-154">Rozważmy poniższy przykład, który definiuje kolory tła dla każdego z tych elementów w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ade73-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="ade73-155">Na poniższym rysunku przedstawiono sposób renderowania w tym przykładzie (przedstawiający tylko kolory tła).</span><span class="sxs-lookup"><span data-stu-id="ade73-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="ade73-156">![Zrzut ekranu: Tabela z&#45;kolejności](./media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="ade73-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="ade73-157">Obejmujące wiersze lub kolumny</span><span class="sxs-lookup"><span data-stu-id="ade73-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="ade73-158">Komórki tabeli mogą być skonfigurowane tak, aby <xref:System.Windows.Documents.TableCell.RowSpan%2A> obejmowały <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> wiele wierszy lub kolumn, używając odpowiednio atrybutów lub.</span><span class="sxs-lookup"><span data-stu-id="ade73-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="ade73-159">Rozważmy poniższy przykład, w którym komórka obejmuje trzy kolumny.</span><span class="sxs-lookup"><span data-stu-id="ade73-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="ade73-160">Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ade73-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="ade73-161">![Zrzut ekranu: komórka obejmująca wszystkie trzy kolumny](./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="ade73-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>
## <a name="building-a-table-with-code"></a><span data-ttu-id="ade73-162">Tworzenie tabeli z kodem</span><span class="sxs-lookup"><span data-stu-id="ade73-162">Building a Table With Code</span></span>  
 <span data-ttu-id="ade73-163">Poniższe przykłady pokazują, jak programowo utworzyć <xref:System.Windows.Documents.Table> i wypełnić go zawartością.</span><span class="sxs-lookup"><span data-stu-id="ade73-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="ade73-164">Zawartość tabeli są podzielone na pięć wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> obiekty <xref:System.Windows.Documents.Table.RowGroups%2A> zawarte w obiekcie) i <xref:System.Windows.Documents.TableColumn> sześć kolumn (reprezentowane przez obiekty).</span><span class="sxs-lookup"><span data-stu-id="ade73-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="ade73-165">Wiersze są używane do różnych celów prezentacji, w tym wiersza tytułu przeznaczonego do tytułu całej tabeli, wiersza nagłówka opisującego kolumny danych w tabeli oraz wiersza stopki z informacjami podsumowującymi.</span><span class="sxs-lookup"><span data-stu-id="ade73-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="ade73-166">Należy zauważyć, że pojęcie "tytuł", "nagłówek" i "stopka" wiersze nie są związane z tabeli; są to po prostu rzędy o różnych cechach.</span><span class="sxs-lookup"><span data-stu-id="ade73-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="ade73-167">Komórki tabeli zawierają rzeczywistą zawartość, która może składać się [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] z tekstu, obrazów lub prawie każdego innego elementu.</span><span class="sxs-lookup"><span data-stu-id="ade73-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="ade73-168">Po pierwsze, <xref:System.Windows.Documents.FlowDocument> a jest <xref:System.Windows.Documents.Table>tworzony do <xref:System.Windows.Documents.Table> hosta , i nowy <xref:System.Windows.Documents.FlowDocument>jest tworzony i dodawany do zawartości .</span><span class="sxs-lookup"><span data-stu-id="ade73-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="ade73-169">Następnie sześć <xref:System.Windows.Documents.TableColumn> obiektów są tworzone i dodawane do <xref:System.Windows.Documents.Table.Columns%2A> kolekcji tabeli, z niektórych formatowania stosowane.</span><span class="sxs-lookup"><span data-stu-id="ade73-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ade73-170">Należy zauważyć, że <xref:System.Windows.Documents.Table.Columns%2A> kolekcja tabeli używa standardowego indeksowania opartego na wartości zero.</span><span class="sxs-lookup"><span data-stu-id="ade73-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="ade73-171">Następnie tworzony jest wiersz tytułu i dodawany do tabeli z zastosowanym formatowaniem.</span><span class="sxs-lookup"><span data-stu-id="ade73-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="ade73-172">Wiersz tytułu zawiera pojedynczą komórkę, która obejmuje wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ade73-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="ade73-173">Następnie tworzony jest i dodawany wiersz nagłówka do tabeli, a komórki w wierszu nagłówka są tworzone i wypełniane zawartością.</span><span class="sxs-lookup"><span data-stu-id="ade73-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="ade73-174">Następnie tworzony jest wiersz danych i dodawany do tabeli, a komórki w tym wierszu są tworzone i wypełniane zawartością.</span><span class="sxs-lookup"><span data-stu-id="ade73-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="ade73-175">Tworzenie tego wiersza jest podobne do tworzenia wiersza nagłówka z nieco innym formatowaniem.</span><span class="sxs-lookup"><span data-stu-id="ade73-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="ade73-176">Na koniec tworzony jest wiersz stopki, dodawany i sformatowany.</span><span class="sxs-lookup"><span data-stu-id="ade73-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="ade73-177">Podobnie jak wiersz tytułu, stopka zawiera pojedynczą komórkę, która obejmuje wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ade73-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="ade73-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ade73-178">See also</span></span>

- [<span data-ttu-id="ade73-179">Przegląd dokumentu przepływu</span><span class="sxs-lookup"><span data-stu-id="ade73-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="ade73-180">Definiowanie tabeli przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="ade73-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="ade73-181">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="ade73-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="ade73-182">Używanie elementów zawartości przepływu</span><span class="sxs-lookup"><span data-stu-id="ade73-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
