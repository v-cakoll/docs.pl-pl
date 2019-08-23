---
title: 'Instrukcje: Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups'
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
ms.openlocfilehash: 195920af64888bd3671b45befc0fe4cde463ae7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913558"
---
# <a name="how-to-manipulate-a-tables-row-groups-through-the-rowgroups-property"></a><span data-ttu-id="5f6dc-102">Instrukcje: Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="5f6dc-102">How to: Manipulate a Table's Row Groups through the RowGroups Property</span></span>
<span data-ttu-id="5f6dc-103">W tym przykładzie przedstawiono niektóre z bardziej typowych operacji, które mogą być wykonywane w grupach wierszy tabeli za pomocą <xref:System.Windows.Documents.Table.RowGroups%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-103">This example demonstrates some of the more common operations that can be performed on a table's row groups through the <xref:System.Windows.Documents.Table.RowGroups%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f6dc-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6dc-104">Example</span></span>  
 <span data-ttu-id="5f6dc-105">Poniższy przykład tworzy nową tabelę, a następnie używa <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> metody do dodawania kolumn do <xref:System.Windows.Documents.Table.RowGroups%2A> kolekcji tabeli.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.RowGroups%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a><span data-ttu-id="5f6dc-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6dc-106">Example</span></span>  
 <span data-ttu-id="5f6dc-107">Poniższy przykład wstawia nowy <xref:System.Windows.Documents.TableRowGroup>.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-107">The following example inserts a new <xref:System.Windows.Documents.TableRowGroup>.</span></span>  <span data-ttu-id="5f6dc-108">Nowa kolumna zostanie wstawiona przy pozycji indeksu 0, co oznacza, że jest to nowa pierwsza grupa wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-108">The new column is inserted at index position 0, making it the new first row group in the table.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f6dc-109"><xref:System.Windows.Documents.TableRowGroupCollection> Kolekcja używa standardowego indeksowania opartego na zero.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-109">The <xref:System.Windows.Documents.TableRowGroupCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a><span data-ttu-id="5f6dc-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6dc-110">Example</span></span>  
 <span data-ttu-id="5f6dc-111">Poniższy przykład dodaje kilka wierszy do określonego <xref:System.Windows.Documents.TableRowGroup> (określony przez indeks) w tabeli.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-111">The following example adds several rows to a particular <xref:System.Windows.Documents.TableRowGroup> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a><span data-ttu-id="5f6dc-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6dc-112">Example</span></span>  
 <span data-ttu-id="5f6dc-113">Poniższy przykład uzyskuje dostęp do niektórych arbitralnych właściwości wierszy w pierwszej grupie wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-113">The following example accesses some arbitrary properties on rows in the first row group in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a><span data-ttu-id="5f6dc-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6dc-114">Example</span></span>  
 <span data-ttu-id="5f6dc-115">Poniższy przykład dodaje kilka komórek do określonego <xref:System.Windows.Documents.TableRow> (określony przez indeks) w tabeli.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-115">The following example adds several cells to a particular <xref:System.Windows.Documents.TableRow> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a><span data-ttu-id="5f6dc-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6dc-116">Example</span></span>  
 <span data-ttu-id="5f6dc-117">W poniższym przykładzie są dostępne dowolne metody i właściwości w komórkach pierwszego wiersza w pierwszej grupie wierszy.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-117">The following example access some arbitrary methods and properties on cells in the first row in the first row group.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a><span data-ttu-id="5f6dc-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6dc-118">Example</span></span>  
 <span data-ttu-id="5f6dc-119">Poniższy przykład zwraca liczbę <xref:System.Windows.Documents.TableRowGroup> elementów hostowanych przez tabelę.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-119">The following example returns the number of <xref:System.Windows.Documents.TableRowGroup> elements hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a><span data-ttu-id="5f6dc-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6dc-120">Example</span></span>  
 <span data-ttu-id="5f6dc-121">Poniższy przykład usuwa konkretną grupę wierszy według odwołania.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-121">The following example removes a particular row group by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a><span data-ttu-id="5f6dc-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6dc-122">Example</span></span>  
 <span data-ttu-id="5f6dc-123">Poniższy przykład usuwa konkretną grupę wierszy według indeksu.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-123">The following example removes a particular row group by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a><span data-ttu-id="5f6dc-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f6dc-124">Example</span></span>  
 <span data-ttu-id="5f6dc-125">Poniższy przykład usuwa wszystkie grupy wierszy z kolekcji grupy wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-125">The following example removes all row groups from the table's row groups collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="5f6dc-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f6dc-126">See also</span></span>

- [<span data-ttu-id="5f6dc-127">Instrukcje: Manipulowanie przepływem elementów zawartości za pomocą właściwości Inlines</span><span class="sxs-lookup"><span data-stu-id="5f6dc-127">How-to: Manipulate Flow Content Elements through the Inlines Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="5f6dc-128">Zarządzanie parametrem FlowDocument przez właściwość Blocks</span><span class="sxs-lookup"><span data-stu-id="5f6dc-128">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="5f6dc-129">Zarządzanie kolumnami tabeli za pomocą właściwości Columns</span><span class="sxs-lookup"><span data-stu-id="5f6dc-129">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
