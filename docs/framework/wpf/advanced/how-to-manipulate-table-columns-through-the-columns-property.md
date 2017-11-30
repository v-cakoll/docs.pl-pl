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
ms.openlocfilehash: d0f15339b829335798d7ee21dcc90b81cb536cf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manipulate-a-table39s-columns-through-the-columns-property"></a>Porady: manipulowanie tabeli &#39; s kolumn za pomocą właściwości kolumn
W tym przykładzie przedstawiono niektóre z najczęściej operacje wykonywane na kolumnach tabeli do <xref:System.Windows.Documents.Table.Columns%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nową tabelę, a następnie używa <xref:System.Windows.Documents.TableColumnCollection.Add%2A> metody, aby dodać kolumny do tabeli <xref:System.Windows.Documents.Table.Columns%2A> kolekcji.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład Wstawia nowy <xref:System.Windows.Documents.TableColumn>.  Nowa kolumna są wstawiane na pozycji indeksu 0, dzięki czemu nowe pierwszej kolumny w tabeli.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableColumnCollection> Kolekcja używa standardowych indeksowania liczony od zera.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład uzyskuje dostęp do niektórych właściwości dowolnego dla kolumn w <xref:System.Windows.Documents.TableColumnCollection> kolekcji odwołujących się do określonej kolumny według indeksu.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera liczbę kolumn, które obecnie są obsługiwane przez tabelę.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia usunięcie określonej kolumny przez odwołanie.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia usunięcie określonej kolumny według indeksu.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia usunięcie wszystkich kolumn z tabeli kolumn kolekcji.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd tabeli](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [Zdefiniuj tabelę z XAML](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [Programowe tworzenie tabeli](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)  
 [Manipulowanie grupy wierszy tabeli za pomocą właściwości RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [Manipulowanie FlowDocument za pośrednictwem właściwości bloków](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Manipulowanie grupy wierszy tabeli za pomocą właściwości RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
