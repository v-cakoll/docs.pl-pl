---
title: Jak upewnić się, że GridSplitter jest widoczny
ms.date: 03/30/2017
helpviewer_keywords:
- GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
ms.openlocfilehash: 926df118bfd8e7ab3d1f0c953d0b6debafd59073
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a><span data-ttu-id="e7aa9-102">Jak upewnić się, że GridSplitter jest widoczny</span><span class="sxs-lookup"><span data-stu-id="e7aa9-102">How to: Make Sure That a GridSplitter Is Visible</span></span>
<span data-ttu-id="e7aa9-103">W tym przykładzie pokazano, jak upewnij się, że <xref:System.Windows.Controls.GridSplitter> formantu nie jest ukryty przez inne formanty w <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="e7aa9-103">This example shows how to make sure a <xref:System.Windows.Controls.GridSplitter> control is not hidden by the other controls in a <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7aa9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7aa9-104">Example</span></span>  
 <span data-ttu-id="e7aa9-105"><xref:System.Windows.Controls.Panel.Children%2A> z <xref:System.Windows.Controls.Grid> formantu są renderowane w kolejności, że są one zdefiniowane w znaczników lub kodu.</span><span class="sxs-lookup"><span data-stu-id="e7aa9-105">The <xref:System.Windows.Controls.Panel.Children%2A> of a <xref:System.Windows.Controls.Grid> control are rendered in the order that they are defined in markup or code.</span></span> <span data-ttu-id="e7aa9-106"><xref:System.Windows.Controls.GridSplitter> Formanty można ukryć przez inne formanty, jeśli nie definiują jako ostatni elementów w <xref:System.Windows.Controls.Panel.Children%2A> kolekcji lub jeśli musisz podać inne formanty wyższej <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span><span class="sxs-lookup"><span data-stu-id="e7aa9-106"><xref:System.Windows.Controls.GridSplitter> controls can be hidden by other controls if you do not define them as the last elements in the <xref:System.Windows.Controls.Panel.Children%2A> collection or if you give other controls a higher <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span></span>  
  
 <span data-ttu-id="e7aa9-107">Aby zapobiec ukryte <xref:System.Windows.Controls.GridSplitter> formantów, wykonaj jedną z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="e7aa9-107">To prevent hidden <xref:System.Windows.Controls.GridSplitter> controls, do one of the following.</span></span>  
  
-   <span data-ttu-id="e7aa9-108">Upewnij się, że <xref:System.Windows.Controls.GridSplitter> kontrolki są ostatniego <xref:System.Windows.Controls.Panel.Children%2A> dodane do <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="e7aa9-108">Make sure that <xref:System.Windows.Controls.GridSplitter> controls are the last <xref:System.Windows.Controls.Panel.Children%2A> added to the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="e7aa9-109">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.GridSplitter> jako ostatni element <xref:System.Windows.Controls.Panel.Children%2A> kolekcji <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="e7aa9-109">The following example shows the <xref:System.Windows.Controls.GridSplitter> as the last element in the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   <span data-ttu-id="e7aa9-110">Ustaw <xref:System.Windows.Controls.Panel.ZIndexProperty> na <xref:System.Windows.Controls.GridSplitter> wyższe niż kontroli, które w przeciwnym razie spowoduje ukrycie.</span><span class="sxs-lookup"><span data-stu-id="e7aa9-110">Set the <xref:System.Windows.Controls.Panel.ZIndexProperty> on the <xref:System.Windows.Controls.GridSplitter> to be higher than a control that would otherwise hide it.</span></span> <span data-ttu-id="e7aa9-111">Poniższy przykład zawiera <xref:System.Windows.Controls.GridSplitter> kontrolować wyższej <xref:System.Windows.Controls.Panel.ZIndexProperty> niż <xref:System.Windows.Controls.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="e7aa9-111">The following example gives the <xref:System.Windows.Controls.GridSplitter> control a higher <xref:System.Windows.Controls.Panel.ZIndexProperty> than the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   <span data-ttu-id="e7aa9-112">Ustaw marginesy w formancie, które w przeciwnym razie spowoduje ukrycie <xref:System.Windows.Controls.GridSplitter> , aby <xref:System.Windows.Controls.GridSplitter> jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="e7aa9-112">Set margins on the control that would otherwise hide the <xref:System.Windows.Controls.GridSplitter> so that the <xref:System.Windows.Controls.GridSplitter> is exposed.</span></span> <span data-ttu-id="e7aa9-113">Poniższy przykład przedstawia marginesy na formant, który będzie w przeciwnym razie nakładki i Ukryj <xref:System.Windows.Controls.GridSplitter>.</span><span class="sxs-lookup"><span data-stu-id="e7aa9-113">The following example sets margins on a control that would otherwise overlay and hide the <xref:System.Windows.Controls.GridSplitter>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a><span data-ttu-id="e7aa9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7aa9-114">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="e7aa9-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="e7aa9-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
