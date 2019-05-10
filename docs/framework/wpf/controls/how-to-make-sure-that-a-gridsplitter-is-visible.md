---
title: 'Instrukcje: Upewnianie się, że kontrolka GridSplitter jest widoczna'
ms.date: 03/30/2017
helpviewer_keywords:
- GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
ms.openlocfilehash: 2085ac5cec206d8692a1267acf132688f0aa9082
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663318"
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a><span data-ttu-id="d885b-102">Instrukcje: Upewnianie się, że kontrolka GridSplitter jest widoczna</span><span class="sxs-lookup"><span data-stu-id="d885b-102">How to: Make Sure That a GridSplitter Is Visible</span></span>
<span data-ttu-id="d885b-103">W tym przykładzie pokazano, jak upewnić się, że <xref:System.Windows.Controls.GridSplitter> kontrolki nie jest ukryty przez inne formanty w <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="d885b-103">This example shows how to make sure a <xref:System.Windows.Controls.GridSplitter> control is not hidden by the other controls in a <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d885b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d885b-104">Example</span></span>  
 <span data-ttu-id="d885b-105"><xref:System.Windows.Controls.Panel.Children%2A> z <xref:System.Windows.Controls.Grid> kontroli — zostaną zrenderowane w kolejności, że są zdefiniowane w znaczników lub innego kodu.</span><span class="sxs-lookup"><span data-stu-id="d885b-105">The <xref:System.Windows.Controls.Panel.Children%2A> of a <xref:System.Windows.Controls.Grid> control are rendered in the order that they are defined in markup or code.</span></span> <span data-ttu-id="d885b-106"><xref:System.Windows.Controls.GridSplitter> Formanty może być ukryte przez inne formanty, jeżeli nie zdefiniujesz jako ostatnie elementy <xref:System.Windows.Controls.Panel.Children%2A> kolekcji lub jeśli musisz udzielić inne kontrolki wyższe <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span><span class="sxs-lookup"><span data-stu-id="d885b-106"><xref:System.Windows.Controls.GridSplitter> controls can be hidden by other controls if you do not define them as the last elements in the <xref:System.Windows.Controls.Panel.Children%2A> collection or if you give other controls a higher <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span></span>  
  
 <span data-ttu-id="d885b-107">Aby zapobiec ukryte <xref:System.Windows.Controls.GridSplitter> formantów, wykonaj jedną z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="d885b-107">To prevent hidden <xref:System.Windows.Controls.GridSplitter> controls, do one of the following.</span></span>  
  
- <span data-ttu-id="d885b-108">Upewnij się, że <xref:System.Windows.Controls.GridSplitter> formanty są ostatniego <xref:System.Windows.Controls.Panel.Children%2A> dodane do <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="d885b-108">Make sure that <xref:System.Windows.Controls.GridSplitter> controls are the last <xref:System.Windows.Controls.Panel.Children%2A> added to the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="d885b-109">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.GridSplitter> jako po ostatnim elemencie w <xref:System.Windows.Controls.Panel.Children%2A> zbiór <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="d885b-109">The following example shows the <xref:System.Windows.Controls.GridSplitter> as the last element in the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
- <span data-ttu-id="d885b-110">Ustaw <xref:System.Windows.Controls.Panel.ZIndexProperty> na <xref:System.Windows.Controls.GridSplitter> większe niż kontrolki, które w przeciwnym razie spowoduje ukrycie.</span><span class="sxs-lookup"><span data-stu-id="d885b-110">Set the <xref:System.Windows.Controls.Panel.ZIndexProperty> on the <xref:System.Windows.Controls.GridSplitter> to be higher than a control that would otherwise hide it.</span></span> <span data-ttu-id="d885b-111">Poniższy przykład daje <xref:System.Windows.Controls.GridSplitter> kontrolować wyższe <xref:System.Windows.Controls.Panel.ZIndexProperty> niż <xref:System.Windows.Controls.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d885b-111">The following example gives the <xref:System.Windows.Controls.GridSplitter> control a higher <xref:System.Windows.Controls.Panel.ZIndexProperty> than the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
- <span data-ttu-id="d885b-112">Ustaw marginesy kontrolki, które w przeciwnym razie spowoduje ukrycie <xref:System.Windows.Controls.GridSplitter> tak, aby <xref:System.Windows.Controls.GridSplitter> jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="d885b-112">Set margins on the control that would otherwise hide the <xref:System.Windows.Controls.GridSplitter> so that the <xref:System.Windows.Controls.GridSplitter> is exposed.</span></span> <span data-ttu-id="d885b-113">W poniższym przykładzie ustawiono marginesów zaznaczania kontrolki, które w przeciwnym razie mogłyby nakładki i Ukryj <xref:System.Windows.Controls.GridSplitter>.</span><span class="sxs-lookup"><span data-stu-id="d885b-113">The following example sets margins on a control that would otherwise overlay and hide the <xref:System.Windows.Controls.GridSplitter>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a><span data-ttu-id="d885b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d885b-114">See also</span></span>

- <xref:System.Windows.Controls.GridSplitter>
- [<span data-ttu-id="d885b-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="d885b-115">How-to Topics</span></span>](gridsplitter-how-to-topics.md)
