---
title: "Jak utworzyć obiekt LineSegment w PathGeometry"
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
- line segments [WPF], creating
- graphics [WPF], line segments
ms.assetid: 0155ed47-a20d-49a7-a306-186d8e07fbc4
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aa7ea915afa2dc80e19d270abb86ec12a39d5865
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a>Jak utworzyć obiekt LineSegment w PathGeometry
W tym przykładzie przedstawiono sposób tworzenia segment linii. Aby utworzyć segmentu linii, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.LineSegment> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższe przykłady rysowania <xref:System.Windows.Media.LineSegment> z (10, 50) do (200, 70). Na poniższej ilustracji przedstawiono powstałe w ten sposób <xref:System.Windows.Media.LineSegment>; tło siatki został dodany do wyświetlenia układ współrzędnych.  
  
 ![LineSegment w PathFigure](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment")  
Obiekt LineSegment rysowane z (10,50) (200,70)  
  
 [xaml]  
  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], może użyć składni atrybut opisujący ścieżkę.  
  
```xaml  
<Path Stroke="Black" StrokeThickness="1"    
  Data="M 10,50 L 200,70" />  
```  
  
 [xaml]  
  
 (Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, wersja wagi jaśniejszego <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz [składnia znacznika ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) strony.)  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], może również zwrócić segment linii przy użyciu składni elementu obiektu. Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.  
  
```xaml  
<Path Stroke="Black" StrokeThickness="1">  
  <Path.Data>  
    <PathGeometry>  
      <PathFigure StartPoint="10,50">  
        <LineSegment Point="200,70" />  
      </PathFigure>  
    </PathGeometry>  
  </Path.Data>  
</Path>  
```  
  
```csharp  
PathFigure myPathFigure = new PathFigure();  
myPathFigure.StartPoint = new Point(10, 50);  
  
LineSegment myLineSegment = new LineSegment();  
myLineSegment.Point = new Point(200, 70);  
  
PathSegmentCollection myPathSegmentCollection = new PathSegmentCollection();  
myPathSegmentCollection.Add(myLineSegment);  
  
myPathFigure.Segments = myPathSegmentCollection;  
  
PathFigureCollection myPathFigureCollection = new PathFigureCollection();  
myPathFigureCollection.Add(myPathFigure);  
  
PathGeometry myPathGeometry = new PathGeometry();  
myPathGeometry.Figures = myPathFigureCollection;  
  
Path myPath = new Path();  
myPath.Stroke = Brushes.Black;  
myPath.StrokeThickness = 1;  
myPath.Data = myPathGeometry;  
```  
  
```vb  
Dim myPathFigure As New PathFigure()  
            myPathFigure.StartPoint = New Point(10, 50)  
  
            Dim myLineSegment As New LineSegment()  
            myLineSegment.Point = New Point(200, 70)  
  
            Dim myPathSegmentCollection As New PathSegmentCollection()  
            myPathSegmentCollection.Add(myLineSegment)  
  
            myPathFigure.Segments = myPathSegmentCollection  
  
            Dim myPathFigureCollection As New PathFigureCollection()  
            myPathFigureCollection.Add(myPathFigure)  
  
            Dim myPathGeometry As New PathGeometry()  
            myPathGeometry.Figures = myPathFigureCollection  
  
            Dim myPath As New Path()  
            myPath.Stroke = Brushes.Black  
            myPath.StrokeThickness = 1  
            myPath.Data = myPathGeometry  
```  
  
 Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [próbki mają geometrię](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.PathFigure>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.GeometryDrawing>  
 <xref:System.Windows.Shapes.Path>  
 [Omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
