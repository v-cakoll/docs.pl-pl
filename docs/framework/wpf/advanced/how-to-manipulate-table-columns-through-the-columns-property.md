---
title: "Porady: manipulowanie tabeli &#39; s kolumn za pomocą właściwości kolumn"
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
- documents [WPF], manipulating table columns
- properties [WPF], Columns [WPF], manipulating table columns
- tables [WPF], manipulating columns
- Columns property [WPF]
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8264e49b29f5a790e37c97c3683d7bf09e850c3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manipulate-a-table39s-columns-through-the-columns-property"></a><span data-ttu-id="d9e8b-102">Porady: manipulowanie tabeli &#39; s kolumn za pomocą właściwości kolumn</span><span class="sxs-lookup"><span data-stu-id="d9e8b-102">How to: Manipulate a Table&#39;s Columns through the Columns Property</span></span>
<span data-ttu-id="d9e8b-103">W tym przykładzie przedstawiono niektóre z najczęściej operacje wykonywane na kolumnach tabeli do <xref:System.Windows.Documents.Table.Columns%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9e8b-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9e8b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9e8b-104">Example</span></span>  
 <span data-ttu-id="d9e8b-105">Poniższy przykład tworzy nową tabelę, a następnie używa <xref:System.Windows.Documents.TableColumnCollection.Add%2A> metody, aby dodać kolumny do tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d9e8b-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="d9e8b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9e8b-106">Example</span></span>  
 <span data-ttu-id="d9e8b-107">Poniższy przykład Wstawia nowy <xref:System.Windows.Documents.TableColumn>.</span><span class="sxs-lookup"><span data-stu-id="d9e8b-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="d9e8b-108">Nowa kolumna są wstawiane na pozycji indeksu 0, dzięki czemu nowe pierwszej kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9e8b-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9e8b-109"><xref:System.Windows.Documents.TableColumnCollection> Kolekcja używa standardowych indeksowania liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="d9e8b-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="d9e8b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9e8b-110">Example</span></span>  
 <span data-ttu-id="d9e8b-111">Poniższy przykład uzyskuje dostęp do niektórych właściwości dowolnego dla kolumn w <xref:System.Windows.Documents.TableColumnCollection> kolekcji odwołujących się do określonej kolumny według indeksu.</span><span class="sxs-lookup"><span data-stu-id="d9e8b-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="d9e8b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9e8b-112">Example</span></span>  
 <span data-ttu-id="d9e8b-113">Poniższy przykład pobiera liczbę kolumn, które obecnie są obsługiwane przez tabelę.</span><span class="sxs-lookup"><span data-stu-id="d9e8b-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="d9e8b-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9e8b-114">Example</span></span>  
 <span data-ttu-id="d9e8b-115">Poniższy przykład umożliwia usunięcie określonej kolumny przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d9e8b-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="d9e8b-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9e8b-116">Example</span></span>  
 <span data-ttu-id="d9e8b-117">Poniższy przykład umożliwia usunięcie określonej kolumny według indeksu.</span><span class="sxs-lookup"><span data-stu-id="d9e8b-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="d9e8b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9e8b-118">Example</span></span>  
 <span data-ttu-id="d9e8b-119">Poniższy przykład umożliwia usunięcie wszystkich kolumn z tabeli kolumn kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d9e8b-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="d9e8b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9e8b-120">See Also</span></span>  
 [<span data-ttu-id="d9e8b-121">Przegląd tabeli</span><span class="sxs-lookup"><span data-stu-id="d9e8b-121">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [<span data-ttu-id="d9e8b-122">Definiowanie tabeli przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="d9e8b-122">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [<span data-ttu-id="d9e8b-123">Programowe tworzenie tabeli</span><span class="sxs-lookup"><span data-stu-id="d9e8b-123">Build a Table Programmatically</span></span>](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)  
 [<span data-ttu-id="d9e8b-124">Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="d9e8b-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="d9e8b-125">Zarządzanie parametrem FlowDocument przez właściwość Blocks</span><span class="sxs-lookup"><span data-stu-id="d9e8b-125">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="d9e8b-126">Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="d9e8b-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
