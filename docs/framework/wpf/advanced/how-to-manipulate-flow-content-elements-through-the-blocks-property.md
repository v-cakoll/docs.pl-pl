---
title: Jak zarządzać przepływem elementów zawartość za pomocą właściwości bloków
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
ms.openlocfilehash: 74710c4a6dd58cf2836cd7671a3e39401a5ea774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544553"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-blocks-property"></a><span data-ttu-id="88dc2-102">Jak zarządzać przepływem elementów zawartość za pomocą właściwości bloków</span><span class="sxs-lookup"><span data-stu-id="88dc2-102">How to: Manipulate Flow Content Elements through the Blocks Property</span></span>
<span data-ttu-id="88dc2-103">Następujące przykłady przedstawiają niektóre z najczęściej operacje wykonywane na przepływ elementów zawartości przy użyciu **bloków** właściwości.</span><span class="sxs-lookup"><span data-stu-id="88dc2-103">These examples demonstrate some of the more common operations that can be performed on flow content elements through the **Blocks** property.</span></span> <span data-ttu-id="88dc2-104">Ta właściwość jest używana do dodawania i usuwania elementów z <xref:System.Windows.Documents.BlockCollection>.</span><span class="sxs-lookup"><span data-stu-id="88dc2-104">This property is used to add and remove items from <xref:System.Windows.Documents.BlockCollection>.</span></span> <span data-ttu-id="88dc2-105">Przepływ zawartości elementy tej funkcji **bloków** właściwości obejmują:</span><span class="sxs-lookup"><span data-stu-id="88dc2-105">Flow content elements that feature a **Blocks** property include:</span></span>  
  
-   <xref:System.Windows.Documents.Figure>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.ListItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="88dc2-106">Te przykłady stanie się użyć <xref:System.Windows.Documents.Section> jako przepływ elementu zawartości, ale te techniki mają zastosowanie do wszystkich elementów, które hosta przepływu kolekcji elementu zawartości.</span><span class="sxs-lookup"><span data-stu-id="88dc2-106">These examples happen to use <xref:System.Windows.Documents.Section> as the flow content element, but these techniques are applicable to all elements that host a flow content element collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88dc2-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="88dc2-107">Example</span></span>  
 <span data-ttu-id="88dc2-108">Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Section> , a następnie używa **Dodaj** metodę, aby dodać nowy akapit do **sekcji** zawartość.</span><span class="sxs-lookup"><span data-stu-id="88dc2-108">The following example creates a new <xref:System.Windows.Documents.Section> and then uses the **Add** method to add a new Paragraph to the **Section** contents.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## <a name="example"></a><span data-ttu-id="88dc2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="88dc2-109">Example</span></span>  
 <span data-ttu-id="88dc2-110">Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Paragraph> element i wstawia go na początku <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="88dc2-110">The following example creates a new <xref:System.Windows.Documents.Paragraph> element and inserts it at the beginning of the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## <a name="example"></a><span data-ttu-id="88dc2-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="88dc2-111">Example</span></span>  
 <span data-ttu-id="88dc2-112">Poniższy przykład pobiera liczbę najwyższego poziomu <xref:System.Windows.Documents.Block> elementów zawartych w <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="88dc2-112">The following example gets the number of top-level <xref:System.Windows.Documents.Block> elements contained in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## <a name="example"></a><span data-ttu-id="88dc2-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="88dc2-113">Example</span></span>  
 <span data-ttu-id="88dc2-114">Poniższy przykład powoduje usunięcie ostatniego <xref:System.Windows.Documents.Block> element <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="88dc2-114">The following example deletes the last <xref:System.Windows.Documents.Block> element in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## <a name="example"></a><span data-ttu-id="88dc2-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="88dc2-115">Example</span></span>  
 <span data-ttu-id="88dc2-116">Poniższy przykład Czyści całą zawartość (<xref:System.Windows.Documents.Block> elementy) z <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="88dc2-116">The following example clears all of the contents (<xref:System.Windows.Documents.Block> elements) from the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## <a name="see-also"></a><span data-ttu-id="88dc2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88dc2-117">See Also</span></span>  
 <xref:System.Windows.Documents.BlockCollection>  
 <xref:System.Windows.Documents.InlineCollection>  
 <xref:System.Windows.Documents.ListItemCollection>  
 [<span data-ttu-id="88dc2-118">Przegląd dokumentu przepływu</span><span class="sxs-lookup"><span data-stu-id="88dc2-118">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [<span data-ttu-id="88dc2-119">Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="88dc2-119">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="88dc2-120">Zarządzanie kolumnami tabeli za pomocą właściwości Columns</span><span class="sxs-lookup"><span data-stu-id="88dc2-120">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [<span data-ttu-id="88dc2-121">Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="88dc2-121">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
