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
ms.openlocfilehash: 6485aa9f2094b734f796ff38a33f4e0d3434e004
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317665"
---
# <a name="table-overview"></a><span data-ttu-id="9d482-102">Przegląd Tabela</span><span class="sxs-lookup"><span data-stu-id="9d482-102">Table Overview</span></span>
<span data-ttu-id="9d482-103"><xref:System.Windows.Documents.Table> jest element poziomu bloku, który obsługuje oparte na siatce prezentacji zawartości dokumentu przepływu.</span><span class="sxs-lookup"><span data-stu-id="9d482-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="9d482-104">Elastyczność tego elementu sprawia, że bardzo przydatne, ale także stanowi bardziej skomplikowane, aby zrozumieć i zastosować poprawnie.</span><span class="sxs-lookup"><span data-stu-id="9d482-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="9d482-105">Ten temat zawiera następujące sekcje.</span><span class="sxs-lookup"><span data-stu-id="9d482-105">This topic contains the following sections.</span></span>  
  
-   [<span data-ttu-id="9d482-106">Podstawowe informacje dotyczące tabeli</span><span class="sxs-lookup"><span data-stu-id="9d482-106">Table Basics</span></span>](#table_basics)  
  
-   [<span data-ttu-id="9d482-107">W jaki sposób innej tabeli, a następnie siatki?</span><span class="sxs-lookup"><span data-stu-id="9d482-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
-   [<span data-ttu-id="9d482-108">Struktura tabeli podstawowej</span><span class="sxs-lookup"><span data-stu-id="9d482-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
-   [<span data-ttu-id="9d482-109">Tabela zawierania</span><span class="sxs-lookup"><span data-stu-id="9d482-109">Table Containment</span></span>](#table_containment)  
  
-   [<span data-ttu-id="9d482-110">Grupowań wierszy</span><span class="sxs-lookup"><span data-stu-id="9d482-110">Row Groupings</span></span>](#row_groupings)  
  
-   [<span data-ttu-id="9d482-111">Pierwszeństwo renderowania w tle</span><span class="sxs-lookup"><span data-stu-id="9d482-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
-   [<span data-ttu-id="9d482-112">Łączenie wierszy lub kolumn</span><span class="sxs-lookup"><span data-stu-id="9d482-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
-   [<span data-ttu-id="9d482-113">Tworzenie tabeli przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="9d482-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
-   <span data-ttu-id="9d482-114">[Tematy pokrewne]</span><span class="sxs-lookup"><span data-stu-id="9d482-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="9d482-115">Podstawowe informacje dotyczące tabeli</span><span class="sxs-lookup"><span data-stu-id="9d482-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="9d482-116">W jaki sposób innej tabeli, a następnie siatki?</span><span class="sxs-lookup"><span data-stu-id="9d482-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="9d482-117"><xref:System.Windows.Documents.Table> i <xref:System.Windows.Controls.Grid> udostępnianie niektóre typowe funkcje, ale każdy jest najbardziej odpowiednie dla różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="9d482-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="9d482-118">A <xref:System.Windows.Documents.Table> jest przeznaczony do użytku w ramach dowolnej zawartości (zobacz [Przegląd dokumentu przepływu](flow-document-overview.md) więcej informacji na temat zawartości przepływu).</span><span class="sxs-lookup"><span data-stu-id="9d482-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="9d482-119">Siatki najlepiej sprawdzają się wewnątrz formularzy (zasadniczo dowolne miejsce poza przepływ zawartości).</span><span class="sxs-lookup"><span data-stu-id="9d482-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="9d482-120">W ramach <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> obsługuje przepływ zawartości zachowań, takich jak podział na strony, ze zmianą ułożenia kolumny i zawartości zaznaczenia podczas <xref:System.Windows.Controls.Grid> nie.</span><span class="sxs-lookup"><span data-stu-id="9d482-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="9d482-121">A <xref:System.Windows.Controls.Grid> z drugiej strony najlepiej nadaje się poza <xref:System.Windows.Documents.FlowDocument> wiele powodów, takich jak <xref:System.Windows.Controls.Grid> dodaje elementy w oparciu o indeks wierszy i kolumn <xref:System.Windows.Documents.Table> nie.</span><span class="sxs-lookup"><span data-stu-id="9d482-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="9d482-122"><xref:System.Windows.Controls.Grid> Elementu umożliwia warstwowe zawartość elementu podrzędnego, dzięki czemu więcej niż jeden element istnieje w jednej "komórki."</span><span class="sxs-lookup"><span data-stu-id="9d482-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="9d482-123"><xref:System.Windows.Documents.Table> nie obsługują warstw.</span><span class="sxs-lookup"><span data-stu-id="9d482-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="9d482-124">Elementy podrzędne <xref:System.Windows.Controls.Grid> można pozycjonowane absolutnie względem pola ich granice "komórki".</span><span class="sxs-lookup"><span data-stu-id="9d482-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="9d482-125"><xref:System.Windows.Documents.Table> nie obsługuje tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="9d482-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="9d482-126">Na koniec <xref:System.Windows.Controls.Grid> wymaga mniej zasobów, a następnie <xref:System.Windows.Documents.Table> zatem należy wziąć pod uwagę przy użyciu <xref:System.Windows.Controls.Grid> poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="9d482-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="9d482-127">Struktura tabeli podstawowej</span><span class="sxs-lookup"><span data-stu-id="9d482-127">Basic Table Structure</span></span>  
 <span data-ttu-id="9d482-128"><xref:System.Windows.Documents.Table> zapewnia prezentację na podstawie siatki składający się z kolumn (reprezentowane przez <xref:System.Windows.Documents.TableColumn> elementy) i wiersze (reprezentowane przez <xref:System.Windows.Documents.TableRow> elementów).</span><span class="sxs-lookup"><span data-stu-id="9d482-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="9d482-129"><xref:System.Windows.Documents.TableColumn> elementy nie jest hostem zawartości; określają one po prostu, kolumn i właściwości kolumn.</span><span class="sxs-lookup"><span data-stu-id="9d482-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="9d482-130"><xref:System.Windows.Documents.TableRow> elementy muszą być hostowane w <xref:System.Windows.Documents.TableRowGroup> element, który definiuje grupowanie wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="9d482-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="9d482-131"><xref:System.Windows.Documents.TableCell> elementy, które zawierają rzeczywistej zawartości, które mają zostać wyświetlone w tabeli, musi być hostowany w <xref:System.Windows.Documents.TableRow> elementu.</span><span class="sxs-lookup"><span data-stu-id="9d482-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="9d482-132"><xref:System.Windows.Documents.TableCell> może zawierać tylko elementy, które wynikają z <xref:System.Windows.Documents.Block>.</span><span class="sxs-lookup"><span data-stu-id="9d482-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="9d482-133">Elementy prawidłowy element podrzędny dla <xref:System.Windows.Documents.TableCell> obejmują.</span><span class="sxs-lookup"><span data-stu-id="9d482-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <span data-ttu-id="9d482-134"><xref:System.Windows.Documents.TableCell> elementy nie mogą bezpośrednio hostem zawartości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="9d482-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="9d482-135">Aby uzyskać więcej informacji o regułach zawierania dla przepływu, takich jak elementy zawartości <xref:System.Windows.Documents.TableCell>, zobacz [Przegląd dokumentu przepływu](flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9d482-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d482-136"><xref:System.Windows.Documents.Table> jest podobny do <xref:System.Windows.Controls.Grid> element ale ma więcej możliwości i, w związku z tym, wymaga większe obciążenie zasobów.</span><span class="sxs-lookup"><span data-stu-id="9d482-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="9d482-137">W poniższym przykładzie zdefiniowano prostej tabeli 2 x 3 z [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d482-137">The following example defines a simple 2 x 3 table with [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="9d482-138">Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9d482-138">The following figure shows how this example renders.</span></span>  
  
 ![Zrzut ekranu pokazujący, jak renderuje tabeli podstawowej.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="9d482-140">Tabela zawierania</span><span class="sxs-lookup"><span data-stu-id="9d482-140">Table Containment</span></span>  
 <span data-ttu-id="9d482-141"><xref:System.Windows.Documents.Table> pochodzi od klasy <xref:System.Windows.Documents.Block> element i stosuje reguły wspólnej <xref:System.Windows.Documents.Block> na poziomie elementów.</span><span class="sxs-lookup"><span data-stu-id="9d482-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="9d482-142">Element <xref:System.Windows.Documents.Table> elementu mogą znajdować się według dowolnej z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="9d482-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="9d482-143">Grupowań wierszy</span><span class="sxs-lookup"><span data-stu-id="9d482-143">Row Groupings</span></span>  
 <span data-ttu-id="9d482-144"><xref:System.Windows.Documents.TableRowGroup> Element zapewnia sposób arbitralnie grupowanie wierszy w tabeli; każdy wiersz w tabeli musi należeć do grupowań wierszy.</span><span class="sxs-lookup"><span data-stu-id="9d482-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="9d482-145">Często wierszy w obrębie grupy wierszy udostępniać typowe opcje i może być wstawiony jako grupa.</span><span class="sxs-lookup"><span data-stu-id="9d482-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="9d482-146">Typowym zastosowaniem dla grupowań wierszy jest do rozdzielania wierszy specjalnych, takich jak tytuł, nagłówek i stopka wierszy z podstawowego zawartości, zawartych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="9d482-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="9d482-147">W poniższym przykładzie użyto [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] do definiowania tabeli ze stylem wierszy w nagłówku i stopce.</span><span class="sxs-lookup"><span data-stu-id="9d482-147">The following example uses [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="9d482-148">Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9d482-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="9d482-149">![Zrzut ekranu: Grupami wierszy tabeli](./media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="9d482-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="9d482-150">Pierwszeństwo renderowania w tle</span><span class="sxs-lookup"><span data-stu-id="9d482-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="9d482-151">Elementy tabeli renderowane w następującej kolejności (porządek od najniższej do najwyższej).</span><span class="sxs-lookup"><span data-stu-id="9d482-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="9d482-152">Nie można zmienić tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="9d482-152">This order cannot be changed.</span></span> <span data-ttu-id="9d482-153">Na przykład nie ma żadnej właściwości "Kolejności Z" dla tych elementów, których można zmienić tę kolejność ustalonych.</span><span class="sxs-lookup"><span data-stu-id="9d482-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="9d482-154">Rozważmy następujący przykład, który definiuje kolory tła dla każdego z tych elementów w tabeli.</span><span class="sxs-lookup"><span data-stu-id="9d482-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="9d482-155">Na poniższej ilustracji przedstawiono, jak w tym przykładzie powoduje wyświetlenie (tylko kolory tła przedstawiający).</span><span class="sxs-lookup"><span data-stu-id="9d482-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="9d482-156">![Zrzut ekranu: Tabela z&#45;kolejności](./media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="9d482-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="9d482-157">Łączenie wierszy lub kolumn</span><span class="sxs-lookup"><span data-stu-id="9d482-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="9d482-158">Komórki tabeli może być skonfigurowany na wiele wierszy lub kolumn przy użyciu <xref:System.Windows.Documents.TableCell.RowSpan%2A> lub <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> , odpowiednio, atrybutów.</span><span class="sxs-lookup"><span data-stu-id="9d482-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="9d482-159">Rozważmy następujący przykład, w którym komórki obejmuje trzy kolumny.</span><span class="sxs-lookup"><span data-stu-id="9d482-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="9d482-160">Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9d482-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="9d482-161">![Zrzut ekranu: Komórka obejmująca wszystkie trzy kolumny](./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="9d482-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="9d482-162">Tworzenie tabeli przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="9d482-162">Building a Table With Code</span></span>  
 <span data-ttu-id="9d482-163">W poniższych przykładach pokazano, jak programowo utworzyć <xref:System.Windows.Documents.Table> i wypełnianie jej zawartości.</span><span class="sxs-lookup"><span data-stu-id="9d482-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="9d482-164">Zawartość tej tabeli są rozdzielone na pięć wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> obiektów zawartych w <xref:System.Windows.Documents.Table.RowGroups%2A> obiekt) i 6 kolumn (reprezentowane przez <xref:System.Windows.Documents.TableColumn> obiektów).</span><span class="sxs-lookup"><span data-stu-id="9d482-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="9d482-165">Wiersze są używane do celów innej prezentacji, w tym wiersz tytułu przeznaczone do tytułu całą tabelę, wiersz nagłówka do opisania kolumn danych w tabeli i wiersz stopki z podsumowaniem.</span><span class="sxs-lookup"><span data-stu-id="9d482-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="9d482-166">Należy pamiętać, że pojęcie "title", "header" i "stopka" wierszy nie są wbudowane w tabeli; są to po prostu wiersze o różnej charakterystyce.</span><span class="sxs-lookup"><span data-stu-id="9d482-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="9d482-167">Komórki tabeli zawierają rzeczywistej zawartości może składać się z tekstu, obrazów lub niemal każdy inny [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="9d482-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="9d482-168">Najpierw <xref:System.Windows.Documents.FlowDocument> jest tworzona na hoście <xref:System.Windows.Documents.Table>, nowy <xref:System.Windows.Documents.Table> zostanie utworzony i dodany do zawartości <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="9d482-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="9d482-169">Następnie sześciu <xref:System.Windows.Documents.TableColumn> obiekty są tworzone i dodawane do tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcji z niektórych zastosowanym formatowaniem.</span><span class="sxs-lookup"><span data-stu-id="9d482-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d482-170">Należy pamiętać, że tabela <xref:System.Windows.Documents.Table.Columns%2A> kolekcja używa standardowych indeksowania zaczynającego się od zera.</span><span class="sxs-lookup"><span data-stu-id="9d482-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="9d482-171">Następnie wiersz tytułu jest tworzone i dodawane do tabeli za pomocą niektórych zastosowanym formatowaniem.</span><span class="sxs-lookup"><span data-stu-id="9d482-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="9d482-172">Wiersz tytułu odbywa się zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="9d482-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="9d482-173">Następnie wiersz nagłówka zostanie utworzony i dodany do tabeli i komórki w wierszu nagłówka są tworzone i wypełniane zawartością.</span><span class="sxs-lookup"><span data-stu-id="9d482-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="9d482-174">Następnie wiersz danych zostanie utworzony i dodany do tabeli i komórek w tym wierszu są tworzone i wypełniane zawartością.</span><span class="sxs-lookup"><span data-stu-id="9d482-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="9d482-175">Tworzenie tego wiersza jest podobne do tworzenia wiersz nagłówka z zastosowanym formatowaniem nieco inne.</span><span class="sxs-lookup"><span data-stu-id="9d482-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="9d482-176">Na koniec wiersza stopki utworzone, dodać i sformatowany.</span><span class="sxs-lookup"><span data-stu-id="9d482-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="9d482-177">Podobnie jak wiersz tytułu stopki zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="9d482-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="9d482-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d482-178">See also</span></span>

- [<span data-ttu-id="9d482-179">Przegląd dokumentu przepływu</span><span class="sxs-lookup"><span data-stu-id="9d482-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="9d482-180">Definiowanie tabeli przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="9d482-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="9d482-181">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="9d482-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="9d482-182">Używanie elementów zawartości przepływu</span><span class="sxs-lookup"><span data-stu-id="9d482-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
