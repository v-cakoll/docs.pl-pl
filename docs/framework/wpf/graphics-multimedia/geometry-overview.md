---
title: Przegląd Geometria
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometry classes [WPF]
- graphics [WPF], geometry classes
ms.assetid: 9fba8934-98b7-4af6-82f6-f4ef887f963a
ms.openlocfilehash: 01c460ae18c489a21c860c6d2b10f551e6e68242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558074"
---
# <a name="geometry-overview"></a>Przegląd Geometria
Ten przegląd zawiera opis sposobu używania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> klas opisujących kształtów. W tym temacie uwidocznia także różnice między <xref:System.Windows.Media.Geometry> obiektów i <xref:System.Windows.Shapes.Shape> elementy.  
  
  
<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>Co to jest geometrię?  
 <xref:System.Windows.Media.Geometry> Klasa i klasy, które dziedziczą z niego, takich jak <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>, i <xref:System.Windows.Media.CombinedGeometry>, umożliwiają opisano geometrii kształtu 2-D. Poniższe opisy geometrycznych ma wielu zastosowań, takich definiowanie kształtu do malowania do ekranu lub Definiowanie trafień testu i klip regionów. Można nawet umożliwia geometrię zdefiniował ścieżki animacji.  
  
 <xref:System.Windows.Media.Geometry> obiekty mogą być prosty, takie jak prostokąty i okręgi lub złożone, utworzone na podstawie co najmniej dwa obiekty geometrii.  Można tworzyć bardziej złożone mają geometrię przy użyciu <xref:System.Windows.Media.PathGeometry> i <xref:System.Windows.Media.StreamGeometry> klasy, które umożliwiają opisano łuki i krzywych.  
  
 Ponieważ <xref:System.Windows.Media.Geometry> jest typem <xref:System.Windows.Freezable>, <xref:System.Windows.Media.Geometry> obiektów udostępnia kilka funkcje specjalne: mogą być deklarowane jako [zasobów](../../../../docs/framework/wpf/advanced/xaml-resources.md)współużytkowanych przez wiele obiektów, aby zwiększyć wydajność, sklonowany, jest tylko do odczytu i wprowadzone wątkowo. Aby uzyskać więcej informacji o różnych funkcjach dostarczonych przez <xref:System.Windows.Freezable> obiekty, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Mają geometrię vs. Kształty  
 <xref:System.Windows.Media.Geometry> i <xref:System.Windows.Shapes.Shape> klasy wydaje się podobnie, w tym opisują kształty 2-(porównania <xref:System.Windows.Media.EllipseGeometry> i <xref:System.Windows.Shapes.Ellipse> na przykład), ale różnią się ważne.  
  
 Dla jednego <xref:System.Windows.Media.Geometry> klasa dziedziczy <xref:System.Windows.Freezable> klasy podczas <xref:System.Windows.Shapes.Shape> klasa dziedziczy <xref:System.Windows.FrameworkElement>. Ponieważ są one elementy, <xref:System.Windows.Shapes.Shape> obiektów można samodzielnie renderowania i uczestniczyć w systemie układ podczas <xref:System.Windows.Media.Geometry> nie obiektów.  
  
 Mimo że <xref:System.Windows.Shapes.Shape> obiekty są łatwiej można używać niż <xref:System.Windows.Media.Geometry> obiektów, <xref:System.Windows.Media.Geometry> obiekty są bardziej elastyczne. Gdy <xref:System.Windows.Shapes.Shape> obiekt jest używany do renderowania grafiki 2-D <xref:System.Windows.Media.Geometry> obiekt może służyć do zdefiniować geometrycznych region grafiki 2-D, zdefiniować region dla wycinka lub zdefiniować region testowania trafień, np.  
  
### <a name="the-path-shape"></a>Kształt ścieżki  
 Jeden <xref:System.Windows.Shapes.Shape>, <xref:System.Windows.Shapes.Path> klasy faktycznie używa <xref:System.Windows.Media.Geometry> do opisywania jego zawartość. Przez ustawienie <xref:System.Windows.Shapes.Path.Data%2A> właściwość <xref:System.Windows.Shapes.Path> z <xref:System.Windows.Media.Geometry> i ustawienie jej <xref:System.Windows.Shapes.Shape.Fill%2A> i <xref:System.Windows.Shapes.Shape.Stroke%2A> właściwości, umożliwiający renderowanie <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Wspólne właściwości, które przyjmują geometrię  
 Poprzednich sekcjach wspomniano, że geometrii obiekty mogą być używane z innymi obiektami do różnych celów, takich jak rysowanie kształtów, animacji i wycinka. W poniższej tabeli wymieniono kilka klas, które mają właściwości, które przyjmują <xref:System.Windows.Media.Geometry> obiektu.  
  
|Typ|Właściwość|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Typy geometrii proste  
 Klasa podstawowa dla wszystkich mają geometrię jest klasa abstrakcyjna <xref:System.Windows.Media.Geometry>.  Klasy, które wynikają z <xref:System.Windows.Media.Geometry> klasy może być około podzielone na trzy kategorie: prosty mają geometrię, mają ścieżki geometrię i złożone mają geometrię.  
  
 Proste geometrii klasy mają <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, i <xref:System.Windows.Media.EllipseGeometry> i służą do tworzenia prostych kształtów geometryczne, takie jak wiersze, prostokąty i okręgi.  
  
-   A <xref:System.Windows.Media.LineGeometry> jest zdefiniowany, określając punkt początkowy linii i punktu końcowego.  
  
-   A <xref:System.Windows.Media.RectangleGeometry> jest zdefiniowana z <xref:System.Windows.Rect> struktury, która określa jego względne położenie i jej wysokości i szerokości. Zaokrąglony prostokąt można utworzyć przez ustawienie <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> właściwości.  
  
-   <xref:System.Windows.Media.EllipseGeometry> Jest definiowana za pomocą punktu centralnego, radius x i y-radius.  Poniższe przykłady przedstawiają sposób tworzenia prostego mają geometrię renderowania i wycinka.  
  
 Te kształtów tego samego typu, a także bardziej złożonych kształtów, można utworzyć przy użyciu <xref:System.Windows.Media.PathGeometry> lub łącząc obiektów geometry, ale te klasy umożliwiają łatwiejsze do produkcji tych podstawowych kształtów geometrycznych.  
  
 Poniższy przykład przedstawia sposób tworzenia i renderowania <xref:System.Windows.Media.LineGeometry>.  Jak wspomniano wcześniej, <xref:System.Windows.Media.Geometry> obiektu nie jest w stanie do rysowania, więc w przykładzie użyto <xref:System.Windows.Shapes.Path> kształtu do renderowania wiersza.  Ponieważ wiersz nie ma żadnych obszaru, ustawienie <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość <xref:System.Windows.Shapes.Path> czy nie obowiązują; zamiast tego tylko <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> właściwości są określone. Na poniższej ilustracji przedstawiono dane wyjściowe w przykładzie.  
  
 ![Obiekt LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Obiekt LineGeometry rysowane z (10,20) (100,130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 W kolejnym przykładzie pokazano sposób tworzenia i renderowania <xref:System.Windows.Media.EllipseGeometry>.  Ustawia przykłady <xref:System.Windows.Media.EllipseGeometry.Center%2A> z <xref:System.Windows.Media.EllipseGeometry> ma ustawioną wartość punktu `50,50` i x radius i y-radius są ustawione na `50`, co powoduje koło z średnicy 100.  Wewnątrz elipsy jest malowane przez przypisanie wartości do właściwości wypełnienia elementu ścieżki, w tym przypadku <xref:System.Windows.Media.Brushes.Gold%2A>. Na poniższej ilustracji przedstawiono dane wyjściowe w przykładzie.  
  
 ![EllipseGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
EllipseGeometry rysowane (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 Poniższy przykład przedstawia sposób tworzenia i renderowania <xref:System.Windows.Media.RectangleGeometry>.  Położenie i wymiary prostokąta są definiowane przez <xref:System.Windows.Rect> struktury. Pozycja `50,50` i wysokość i szerokość są `25`, co powoduje kwadrat. Na poniższej ilustracji przedstawiono dane wyjściowe w przykładzie.  
  
 ![Obiekt RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
Obiekt RectangleGeometry rysowane 50,50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Media.EllipseGeometry> jako obszar przycinania obrazu.  <xref:System.Windows.Controls.Image> Obiektu jest zdefiniowana z <xref:System.Windows.FrameworkElement.Width%2A> 200 i <xref:System.Windows.FrameworkElement.Height%2A> 150.  <xref:System.Windows.Media.EllipseGeometry> z <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> wartość 100, <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> wartość 75, a <xref:System.Windows.Media.EllipseGeometry.Center%2A> ma ustawioną wartość 100,75 <xref:System.Windows.UIElement.Clip%2A> właściwości obrazu.  Wyświetlane są tylko część obrazu, który znajduje się w obszarze elipsy. Na poniższej ilustracji przedstawiono dane wyjściowe w przykładzie.  
  
 ![Obraz z lub bez wycinka](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
EllipseGeometry umożliwia obcina formantu obrazu  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Ścieżka mają geometrię  
 <xref:System.Windows.Media.PathGeometry> Klasy i jej odpowiednik lekki <xref:System.Windows.Media.StreamGeometry> klasy, podaj sposób opisują wiele złożonych rysunki składa się z łuki, krzywych i linii.  
  
 Istotą <xref:System.Windows.Media.PathGeometry> jest kolekcją <xref:System.Windows.Media.PathFigure> obiektów o nazwie tak, ponieważ każdy rysunek opisuje dyskretne kształtu w <xref:System.Windows.Media.PathGeometry>. Każdy <xref:System.Windows.Media.PathFigure> sam składa się z co najmniej jednego <xref:System.Windows.Media.PathSegment> obiektów, z których każdy zawiera opis segment rysunku.  
  
 Istnieje wiele typów segmentów.  
  
|Typ segmentu|Opis|Przykład|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Tworzy łuku między dwoma punktami.|[Utwórz łuku](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Tworzy sześcienny krzywej Beziera między dwoma punktami.|[Tworzenie sześcienny krzywej Beziera](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Tworzy linię między dwoma punktami.|[Tworzenie obiektu LineSegment w elemencie PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Tworzy serię sześcienny krzywych Beziera.|Zobacz <xref:System.Windows.Media.PolyBezierSegment> typu strony.|  
|<xref:System.Windows.Media.PolyLineSegment>|Tworzy serię wierszy.|Zobacz <xref:System.Windows.Media.PolyLineSegment> typu strony.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Tworzy serię kwadratową krzywych Beziera.|Zobacz <xref:System.Windows.Media.PolyQuadraticBezierSegment> strony.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Tworzy kwadratową krzywą Beziera.|[Tworzenie kwadratową krzywej Beziera](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).|  
  
 Segmenty wewnątrz <xref:System.Windows.Media.PathFigure> są łączone do pojedynczego kształtu geometrycznego z punktu końcowego każdego segmentu jest punkt początkowy następnego segmentu. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Właściwość <xref:System.Windows.Media.PathFigure> określa punkt, z którego ma zostać narysowana pierwszy segment. Każdy z segmentów kolejnych zostanie uruchomiony w punkcie końcowym poprzedniego segmentu. Na przykład linią pionową z `10,50` do `10,150` można zdefiniować ustawiając <xref:System.Windows.Media.PathFigure.StartPoint%2A> właściwości `10,50` i tworzenie <xref:System.Windows.Media.LineSegment> z <xref:System.Windows.Media.LineSegment.Point%2A> ustawienie właściwości `10,150`.  
  
 Poniższy przykład tworzy prosty <xref:System.Windows.Media.PathGeometry> obejmuje jedną <xref:System.Windows.Media.PathFigure> z <xref:System.Windows.Media.LineSegment> i wyświetla je przy użyciu <xref:System.Windows.Shapes.Path> elementu. <xref:System.Windows.Media.PathFigure> Obiektu <xref:System.Windows.Media.PathFigure.StartPoint%2A> ustawiono `10,20` i <xref:System.Windows.Media.LineSegment> jest zdefiniowana z punktem końcowym `100,130`. Na poniższej ilustracji pokazano <xref:System.Windows.Media.PathGeometry> utworzone przez tego przykładu.  
  
 ![Obiekt LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Obiekt zawierający pojedynczy LineSegment PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Warto kontrastem w tym przykładzie z poprzednim <xref:System.Windows.Media.LineGeometry> przykład.  Składnia służąca do <xref:System.Windows.Media.PathGeometry> jest na pełniejsze niż używany dla prostego <xref:System.Windows.Media.LineGeometry>, i mogą mieć więcej warto użyć <xref:System.Windows.Media.LineGeometry> klasy w tym przypadku, ale pełne składnia <xref:System.Windows.Media.PathGeometry> umożliwia bardzo skomplikowanych i złożone regiony geometrycznej.  
  
 Można tworzyć bardziej złożone mają geometrię przy użyciu kombinacji <xref:System.Windows.Media.PathSegment> obiektów.  
  
 W następnym przykładzie użyto <xref:System.Windows.Media.BezierSegment>, <xref:System.Windows.Media.LineSegment>i <xref:System.Windows.Media.ArcSegment> można utworzyć kształtu. Najpierw tworzony sześcienny Beziera krzywej jest definiując cztery punkty: punkt początkowy, który jest punktem końcowym poprzedniego segmentu, punkt końcowy (<xref:System.Windows.Media.BezierSegment.Point3%2A>), dwa punktów kontrolnych i (<xref:System.Windows.Media.BezierSegment.Point1%2A> i <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Punkty kontrolne dwóch sześcienny krzywej Beziera przypominają pól korzystające z części co byłoby prostej kierunku, tworzenie krzywą. Formant pierwszego punktu, <xref:System.Windows.Media.BezierSegment.Point1%2A>, ma wpływ na początku części krzywej; drugi punkt kontrolny, <xref:System.Windows.Media.BezierSegment.Point2%2A>, ma wpływ na końcową części krzywej.  
  
 Przykład następnie dodaje <xref:System.Windows.Media.LineSegment>, który pochodzi od poprzedniego punktu końcowego <xref:System.Windows.Media.BezierSegment> który poprzedzone punktu określonego przez jego <xref:System.Windows.Media.LineSegment> właściwości.  
  
 Następnie dodaje przykładzie <xref:System.Windows.Media.ArcSegment>, która pochodzi z poprzedniego punktu końcowego <xref:System.Windows.Media.LineSegment> do punktu określonego przez jego <xref:System.Windows.Media.ArcSegment.Point%2A> właściwości. W przykładzie określa również łuku x i y-radius (<xref:System.Windows.Media.ArcSegment.Size%2A>), kąt obrotu (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), flagę wskazującą, jak duże powinny być kąt wynikowy łuk (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>) i wartość wskazującą, w kierunku łuku (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). Na poniższej ilustracji przedstawiono utworzone w tym przykładzie kształtu.  
  
 ![Obiekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path2.gif "graphicsmm_path2")  
Obiekt PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Można tworzyć bardziej złożone mają geometrię za pomocą wielu <xref:System.Windows.Media.PathFigure> obiektów w ramach <xref:System.Windows.Media.PathGeometry>.  
  
 Poniższy przykład tworzy <xref:System.Windows.Media.PathGeometry> z dwoma <xref:System.Windows.Media.PathFigure> obiektów, z których każdy zawiera wiele <xref:System.Windows.Media.PathSegment> obiektów.  <xref:System.Windows.Media.PathFigure> w powyższym przykładzie i <xref:System.Windows.Media.PathFigure> z <xref:System.Windows.Media.PolyLineSegment> i <xref:System.Windows.Media.QuadraticBezierSegment> są używane.  A <xref:System.Windows.Media.PolyLineSegment> jest zdefiniowana z tablicy punktów i <xref:System.Windows.Media.QuadraticBezierSegment> jest zdefiniowana z punktu kontrolnego i punkt końcowy. Na poniższej ilustracji przedstawiono utworzone w tym przykładzie kształtu.  
  
 ![Obiekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry z wielu wartości  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Podobnie jak <xref:System.Windows.Media.PathGeometry> klasy <xref:System.Windows.Media.StreamGeometry> definiuje złożonych kształtu geometrycznego, który może zawierać krzywych, łuki i wierszy. W odróżnieniu od <xref:System.Windows.Media.PathGeometry>, zawartość <xref:System.Windows.Media.StreamGeometry> nie obsługuje wiązania danych, animacji lub modyfikacji. Użyj <xref:System.Windows.Media.StreamGeometry> potrzebne do opisywania złożonych geometry, ale nie chcesz koszty obsługi wiązania z danymi, animacji lub modyfikacji. Ze względu na jego wydajność <xref:System.Windows.Media.StreamGeometry> klasy jest dobrym rozwiązaniem dla opisu modułu definiowania układu kodu.  
  
 Na przykład zobacz [Utwórz kształt za pomocą StreamGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Składni znacznikowania ścieżki  
 <xref:System.Windows.Media.PathGeometry> i <xref:System.Windows.Media.StreamGeometry> typy obsługi [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] atrybutu składni, używając szeregu specjalne przenoszenia i rysowanie poleceń. Aby uzyskać więcej informacji, zobacz [składnia znacznika ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Złożone mają geometrię  
 Obiekty złożone geometrii mogą być tworzone przy użyciu <xref:System.Windows.Media.GeometryGroup>, <xref:System.Windows.Media.CombinedGeometry>, lub przez wywołanie metody statycznych <xref:System.Windows.Media.Geometry> — metoda <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
-   <xref:System.Windows.Media.CombinedGeometry> Obiektu i <xref:System.Windows.Media.Geometry.Combine%2A> metoda przeprowadza operacja logiczna połączyć obszar zdefiniowany przez dwa mają geometrię. <xref:System.Windows.Media.Geometry> obiektów, które ma obszaru są odrzucane. Tylko dwa <xref:System.Windows.Media.Geometry> obiekty można łączyć (mimo że te dwa mają geometrię może być również złożone mają geometrię).  
  
-   <xref:System.Windows.Media.GeometryGroup> Klasy tworzy połączenie <xref:System.Windows.Media.Geometry> obiekty zawiera bez łączenie ich obszaru. Dowolną liczbę <xref:System.Windows.Media.Geometry> obiekty mogą być dodawane do <xref:System.Windows.Media.GeometryGroup>. Na przykład zobacz [Tworzenie złożonego kształtu](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md).  
  
 Ponieważ nie wykonuj operację łączenia, za pomocą <xref:System.Windows.Media.GeometryGroup> obiektów zapewnia korzyści wydajności w przypadku <xref:System.Windows.Media.CombinedGeometry> obiektów lub <xref:System.Windows.Media.Geometry.Combine%2A> metody.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Łączna mają geometrię  
 Poprzedniej sekcji, o których wspomniano <xref:System.Windows.Media.CombinedGeometry> obiektu i <xref:System.Windows.Media.Geometry.Combine%2A> metoda łączenia obszar zdefiniowany przez mają geometrię, zawierają one. <xref:System.Windows.Media.GeometryCombineMode> Wyliczenie Określa, jak mają geometrię są połączone. Możliwe wartości <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> właściwości są: <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>, i <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 W poniższym przykładzie <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany w trybie łączenia Unii.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi tej samej usługi radius, ale z przesunięciem centrów o 50.  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Wyniki Unii połączyć tryb](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 W poniższym przykładzie <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany w trybie łączenia z <xref:System.Windows.Media.GeometryCombineMode.Xor>.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi tej samej usługi radius, ale z przesunięciem centrów o 50.  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Wyniki Xor połączyć tryb](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Dodatkowe przykłady można znaleźć [Tworzenie złożonego kształtu](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md) i [utworzyć geometrię łączyć](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Funkcje obiektu freezable  
 Ponieważ dziedziczy on z <xref:System.Windows.Freezable> klasy <xref:System.Windows.Media.Geometry> klasy udostępnia kilka funkcje specjalne: <xref:System.Windows.Media.Geometry> obiekty mogą być deklarowane jako [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)współużytkowanych przez wiele obiektów, aby poprawić jest tylko do odczytu wydajność, sklonowany, a wprowadzone wątkowo. Aby uzyskać więcej informacji o różnych funkcjach dostarczonych przez <xref:System.Windows.Freezable> obiekty, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Inne funkcje geometrii  
 <xref:System.Windows.Media.Geometry> Klasa udostępnia również metody narzędziowe przydatne, takie jak następujące:  
  
-   <xref:System.Windows.Media.Geometry.GetArea%2A> -Pobiera obszar <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.FillContains%2A> — Określa, czy geometrii zawiera inny <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.StrokeContains%2A> — Określa, czy obrysu <xref:System.Windows.Media.Geometry> zawiera określony punkt.  
  
 Zobacz <xref:System.Windows.Media.Geometry> klasy, aby uzyskać pełną listę metod.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Geometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Składnia znacznikowania ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Kształty i podstawowe rysowanie w programie WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
