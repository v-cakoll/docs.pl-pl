---
title: "Jak zarządzać przepływem elementów zawartość za pomocą właściwości bloków"
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
- documents [WPF], manipulating flow content elements through Blocks property
- flow content elements [WPF], manipulating through Blocks property
- properties [WPF], Blocks [WPF], manipulating flow content elements
- Blocks property [WPF], manipulating flow content elements
ms.assetid: aeda4ece-b979-4818-a093-ef938e908751
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f246b7ab5eae52b745849daf2bedadb7431d7d34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manipulate-flow-content-elements-through-the-blocks-property"></a>Jak zarządzać przepływem elementów zawartość za pomocą właściwości bloków
Następujące przykłady przedstawiają niektóre z najczęściej operacje wykonywane na przepływ elementów zawartości przy użyciu **bloków** właściwości. Ta właściwość jest używana do dodawania i usuwania elementów z <xref:System.Windows.Documents.BlockCollection>. Przepływ zawartości elementy tej funkcji **bloków** właściwości obejmują:  
  
-   <xref:System.Windows.Documents.Figure>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.ListItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
 Te przykłady stanie się użyć <xref:System.Windows.Documents.Section> jako przepływ elementu zawartości, ale te techniki mają zastosowanie do wszystkich elementów, które hosta przepływu kolekcji elementu zawartości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Section> , a następnie używa **Dodaj** metodę, aby dodać nowy akapit do **sekcji** zawartość.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Paragraph> element i wstawia go na początku <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera liczbę najwyższego poziomu <xref:System.Windows.Documents.Block> elementów zawartych w <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje usunięcie ostatniego <xref:System.Windows.Documents.Block> element <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład Czyści całą zawartość (<xref:System.Windows.Documents.Block> elementy) z <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Documents.BlockCollection>  
 <xref:System.Windows.Documents.InlineCollection>  
 <xref:System.Windows.Documents.ListItemCollection>  
 [Przepływ dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Manipulowanie grupy wierszy tabeli za pomocą właściwości RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [Manipulowanie kolumnami tabeli za pomocą właściwości kolumn](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [Manipulowanie grupy wierszy tabeli za pomocą właściwości RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
