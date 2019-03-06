---
title: 'Instrukcje: Zarządzaj przepływem elementów zawartości za pomocą właściwości Inlines'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], manipulating through Inlines property
- documents [WPF], manipulating flow Content elements through Inlines property
- Inlines property [WPF], manipulating flow Content elements
- properties [WPF], Inlines [WPF], manipulating flow Content elements
ms.assetid: 510780d2-3da1-4360-8763-7054bda22ea3
ms.openlocfilehash: 2631d088d677c5edb1ae73a3cb40d15bf4beb71f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361814"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-inlines-property"></a><span data-ttu-id="8c470-102">Instrukcje: Zarządzaj przepływem elementów zawartości za pomocą właściwości Inlines</span><span class="sxs-lookup"><span data-stu-id="8c470-102">How to: Manipulate Flow Content Elements through the Inlines Property</span></span>
<span data-ttu-id="8c470-103">Przykłady te pokazują niektóre bardziej typowe operacje, które mogą być wykonywane na tekście przepływem elementów zawartości (i kontenery takie elementy, takie jak <xref:System.Windows.Controls.TextBlock>) za pośrednictwem **Inlines** właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c470-103">These examples demonstrate some of the more common operations that can be performed on inline flow content elements (and containers of such elements, such as <xref:System.Windows.Controls.TextBlock>) through the **Inlines** property.</span></span> <span data-ttu-id="8c470-104">Ta właściwość jest używana do dodawania i usuwania elementów z <xref:System.Windows.Documents.InlineCollection>.</span><span class="sxs-lookup"><span data-stu-id="8c470-104">This property is used to add and remove items from <xref:System.Windows.Documents.InlineCollection>.</span></span> <span data-ttu-id="8c470-105">Przepływ zawartości elementów tej funkcji **Inlines** właściwości obejmują:</span><span class="sxs-lookup"><span data-stu-id="8c470-105">Flow content elements that feature an **Inlines** property include:</span></span>  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 <span data-ttu-id="8c470-106">Te przykłady się zdarzyć, aby użyć <xref:System.Windows.Documents.Span> co przepływ elementu zawartości, ale techniki te mają zastosowanie do wszystkich elementów lub kontrolki, które hostują <xref:System.Windows.Documents.InlineCollection> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8c470-106">These examples happen to use <xref:System.Windows.Documents.Span> as the flow content element, but these techniques are applicable to all elements or controls that host an <xref:System.Windows.Documents.InlineCollection> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c470-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c470-107">Example</span></span>  
 <span data-ttu-id="8c470-108">Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Span> obiektu, a następnie używa **Dodaj** metody w celu dodania dwóch tekstu działa jako zawartości elementy podrzędne <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="8c470-108">The following example creates a new <xref:System.Windows.Documents.Span> object, and then uses the **Add** method to add two text runs as content children of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## <a name="example"></a><span data-ttu-id="8c470-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c470-109">Example</span></span>  
 <span data-ttu-id="8c470-110">Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Run> elementów i wstawia go na początku <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="8c470-110">The following example creates a new <xref:System.Windows.Documents.Run> element and inserts it at the beginning of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## <a name="example"></a><span data-ttu-id="8c470-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c470-111">Example</span></span>  
 <span data-ttu-id="8c470-112">Poniższy przykład pobiera liczba najwyższego poziomu <xref:System.Windows.Documents.Inline> elementów zawartych w słowniku <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="8c470-112">The following example gets the number of top-level <xref:System.Windows.Documents.Inline> elements contained in the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## <a name="example"></a><span data-ttu-id="8c470-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c470-113">Example</span></span>  
 <span data-ttu-id="8c470-114">Poniższy przykład usuwa ostatni <xref:System.Windows.Documents.Inline> element <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="8c470-114">The following example deletes the last <xref:System.Windows.Documents.Inline> element in the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## <a name="example"></a><span data-ttu-id="8c470-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c470-115">Example</span></span>  
 <span data-ttu-id="8c470-116">Poniższy przykład Czyści całą zawartość (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="8c470-116">The following example clears all of the contents (<xref:System.Windows.Documents.Inline> elements) from the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## <a name="see-also"></a><span data-ttu-id="8c470-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c470-117">See also</span></span>
- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [<span data-ttu-id="8c470-118">Przegląd dokumentu przepływu</span><span class="sxs-lookup"><span data-stu-id="8c470-118">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="8c470-119">Zarządzanie parametrem FlowDocument przez właściwość Blocks</span><span class="sxs-lookup"><span data-stu-id="8c470-119">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="8c470-120">Zarządzanie kolumnami tabeli za pomocą właściwości Columns</span><span class="sxs-lookup"><span data-stu-id="8c470-120">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
- [<span data-ttu-id="8c470-121">Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups</span><span class="sxs-lookup"><span data-stu-id="8c470-121">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
