---
title: "Jak zarządzać FlowDocument przez właściwość bloku"
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
- 'documents [WPF], manipulating FlowDocuments through Blocks property [WPF], , '
- ', '
ms.assetid: cbb7291e-3f1b-433e-9e16-f4d93ced14e8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7285d524d102158524301c2e3a9236b187097477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manipulate-a-flowdocument-through-the-blocks-property"></a><span data-ttu-id="dcc68-102">Jak zarządzać FlowDocument przez właściwość bloku</span><span class="sxs-lookup"><span data-stu-id="dcc68-102">How to: Manipulate a FlowDocument through the Blocks Property</span></span>
<span data-ttu-id="dcc68-103">Następujące przykłady przedstawiają niektóre z najczęściej operacje wykonywane na <xref:System.Windows.Documents.FlowDocument> za pośrednictwem <xref:System.Windows.Documents.FlowDocument.Blocks%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcc68-103">These examples demonstrate some of the more common operations that can be performed on a <xref:System.Windows.Documents.FlowDocument> through the <xref:System.Windows.Documents.FlowDocument.Blocks%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcc68-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="dcc68-104">Example</span></span>  
 <span data-ttu-id="dcc68-105">Poniższy przykład tworzy nowy <xref:System.Windows.Documents.FlowDocument> , a następnie dołącza nowy <xref:System.Windows.Documents.Paragraph> elementu <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="dcc68-105">The following example creates a new <xref:System.Windows.Documents.FlowDocument> and then appends a new <xref:System.Windows.Documents.Paragraph> element to the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksadd)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksadd)]  
  
## <a name="example"></a><span data-ttu-id="dcc68-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="dcc68-106">Example</span></span>  
 <span data-ttu-id="dcc68-107">Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Paragraph> element i wstawia go na początku <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="dcc68-107">The following example creates a new <xref:System.Windows.Documents.Paragraph> element and inserts it at the beginning of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksinsert)]  
  
## <a name="example"></a><span data-ttu-id="dcc68-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="dcc68-108">Example</span></span>  
 <span data-ttu-id="dcc68-109">Poniższy przykład pobiera liczbę najwyższego poziomu <xref:System.Windows.Documents.Block> elementów zawartych w <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="dcc68-109">The following example gets the number of top-level <xref:System.Windows.Documents.Block> elements contained in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblockscount)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblockscount)]  
  
## <a name="example"></a><span data-ttu-id="dcc68-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="dcc68-110">Example</span></span>  
 <span data-ttu-id="dcc68-111">Poniższy przykład powoduje usunięcie ostatniego <xref:System.Windows.Documents.Block> element <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="dcc68-111">The following example deletes the last <xref:System.Windows.Documents.Block> element in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksremovelast)]  
  
## <a name="example"></a><span data-ttu-id="dcc68-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="dcc68-112">Example</span></span>  
 <span data-ttu-id="dcc68-113">Poniższy przykład Czyści całą zawartość (<xref:System.Windows.Documents.Block> elementy) z <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="dcc68-113">The following example clears all of the contents (<xref:System.Windows.Documents.Block> elements) from the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksclear)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksclear)]  
  
## <a name="see-also"></a><span data-ttu-id="dcc68-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dcc68-114">See Also</span></span>  
 [<span data-ttu-id="dcc68-115">Manipulowanie grupy wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="dcc68-115">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="dcc68-116">Manipulowanie kolumnami tabeli za pomocą właściwości kolumn</span><span class="sxs-lookup"><span data-stu-id="dcc68-116">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [<span data-ttu-id="dcc68-117">Manipulowanie grupy wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="dcc68-117">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
