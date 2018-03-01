---
title: "Jak utworzyć linię używając LineGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 487a5ffaf952450c6196f5fe0d00fd249177b054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a>Jak utworzyć linię używając LineGeometry
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.LineGeometry> klasy do opisywania wiersza. A <xref:System.Windows.Media.LineGeometry> jest definiowana za pomocą jego początkowego i końcowego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia i renderowania <xref:System.Windows.Media.LineGeometry>.  A <xref:System.Windows.Shapes.Path> element jest używany do renderowania wiersza.  Ponieważ wiersz nie ma żadnych obszaru <xref:System.Windows.Shapes.Path> obiektu <xref:System.Windows.Shapes.Shape.Fill%2A> nie jest określona; zamiast tego <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> właściwości są używane.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 ![Obiekt LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Obiekt LineGeometry rysowane z (10,20) (100,130)  
  
 Inne klasy proste geometrii obejmują <xref:System.Windows.Media.LineGeometry> i <xref:System.Windows.Media.EllipseGeometry>. Te mają geometrię, a także bardziej złożonych z nich, można również tworzyć przy użyciu <xref:System.Windows.Media.PathGeometry> lub <xref:System.Windows.Media.StreamGeometry>. Aby uzyskać więcej informacji, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Geometria — przegląd](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Tworzenie kształtu złożonego](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Tworzenie kształtu przy użyciu elementu PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
