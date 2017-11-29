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
ms.openlocfilehash: bb9edf0439c985af015d6badd11c026449a82f57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="table-overview"></a><span data-ttu-id="919cb-102">Przegląd Tabela</span><span class="sxs-lookup"><span data-stu-id="919cb-102">Table Overview</span></span>
<span data-ttu-id="919cb-103"><xref:System.Windows.Documents.Table>jest elementem poziomu bloku, który obsługuje oparte na siatce prezentacji zawartości dokumentu przepływu.</span><span class="sxs-lookup"><span data-stu-id="919cb-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="919cb-104">Elastyczność tego elementu ułatwia bardzo przydatne, ale również umożliwia bardziej skomplikowane zrozumieniu i użytkowaniu poprawnie.</span><span class="sxs-lookup"><span data-stu-id="919cb-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="919cb-105">Ten temat zawiera następujące sekcje.</span><span class="sxs-lookup"><span data-stu-id="919cb-105">This topic contains the following sections.</span></span>  
  
-   [<span data-ttu-id="919cb-106">Podstawowe informacje dotyczące tabeli</span><span class="sxs-lookup"><span data-stu-id="919cb-106">Table Basics</span></span>](#table_basics)  
  
-   [<span data-ttu-id="919cb-107">W jaki sposób innej tabeli, a następnie siatki?</span><span class="sxs-lookup"><span data-stu-id="919cb-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
-   [<span data-ttu-id="919cb-108">Struktura tabeli podstawowej</span><span class="sxs-lookup"><span data-stu-id="919cb-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
-   [<span data-ttu-id="919cb-109">Zawieranie tabeli</span><span class="sxs-lookup"><span data-stu-id="919cb-109">Table Containment</span></span>](#table_containment)  
  
-   [<span data-ttu-id="919cb-110">Grupowań wierszy</span><span class="sxs-lookup"><span data-stu-id="919cb-110">Row Groupings</span></span>](#row_groupings)  
  
-   [<span data-ttu-id="919cb-111">Pierwszeństwo renderowania tła</span><span class="sxs-lookup"><span data-stu-id="919cb-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
-   [<span data-ttu-id="919cb-112">Łączenie węzłów wierszy lub kolumn</span><span class="sxs-lookup"><span data-stu-id="919cb-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
-   [<span data-ttu-id="919cb-113">Tworzenie tabeli z kodem</span><span class="sxs-lookup"><span data-stu-id="919cb-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
-   <span data-ttu-id="919cb-114">[Tematy pokrewne]</span><span class="sxs-lookup"><span data-stu-id="919cb-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="919cb-115">Podstawowe informacje dotyczące tabeli</span><span class="sxs-lookup"><span data-stu-id="919cb-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="919cb-116">W jaki sposób innej tabeli, a następnie siatki?</span><span class="sxs-lookup"><span data-stu-id="919cb-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="919cb-117"><xref:System.Windows.Documents.Table>i <xref:System.Windows.Controls.Grid> udostępnianie niektóre typowe funkcje, ale każda jest najbardziej odpowiednie dla różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="919cb-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="919cb-118">A <xref:System.Windows.Documents.Table> jest przeznaczony do użytku w dowolnej zawartości (zobacz [przepływu dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md) uzyskać więcej informacji o dowolnej zawartości).</span><span class="sxs-lookup"><span data-stu-id="919cb-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](../../../../docs/framework/wpf/advanced/flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="919cb-119">Najlepiej sprawdzają siatki wewnątrz formularzy (zasadniczo dowolnym poza przepływ zawartości).</span><span class="sxs-lookup"><span data-stu-id="919cb-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="919cb-120">W ramach <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> obsługuje przepływ zachowania zawartości, takie jak podział na strony, ze zmianą ułożenia kolumn i wybór zawartości podczas <xref:System.Windows.Controls.Grid> nie.</span><span class="sxs-lookup"><span data-stu-id="919cb-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="919cb-121">A <xref:System.Windows.Controls.Grid> z drugiej strony najlepiej jest używana poza <xref:System.Windows.Documents.FlowDocument> wielu powodów, takich jak <xref:System.Windows.Controls.Grid> dodaje elementy oparte na indeks wierszy i kolumn <xref:System.Windows.Documents.Table> nie.</span><span class="sxs-lookup"><span data-stu-id="919cb-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="919cb-122"><xref:System.Windows.Controls.Grid> Element umożliwia warstwy zawartość elementu podrzędnego, dzięki czemu więcej niż jeden element istnieje w jednym "komórki."</span><span class="sxs-lookup"><span data-stu-id="919cb-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="919cb-123"><xref:System.Windows.Documents.Table>nie obsługuje tworzenie warstw.</span><span class="sxs-lookup"><span data-stu-id="919cb-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="919cb-124">Elementy podrzędne <xref:System.Windows.Controls.Grid> można bezwzględnego względem obszaru ich granice "komórki".</span><span class="sxs-lookup"><span data-stu-id="919cb-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="919cb-125"><xref:System.Windows.Documents.Table>nie obsługuje tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="919cb-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="919cb-126">Na koniec <xref:System.Windows.Controls.Grid> wymaga mniej zasobów, a następnie <xref:System.Windows.Documents.Table> tak, rozważ użycie <xref:System.Windows.Controls.Grid> do zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="919cb-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="919cb-127">Struktura tabeli podstawowej</span><span class="sxs-lookup"><span data-stu-id="919cb-127">Basic Table Structure</span></span>  
 <span data-ttu-id="919cb-128"><xref:System.Windows.Documents.Table>zapewnia oparte na siatce prezentacji składający się z kolumn (reprezentowane przez <xref:System.Windows.Documents.TableColumn> elementy), jak i wiersze (reprezentowane przez <xref:System.Windows.Documents.TableRow> elementów).</span><span class="sxs-lookup"><span data-stu-id="919cb-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="919cb-129"><xref:System.Windows.Documents.TableColumn>elementy nie obsługują zawartość; po prostu definiują, kolumny i właściwości kolumn.</span><span class="sxs-lookup"><span data-stu-id="919cb-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="919cb-130"><xref:System.Windows.Documents.TableRow>elementy muszą być hostowane w <xref:System.Windows.Documents.TableRowGroup> element, który definiuje grupowania wierszy dla tabeli.</span><span class="sxs-lookup"><span data-stu-id="919cb-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="919cb-131"><xref:System.Windows.Documents.TableCell>elementów, które zawierają rzeczywiste zawartości będą widoczne w tabeli, musi być obsługiwana przez <xref:System.Windows.Documents.TableRow> elementu.</span><span class="sxs-lookup"><span data-stu-id="919cb-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="919cb-132"><xref:System.Windows.Documents.TableCell>może zawierać tylko elementy, które pochodzą z <xref:System.Windows.Documents.Block>.</span><span class="sxs-lookup"><span data-stu-id="919cb-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="919cb-133">Elementy podrzędne prawidłowy dla <xref:System.Windows.Documents.TableCell> obejmują.</span><span class="sxs-lookup"><span data-stu-id="919cb-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <span data-ttu-id="919cb-134"><xref:System.Windows.Documents.TableCell>elementy nie mogą bezpośrednio hostem zawartości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="919cb-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="919cb-135">Aby uzyskać więcej informacji o regułach zawierania dla przepływu elementów zawartości, takich jak <xref:System.Windows.Documents.TableCell>, zobacz [przepływu dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="919cb-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](../../../../docs/framework/wpf/advanced/flow-document-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="919cb-136"><xref:System.Windows.Documents.Table>przypomina <xref:System.Windows.Controls.Grid> element a ma więcej możliwości i, w związku z tym wymaga większe obciążenie zasobów.</span><span class="sxs-lookup"><span data-stu-id="919cb-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="919cb-137">W poniższym przykładzie zdefiniowano prostą tabelę 2 x 3 z [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="919cb-137">The following example defines a simple 2 x 3 table with [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="919cb-138">Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="919cb-138">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="919cb-139">![Zrzut ekranu: Renderowanie podstawowej tabeli](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")</span><span class="sxs-lookup"><span data-stu-id="919cb-139">![Screenshot: Render a basic table](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")</span></span>  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="919cb-140">Zawieranie tabeli</span><span class="sxs-lookup"><span data-stu-id="919cb-140">Table Containment</span></span>  
 <span data-ttu-id="919cb-141"><xref:System.Windows.Documents.Table>pochodną <xref:System.Windows.Documents.Block> element i stosuje wspólne zasady dla <xref:System.Windows.Documents.Block> poziomu elementów.</span><span class="sxs-lookup"><span data-stu-id="919cb-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="919cb-142">A <xref:System.Windows.Documents.Table> elementu mogą znajdować się za pomocą dowolnej z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="919cb-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="919cb-143">Grupowań wierszy</span><span class="sxs-lookup"><span data-stu-id="919cb-143">Row Groupings</span></span>  
 <span data-ttu-id="919cb-144"><xref:System.Windows.Documents.TableRowGroup> Element umożliwia arbitralnie grupy wierszy w tabeli; każdego wiersza w tabeli muszą należeć do grupowania wierszy.</span><span class="sxs-lookup"><span data-stu-id="919cb-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="919cb-145">Często wierszy w obrębie grupy wierszy udostępniać typowe opcje i może zostać wstawiony jako grupa.</span><span class="sxs-lookup"><span data-stu-id="919cb-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="919cb-146">Użycia grupowań wierszy ma oddzielić wierszy specjalnych, takich jak tytuł, nagłówku i stopce wierszy, od podstawowego zawartość w tabeli.</span><span class="sxs-lookup"><span data-stu-id="919cb-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="919cb-147">W poniższym przykładzie użyto [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] do definiowania tabeli z styl nagłówków i stopek wierszy.</span><span class="sxs-lookup"><span data-stu-id="919cb-147">The following example uses [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="919cb-148">Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="919cb-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="919cb-149">![Zrzut ekranu: Tabela grupy wierszy](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="919cb-149">![Screenshot: Table row groups](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="919cb-150">Pierwszeństwo renderowania tła</span><span class="sxs-lookup"><span data-stu-id="919cb-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="919cb-151">Renderowanie elementów tabeli w następującej kolejności (porządek osi z najniższą najwyższe).</span><span class="sxs-lookup"><span data-stu-id="919cb-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="919cb-152">Nie można zmienić tego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="919cb-152">This order cannot be changed.</span></span> <span data-ttu-id="919cb-153">Na przykład nie ma właściwości "Porządek osi", dla tych elementów, które służą do przesłonięcia tego zamówienia ustalonych.</span><span class="sxs-lookup"><span data-stu-id="919cb-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="919cb-154">Rozważmy poniższy przykład, który definiuje kolory tła dla każdego z tych elementów w tabeli.</span><span class="sxs-lookup"><span data-stu-id="919cb-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="919cb-155">Na poniższej ilustracji przedstawiono, jak w tym przykładzie powoduje (tylko kolory tła przedstawiający).</span><span class="sxs-lookup"><span data-stu-id="919cb-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="919cb-156">![Zrzut ekranu: Tabela z &#45; kolejność](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="919cb-156">![Screenshot: Table z&#45;order](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="919cb-157">Łączenie węzłów wierszy lub kolumn</span><span class="sxs-lookup"><span data-stu-id="919cb-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="919cb-158">Komórek tabeli może być skonfigurowany tak, aby obejmować wiele wierszy lub kolumn za pomocą <xref:System.Windows.Documents.TableCell.RowSpan%2A> lub <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> atrybuty odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="919cb-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="919cb-159">Rozważmy poniższy przykład, w którym komórki obejmuje trzy kolumny.</span><span class="sxs-lookup"><span data-stu-id="919cb-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="919cb-160">Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="919cb-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="919cb-161">![Zrzut ekranu: Komórka obejmująca wszystkie trzy kolumny](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="919cb-161">![Screenshot: Cell spanning all three columns](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="919cb-162">Tworzenie tabeli z kodem</span><span class="sxs-lookup"><span data-stu-id="919cb-162">Building a Table With Code</span></span>  
 <span data-ttu-id="919cb-163">W poniższych przykładach pokazano, jak utworzyć programowo <xref:System.Windows.Documents.Table> i wypełnianie jej zawartości.</span><span class="sxs-lookup"><span data-stu-id="919cb-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="919cb-164">Zawartość tabeli są rozdzielone do pięciu wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> obiektów zawartych w <xref:System.Windows.Documents.Table.RowGroups%2A> obiektu) i sześć kolumn (reprezentowane przez <xref:System.Windows.Documents.TableColumn> obiektów).</span><span class="sxs-lookup"><span data-stu-id="919cb-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="919cb-165">Wiersze są używane do przedstawienia różnych celów, w tym tytuł wiersz przeznaczony do title całą tabelę, wiersz nagłówka do opisywania kolumn danych w tabeli i wiersz stopki z podsumowaniem.</span><span class="sxs-lookup"><span data-stu-id="919cb-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="919cb-166">Należy pamiętać, że pojęcie "title", "header" i "stopka" wierszy nie są włączone do tabeli; są to po prostu wierszy o różnej charakterystyce.</span><span class="sxs-lookup"><span data-stu-id="919cb-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="919cb-167">Komórki tabeli zawierają rzeczywistej zawartości, może składać się z tekstu, obrazów lub niemal każdy inny [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="919cb-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="919cb-168">Najpierw <xref:System.Windows.Documents.FlowDocument> jest tworzony na hoście <xref:System.Windows.Documents.Table>i nowy <xref:System.Windows.Documents.Table> jest tworzony i dodawany do zawartości <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="919cb-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="919cb-169">Następnie sześciu <xref:System.Windows.Documents.TableColumn> obiekty są tworzone i dodawane do tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcji z niektórych formatowanie zastosowane.</span><span class="sxs-lookup"><span data-stu-id="919cb-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="919cb-170">Należy pamiętać, że tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcja używa standardowych indeksowania liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="919cb-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="919cb-171">Następnie wiersz tytuł jest utworzony i dodane do tabeli z niektórych formatowanie zastosowane.</span><span class="sxs-lookup"><span data-stu-id="919cb-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="919cb-172">Wiersz tytułu odbywa się zawiera jedną komórkę, które obejmuje wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="919cb-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="919cb-173">Następnie wiersz nagłówka jest tworzony i dodawany do tabeli i komórek w wierszu nagłówka są tworzone i wypełniane przy użyciu zawartości.</span><span class="sxs-lookup"><span data-stu-id="919cb-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="919cb-174">Następnie wiersz danych jest tworzony i dodawany do tabeli i komórek w tym wierszu są tworzone i wypełniane przy użyciu zawartości.</span><span class="sxs-lookup"><span data-stu-id="919cb-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="919cb-175">Tworzenie tego wiersza jest podobny do budowania wiersz nagłówka z zastosowanym formatowaniem nieco inne.</span><span class="sxs-lookup"><span data-stu-id="919cb-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="919cb-176">Na koniec wiersza stopki jest utworzony, dodane i sformatowany.</span><span class="sxs-lookup"><span data-stu-id="919cb-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="919cb-177">Podobnie jak wiersz tytuł stopki zawiera jedną komórkę, które obejmuje wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="919cb-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="919cb-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="919cb-178">See Also</span></span>  
 [<span data-ttu-id="919cb-179">Przepływ dokumentami — omówienie</span><span class="sxs-lookup"><span data-stu-id="919cb-179">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [<span data-ttu-id="919cb-180">Zdefiniuj tabelę z XAML</span><span class="sxs-lookup"><span data-stu-id="919cb-180">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [<span data-ttu-id="919cb-181">Dokumentów na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="919cb-181">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="919cb-182">Elementy zawartości przepływu</span><span class="sxs-lookup"><span data-stu-id="919cb-182">Use Flow Content Elements</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)
