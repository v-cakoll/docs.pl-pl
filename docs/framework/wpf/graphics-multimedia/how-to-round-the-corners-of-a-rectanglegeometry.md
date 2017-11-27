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
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a>Jak zaokrąglić rogi RectangleGeometry
Do zaokrąglania narożników <xref:System.Windows.Media.RectangleGeometry>, ustaw jej <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> właściwości na wartość większą niż zero. Im większa wartości, bardziej okrągłe prostokąta.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano kilka <xref:System.Windows.Media.RectangleGeometry> obiekty o różnych <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> ustawienia. <xref:System.Windows.Media.RectangleGeometry> Obiekty są wyświetlane przy użyciu <xref:System.Windows.Shapes.Path> elementów.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![Prostokąty o różnych RadiusX &#47; Ustawienia radiusY](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")  
Prostokąty z zaokrąglonymi narożnikami  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Tworzenie złożonego kształtu](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Tworzenie za pomocą PathGeometry kształtu](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
