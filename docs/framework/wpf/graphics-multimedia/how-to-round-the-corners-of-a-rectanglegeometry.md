---
title: Jak zaokrąglić rogi RectangleGeometry
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: e4f1d37e2c0f26967affff14ed6475fc8c0cb28c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="3aacc-102">Jak zaokrąglić rogi RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="3aacc-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="3aacc-103">Do zaokrąglania narożników <xref:System.Windows.Media.RectangleGeometry>, ustaw jej <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> właściwości na wartość większą niż zero.</span><span class="sxs-lookup"><span data-stu-id="3aacc-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="3aacc-104">Im większa wartości, bardziej okrągłe prostokąta.</span><span class="sxs-lookup"><span data-stu-id="3aacc-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aacc-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3aacc-105">Example</span></span>  
 <span data-ttu-id="3aacc-106">W poniższym przykładzie pokazano kilka <xref:System.Windows.Media.RectangleGeometry> obiekty o różnych <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> ustawienia.</span><span class="sxs-lookup"><span data-stu-id="3aacc-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="3aacc-107"><xref:System.Windows.Media.RectangleGeometry> Obiekty są wyświetlane przy użyciu <xref:System.Windows.Shapes.Path> elementów.</span><span class="sxs-lookup"><span data-stu-id="3aacc-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="3aacc-108">![Prostokąty o różnych RadiusX&#47;RadiusY ustawienia](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="3aacc-108">![Rectangles with different RadiusX&#47;RadiusY settings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="3aacc-109">Prostokąty z zaokrąglonymi narożnikami</span><span class="sxs-lookup"><span data-stu-id="3aacc-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aacc-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3aacc-110">See Also</span></span>  
 [<span data-ttu-id="3aacc-111">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="3aacc-111">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="3aacc-112">Tworzenie kształtu złożonego</span><span class="sxs-lookup"><span data-stu-id="3aacc-112">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="3aacc-113">Tworzenie kształtu przy użyciu elementu PathGeometry</span><span class="sxs-lookup"><span data-stu-id="3aacc-113">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
