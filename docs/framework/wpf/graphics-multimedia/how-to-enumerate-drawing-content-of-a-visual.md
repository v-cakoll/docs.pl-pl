---
title: 'Instrukcje: Wykaż zawartość rysowania Visual'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: a3131b6c86b0f6a7aa79cca305b9c3b2496346f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561951"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="9be28-102">Instrukcje: Wykaż zawartość rysowania Visual</span><span class="sxs-lookup"><span data-stu-id="9be28-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="9be28-103"><xref:System.Windows.Media.Drawing> Obiektu podaje modelu obiektu dla wyliczanie zawartości <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="9be28-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9be28-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9be28-104">Example</span></span>  
 <span data-ttu-id="9be28-105">W poniższym przykładzie użyto <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodę, która pobierze <xref:System.Windows.Media.DrawingGroup> wartość <xref:System.Windows.Media.Visual> i ją wyliczanie.</span><span class="sxs-lookup"><span data-stu-id="9be28-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9be28-106">Gdy wyliczają to zawartość wizualizacji, są pobierane <xref:System.Windows.Media.Drawing> obiektów i nie podstawowej reprezentacji danych renderowania jako lista instrukcji grafiki wektorowej.</span><span class="sxs-lookup"><span data-stu-id="9be28-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="9be28-107">Aby uzyskać więcej informacji, zobacz [Przegląd Renderowanie grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9be28-107">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="9be28-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9be28-108">See also</span></span>
- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="9be28-109">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="9be28-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="9be28-110">Renderowanie grafiki WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="9be28-110">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
