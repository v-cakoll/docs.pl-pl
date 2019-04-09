---
title: 'Instrukcje: Tworzenie złożonego rysunku'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: 0af7fbca593627ebe8cd102a02617a27eac50aa5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132473"
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="cc1f8-102">Instrukcje: Tworzenie złożonego rysunku</span><span class="sxs-lookup"><span data-stu-id="cc1f8-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="cc1f8-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.DrawingGroup> do tworzenia złożonych rysunków, łącząc wiele <xref:System.Windows.Media.Drawing> obiekty w jeden złożony.</span><span class="sxs-lookup"><span data-stu-id="cc1f8-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc1f8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc1f8-104">Example</span></span>  
 <span data-ttu-id="cc1f8-105">W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingGroup> do utworzenia złożonego rysunku <xref:System.Windows.Media.GeometryDrawing> i <xref:System.Windows.Media.ImageDrawing> obiektów.</span><span class="sxs-lookup"><span data-stu-id="cc1f8-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="cc1f8-106">Poniższa ilustracja przedstawia ten przykład generuje dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="cc1f8-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="cc1f8-107">![DrawingGroup przy użyciu wielu rysunków](./media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="cc1f8-107">![A DrawingGroup with multiple drawings](./media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="cc1f8-108">Złożony rysunek, która jest tworzona przy użyciu DrawingGroup</span><span class="sxs-lookup"><span data-stu-id="cc1f8-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="cc1f8-109">Należy pamiętać, szare obramowanie granice rysunku przedstawiono.</span><span class="sxs-lookup"><span data-stu-id="cc1f8-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="cc1f8-110">Możesz użyć <xref:System.Windows.Media.DrawingGroup> do zastosowania <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> ustawienie <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, lub <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> rysunkach zawiera.</span><span class="sxs-lookup"><span data-stu-id="cc1f8-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="cc1f8-111">Ponieważ <xref:System.Windows.Media.DrawingGroup> jest również <xref:System.Windows.Media.Drawing>, może zawierać inne <xref:System.Windows.Media.DrawingGroup> obiektów.</span><span class="sxs-lookup"><span data-stu-id="cc1f8-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="cc1f8-112">Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że używa dodatkowe <xref:System.Windows.Media.DrawingGroup> obiektów do i stosować w efektów mapy bitowej maski krycia niektóre z jego rysunki.</span><span class="sxs-lookup"><span data-stu-id="cc1f8-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="cc1f8-113">Poniższa ilustracja przedstawia ten przykład generuje dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="cc1f8-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="cc1f8-114">![DrawingGroup przy użyciu wielu rysunków](./media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="cc1f8-114">![A DrawingGroup with multiple drawings](./media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="cc1f8-115">Złożonego rysowania, który ma wiele DrawingGroup — obiekty</span><span class="sxs-lookup"><span data-stu-id="cc1f8-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="cc1f8-116">Należy pamiętać, szare obramowanie granice rysunku przedstawiono.</span><span class="sxs-lookup"><span data-stu-id="cc1f8-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="cc1f8-117">Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Drawing> obiekty, zobacz [Przegląd obiektów rysowania](drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cc1f8-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc1f8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc1f8-118">See also</span></span>

- <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>
- <xref:System.Windows.Media.DrawingGroup.Transform%2A>
- <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>
- <xref:System.Windows.Media.DrawingGroup.Opacity%2A>
- <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>
- <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>
- [<span data-ttu-id="cc1f8-119">Przegląd Rysowanie obiektów</span><span class="sxs-lookup"><span data-stu-id="cc1f8-119">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
