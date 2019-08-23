---
title: 'Instrukcje: Wyliczanie zawartości rysowania wizualizacji'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 25aa0c3706005c1e16cedd7e06914db764545ebb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930070"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="66839-102">Instrukcje: Wyliczanie zawartości rysowania wizualizacji</span><span class="sxs-lookup"><span data-stu-id="66839-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="66839-103">Obiekt udostępnia model obiektów do wyliczania zawartości <xref:System.Windows.Media.Visual>. <xref:System.Windows.Media.Drawing></span><span class="sxs-lookup"><span data-stu-id="66839-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66839-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="66839-104">Example</span></span>  
 <span data-ttu-id="66839-105">W poniższym przykładzie zastosowano <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodę, aby <xref:System.Windows.Media.DrawingGroup> pobrać wartość <xref:System.Windows.Media.Visual> a i wyliczyć ją.</span><span class="sxs-lookup"><span data-stu-id="66839-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66839-106">Gdy wyliczasz zawartość wizualizacji, pobierasz <xref:System.Windows.Media.Drawing> obiekty, a nie źródłowa reprezentacja danych renderowania jako listę instrukcji grafiki wektorowej.</span><span class="sxs-lookup"><span data-stu-id="66839-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="66839-107">Aby uzyskać więcej informacji, zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66839-107">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="66839-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66839-108">See also</span></span>

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="66839-109">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="66839-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="66839-110">Renderowanie grafiki WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="66839-110">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
