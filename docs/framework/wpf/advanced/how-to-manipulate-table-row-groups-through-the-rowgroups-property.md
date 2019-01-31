---
title: 'Instrukcje: Zarządzaj grupami wierszy tabeli za pomocą właściwości RowGroups'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- row groups [WPF], manipulating through RowGroups property
- RowGroups property [WPF], manipulating row groups
- documents [WPF], manipulating row groups through RowGroups property
- properties [WPF], RowGroups [WPF], manipulating row groups
ms.assetid: ea61440f-08ae-44ed-b314-5716aaaae3ed
ms.openlocfilehash: 6c1e3318afeb8147e96dc3abc5417f2c29509d13
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274901"
---
# <a name="how-to-manipulate-a-tables-row-groups-through-the-rowgroups-property"></a><span data-ttu-id="26ba3-102">Instrukcje: Zarządzaj grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="26ba3-102">How to: Manipulate a Table's Row Groups through the RowGroups Property</span></span>
<span data-ttu-id="26ba3-103">W tym przykładzie przedstawiono niektóre typowe operacje, które mogą być wykonywane na grupami wierszy tabeli za <xref:System.Windows.Documents.Table.RowGroups%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="26ba3-103">This example demonstrates some of the more common operations that can be performed on a table's row groups through the <xref:System.Windows.Documents.Table.RowGroups%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26ba3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="26ba3-104">Example</span></span>  
 <span data-ttu-id="26ba3-105">Poniższy przykład tworzy nową tabelę, a następnie używa <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> metodę, aby dodać kolumny w tabeli <xref:System.Windows.Documents.Table.RowGroups%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="26ba3-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.RowGroups%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a><span data-ttu-id="26ba3-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="26ba3-106">Example</span></span>  
 <span data-ttu-id="26ba3-107">Poniższy przykład Wstawia nowy <xref:System.Windows.Documents.TableRowGroup>.</span><span class="sxs-lookup"><span data-stu-id="26ba3-107">The following example inserts a new <xref:System.Windows.Documents.TableRowGroup>.</span></span>  <span data-ttu-id="26ba3-108">Nowa kolumna zostanie wstawiony na pozycji indeksu 0, dzięki czemu nowe pierwszy wiersz w tabeli.</span><span class="sxs-lookup"><span data-stu-id="26ba3-108">The new column is inserted at index position 0, making it the new first row group in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26ba3-109"><xref:System.Windows.Documents.TableRowGroupCollection> Kolekcja używa standardowych indeksowania zaczynającego się od zera.</span><span class="sxs-lookup"><span data-stu-id="26ba3-109">The <xref:System.Windows.Documents.TableRowGroupCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a><span data-ttu-id="26ba3-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="26ba3-110">Example</span></span>  
 <span data-ttu-id="26ba3-111">Poniższy przykład dodaje kilka wierszy do określonego <xref:System.Windows.Documents.TableRowGroup> (określony przez indeks) w tabeli.</span><span class="sxs-lookup"><span data-stu-id="26ba3-111">The following example adds several rows to a particular <xref:System.Windows.Documents.TableRowGroup> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a><span data-ttu-id="26ba3-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="26ba3-112">Example</span></span>  
 <span data-ttu-id="26ba3-113">Poniższy przykład uzyskuje dostęp do niektórych właściwości dowolnych wierszy w pierwszej grupy wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="26ba3-113">The following example accesses some arbitrary properties on rows in the first row group in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a><span data-ttu-id="26ba3-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="26ba3-114">Example</span></span>  
 <span data-ttu-id="26ba3-115">Poniższy przykład dodaje wielu komórek do określonego <xref:System.Windows.Documents.TableRow> (określony przez indeks) w tabeli.</span><span class="sxs-lookup"><span data-stu-id="26ba3-115">The following example adds several cells to a particular <xref:System.Windows.Documents.TableRow> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a><span data-ttu-id="26ba3-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="26ba3-116">Example</span></span>  
 <span data-ttu-id="26ba3-117">Poniższy przykład dostęp do niektórych dowolnych metod i właściwości na komórki z pierwszego wiersza w pierwszej grupie wierszy.</span><span class="sxs-lookup"><span data-stu-id="26ba3-117">The following example access some arbitrary methods and properties on cells in the first row in the first row group.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a><span data-ttu-id="26ba3-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="26ba3-118">Example</span></span>  
 <span data-ttu-id="26ba3-119">Poniższy przykład zwraca liczbę <xref:System.Windows.Documents.TableRowGroup> elementy pracujących w tabeli.</span><span class="sxs-lookup"><span data-stu-id="26ba3-119">The following example returns the number of <xref:System.Windows.Documents.TableRowGroup> elements hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a><span data-ttu-id="26ba3-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="26ba3-120">Example</span></span>  
 <span data-ttu-id="26ba3-121">Poniższy przykład usuwa grupę określonego wiersza przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="26ba3-121">The following example removes a particular row group by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a><span data-ttu-id="26ba3-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="26ba3-122">Example</span></span>  
 <span data-ttu-id="26ba3-123">Poniższy przykład usuwa grupę określonego wiersza za pomocą indeksu.</span><span class="sxs-lookup"><span data-stu-id="26ba3-123">The following example removes a particular row group by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a><span data-ttu-id="26ba3-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="26ba3-124">Example</span></span>  
 <span data-ttu-id="26ba3-125">Poniższy przykład usuwa wszystkich grup wierszy z kolekcji grup wierszy tabeli.</span><span class="sxs-lookup"><span data-stu-id="26ba3-125">The following example removes all row groups from the table's row groups collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="26ba3-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26ba3-126">See also</span></span>
- [<span data-ttu-id="26ba3-127">Instrukcje: Zarządzaj przepływem elementów zawartości za pomocą właściwości Inlines</span><span class="sxs-lookup"><span data-stu-id="26ba3-127">How-to: Manipulate Flow Content Elements through the Inlines Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="26ba3-128">Zarządzanie parametrem FlowDocument przez właściwość Blocks</span><span class="sxs-lookup"><span data-stu-id="26ba3-128">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="26ba3-129">Zarządzanie kolumnami tabeli za pomocą właściwości Columns</span><span class="sxs-lookup"><span data-stu-id="26ba3-129">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)
