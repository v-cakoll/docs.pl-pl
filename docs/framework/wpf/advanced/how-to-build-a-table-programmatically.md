---
title: 'Instrukcje: Programowe tworzenie tabeli'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 9c9061d3c4d6b3de5e1ab42a6b98c20813835ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964158"
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="1d288-102">Instrukcje: Programowe tworzenie tabeli</span><span class="sxs-lookup"><span data-stu-id="1d288-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="1d288-103">W poniższych przykładach pokazano, jak programowo utworzyć <xref:System.Windows.Documents.Table> i wypełnić zawartość.</span><span class="sxs-lookup"><span data-stu-id="1d288-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="1d288-104">Zawartość tabeli jest przydzielona do pięciu wierszy (reprezentowanych przez <xref:System.Windows.Documents.TableRow> obiekty zawarte <xref:System.Windows.Documents.Table.RowGroups%2A> w obiekcie) i sześciu kolumn (reprezentowanych <xref:System.Windows.Documents.TableColumn> przez obiekty).</span><span class="sxs-lookup"><span data-stu-id="1d288-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="1d288-105">Wiersze są używane do różnych celów prezentacji, łącznie z wierszem tytułu, który ma tytuł całej tabeli, wiersz nagłówka opisujący kolumny danych w tabeli oraz wiersz stopki z informacjami podsumowującymi.</span><span class="sxs-lookup"><span data-stu-id="1d288-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="1d288-106">Należy zauważyć, że pojęcie wierszy "title", "Header" i "Stopka" nie jest związane z tabelą; są to po prostu wiersze o różnej charakterystyce.</span><span class="sxs-lookup"><span data-stu-id="1d288-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="1d288-107">Komórki tabeli zawierają rzeczywistą zawartość, która może składać się z tekstu, obrazów lub niemal dowolnego innego [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="1d288-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d288-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d288-108">Example</span></span>  
 <span data-ttu-id="1d288-109">Najpierw jest tworzony w celu <xref:System.Windows.Documents.Table>hostowania, a nowy <xref:System.Windows.Documents.Table> jest <xref:System.Windows.Documents.FlowDocument>tworzony i dodawany do zawartości. <xref:System.Windows.Documents.FlowDocument></span><span class="sxs-lookup"><span data-stu-id="1d288-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="1d288-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d288-110">Example</span></span>  
 <span data-ttu-id="1d288-111">Następnie do <xref:System.Windows.Documents.Table.Columns%2A> kolekcji <xref:System.Windows.Documents.TableColumn> tabel są tworzone i dodawane sześć obiektów z zastosowaniem formatowania.</span><span class="sxs-lookup"><span data-stu-id="1d288-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d288-112">Należy zauważyć, że <xref:System.Windows.Documents.Table.Columns%2A> kolekcja tabeli używa standardowego indeksowania opartego na zero.</span><span class="sxs-lookup"><span data-stu-id="1d288-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="1d288-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d288-113">Example</span></span>  
 <span data-ttu-id="1d288-114">Następnie wiersz tytułu zostanie utworzony i dodany do tabeli z zastosowaniem formatowania.</span><span class="sxs-lookup"><span data-stu-id="1d288-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="1d288-115">Wiersz tytułu ma zawierać pojedynczą komórkę obejmującą wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="1d288-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="1d288-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d288-116">Example</span></span>  
 <span data-ttu-id="1d288-117">Następnie wiersz nagłówka jest tworzony i dodawany do tabeli, a komórki w wierszu nagłówka są tworzone i wypełniane zawartością.</span><span class="sxs-lookup"><span data-stu-id="1d288-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="1d288-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d288-118">Example</span></span>  
 <span data-ttu-id="1d288-119">Następnie wiersz danych jest tworzony i dodawany do tabeli, a komórki w tym wierszu są tworzone i wypełniane zawartością.</span><span class="sxs-lookup"><span data-stu-id="1d288-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="1d288-120">Kompilowanie tego wiersza jest podobne do tworzenia wiersza nagłówka z niewielkim innym formatowaniem.</span><span class="sxs-lookup"><span data-stu-id="1d288-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="1d288-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d288-121">Example</span></span>  
 <span data-ttu-id="1d288-122">Na koniec wiersz stopki jest tworzony, dodawany i sformatowany.</span><span class="sxs-lookup"><span data-stu-id="1d288-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="1d288-123">Podobnie jak w przypadku wiersza tytułu, stopka zawiera jedną komórkę, która obejmuje wszystkie sześć kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="1d288-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="1d288-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d288-124">See also</span></span>

- [<span data-ttu-id="1d288-125">Przegląd tabeli</span><span class="sxs-lookup"><span data-stu-id="1d288-125">Table Overview</span></span>](table-overview.md)
