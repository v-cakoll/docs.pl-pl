---
title: 'Instrukcje: Zarządzanie kolumnami tabeli za pomocą właściwości Columns'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating table columns
- properties [WPF], Columns [WPF], manipulating table columns
- tables [WPF], manipulating columns
- Columns property [WPF]
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
ms.openlocfilehash: d379d1a98bff614ff9e16cdd340bb69644988743
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078424"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a><span data-ttu-id="1c4c9-102">Instrukcje: Zarządzanie kolumnami tabeli za pomocą właściwości Columns</span><span class="sxs-lookup"><span data-stu-id="1c4c9-102">How to: Manipulate a Table's Columns through the Columns Property</span></span>
<span data-ttu-id="1c4c9-103">W tym przykładzie przedstawiono niektóre typowe operacje, które mogą być wykonywane w kolumnach tabeli za pomocą <xref:System.Windows.Documents.Table.Columns%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1c4c9-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c4c9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c4c9-104">Example</span></span>  
 <span data-ttu-id="1c4c9-105">Poniższy przykład tworzy nową tabelę, a następnie używa <xref:System.Windows.Documents.TableColumnCollection.Add%2A> metodę, aby dodać kolumny w tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1c4c9-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="1c4c9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c4c9-106">Example</span></span>  
 <span data-ttu-id="1c4c9-107">Poniższy przykład Wstawia nowy <xref:System.Windows.Documents.TableColumn>.</span><span class="sxs-lookup"><span data-stu-id="1c4c9-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="1c4c9-108">Nowa kolumna zostanie wstawiony na pozycji indeksu 0, dzięki czemu nowe pierwszej kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="1c4c9-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c4c9-109"><xref:System.Windows.Documents.TableColumnCollection> Kolekcja używa standardowych indeksowania zaczynającego się od zera.</span><span class="sxs-lookup"><span data-stu-id="1c4c9-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="1c4c9-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c4c9-110">Example</span></span>  
 <span data-ttu-id="1c4c9-111">Poniższy przykład uzyskuje dostęp do niektórych właściwości dowolnego dla kolumn w <xref:System.Windows.Documents.TableColumnCollection> kolekcji, odnoszące się do kolumn określonej przez indeks.</span><span class="sxs-lookup"><span data-stu-id="1c4c9-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="1c4c9-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c4c9-112">Example</span></span>  
 <span data-ttu-id="1c4c9-113">Poniższy przykład pobiera liczba kolumn, które obecnie pracujących w tabeli.</span><span class="sxs-lookup"><span data-stu-id="1c4c9-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="1c4c9-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c4c9-114">Example</span></span>  
 <span data-ttu-id="1c4c9-115">Poniższy przykład umożliwia usunięcie określonej kolumny według odwołania.</span><span class="sxs-lookup"><span data-stu-id="1c4c9-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="1c4c9-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c4c9-116">Example</span></span>  
 <span data-ttu-id="1c4c9-117">Poniższy przykład umożliwia usunięcie określonej kolumny według indeksu.</span><span class="sxs-lookup"><span data-stu-id="1c4c9-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="1c4c9-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c4c9-118">Example</span></span>  
 <span data-ttu-id="1c4c9-119">Poniższy przykład usuwa wszystkie kolumny z kolekcji kolumn tabeli.</span><span class="sxs-lookup"><span data-stu-id="1c4c9-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="1c4c9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c4c9-120">See also</span></span>

- [<span data-ttu-id="1c4c9-121">Przegląd Tabela</span><span class="sxs-lookup"><span data-stu-id="1c4c9-121">Table Overview</span></span>](table-overview.md)
- [<span data-ttu-id="1c4c9-122">Definiowanie tabeli przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="1c4c9-122">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="1c4c9-123">Programowe tworzenie tabeli</span><span class="sxs-lookup"><span data-stu-id="1c4c9-123">Build a Table Programmatically</span></span>](how-to-build-a-table-programmatically.md)
- [<span data-ttu-id="1c4c9-124">Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="1c4c9-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="1c4c9-125">Zarządzanie parametrem FlowDocument przez właściwość Blocks</span><span class="sxs-lookup"><span data-stu-id="1c4c9-125">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="1c4c9-126">Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="1c4c9-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
