---
title: 'Instrukcje: Zmień rozmiar kanwy przy użyciu kciuka'
ms.date: 03/30/2017
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
ms.openlocfilehash: d0873656e71df928ac3bd5a767b5e15d2f2c7836
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591461"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="cbc67-102">Instrukcje: Zmień rozmiar kanwy przy użyciu kciuka</span><span class="sxs-lookup"><span data-stu-id="cbc67-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="cbc67-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.Primitives.Thumb> formantu, aby zmienić rozmiar <xref:System.Windows.Controls.Canvas> kontroli.</span><span class="sxs-lookup"><span data-stu-id="cbc67-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbc67-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbc67-104">Example</span></span>  
 <span data-ttu-id="cbc67-105"><xref:System.Windows.Controls.Primitives.Thumb> Control oferuje funkcje przeciągania, który może służyć do przeniesienia lub zmiany rozmiaru kontrolek poprzez monitorowanie <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zdarzenia <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="cbc67-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="cbc67-106">Użytkownik rozpoczyna się operacja przeciągania, naciskając klawisze lewy przycisk myszy, gdy wskaźnik myszy jest wstrzymana na <xref:System.Windows.Controls.Primitives.Thumb> kontroli.</span><span class="sxs-lookup"><span data-stu-id="cbc67-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="cbc67-107">Operacja przeciągania nadal nie zostanie po naciśnięciu lewego przycisku myszy.</span><span class="sxs-lookup"><span data-stu-id="cbc67-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="cbc67-108">Podczas operacji przeciągania <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> może wystąpić więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="cbc67-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="cbc67-109">Każdorazowo, wystąpi, <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> klasa udostępnia zmianę pozycji, która odnosi się do zmian w miejscu położenia wskaźnika myszy.</span><span class="sxs-lookup"><span data-stu-id="cbc67-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="cbc67-110">Gdy użytkownik zwolni przycisk myszy po lewej stronie, operacja przeciągania została zakończona.</span><span class="sxs-lookup"><span data-stu-id="cbc67-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="cbc67-111">Operacja przeciągania zapewnia tylko nowe współrzędne; go nie zmieniaj położenia automatycznie <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="cbc67-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="cbc67-112">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb> kontrolować czyli element podrzędny elementu <xref:System.Windows.Controls.Canvas> kontroli.</span><span class="sxs-lookup"><span data-stu-id="cbc67-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="cbc67-113">Program obsługi zdarzeń dla jego <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> zdarzenia udostępnia logikę, aby przenieść <xref:System.Windows.Controls.Primitives.Thumb> i zmienianie rozmiaru <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="cbc67-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="cbc67-114">Programy obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zdarzenia Zmień kolor <xref:System.Windows.Controls.Primitives.Thumb> podczas operacji przeciągania.</span><span class="sxs-lookup"><span data-stu-id="cbc67-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="cbc67-115">W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="cbc67-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="cbc67-116">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> programu obsługi zdarzeń, który przenosi <xref:System.Windows.Controls.Primitives.Thumb> i zmienia rozmiar <xref:System.Windows.Controls.Canvas> w odpowiedzi na ruchów myszy.</span><span class="sxs-lookup"><span data-stu-id="cbc67-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="cbc67-117">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cbc67-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="cbc67-118">W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cbc67-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="cbc67-119">Aby uzyskać pełny przykład, zobacz [Przykładowe funkcje przeciągania Thumb](https://go.microsoft.com/fwlink/?LinkID=160042).</span><span class="sxs-lookup"><span data-stu-id="cbc67-119">For the complete sample, see [Thumb Drag Functionality Sample](https://go.microsoft.com/fwlink/?LinkID=160042).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc67-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbc67-120">See also</span></span>
- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
