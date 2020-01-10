---
title: Jak przeprowadzić test trafień za pomocą konteneru hosta Win32
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: b71783f2d061c9139de4449d8e0106eb00345894
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740178"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="30732-102">Jak przeprowadzić test trafień za pomocą konteneru hosta Win32</span><span class="sxs-lookup"><span data-stu-id="30732-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="30732-103">Obiekty wizualne można tworzyć w oknie Win32, dostarczając kontener okna hosta dla obiektów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="30732-103">You can create visual objects within a Win32 window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="30732-104">Aby zapewnić obsługę zdarzeń dla zawartych obiektów wizualizacji, przetwarzasz komunikaty przesyłane do pętli filtru komunikatów kontenera okna hosta.</span><span class="sxs-lookup"><span data-stu-id="30732-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="30732-105">Zapoznaj się z [samouczkiem: hosting obiektów wizualnych w aplikacji Win32,](tutorial-hosting-visual-objects-in-a-win32-application.md) Aby uzyskać więcej informacji na temat hostowania obiektów wizualizacji w oknie Win32.</span><span class="sxs-lookup"><span data-stu-id="30732-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a Win32 window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30732-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="30732-106">Example</span></span>  
 <span data-ttu-id="30732-107">Poniższy kod pokazuje, jak skonfigurować programy obsługi zdarzeń myszy dla okna Win32, które jest używane jako kontener hosta dla obiektów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="30732-107">The following code shows how to set up mouse event handlers for a Win32 window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="30732-108">Poniższy przykład pokazuje, jak skonfigurować test trafień w odpowiedzi na zalewkowanie określonych zdarzeń myszy.</span><span class="sxs-lookup"><span data-stu-id="30732-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="30732-109">Obiekt <xref:System.Windows.Interop.HwndSource> prezentuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartość w oknie Win32.</span><span class="sxs-lookup"><span data-stu-id="30732-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a Win32 window.</span></span> <span data-ttu-id="30732-110">Wartość właściwości <xref:System.Windows.Interop.HwndSource.RootVisual%2A> obiektu <xref:System.Windows.Interop.HwndSource> reprezentuje węzeł najwyższego poziomu w hierarchii drzewa wizualnego.</span><span class="sxs-lookup"><span data-stu-id="30732-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="30732-111">Aby zapoznać się z kompletnym przykładem przy testowaniu obiektów przy użyciu kontenera hosta Win32, zobacz [test trafień z funkcją międzyoperacyjności Win32](https://go.microsoft.com/fwlink/?LinkID=159995).</span><span class="sxs-lookup"><span data-stu-id="30732-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30732-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30732-112">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="30732-113">Test trafienia w warstwie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="30732-113">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="30732-114">Samouczek: hosting obiektów wizualnych w aplikacji Win32</span><span class="sxs-lookup"><span data-stu-id="30732-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](tutorial-hosting-visual-objects-in-a-win32-application.md)
