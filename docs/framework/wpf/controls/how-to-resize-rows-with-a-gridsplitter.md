---
title: "Jak zmienić rozmiar wierszy przy użyciu GridSplitter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d4cf06a86a1da7bb34074623f8f19f4bda7a724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a><span data-ttu-id="c4f69-102">Jak zmienić rozmiar wierszy przy użyciu GridSplitter</span><span class="sxs-lookup"><span data-stu-id="c4f69-102">How to: Resize Rows with a GridSplitter</span></span>
<span data-ttu-id="c4f69-103">Ten przykład przedstawia sposób użycia poziomym <xref:System.Windows.Controls.GridSplitter> ponowne przydzielenie miejsca między wierszami w <xref:System.Windows.Controls.Grid> bez zmieniania wymiary <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="c4f69-103">This example shows how to use a horizontal <xref:System.Windows.Controls.GridSplitter> to redistribute the space between two rows in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4f69-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4f69-104">Example</span></span>  
 <span data-ttu-id="c4f69-105">**Jak utworzyć GridSplitter nakładany na krawędzi wiersza**</span><span class="sxs-lookup"><span data-stu-id="c4f69-105">**How to create a GridSplitter that overlays the edge of a row**</span></span>  
  
 <span data-ttu-id="c4f69-106">Aby określić <xref:System.Windows.Controls.GridSplitter> który zmienia rozmiar wierszy sąsiadujących ze sobą w <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Row%2A> dołączona właściwość do jednego z wierszy, które chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="c4f69-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="c4f69-107">Jeśli Twoje <xref:System.Windows.Controls.Grid> ma więcej niż jedną kolumnę, ustaw <xref:System.Windows.Controls.Grid.ColumnSpan%2A> dołączona właściwość, aby określić liczbę kolumn.</span><span class="sxs-lookup"><span data-stu-id="c4f69-107">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to specify the number of columns.</span></span> <span data-ttu-id="c4f69-108">Następnie ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> do <xref:System.Windows.VerticalAlignment.Top> lub <xref:System.Windows.VerticalAlignment.Bottom> (wyrównanie, które można ustawić zależy od na dwa wiersze, które chcesz zmienić).</span><span class="sxs-lookup"><span data-stu-id="c4f69-108">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Top> or <xref:System.Windows.VerticalAlignment.Bottom> (which alignment you set depends on which two rows you want to resize).</span></span> <span data-ttu-id="c4f69-109">Wreszcie, ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości <xref:System.Windows.HorizontalAlignment.Stretch>.</span><span class="sxs-lookup"><span data-stu-id="c4f69-109">Finally, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>.</span></span>  
  
 <span data-ttu-id="c4f69-110">Poniższy przykład przedstawia sposób definiowania poziomej <xref:System.Windows.Controls.GridSplitter> który zmienia rozmiar wierszy sąsiadujących ze sobą.</span><span class="sxs-lookup"><span data-stu-id="c4f69-110">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 <span data-ttu-id="c4f69-111">A <xref:System.Windows.Controls.GridSplitter> który nie zajmują swój własny wiersz mogą przesłaniać przez inne formanty <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="c4f69-111">A <xref:System.Windows.Controls.GridSplitter> that does not occupy its own row may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="c4f69-112">Aby uzyskać więcej informacji na temat uniknąć tego problemu, zobacz [Sure upewnij, że GridSplitter jest widoczny](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span><span class="sxs-lookup"><span data-stu-id="c4f69-112">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="c4f69-113">**Jak utworzyć GridSplitter, która zajmuje wiersza**</span><span class="sxs-lookup"><span data-stu-id="c4f69-113">**How to create a GridSplitter that occupies a row**</span></span>  
  
 <span data-ttu-id="c4f69-114">Aby określić <xref:System.Windows.Controls.GridSplitter> który zajmuje wiersza w <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Row%2A> dołączona właściwość do jednego z wierszy, które chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="c4f69-114">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a row in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="c4f69-115">Jeśli Twoje <xref:System.Windows.Controls.Grid> ma więcej niż jedną kolumnę, ustaw <xref:System.Windows.Controls.Grid.ColumnSpan%2A> dołączona właściwość do liczby kolumn.</span><span class="sxs-lookup"><span data-stu-id="c4f69-115">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to the number of columns.</span></span> <span data-ttu-id="c4f69-116">Następnie ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> do <xref:System.Windows.VerticalAlignment.Center>ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości <xref:System.Windows.HorizontalAlignment.Stretch>i ustaw <xref:System.Windows.Controls.RowDefinition.Height%2A> wiersza, który zawiera <xref:System.Windows.Controls.GridSplitter> do <xref:System.Windows.GridLength.Auto%2A>.</span><span class="sxs-lookup"><span data-stu-id="c4f69-116">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>, and set the <xref:System.Windows.Controls.RowDefinition.Height%2A> of the row that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="c4f69-117">Poniższy przykład przedstawia sposób definiowania poziomej <xref:System.Windows.Controls.GridSplitter> zajmuje wiersza i zmienia rozmiar wierszy na każdej stronie.</span><span class="sxs-lookup"><span data-stu-id="c4f69-117">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that occupies a row and resizes the rows on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="c4f69-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4f69-118">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="c4f69-119">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c4f69-119">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
