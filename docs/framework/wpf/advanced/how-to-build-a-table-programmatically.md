---
title: 'Instrukcje: Programowe tworzenie tabeli'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 315154b37218c0a6845f0a46149fc056780ee650
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172630"
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="a606d-102">Instrukcje: Programowe tworzenie tabeli</span><span class="sxs-lookup"><span data-stu-id="a606d-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="a606d-103">W poniższych przykładach pokazano, jak programowo utworzyć <xref:System.Windows.Documents.Table> i wypełnianie jej zawartości.</span><span class="sxs-lookup"><span data-stu-id="a606d-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="a606d-104">Zawartość tej tabeli są rozdzielone na pięć wierszy (reprezentowane przez <xref:System.Windows.Documents.TableRow> obiektów zawartych w <xref:System.Windows.Documents.Table.RowGroups%2A> obiekt) i 6 kolumn (reprezentowane przez <xref:System.Windows.Documents.TableColumn> obiektów).</span><span class="sxs-lookup"><span data-stu-id="a606d-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="a606d-105">Wiersze są używane do celów innej prezentacji, w tym wiersz tytułu przeznaczone do tytułu całą tabelę, wiersz nagłówka do opisania kolumn danych w tabeli i wiersz stopki z podsumowaniem.</span><span class="sxs-lookup"><span data-stu-id="a606d-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="a606d-106">Należy pamiętać, że pojęcie "title", "header" i "stopka" wierszy nie są wbudowane w tabeli; są to po prostu wiersze o różnej charakterystyce.</span><span class="sxs-lookup"><span data-stu-id="a606d-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="a606d-107">Komórki tabeli zawierają rzeczywistej zawartości może składać się z tekstu, obrazów lub niemal każdy inny [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="a606d-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a606d-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a606d-108">Example</span></span>  
 <span data-ttu-id="a606d-109">Najpierw <xref:System.Windows.Documents.FlowDocument> jest tworzona na hoście <xref:System.Windows.Documents.Table>, nowy <xref:System.Windows.Documents.Table> zostanie utworzony i dodany do zawartości <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="a606d-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="a606d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a606d-110">Example</span></span>  
 <span data-ttu-id="a606d-111">Następnie sześciu <xref:System.Windows.Documents.TableColumn> obiekty są tworzone i dodawane do tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcji z niektórych zastosowanym formatowaniem.</span><span class="sxs-lookup"><span data-stu-id="a606d-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a606d-112">Należy pamiętać, że tabela <xref:System.Windows.Documents.Table.Columns%2A> kolekcja używa standardowych indeksowania zaczynającego się od zera.</span><span class="sxs-lookup"><span data-stu-id="a606d-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="a606d-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a606d-113">Example</span></span>  
 <span data-ttu-id="a606d-114">Następnie wiersz tytułu jest tworzone i dodawane do tabeli za pomocą niektórych zastosowanym formatowaniem.</span><span class="sxs-lookup"><span data-stu-id="a606d-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="a606d-115">Wiersz tytułu odbywa się zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a606d-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="a606d-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="a606d-116">Example</span></span>  
 <span data-ttu-id="a606d-117">Następnie wiersz nagłówka zostanie utworzony i dodany do tabeli i komórki w wierszu nagłówka są tworzone i wypełniane zawartością.</span><span class="sxs-lookup"><span data-stu-id="a606d-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="a606d-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="a606d-118">Example</span></span>  
 <span data-ttu-id="a606d-119">Następnie wiersz danych zostanie utworzony i dodany do tabeli i komórek w tym wierszu są tworzone i wypełniane zawartością.</span><span class="sxs-lookup"><span data-stu-id="a606d-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="a606d-120">Tworzenie tego wiersza jest podobne do tworzenia wiersz nagłówka z zastosowanym formatowaniem nieco inne.</span><span class="sxs-lookup"><span data-stu-id="a606d-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="a606d-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="a606d-121">Example</span></span>  
 <span data-ttu-id="a606d-122">Na koniec wiersza stopki utworzone, dodać i sformatowany.</span><span class="sxs-lookup"><span data-stu-id="a606d-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="a606d-123">Podobnie jak wiersz tytułu stopki zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a606d-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="a606d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a606d-124">See also</span></span>

- [<span data-ttu-id="a606d-125">Przegląd tabeli</span><span class="sxs-lookup"><span data-stu-id="a606d-125">Table Overview</span></span>](table-overview.md)
