---
title: 'Instrukcje: Zarządzanie przepływem elementów zawartości za pomocą właściwości Blocks'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating flow content elements through Blocks property
- flow content elements [WPF], manipulating through Blocks property
- properties [WPF], Blocks [WPF], manipulating flow content elements
- Blocks property [WPF], manipulating flow content elements
ms.assetid: aeda4ece-b979-4818-a093-ef938e908751
ms.openlocfilehash: e0e1e1333a54946f3bdf474e353de0301eb42447
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150140"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-blocks-property"></a>Instrukcje: Zarządzanie przepływem elementów zawartości za pomocą właściwości Blocks
Przykłady te pokazują niektóre bardziej typowych operacji, które mogą być wykonywane na przepływem elementów zawartości za pomocą **bloki** właściwości. Ta właściwość jest używana do dodawania i usuwania elementów z <xref:System.Windows.Documents.BlockCollection>. Przepływ zawartości elementów tej funkcji **bloki** właściwości obejmują:  
  
-   <xref:System.Windows.Documents.Figure>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.ListItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
 Te przykłady się zdarzyć, aby użyć <xref:System.Windows.Documents.Section> co przepływ elementu zawartości, ale techniki te mają zastosowanie do wszystkich elementów, które hostują kolekcję elementów zawartości przepływu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Section> , a następnie używa **Dodaj** metodę, aby dodać nowy akapit, aby **sekcji** zawartość.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Paragraph> elementów i wstawia go na początku <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera liczba najwyższego poziomu <xref:System.Windows.Documents.Block> elementów zawartych w słowniku <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa ostatni <xref:System.Windows.Documents.Block> element <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład Czyści całą zawartość (<xref:System.Windows.Documents.Block> elementy) z <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [Przegląd dokumentu przepływu](flow-document-overview.md)
- [Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [Zarządzanie kolumnami tabeli za pomocą właściwości Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
