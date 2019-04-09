---
title: 'Instrukcje: Upewnianie się, że kontrolka GridSplitter jest widoczna'
ms.date: 03/30/2017
helpviewer_keywords:
- GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
ms.openlocfilehash: b7543d14ba39d854b5a2c3f4d0d19b9a457ea89b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147150"
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a><span data-ttu-id="7ef09-102">Instrukcje: Upewnianie się, że kontrolka GridSplitter jest widoczna</span><span class="sxs-lookup"><span data-stu-id="7ef09-102">How to: Make Sure That a GridSplitter Is Visible</span></span>
<span data-ttu-id="7ef09-103">W tym przykładzie pokazano, jak upewnić się, że <xref:System.Windows.Controls.GridSplitter> kontrolki nie jest ukryty przez inne formanty w <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="7ef09-103">This example shows how to make sure a <xref:System.Windows.Controls.GridSplitter> control is not hidden by the other controls in a <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ef09-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ef09-104">Example</span></span>  
 <span data-ttu-id="7ef09-105"><xref:System.Windows.Controls.Panel.Children%2A> z <xref:System.Windows.Controls.Grid> kontroli — zostaną zrenderowane w kolejności, że są zdefiniowane w znaczników lub innego kodu.</span><span class="sxs-lookup"><span data-stu-id="7ef09-105">The <xref:System.Windows.Controls.Panel.Children%2A> of a <xref:System.Windows.Controls.Grid> control are rendered in the order that they are defined in markup or code.</span></span> <xref:System.Windows.Controls.GridSplitter> <span data-ttu-id="7ef09-106">Formanty może być ukryte przez inne formanty, jeżeli nie zdefiniujesz jako ostatnie elementy <xref:System.Windows.Controls.Panel.Children%2A> kolekcji lub jeśli musisz udzielić inne kontrolki wyższe <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span><span class="sxs-lookup"><span data-stu-id="7ef09-106">controls can be hidden by other controls if you do not define them as the last elements in the <xref:System.Windows.Controls.Panel.Children%2A> collection or if you give other controls a higher <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span></span>  
  
 <span data-ttu-id="7ef09-107">Aby zapobiec ukryte <xref:System.Windows.Controls.GridSplitter> formantów, wykonaj jedną z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="7ef09-107">To prevent hidden <xref:System.Windows.Controls.GridSplitter> controls, do one of the following.</span></span>  
  
-   <span data-ttu-id="7ef09-108">Upewnij się, że <xref:System.Windows.Controls.GridSplitter> formanty są ostatniego <xref:System.Windows.Controls.Panel.Children%2A> dodane do <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="7ef09-108">Make sure that <xref:System.Windows.Controls.GridSplitter> controls are the last <xref:System.Windows.Controls.Panel.Children%2A> added to the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="7ef09-109">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.GridSplitter> jako po ostatnim elemencie w <xref:System.Windows.Controls.Panel.Children%2A> zbiór <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="7ef09-109">The following example shows the <xref:System.Windows.Controls.GridSplitter> as the last element in the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   <span data-ttu-id="7ef09-110">Ustaw <xref:System.Windows.Controls.Panel.ZIndexProperty> na <xref:System.Windows.Controls.GridSplitter> większe niż kontrolki, które w przeciwnym razie spowoduje ukrycie.</span><span class="sxs-lookup"><span data-stu-id="7ef09-110">Set the <xref:System.Windows.Controls.Panel.ZIndexProperty> on the <xref:System.Windows.Controls.GridSplitter> to be higher than a control that would otherwise hide it.</span></span> <span data-ttu-id="7ef09-111">Poniższy przykład daje <xref:System.Windows.Controls.GridSplitter> kontrolować wyższe <xref:System.Windows.Controls.Panel.ZIndexProperty> niż <xref:System.Windows.Controls.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7ef09-111">The following example gives the <xref:System.Windows.Controls.GridSplitter> control a higher <xref:System.Windows.Controls.Panel.ZIndexProperty> than the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   <span data-ttu-id="7ef09-112">Ustaw marginesy kontrolki, które w przeciwnym razie spowoduje ukrycie <xref:System.Windows.Controls.GridSplitter> tak, aby <xref:System.Windows.Controls.GridSplitter> jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="7ef09-112">Set margins on the control that would otherwise hide the <xref:System.Windows.Controls.GridSplitter> so that the <xref:System.Windows.Controls.GridSplitter> is exposed.</span></span> <span data-ttu-id="7ef09-113">W poniższym przykładzie ustawiono marginesów zaznaczania kontrolki, które w przeciwnym razie mogłyby nakładki i Ukryj <xref:System.Windows.Controls.GridSplitter>.</span><span class="sxs-lookup"><span data-stu-id="7ef09-113">The following example sets margins on a control that would otherwise overlay and hide the <xref:System.Windows.Controls.GridSplitter>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a><span data-ttu-id="7ef09-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ef09-114">See also</span></span>

- <xref:System.Windows.Controls.GridSplitter>
- [<span data-ttu-id="7ef09-115">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="7ef09-115">How-to Topics</span></span>](gridsplitter-how-to-topics.md)
