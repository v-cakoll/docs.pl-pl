---
title: Jak użyć rysowania jako źródła obrazu
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: 7da8a2a594b0562667aaf417d736159d98818a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a><span data-ttu-id="b82f5-102">Jak użyć rysowania jako źródła obrazu</span><span class="sxs-lookup"><span data-stu-id="b82f5-102">How to: Use a Drawing as an Image Source</span></span>
<span data-ttu-id="b82f5-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Drawing> jako <xref:System.Windows.Controls.Image.Source%2A> dla <xref:System.Windows.Controls.Image> formantu.</span><span class="sxs-lookup"><span data-stu-id="b82f5-103">This example shows how to use a <xref:System.Windows.Media.Drawing> as the <xref:System.Windows.Controls.Image.Source%2A> for an <xref:System.Windows.Controls.Image> control.</span></span> <span data-ttu-id="b82f5-104">Aby wyświetlić <xref:System.Windows.Media.Drawing> z <xref:System.Windows.Controls.Image> kontrolować, użyj <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> formantu <xref:System.Windows.Controls.Image.Source%2A> i ustaw <xref:System.Windows.Media.DrawingImage> obiektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> właściwości do rysunku mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b82f5-104">To display a <xref:System.Windows.Media.Drawing> with an <xref:System.Windows.Controls.Image> control, use a <xref:System.Windows.Media.DrawingImage> as the <xref:System.Windows.Controls.Image> control's <xref:System.Windows.Controls.Image.Source%2A> and set the <xref:System.Windows.Media.DrawingImage> object's <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> property to the drawing you want to display.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b82f5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b82f5-105">Example</span></span>  
 <span data-ttu-id="b82f5-106">W poniższym przykładzie użyto <xref:System.Windows.Media.DrawingImage> i <xref:System.Windows.Controls.Image> formantu, aby wyświetlić <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="b82f5-106">The following example uses a <xref:System.Windows.Media.DrawingImage> and an <xref:System.Windows.Controls.Image> control to display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="b82f5-107">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b82f5-107">This example produces the following output:</span></span>  
  
 <span data-ttu-id="b82f5-108">![GeometryDrawing zawierający dwie elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="b82f5-108">![A GeometryDrawing of two ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
<span data-ttu-id="b82f5-109">DrawingImage</span><span class="sxs-lookup"><span data-stu-id="b82f5-109">A DrawingImage</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b82f5-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b82f5-110">See Also</span></span>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [<span data-ttu-id="b82f5-111">Rysowanie obrazu z użyciem elementu ImageDrawing</span><span class="sxs-lookup"><span data-stu-id="b82f5-111">Draw an Image Using ImageDrawing</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)  
 [<span data-ttu-id="b82f5-112">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="b82f5-112">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="b82f5-113">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="b82f5-113">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="b82f5-114">PresentationOptions:Freeze, atrybut</span><span class="sxs-lookup"><span data-stu-id="b82f5-114">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
