---
title: 'Instrukcje: Przeprowadź test trafień za pomocą konteneru hosta Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: 19526c064efefd80c17fdb4f544b65fcda872bf7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360761"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="02de8-102">Instrukcje: Przeprowadź test trafień za pomocą konteneru hosta Win32</span><span class="sxs-lookup"><span data-stu-id="02de8-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="02de8-103">Można utworzyć obiektów wizualnych w ramach [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okna, zapewniając hosta okna kontener dla obiektów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="02de8-103">You can create visual objects within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="02de8-104">Zapewnienie obsługi dla zawartych obiektów wizualnych zdarzeń można przetwarzać komunikaty przesyłane do kontenera okna hosta pętli komunikatów dla filtru.</span><span class="sxs-lookup"><span data-stu-id="02de8-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="02de8-105">Zapoznaj się [samouczka: Hosting obiektów Visual w aplikacji Win32](tutorial-hosting-visual-objects-in-a-win32-application.md) Aby uzyskać więcej informacji na temat sposobu obsługi obiektów wizualnych w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.</span><span class="sxs-lookup"><span data-stu-id="02de8-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02de8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="02de8-106">Example</span></span>  
 <span data-ttu-id="02de8-107">Poniższy kod przedstawia sposób konfigurowania obsługi zdarzeń myszy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, która jest używana jako kontenera hosta dla obiektów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="02de8-107">The following code shows how to set up mouse event handlers for a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="02de8-108">Poniższy przykład pokazuje, jak skonfigurować hit test w odpowiedzi na generują pułapki zdarzeń myszy określone.</span><span class="sxs-lookup"><span data-stu-id="02de8-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="02de8-109"><xref:System.Windows.Interop.HwndSource> Obiektu przedstawia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartość w ramach [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okna.</span><span class="sxs-lookup"><span data-stu-id="02de8-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window.</span></span> <span data-ttu-id="02de8-110">Wartość <xref:System.Windows.Interop.HwndSource.RootVisual%2A> właściwość <xref:System.Windows.Interop.HwndSource> obiekt reprezentuje węzeł najważniejsze w hierarchii drzewa wizualnego.</span><span class="sxs-lookup"><span data-stu-id="02de8-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="02de8-111">Aby uzyskać pełny przykład testowania trafień obiektów za pomocą konteneru hosta Win32, zobacz [Test trafień Win32 — współdziałanie przykład](https://go.microsoft.com/fwlink/?LinkID=159995).</span><span class="sxs-lookup"><span data-stu-id="02de8-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02de8-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02de8-112">See also</span></span>
- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="02de8-113">Test trafienia w warstwie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="02de8-113">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="02de8-114">Samouczek: Hosting obiektów Visual w aplikacji Win32</span><span class="sxs-lookup"><span data-stu-id="02de8-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](tutorial-hosting-visual-objects-in-a-win32-application.md)
