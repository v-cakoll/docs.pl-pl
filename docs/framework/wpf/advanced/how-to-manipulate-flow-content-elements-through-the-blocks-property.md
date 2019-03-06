---
title: 'Instrukcje: Zarządzaj przepływem elementów zawartości za pomocą właściwości bloków'
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
ms.openlocfilehash: a988f47b6b147b0db285af1928a4260c5deba542
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365857"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-blocks-property"></a><span data-ttu-id="db28c-102">Instrukcje: Zarządzaj przepływem elementów zawartości za pomocą właściwości bloków</span><span class="sxs-lookup"><span data-stu-id="db28c-102">How to: Manipulate Flow Content Elements through the Blocks Property</span></span>
<span data-ttu-id="db28c-103">Przykłady te pokazują niektóre bardziej typowych operacji, które mogą być wykonywane na przepływem elementów zawartości za pomocą **bloki** właściwości.</span><span class="sxs-lookup"><span data-stu-id="db28c-103">These examples demonstrate some of the more common operations that can be performed on flow content elements through the **Blocks** property.</span></span> <span data-ttu-id="db28c-104">Ta właściwość jest używana do dodawania i usuwania elementów z <xref:System.Windows.Documents.BlockCollection>.</span><span class="sxs-lookup"><span data-stu-id="db28c-104">This property is used to add and remove items from <xref:System.Windows.Documents.BlockCollection>.</span></span> <span data-ttu-id="db28c-105">Przepływ zawartości elementów tej funkcji **bloki** właściwości obejmują:</span><span class="sxs-lookup"><span data-stu-id="db28c-105">Flow content elements that feature a **Blocks** property include:</span></span>  
  
-   <xref:System.Windows.Documents.Figure>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.ListItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="db28c-106">Te przykłady się zdarzyć, aby użyć <xref:System.Windows.Documents.Section> co przepływ elementu zawartości, ale techniki te mają zastosowanie do wszystkich elementów, które hostują kolekcję elementów zawartości przepływu.</span><span class="sxs-lookup"><span data-stu-id="db28c-106">These examples happen to use <xref:System.Windows.Documents.Section> as the flow content element, but these techniques are applicable to all elements that host a flow content element collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db28c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="db28c-107">Example</span></span>  
 <span data-ttu-id="db28c-108">Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Section> , a następnie używa **Dodaj** metodę, aby dodać nowy akapit, aby **sekcji** zawartość.</span><span class="sxs-lookup"><span data-stu-id="db28c-108">The following example creates a new <xref:System.Windows.Documents.Section> and then uses the **Add** method to add a new Paragraph to the **Section** contents.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## <a name="example"></a><span data-ttu-id="db28c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="db28c-109">Example</span></span>  
 <span data-ttu-id="db28c-110">Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Paragraph> elementów i wstawia go na początku <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="db28c-110">The following example creates a new <xref:System.Windows.Documents.Paragraph> element and inserts it at the beginning of the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## <a name="example"></a><span data-ttu-id="db28c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="db28c-111">Example</span></span>  
 <span data-ttu-id="db28c-112">Poniższy przykład pobiera liczba najwyższego poziomu <xref:System.Windows.Documents.Block> elementów zawartych w słowniku <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="db28c-112">The following example gets the number of top-level <xref:System.Windows.Documents.Block> elements contained in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## <a name="example"></a><span data-ttu-id="db28c-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="db28c-113">Example</span></span>  
 <span data-ttu-id="db28c-114">Poniższy przykład usuwa ostatni <xref:System.Windows.Documents.Block> element <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="db28c-114">The following example deletes the last <xref:System.Windows.Documents.Block> element in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## <a name="example"></a><span data-ttu-id="db28c-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="db28c-115">Example</span></span>  
 <span data-ttu-id="db28c-116">Poniższy przykład Czyści całą zawartość (<xref:System.Windows.Documents.Block> elementy) z <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="db28c-116">The following example clears all of the contents (<xref:System.Windows.Documents.Block> elements) from the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## <a name="see-also"></a><span data-ttu-id="db28c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db28c-117">See also</span></span>
- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [<span data-ttu-id="db28c-118">Przegląd dokumentu przepływu</span><span class="sxs-lookup"><span data-stu-id="db28c-118">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="db28c-119">Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="db28c-119">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="db28c-120">Zarządzanie kolumnami tabeli za pomocą właściwości Columns</span><span class="sxs-lookup"><span data-stu-id="db28c-120">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
- [<span data-ttu-id="db28c-121">Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="db28c-121">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
