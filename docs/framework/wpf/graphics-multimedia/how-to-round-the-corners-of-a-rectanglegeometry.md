---
title: "Jak zaokrąglić rogi RectangleGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cd857f7ce886095bcbe92ae57c350ce83bb5c7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="f788d-102">Jak zaokrąglić rogi RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="f788d-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="f788d-103">Do zaokrąglania narożników <xref:System.Windows.Media.RectangleGeometry>, ustaw jej <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> właściwości na wartość większą niż zero.</span><span class="sxs-lookup"><span data-stu-id="f788d-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="f788d-104">Im większa wartości, bardziej okrągłe prostokąta.</span><span class="sxs-lookup"><span data-stu-id="f788d-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f788d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f788d-105">Example</span></span>  
 <span data-ttu-id="f788d-106">W poniższym przykładzie pokazano kilka <xref:System.Windows.Media.RectangleGeometry> obiekty o różnych <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> ustawienia.</span><span class="sxs-lookup"><span data-stu-id="f788d-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="f788d-107"><xref:System.Windows.Media.RectangleGeometry> Obiekty są wyświetlane przy użyciu <xref:System.Windows.Shapes.Path> elementów.</span><span class="sxs-lookup"><span data-stu-id="f788d-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="f788d-108">![Prostokąty o różnych RadiusX &#47; Ustawienia radiusY](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="f788d-108">![Rectangles with different RadiusX&#47;RadiusY settings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="f788d-109">Prostokąty z zaokrąglonymi narożnikami</span><span class="sxs-lookup"><span data-stu-id="f788d-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f788d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f788d-110">See Also</span></span>  
 [<span data-ttu-id="f788d-111">Omówienie geometrii</span><span class="sxs-lookup"><span data-stu-id="f788d-111">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="f788d-112">Tworzenie złożonego kształtu</span><span class="sxs-lookup"><span data-stu-id="f788d-112">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="f788d-113">Tworzenie za pomocą PathGeometry kształtu</span><span class="sxs-lookup"><span data-stu-id="f788d-113">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
