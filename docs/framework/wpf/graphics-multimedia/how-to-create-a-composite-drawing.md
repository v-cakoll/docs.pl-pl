---
title: 'Instrukcje: Utwórz złożony rysunek'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: 886956b03bd3e17360283cee1bc0e4db1d2a4731
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491418"
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="42d67-102">Instrukcje: Utwórz złożony rysunek</span><span class="sxs-lookup"><span data-stu-id="42d67-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="42d67-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.DrawingGroup> do tworzenia złożonych rysunków, łącząc wiele <xref:System.Windows.Media.Drawing> obiekty w jeden złożony.</span><span class="sxs-lookup"><span data-stu-id="42d67-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42d67-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="42d67-104">Example</span></span>  
 <span data-ttu-id="42d67-105">W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingGroup> do utworzenia złożonego rysunku <xref:System.Windows.Media.GeometryDrawing> i <xref:System.Windows.Media.ImageDrawing> obiektów.</span><span class="sxs-lookup"><span data-stu-id="42d67-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="42d67-106">Poniższa ilustracja przedstawia ten przykład generuje dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="42d67-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="42d67-107">![DrawingGroup przy użyciu wielu rysunków](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="42d67-107">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="42d67-108">Złożony rysunek, która jest tworzona przy użyciu DrawingGroup</span><span class="sxs-lookup"><span data-stu-id="42d67-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="42d67-109">Należy pamiętać, szare obramowanie granice rysunku przedstawiono.</span><span class="sxs-lookup"><span data-stu-id="42d67-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="42d67-110">Możesz użyć <xref:System.Windows.Media.DrawingGroup> do zastosowania <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> ustawienie <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, lub <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> rysunkach zawiera.</span><span class="sxs-lookup"><span data-stu-id="42d67-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="42d67-111">Ponieważ <xref:System.Windows.Media.DrawingGroup> jest również <xref:System.Windows.Media.Drawing>, może zawierać inne <xref:System.Windows.Media.DrawingGroup> obiektów.</span><span class="sxs-lookup"><span data-stu-id="42d67-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="42d67-112">Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że używa dodatkowe <xref:System.Windows.Media.DrawingGroup> obiektów do i stosować w efektów mapy bitowej maski krycia niektóre z jego rysunki.</span><span class="sxs-lookup"><span data-stu-id="42d67-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="42d67-113">Poniższa ilustracja przedstawia ten przykład generuje dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="42d67-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="42d67-114">![DrawingGroup przy użyciu wielu rysunków](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="42d67-114">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="42d67-115">Złożonego rysowania, który ma wiele DrawingGroup — obiekty</span><span class="sxs-lookup"><span data-stu-id="42d67-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="42d67-116">Należy pamiętać, szare obramowanie granice rysunku przedstawiono.</span><span class="sxs-lookup"><span data-stu-id="42d67-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="42d67-117">Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Drawing> obiekty, zobacz [Przegląd obiektów rysowania](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="42d67-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42d67-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42d67-118">See also</span></span>
- <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>
- <xref:System.Windows.Media.DrawingGroup.Transform%2A>
- <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>
- <xref:System.Windows.Media.DrawingGroup.Opacity%2A>
- <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>
- <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>
- [<span data-ttu-id="42d67-119">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="42d67-119">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
