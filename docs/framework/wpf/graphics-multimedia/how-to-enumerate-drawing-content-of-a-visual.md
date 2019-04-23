---
title: 'Instrukcje: Wyliczanie zawartości rysowania wizualizacji'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 4f0afc1075fe66c7f154fcef3cd883709db55316
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108007"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="8fc48-102">Instrukcje: Wyliczanie zawartości rysowania wizualizacji</span><span class="sxs-lookup"><span data-stu-id="8fc48-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="8fc48-103"><xref:System.Windows.Media.Drawing> Obiektu podaje modelu obiektu dla wyliczanie zawartości <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="8fc48-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fc48-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8fc48-104">Example</span></span>  
 <span data-ttu-id="8fc48-105">W poniższym przykładzie użyto <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodę, która pobierze <xref:System.Windows.Media.DrawingGroup> wartość <xref:System.Windows.Media.Visual> i ją wyliczanie.</span><span class="sxs-lookup"><span data-stu-id="8fc48-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fc48-106">Gdy wyliczają to zawartość wizualizacji, są pobierane <xref:System.Windows.Media.Drawing> obiektów i nie podstawowej reprezentacji danych renderowania jako lista instrukcji grafiki wektorowej.</span><span class="sxs-lookup"><span data-stu-id="8fc48-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="8fc48-107">Aby uzyskać więcej informacji, zobacz [Przegląd Renderowanie grafiki WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8fc48-107">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="8fc48-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fc48-108">See also</span></span>

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="8fc48-109">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="8fc48-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="8fc48-110">Renderowanie grafiki WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="8fc48-110">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
