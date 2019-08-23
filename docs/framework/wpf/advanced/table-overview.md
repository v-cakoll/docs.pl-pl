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
ms.openlocfilehash: 01a5233a5436688caee3783cb26d344284df52e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964298"
---
# <a name="table-overview"></a><span data-ttu-id="91b2e-102">Przegląd Tabela</span><span class="sxs-lookup"><span data-stu-id="91b2e-102">Table Overview</span></span>
<span data-ttu-id="91b2e-103"><xref:System.Windows.Documents.Table>jest elementem poziomu bloku, który obsługuje prezentację zawartości dokumentu przepływu na podstawie siatki.</span><span class="sxs-lookup"><span data-stu-id="91b2e-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="91b2e-104">Elastyczność tego elementu sprawia, że jest to bardzo przydatne, ale również bardziej skomplikowane do zrozumienia i użycia.</span><span class="sxs-lookup"><span data-stu-id="91b2e-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="91b2e-105">Ten temat zawiera następujące sekcje.</span><span class="sxs-lookup"><span data-stu-id="91b2e-105">This topic contains the following sections.</span></span>  
  
- [<span data-ttu-id="91b2e-106">Podstawowe informacje dotyczące tabeli</span><span class="sxs-lookup"><span data-stu-id="91b2e-106">Table Basics</span></span>](#table_basics)  
  
- [<span data-ttu-id="91b2e-107">Czym różni się tabela w tabeli?</span><span class="sxs-lookup"><span data-stu-id="91b2e-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
- [<span data-ttu-id="91b2e-108">Podstawowa struktura tabeli</span><span class="sxs-lookup"><span data-stu-id="91b2e-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
- [<span data-ttu-id="91b2e-109">Zawieranie tabeli</span><span class="sxs-lookup"><span data-stu-id="91b2e-109">Table Containment</span></span>](#table_containment)  
  
- [<span data-ttu-id="91b2e-110">Grupowanie wierszy</span><span class="sxs-lookup"><span data-stu-id="91b2e-110">Row Groupings</span></span>](#row_groupings)  
  
- [<span data-ttu-id="91b2e-111">Pierwszeństwo renderowania w tle</span><span class="sxs-lookup"><span data-stu-id="91b2e-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
- [<span data-ttu-id="91b2e-112">Łączenie wierszy lub kolumn</span><span class="sxs-lookup"><span data-stu-id="91b2e-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
- [<span data-ttu-id="91b2e-113">Kompilowanie tabeli przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="91b2e-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
- <span data-ttu-id="91b2e-114">[Tematy pokrewne]</span><span class="sxs-lookup"><span data-stu-id="91b2e-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="91b2e-115">Podstawowe informacje dotyczące tabeli</span><span class="sxs-lookup"><span data-stu-id="91b2e-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="91b2e-116">Czym różni się tabela w tabeli?</span><span class="sxs-lookup"><span data-stu-id="91b2e-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="91b2e-117"><xref:System.Windows.Documents.Table>i <xref:System.Windows.Controls.Grid> udostępniaj niektóre typowe funkcje, ale każdy z nich jest najlepiej dostosowany do różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="91b2e-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="91b2e-118">Jest <xref:System.Windows.Documents.Table> przeznaczony do użycia w obrębie zawartości przepływu (zobacz temat [Omówienie dokumentu Flow](flow-document-overview.md) , aby uzyskać więcej informacji na temat przepływu zawartości).</span><span class="sxs-lookup"><span data-stu-id="91b2e-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="91b2e-119">Siatki najlepiej używać wewnątrz formularzy (zasadniczo poza zawartością przepływu).</span><span class="sxs-lookup"><span data-stu-id="91b2e-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="91b2e-120">W programie obsługuje zachowania zawartości przepływu, takie jak stronicowanie, Ponowne wlewanie kolumn <xref:System.Windows.Controls.Grid> i wybór zawartości, a nie. <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.FlowDocument></span><span class="sxs-lookup"><span data-stu-id="91b2e-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="91b2e-121">Z drugiej strony najlepiej używać poza a <xref:System.Windows.Documents.FlowDocument> z wielu powodów, takich jak <xref:System.Windows.Controls.Grid> Dodawanie elementów opartych na indeksie wierszy i kolumn, <xref:System.Windows.Documents.Table> nie. <xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="91b2e-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="91b2e-122"><xref:System.Windows.Controls.Grid> Element umożliwia warstwową zawartość elementu podrzędnego, co pozwala na istnienie więcej niż jednego elementu w jednej komórce.</span><span class="sxs-lookup"><span data-stu-id="91b2e-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="91b2e-123"><xref:System.Windows.Documents.Table>nie obsługuje warstw.</span><span class="sxs-lookup"><span data-stu-id="91b2e-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="91b2e-124">Elementy podrzędne elementu <xref:System.Windows.Controls.Grid> mogą być absolutnie pozycjonowane względem obszaru ich granic "komórki".</span><span class="sxs-lookup"><span data-stu-id="91b2e-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="91b2e-125"><xref:System.Windows.Documents.Table>Program nie obsługuje tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="91b2e-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="91b2e-126">Na koniec jest <xref:System.Windows.Controls.Grid> wymagana mniejsza ilość zasobów <xref:System.Windows.Documents.Table> , dlatego należy rozważyć użycie <xref:System.Windows.Controls.Grid> programu w celu poprawienia wydajności.</span><span class="sxs-lookup"><span data-stu-id="91b2e-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="91b2e-127">Podstawowa struktura tabeli</span><span class="sxs-lookup"><span data-stu-id="91b2e-127">Basic Table Structure</span></span>  
 <span data-ttu-id="91b2e-128"><xref:System.Windows.Documents.Table>zapewnia prezentację opartą na siatce składającą się z kolumn <xref:System.Windows.Documents.TableColumn> (reprezentowane przez elementy) i wierszy <xref:System.Windows.Documents.TableRow> (reprezentowane przez elementy).</span><span class="sxs-lookup"><span data-stu-id="91b2e-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="91b2e-129"><xref:System.Windows.Documents.TableColumn>elementy nie obsługują zawartości; po prostu definiują kolumny i właściwości kolumn.</span><span class="sxs-lookup"><span data-stu-id="91b2e-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="91b2e-130"><xref:System.Windows.Documents.TableRow>elementy muszą być hostowane w <xref:System.Windows.Documents.TableRowGroup> elemencie, który definiuje Grupowanie wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="91b2e-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="91b2e-131"><xref:System.Windows.Documents.TableCell>elementy, które zawierają rzeczywistą zawartość, która ma być prezentowana przez tabelę, muszą być hostowane w <xref:System.Windows.Documents.TableRow> elemencie.</span><span class="sxs-lookup"><span data-stu-id="91b2e-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="91b2e-132"><xref:System.Windows.Documents.TableCell>może zawierać tylko elementy pochodne od <xref:System.Windows.Documents.Block>.</span><span class="sxs-lookup"><span data-stu-id="91b2e-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="91b2e-133">Prawidłowe elementy <xref:System.Windows.Documents.TableCell> podrzędne elementu include.</span><span class="sxs-lookup"><span data-stu-id="91b2e-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <span data-ttu-id="91b2e-134"><xref:System.Windows.Documents.TableCell>elementy nie mogą bezpośrednio hostować zawartości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="91b2e-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="91b2e-135">Aby uzyskać więcej informacji na temat reguł zawierania dla elementów zawartości przepływu <xref:System.Windows.Documents.TableCell>, takich jak, zobacz [Omówienie dokumentu przepływu](flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="91b2e-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91b2e-136"><xref:System.Windows.Documents.Table>jest podobny do <xref:System.Windows.Controls.Grid> elementu, ale ma więcej możliwości i w związku z tym wymaga większego obciążenia zasobów.</span><span class="sxs-lookup"><span data-stu-id="91b2e-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="91b2e-137">W poniższym przykładzie zdefiniowano prostą tabelę 2 x 3 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="91b2e-137">The following example defines a simple 2 x 3 table with [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="91b2e-138">Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="91b2e-138">The following figure shows how this example renders.</span></span>  
  
 ![Zrzut ekranu pokazujący sposób renderowania podstawowej tabeli.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="91b2e-140">Zawieranie tabeli</span><span class="sxs-lookup"><span data-stu-id="91b2e-140">Table Containment</span></span>  
 <span data-ttu-id="91b2e-141"><xref:System.Windows.Documents.Table>pochodzi od <xref:System.Windows.Documents.Block> elementu i stosuje się do wspólnych reguł dla <xref:System.Windows.Documents.Block> elementów poziomu.</span><span class="sxs-lookup"><span data-stu-id="91b2e-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="91b2e-142"><xref:System.Windows.Documents.Table> Element może być zawarty w jednym z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="91b2e-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="91b2e-143">Grupowanie wierszy</span><span class="sxs-lookup"><span data-stu-id="91b2e-143">Row Groupings</span></span>  
 <span data-ttu-id="91b2e-144"><xref:System.Windows.Documents.TableRowGroup> Element umożliwia arbitralne Grupowanie wierszy w tabeli; każdy wiersz w tabeli musi należeć do grupowania wierszy.</span><span class="sxs-lookup"><span data-stu-id="91b2e-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="91b2e-145">Wiersze w grupie wierszy często korzystają ze wspólnego zamiaru i mogą być wzorowane jako Grupa.</span><span class="sxs-lookup"><span data-stu-id="91b2e-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="91b2e-146">Typowym zastosowaniem grupowania wierszy jest oddzielenie wierszy specjalnego przeznaczenia, takich jak tytuł, nagłówek i stopka, z zawartości głównej zawartej w tabeli.</span><span class="sxs-lookup"><span data-stu-id="91b2e-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="91b2e-147">Poniższy przykład używa [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] do definiowania tabeli z stylem nagłówkowym i stopką.</span><span class="sxs-lookup"><span data-stu-id="91b2e-147">The following example uses [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="91b2e-148">Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="91b2e-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="91b2e-149">![Zrzut ekranu Grupy]wierszy tabeli(./media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="91b2e-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="91b2e-150">Pierwszeństwo renderowania w tle</span><span class="sxs-lookup"><span data-stu-id="91b2e-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="91b2e-151">Elementy tabeli są renderowane w następującej kolejności (porządek osi z od najniższego do najwyższego).</span><span class="sxs-lookup"><span data-stu-id="91b2e-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="91b2e-152">Nie można zmienić tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="91b2e-152">This order cannot be changed.</span></span> <span data-ttu-id="91b2e-153">Na przykład nie istnieje właściwość "Z-Order" dla tych elementów, których można użyć do przesłonięcia ustalonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="91b2e-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="91b2e-154">Rozważmy poniższy przykład, który definiuje kolory tła dla każdego z tych elementów w tabeli.</span><span class="sxs-lookup"><span data-stu-id="91b2e-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="91b2e-155">Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu (wyświetlane są tylko kolory tła).</span><span class="sxs-lookup"><span data-stu-id="91b2e-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="91b2e-156">![Zrzut ekranu Tabela z&#45;](./media/table-zorder.png "Table_ZOrder") Order z</span><span class="sxs-lookup"><span data-stu-id="91b2e-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="91b2e-157">Łączenie wierszy lub kolumn</span><span class="sxs-lookup"><span data-stu-id="91b2e-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="91b2e-158">Komórki tabeli można skonfigurować tak, aby obejmowały wiele wierszy lub kolumn przy <xref:System.Windows.Documents.TableCell.RowSpan%2A> użyciu <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> odpowiednio atrybutów lub.</span><span class="sxs-lookup"><span data-stu-id="91b2e-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="91b2e-159">Rozważmy poniższy przykład, w którym komórka obejmuje trzy kolumny.</span><span class="sxs-lookup"><span data-stu-id="91b2e-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="91b2e-160">Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="91b2e-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="91b2e-161">![Zrzut ekranu Komórka obejmująca wszystkie trzy kolumny](./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="91b2e-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="91b2e-162">Kompilowanie tabeli przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="91b2e-162">Building a Table With Code</span></span>  
 <span data-ttu-id="91b2e-163">W poniższych przykładach pokazano, jak programowo utworzyć <xref:System.Windows.Documents.Table> i wypełnić zawartość.</span><span class="sxs-lookup"><span data-stu-id="91b2e-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="91b2e-164">Zawartość tabeli jest przydzielona do pięciu wierszy (reprezentowanych przez <xref:System.Windows.Documents.TableRow> obiekty zawarte <xref:System.Windows.Documents.Table.RowGroups%2A> w obiekcie) i sześciu kolumn (reprezentowanych <xref:System.Windows.Documents.TableColumn> przez obiekty).</span><span class="sxs-lookup"><span data-stu-id="91b2e-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="91b2e-165">Wiersze są używane do różnych celów prezentacji, łącznie z wierszem tytułu, który ma tytuł całej tabeli, wiersz nagłówka opisujący kolumny danych w tabeli oraz wiersz stopki z informacjami podsumowującymi.</span><span class="sxs-lookup"><span data-stu-id="91b2e-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="91b2e-166">Należy zauważyć, że pojęcie wierszy "title", "Header" i "Stopka" nie jest związane z tabelą; są to po prostu wiersze o różnej charakterystyce.</span><span class="sxs-lookup"><span data-stu-id="91b2e-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="91b2e-167">Komórki tabeli zawierają rzeczywistą zawartość, która może składać się z tekstu, obrazów lub niemal dowolnego innego [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="91b2e-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="91b2e-168">Najpierw jest tworzony w celu <xref:System.Windows.Documents.Table>hostowania, a nowy <xref:System.Windows.Documents.Table> jest <xref:System.Windows.Documents.FlowDocument>tworzony i dodawany do zawartości. <xref:System.Windows.Documents.FlowDocument></span><span class="sxs-lookup"><span data-stu-id="91b2e-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="91b2e-169">Następnie do <xref:System.Windows.Documents.Table.Columns%2A> kolekcji <xref:System.Windows.Documents.TableColumn> tabel są tworzone i dodawane sześć obiektów z zastosowaniem formatowania.</span><span class="sxs-lookup"><span data-stu-id="91b2e-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91b2e-170">Należy zauważyć, że <xref:System.Windows.Documents.Table.Columns%2A> kolekcja tabeli używa standardowego indeksowania opartego na zero.</span><span class="sxs-lookup"><span data-stu-id="91b2e-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="91b2e-171">Następnie wiersz tytułu zostanie utworzony i dodany do tabeli z zastosowaniem formatowania.</span><span class="sxs-lookup"><span data-stu-id="91b2e-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="91b2e-172">Wiersz tytułu ma zawierać pojedynczą komórkę obejmującą wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="91b2e-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="91b2e-173">Następnie wiersz nagłówka jest tworzony i dodawany do tabeli, a komórki w wierszu nagłówka są tworzone i wypełniane zawartością.</span><span class="sxs-lookup"><span data-stu-id="91b2e-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="91b2e-174">Następnie wiersz danych jest tworzony i dodawany do tabeli, a komórki w tym wierszu są tworzone i wypełniane zawartością.</span><span class="sxs-lookup"><span data-stu-id="91b2e-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="91b2e-175">Kompilowanie tego wiersza jest podobne do tworzenia wiersza nagłówka z niewielkim innym formatowaniem.</span><span class="sxs-lookup"><span data-stu-id="91b2e-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="91b2e-176">Na koniec wiersz stopki jest tworzony, dodawany i sformatowany.</span><span class="sxs-lookup"><span data-stu-id="91b2e-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="91b2e-177">Podobnie jak w przypadku wiersza tytułu, stopka zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="91b2e-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="91b2e-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91b2e-178">See also</span></span>

- [<span data-ttu-id="91b2e-179">Przegląd dokumentu przepływu</span><span class="sxs-lookup"><span data-stu-id="91b2e-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="91b2e-180">Definiowanie tabeli przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="91b2e-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="91b2e-181">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="91b2e-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="91b2e-182">Używanie elementów zawartości przepływu</span><span class="sxs-lookup"><span data-stu-id="91b2e-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
