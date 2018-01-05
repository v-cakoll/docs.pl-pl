---
title: "Porady: manipulowanie tabeli &#39; s grupy wierszy za pośrednictwem właściwości RowGroups"
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
- row groups [WPF], manipulating through RowGroups property
- RowGroups property [WPF], manipulating row groups
- documents [WPF], manipulating row groups through RowGroups property
- properties [WPF], RowGroups [WPF], manipulating row groups
ms.assetid: ea61440f-08ae-44ed-b314-5716aaaae3ed
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f084819c3a5c39ea9d94a5741f8fb4a005d6040c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manipulate-a-table39s-row-groups-through-the-rowgroups-property"></a><span data-ttu-id="3fc96-102">Porady: manipulowanie tabeli &#39; s grupy wierszy za pośrednictwem właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="3fc96-102">How to: Manipulate a Table&#39;s Row Groups through the RowGroups Property</span></span>
<span data-ttu-id="3fc96-103">W tym przykładzie przedstawiono niektóre z najczęściej operacje wykonywane na grupy wierszy tabeli za pomocą <xref:System.Windows.Documents.Table.RowGroups%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3fc96-103">This example demonstrates some of the more common operations that can be performed on a table's row groups through the <xref:System.Windows.Documents.Table.RowGroups%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fc96-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fc96-104">Example</span></span>  
 <span data-ttu-id="3fc96-105">Poniższy przykład tworzy nową tabelę, a następnie używa <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> metody, aby dodać kolumny do tabeli <xref:System.Windows.Documents.Table.RowGroups%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3fc96-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.RowGroups%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a><span data-ttu-id="3fc96-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fc96-106">Example</span></span>  
 <span data-ttu-id="3fc96-107">Poniższy przykład Wstawia nowy <xref:System.Windows.Documents.TableRowGroup>.</span><span class="sxs-lookup"><span data-stu-id="3fc96-107">The following example inserts a new <xref:System.Windows.Documents.TableRowGroup>.</span></span>  <span data-ttu-id="3fc96-108">Nowe kolumny zostaną wstawione na pozycji indeksu 0, dzięki czemu nowe pierwszy wiersz w tabeli.</span><span class="sxs-lookup"><span data-stu-id="3fc96-108">The new column is inserted at index position 0, making it the new first row group in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fc96-109"><xref:System.Windows.Documents.TableRowGroupCollection> Kolekcja używa standardowych indeksowania liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="3fc96-109">The <xref:System.Windows.Documents.TableRowGroupCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a><span data-ttu-id="3fc96-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fc96-110">Example</span></span>  
 <span data-ttu-id="3fc96-111">W poniższym przykładzie dodano kilka wierszy do określonego <xref:System.Windows.Documents.TableRowGroup> (określonej przez indeks) w tabeli.</span><span class="sxs-lookup"><span data-stu-id="3fc96-111">The following example adds several rows to a particular <xref:System.Windows.Documents.TableRowGroup> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a><span data-ttu-id="3fc96-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fc96-112">Example</span></span>  
 <span data-ttu-id="3fc96-113">Poniższy przykład uzyskuje dostęp do niektórych właściwości dowolnego wierszy w pierwszej grupy wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="3fc96-113">The following example accesses some arbitrary properties on rows in the first row group in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a><span data-ttu-id="3fc96-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fc96-114">Example</span></span>  
 <span data-ttu-id="3fc96-115">W poniższym przykładzie dodano wielu komórek do określonego <xref:System.Windows.Documents.TableRow> (określonej przez indeks) w tabeli.</span><span class="sxs-lookup"><span data-stu-id="3fc96-115">The following example adds several cells to a particular <xref:System.Windows.Documents.TableRow> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a><span data-ttu-id="3fc96-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fc96-116">Example</span></span>  
 <span data-ttu-id="3fc96-117">Poniższy przykład dostęp do niektórych dowolnego metod i właściwości komórki w pierwszym wierszu w pierwszej grupy wierszy.</span><span class="sxs-lookup"><span data-stu-id="3fc96-117">The following example access some arbitrary methods and properties on cells in the first row in the first row group.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a><span data-ttu-id="3fc96-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fc96-118">Example</span></span>  
 <span data-ttu-id="3fc96-119">Poniższy przykład zwraca liczbę <xref:System.Windows.Documents.TableRowGroup> elementów, obsługiwane przez tabelę.</span><span class="sxs-lookup"><span data-stu-id="3fc96-119">The following example returns the number of <xref:System.Windows.Documents.TableRowGroup> elements hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a><span data-ttu-id="3fc96-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fc96-120">Example</span></span>  
 <span data-ttu-id="3fc96-121">Poniższy przykład umożliwia usunięcie grupy określonego wiersza przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="3fc96-121">The following example removes a particular row group by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a><span data-ttu-id="3fc96-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fc96-122">Example</span></span>  
 <span data-ttu-id="3fc96-123">Poniższy przykład umożliwia usunięcie grupy określonego wiersza przez indeks.</span><span class="sxs-lookup"><span data-stu-id="3fc96-123">The following example removes a particular row group by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a><span data-ttu-id="3fc96-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fc96-124">Example</span></span>  
 <span data-ttu-id="3fc96-125">Poniższy przykład umożliwia usunięcie wszystkich grup wierszy z kolekcji grup wierszy tabeli.</span><span class="sxs-lookup"><span data-stu-id="3fc96-125">The following example removes all row groups from the table's row groups collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="3fc96-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fc96-126">See Also</span></span>  
 [<span data-ttu-id="3fc96-127">Porada: Manipulowanie przepływu elementów zawartości przy użyciu właściwości Inlines</span><span class="sxs-lookup"><span data-stu-id="3fc96-127">How-to: Manipulate Flow Content Elements through the Inlines Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="3fc96-128">Zarządzanie parametrem FlowDocument przez właściwość Blocks</span><span class="sxs-lookup"><span data-stu-id="3fc96-128">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="3fc96-129">Zarządzanie kolumnami tabeli za pomocą właściwości Columns</span><span class="sxs-lookup"><span data-stu-id="3fc96-129">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)
