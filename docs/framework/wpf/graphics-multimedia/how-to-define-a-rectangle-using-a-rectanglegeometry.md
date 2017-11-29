---
title: "Jak definiować prostokąt przy użyciu RectangleGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 678d6f36c02c63825782b9f1c860285450a6a9f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>Jak definiować prostokąt przy użyciu RectangleGeometry
W tym przykładzie przedstawiono sposób użycia <xref:System.Windows.Media.RectangleGeometry> klasy do opisywania prostokąta.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia i renderowania <xref:System.Windows.Media.RectangleGeometry>.  Względne położenie i wymiary prostokąta są definiowane przez <xref:System.Windows.Rect> struktury. Względne położenie jest `50,50` i wysokość i szerokość są `25` tworzenie kwadrat. Prostokąt wewnętrznego jest malowany <xref:System.Windows.Media.Brushes.LemonChiffon%2A> pędzla i konturu jej jest malowany <xref:System.Windows.Media.Brushes.Black%2A> grubość pociągnięć `1`.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![Obiekt RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Shapes.Path> element do renderowania <xref:System.Windows.Media.RectangleGeometry>, istnieje wiele sposobów używania <xref:System.Windows.Media.RectangleGeometry> obiektów. Na przykład <xref:System.Windows.Media.RectangleGeometry> może służyć do określenia <xref:System.Windows.UIElement.Clip%2A> z <xref:System.Windows.UIElement> lub <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> z <xref:System.Windows.Media.GeometryDrawing>.  
  
 Inne klasy proste geometrii obejmują <xref:System.Windows.Media.LineGeometry> i <xref:System.Windows.Media.EllipseGeometry>. Te mają geometrię, a także bardziej złożonych z nich, można również tworzyć przy użyciu <xref:System.Windows.Media.PathGeometry> lub <xref:System.Windows.Media.StreamGeometry>.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Tworzenie złożonego kształtu](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Tworzenie za pomocą PathGeometry kształtu](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
