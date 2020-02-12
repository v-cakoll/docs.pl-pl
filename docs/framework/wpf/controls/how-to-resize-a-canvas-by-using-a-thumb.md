---
title: Jak zmienić rozmiar kanwy przy użyciu kciuka
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
ms.openlocfilehash: 84f5ac2b53124b7f4d7c15741e94b40e7ee81526
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124302"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="f7067-102">Jak zmienić rozmiar kanwy przy użyciu kciuka</span><span class="sxs-lookup"><span data-stu-id="f7067-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="f7067-103">W tym przykładzie pokazano, jak za pomocą kontrolki <xref:System.Windows.Controls.Primitives.Thumb> zmienić rozmiar kontrolki <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="f7067-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7067-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7067-104">Example</span></span>  
 <span data-ttu-id="f7067-105">Formant <xref:System.Windows.Controls.Primitives.Thumb> zapewnia funkcję przeciągania, która może służyć do przenoszenia lub zmieniania rozmiaru formantów przez monitorowanie <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zdarzeń <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="f7067-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="f7067-106">Użytkownik rozpoczyna operację przeciągania, naciskając lewy przycisk myszy, gdy wskaźnik myszy jest wstrzymany w kontrolce <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="f7067-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="f7067-107">Operacja przeciągania jest kontynuowana, o ile lewy przycisk myszy pozostanie wciśnięty.</span><span class="sxs-lookup"><span data-stu-id="f7067-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="f7067-108">Podczas operacji przeciągania <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> może wystąpić więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="f7067-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="f7067-109">Za każdym razem, gdy występuje, Klasa <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> zapewnia zmianę położenia, która odnosi się do zmiany położenia wskaźnika myszy.</span><span class="sxs-lookup"><span data-stu-id="f7067-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="f7067-110">Gdy użytkownik zwolni lewy przycisk myszy, operacja przeciągania zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="f7067-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="f7067-111">Operacja przeciągania zawiera tylko nowe współrzędne; nie powoduje automatycznego zmiany położenia <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="f7067-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="f7067-112">W poniższym przykładzie pokazano formant <xref:System.Windows.Controls.Primitives.Thumb>, który jest elementem podrzędnym kontrolki <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="f7067-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="f7067-113">Program obsługi zdarzeń dla jego zdarzenia <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> udostępnia logikę do przeniesienia <xref:System.Windows.Controls.Primitives.Thumb> i zmiany rozmiaru <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="f7067-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="f7067-114">Procedury obsługi zdarzeń <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zmieniają kolor <xref:System.Windows.Controls.Primitives.Thumb> podczas operacji przeciągania.</span><span class="sxs-lookup"><span data-stu-id="f7067-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="f7067-115">W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="f7067-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="f7067-116">Poniższy przykład pokazuje procedurę obsługi zdarzeń <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>, która przenosi <xref:System.Windows.Controls.Primitives.Thumb> i zmienia rozmiar <xref:System.Windows.Controls.Canvas> w odpowiedzi na ruch myszy.</span><span class="sxs-lookup"><span data-stu-id="f7067-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="f7067-117">Poniższy przykład pokazuje procedurę obsługi zdarzeń <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>.</span><span class="sxs-lookup"><span data-stu-id="f7067-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="f7067-118">Poniższy przykład pokazuje procedurę obsługi zdarzeń <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>.</span><span class="sxs-lookup"><span data-stu-id="f7067-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="f7067-119">Pełny przykład można znaleźć w sekcji [Przykładowa funkcja przeciągania](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).</span><span class="sxs-lookup"><span data-stu-id="f7067-119">For the complete sample, see [Thumb Drag Functionality Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7067-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7067-120">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
