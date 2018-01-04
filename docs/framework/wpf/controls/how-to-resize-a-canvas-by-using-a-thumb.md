---
title: "Jak zmienić rozmiar kanwy przy użyciu kciuka"
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
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c73509d58112e47f707e82243005bfdf9edca151
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="721de-102">Jak zmienić rozmiar kanwy przy użyciu kciuka</span><span class="sxs-lookup"><span data-stu-id="721de-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="721de-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.Primitives.Thumb> sterowania, aby zmienić rozmiar <xref:System.Windows.Controls.Canvas> formantu.</span><span class="sxs-lookup"><span data-stu-id="721de-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="721de-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="721de-104">Example</span></span>  
 <span data-ttu-id="721de-105"><xref:System.Windows.Controls.Primitives.Thumb> Formant zawiera funkcję przeciągania, która może służyć do przeniesienia lub zmiany rozmiaru formantów przez monitorowanie <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zdarzenia <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="721de-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="721de-106">Użytkownik rozpoczyna się operacja przeciągania, naciskając klawisz lewego przycisku myszy, gdy wskaźnik myszy jest wstrzymana na <xref:System.Windows.Controls.Primitives.Thumb> formantu.</span><span class="sxs-lookup"><span data-stu-id="721de-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="721de-107">Operacja przeciągania nadal lewy przycisk myszy zostanie kliknięty.</span><span class="sxs-lookup"><span data-stu-id="721de-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="721de-108">Podczas operacji przeciągania <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> może występować więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="721de-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="721de-109">Zawsze wystąpi, <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> klasa udostępnia zmiany w pozycji, która odpowiada zmiany pozycji myszy.</span><span class="sxs-lookup"><span data-stu-id="721de-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="721de-110">Gdy użytkownik zwalnia lewego przycisku myszy, operacja przeciągania została zakończona.</span><span class="sxs-lookup"><span data-stu-id="721de-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="721de-111">Operacja przeciągania zapewnia tylko nowe współrzędne; nie automatycznie zmienić <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="721de-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="721de-112">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb> kontrolować będący elementem podrzędnym <xref:System.Windows.Controls.Canvas> formantu.</span><span class="sxs-lookup"><span data-stu-id="721de-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="721de-113">Program obsługi zdarzeń dla jego <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> zdarzeń zapewnia logiki przenoszenia <xref:System.Windows.Controls.Primitives.Thumb> i zmień rozmiar <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="721de-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="721de-114">Programy obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zdarzeń umożliwia zmianę koloru <xref:System.Windows.Controls.Primitives.Thumb> podczas operacji przeciągania.</span><span class="sxs-lookup"><span data-stu-id="721de-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="721de-115">W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="721de-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="721de-116">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> obsługi zdarzeń, który przenosi <xref:System.Windows.Controls.Primitives.Thumb> i zmienia rozmiar <xref:System.Windows.Controls.Canvas> w odpowiedzi na ruchów myszy.</span><span class="sxs-lookup"><span data-stu-id="721de-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="721de-117">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="721de-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="721de-118">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="721de-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="721de-119">Pełny przykład, zobacz [próbki funkcjonalność przeciągania Thumb](http://go.microsoft.com/fwlink/?LinkID=160042).</span><span class="sxs-lookup"><span data-stu-id="721de-119">For the complete sample, see [Thumb Drag Functionality Sample](http://go.microsoft.com/fwlink/?LinkID=160042).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="721de-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="721de-120">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Thumb>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
