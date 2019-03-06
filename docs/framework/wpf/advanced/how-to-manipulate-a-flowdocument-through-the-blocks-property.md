---
title: 'Instrukcje: Zarządzaj FlowDocument przez właściwość bloku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], manipulating FlowDocuments through Blocks property [WPF], , '
- ', '
ms.assetid: cbb7291e-3f1b-433e-9e16-f4d93ced14e8
ms.openlocfilehash: c8098df74bb8472648dae2ca04de7a18f062c9e3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365935"
---
# <a name="how-to-manipulate-a-flowdocument-through-the-blocks-property"></a><span data-ttu-id="4b76b-102">Instrukcje: Zarządzaj FlowDocument przez właściwość bloku</span><span class="sxs-lookup"><span data-stu-id="4b76b-102">How to: Manipulate a FlowDocument through the Blocks Property</span></span>
<span data-ttu-id="4b76b-103">Przykłady te pokazują niektóre bardziej typowe operacje, które mogą być wykonywane na <xref:System.Windows.Documents.FlowDocument> za pośrednictwem <xref:System.Windows.Documents.FlowDocument.Blocks%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4b76b-103">These examples demonstrate some of the more common operations that can be performed on a <xref:System.Windows.Documents.FlowDocument> through the <xref:System.Windows.Documents.FlowDocument.Blocks%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b76b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b76b-104">Example</span></span>  
 <span data-ttu-id="4b76b-105">Poniższy przykład tworzy nowy <xref:System.Windows.Documents.FlowDocument> i następnie dołącza nowe <xref:System.Windows.Documents.Paragraph> elementu <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="4b76b-105">The following example creates a new <xref:System.Windows.Documents.FlowDocument> and then appends a new <xref:System.Windows.Documents.Paragraph> element to the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksadd)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksadd)]  
  
## <a name="example"></a><span data-ttu-id="4b76b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b76b-106">Example</span></span>  
 <span data-ttu-id="4b76b-107">Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Paragraph> elementów i wstawia go na początku <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="4b76b-107">The following example creates a new <xref:System.Windows.Documents.Paragraph> element and inserts it at the beginning of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksinsert)]  
  
## <a name="example"></a><span data-ttu-id="4b76b-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b76b-108">Example</span></span>  
 <span data-ttu-id="4b76b-109">Poniższy przykład pobiera liczba najwyższego poziomu <xref:System.Windows.Documents.Block> elementów zawartych w słowniku <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="4b76b-109">The following example gets the number of top-level <xref:System.Windows.Documents.Block> elements contained in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksCount](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblockscount)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblockscount)]  
  
## <a name="example"></a><span data-ttu-id="4b76b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b76b-110">Example</span></span>  
 <span data-ttu-id="4b76b-111">Poniższy przykład usuwa ostatni <xref:System.Windows.Documents.Block> element <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="4b76b-111">The following example deletes the last <xref:System.Windows.Documents.Block> element in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksremovelast)]  
  
## <a name="example"></a><span data-ttu-id="4b76b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b76b-112">Example</span></span>  
 <span data-ttu-id="4b76b-113">Poniższy przykład Czyści całą zawartość (<xref:System.Windows.Documents.Block> elementy) z <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="4b76b-113">The following example clears all of the contents (<xref:System.Windows.Documents.Block> elements) from the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksClear](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksclear)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksclear)]  
  
## <a name="see-also"></a><span data-ttu-id="4b76b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b76b-114">See also</span></span>
- [<span data-ttu-id="4b76b-115">Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="4b76b-115">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="4b76b-116">Zarządzanie kolumnami tabeli za pomocą właściwości Columns</span><span class="sxs-lookup"><span data-stu-id="4b76b-116">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
- [<span data-ttu-id="4b76b-117">Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="4b76b-117">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
