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
ms.openlocfilehash: 0c30bc99939b7e60e7e36b698776951cc6181497
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532358"
---
# <a name="geometry-overview"></a>Przegląd Geometria
W tym omówieniu opisano sposób użycia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> klas do opisania kształtów. W tym temacie uwidocznia także różnice między <xref:System.Windows.Media.Geometry> obiektów i <xref:System.Windows.Shapes.Shape> elementów.  
  
  
<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>Co to jest geometrii?  
 <xref:System.Windows.Media.Geometry> Klasy i klas, które dziedziczyć po nim, takie jak <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>, i <xref:System.Windows.Media.CombinedGeometry>, umożliwiają opisują geometrii kształtu 2-D. Opisy te geometrycznych mają wiele zastosowań, takich definiowanie kształtu, aby rysować na ekranie lub Definiowanie testowania trafienia i klipu regionów. Geometria umożliwia nawet Definiowanie ścieżką animacji.  
  
 <xref:System.Windows.Media.Geometry> obiekty mogą być proste, takich jak prostokąty i okręgów lub złożone, utworzone na podstawie dwóch lub więcej obiektów geometrii.  Bardziej złożone geometrii można utworzyć za pomocą <xref:System.Windows.Media.PathGeometry> i <xref:System.Windows.Media.StreamGeometry> klasy, które umożliwiają opisują, krzywych i łuki.  
  
 Ponieważ <xref:System.Windows.Media.Geometry> jest typem <xref:System.Windows.Freezable>, <xref:System.Windows.Media.Geometry> obiekty zapewniają kilka funkcji specjalnych: mogą być deklarowane jako [zasobów](../../../../docs/framework/wpf/advanced/xaml-resources.md), udostępnione wśród wielu obiektów, aby zwiększyć wydajność, sklonowany, jest tylko do odczytu i wprowadzone metodą o bezpiecznych wątkach. Aby uzyskać więcej informacji na temat różnych funkcji oferowanych przez <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Vs geometrii. Kształty  
 <xref:System.Windows.Media.Geometry> i <xref:System.Windows.Shapes.Shape> klasy wydają się podobne, w tym opisują kształty 2-D (porównaj <xref:System.Windows.Media.EllipseGeometry> i <xref:System.Windows.Shapes.Ellipse> na przykład), ale istnieją ważne różnice.  
  
 Dla jednego <xref:System.Windows.Media.Geometry> klasa dziedziczy <xref:System.Windows.Freezable> klasy podczas <xref:System.Windows.Shapes.Shape> klasa dziedziczy <xref:System.Windows.FrameworkElement>. Ponieważ są one elementy, <xref:System.Windows.Shapes.Shape> obiekty można samodzielnie renderowania i uczestniczą w systemie układu podczas <xref:System.Windows.Media.Geometry> nie obiektów.  
  
 Mimo że <xref:System.Windows.Shapes.Shape> obiekty są bardziej gotowy do użycia, niż <xref:System.Windows.Media.Geometry> obiektów <xref:System.Windows.Media.Geometry> obiekty są bardziej wszechstronna. Gdy <xref:System.Windows.Shapes.Shape> obiekt jest używany do renderowania grafiki 2-D <xref:System.Windows.Media.Geometry> obiekt może służyć do definiowania geometrycznych region dla grafika 2-D, zdefiniować region dla wycinka lub zdefiniować region do testowania trafień, na przykład.  
  
### <a name="the-path-shape"></a>Kształtu ścieżki  
 Jeden <xref:System.Windows.Shapes.Shape>, <xref:System.Windows.Shapes.Path> klasy faktycznie używany <xref:System.Windows.Media.Geometry> do opisania jego zawartość. Ustawiając <xref:System.Windows.Shapes.Path.Data%2A> właściwość <xref:System.Windows.Shapes.Path> z <xref:System.Windows.Media.Geometry> i ustawienie jej <xref:System.Windows.Shapes.Shape.Fill%2A> i <xref:System.Windows.Shapes.Shape.Stroke%2A> właściwości, umożliwiający renderowanie <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Wspólne właściwości, które przyjmują geometrii  
 Poprzednich sekcji wspomnieć, że obiektów geometrii mogą być używane z innymi obiektami do różnych celów, takich jak rysowanie kształtów, animowanie i przycinania. W poniższej tabeli wymieniono kilka klas, które mają właściwości, które przyjmują <xref:System.Windows.Media.Geometry> obiektu.  
  
|Typ|Właściwość|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Typy proste geometrii  
 Klasa bazowa dla wszystkich geometrii jest klasa abstrakcyjna <xref:System.Windows.Media.Geometry>.  Klasy, które wynikają z <xref:System.Windows.Media.Geometry> klasy, można grubsza podzielić na trzy kategorie: prosty geometrii, geometrii ścieżki i złożone geometrii.  
  
 Klasy geometrii proste obejmują <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, i <xref:System.Windows.Media.EllipseGeometry> i są używane do tworzenia podstawowych kształtów geometrycznych, takich jak linii, prostokąty i kółka.  
  
-   Element <xref:System.Windows.Media.LineGeometry> jest zdefiniowany, określając punkt początkowy linii i punktu końcowego.  
  
-   A <xref:System.Windows.Media.RectangleGeometry> jest zdefiniowana za pomocą <xref:System.Windows.Rect> strukturę, która określa jej położenie względne i jego wysokość i szerokość. Zaokrąglony prostokąt można utworzyć, ustawiając <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> właściwości.  
  
-   <xref:System.Windows.Media.EllipseGeometry> Jest definiowany przez punktu centralnego, promień x i y-radius.  Następujące przykłady przedstawiają sposób tworzenia prostego geometrii renderowania i wycinka.  
  
 Te kształty ten sam, jak również bardziej złożonych kształtów można tworzyć przy użyciu <xref:System.Windows.Media.PathGeometry> lub łącząc razem obiektów geometrii, ale te klasy umożliwiają łatwiejsze do tworzenia tych podstawowych kształtów geometrycznych.  
  
 Poniższy przykład pokazuje, jak utworzyć i renderowania <xref:System.Windows.Media.LineGeometry>.  Jak wspomniano wcześniej, <xref:System.Windows.Media.Geometry> obiektu nie jest w stanie do rysowania, więc w przykładzie użyto <xref:System.Windows.Shapes.Path> kształtu do renderowania wiersza.  Wiersz jest nie obszaru, dlatego ustawiając <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość <xref:System.Windows.Shapes.Path> miałaby żadnego efektu; zamiast tego należy tylko <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> są określone właściwości. Poniższa ilustracja przedstawia dane wyjściowe z przykładu.  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
LineGeometry rysowane z (10,20) (100,130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 W kolejnym przykładzie pokazano sposób tworzenia i renderowania <xref:System.Windows.Media.EllipseGeometry>.  Ustawia przykłady <xref:System.Windows.Media.EllipseGeometry.Center%2A> z <xref:System.Windows.Media.EllipseGeometry> ustawiono punkt `50,50` i promień x i y-radius są ustawione na `50`, co powoduje utworzenie koło z średnica 100.  Wewnątrz elipsy jest malowane przez przypisywanie wartości do właściwości wypełnienia elementu ścieżki, w tym przypadku <xref:System.Windows.Media.Brushes.Gold%2A>. Poniższa ilustracja przedstawia dane wyjściowe z przykładu.  
  
 ![EllipseGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
EllipseGeometry rysowany w (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 Poniższy przykład pokazuje, jak utworzyć i renderowania <xref:System.Windows.Media.RectangleGeometry>.  Położenie i wymiary prostokąta są definiowane przez <xref:System.Windows.Rect> struktury. Pozycja jest `50,50` i wysokość i szerokość są `25`, co powoduje utworzenie kwadrat. Poniższa ilustracja przedstawia dane wyjściowe z przykładu.  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
Rysowany w 50,50 RectangleGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.EllipseGeometry> jako obszar przycinania dla obrazu.  <xref:System.Windows.Controls.Image> Obiektu jest zdefiniowana za pomocą <xref:System.Windows.FrameworkElement.Width%2A> 200 i <xref:System.Windows.FrameworkElement.Height%2A> 150.  <xref:System.Windows.Media.EllipseGeometry> z <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> wartość 100, <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> wartość 75, a <xref:System.Windows.Media.EllipseGeometry.Center%2A> 100,75 jest wartość <xref:System.Windows.UIElement.Clip%2A> właściwości obrazu.  Zostanie wyświetlony tylko część obrazu, który znajduje się w obszarze elipsy. Poniższa ilustracja przedstawia dane wyjściowe z przykładu.  
  
 ![Obraz z lub bez przycinania](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
EllipseGeometry używane, kiedy należy przyciąć kontrolkę typu obraz  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Ścieżka geometrii  
 <xref:System.Windows.Media.PathGeometry> Klasy i równoważnik lekki <xref:System.Windows.Media.StreamGeometry> klasy, zapewniają sposób opisują wiele rysunki złożone składa się z łuki, krzywych i linii.  
  
 Istotą <xref:System.Windows.Media.PathGeometry> to zbiór <xref:System.Windows.Media.PathFigure> obiektów, więc o nazwie, ponieważ każdy rysunek opisuje dyskretnych kształtu w <xref:System.Windows.Media.PathGeometry>. Każdy <xref:System.Windows.Media.PathFigure> sam składa się z co najmniej jeden <xref:System.Windows.Media.PathSegment> obiektów, z których każdy zawiera opis segment rysunku.  
  
 Istnieje wiele typów segmentów.  
  
|Typ segmentu|Opis|Przykład|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Tworzy łuk eliptyczny między dwoma punktami.|[Tworzenie łuku eliptycznego](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Tworzy krzywą Beziera trzeciego stopnia między dwoma punktami.|[Utwórz krzywą Beziera trzeciego stopnia](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Tworzy linię między dwoma punktami.|[Tworzenie obiektu LineSegment w elemencie PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Tworzy serię krzywe Beziera trzeciego stopnia.|Zobacz <xref:System.Windows.Media.PolyBezierSegment> typ strony.|  
|<xref:System.Windows.Media.PolyLineSegment>|Tworzy serię wierszy.|Zobacz <xref:System.Windows.Media.PolyLineSegment> typ strony.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Tworzy serię krzywe Beziera drugiego stopnia.|Zobacz <xref:System.Windows.Media.PolyQuadraticBezierSegment> strony.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Tworzy krzywą Beziera drugiego stopnia.|[Utwórz krzywą Beziera drugiego stopnia](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).|  
  
 Segmenty wewnątrz <xref:System.Windows.Media.PathFigure> są łączone do pojedynczego kształtu geometrycznego z punktu końcowego każdego segmentu jest punkt początkowy następnego segmentu. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Właściwość <xref:System.Windows.Media.PathFigure> określa punkt, z którego jest rysowana pierwszy segment. Każdy z kolejnych segmentów rozpoczyna się w punkcie końcowym poprzedniego segmentu. Na przykład, pionowa linia z `10,50` do `10,150` można zdefiniować, ustawiając <xref:System.Windows.Media.PathFigure.StartPoint%2A> właściwości `10,50` i tworzenie <xref:System.Windows.Media.LineSegment> z <xref:System.Windows.Media.LineSegment.Point%2A> ustawienie właściwości `10,150`.  
  
 Poniższy przykład tworzy prostą <xref:System.Windows.Media.PathGeometry> składające się z pojedynczego <xref:System.Windows.Media.PathFigure> z <xref:System.Windows.Media.LineSegment> i wyświetla je przy użyciu <xref:System.Windows.Shapes.Path> elementu. <xref:System.Windows.Media.PathFigure> Obiektu <xref:System.Windows.Media.PathFigure.StartPoint%2A> ustawiono `10,20` i <xref:System.Windows.Media.LineSegment> jest zdefiniowana z punktem końcowym `100,130`. Poniższa ilustracja przedstawia <xref:System.Windows.Media.PathGeometry> utworzone przez tego przykładu.  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Zawierający pojedynczy LineSegment PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Warto kontrastem w tym przykładzie z poprzednim okresem <xref:System.Windows.Media.LineGeometry> przykład.  Składnia służąca do <xref:System.Windows.Media.PathGeometry> jest znacznie bardziej szczegółowy niż dla prostego <xref:System.Windows.Media.LineGeometry>, i rozsądne może okazać się bardziej zrozumiałe, aby użyć <xref:System.Windows.Media.LineGeometry> klasy w tym przypadku, ale Pełna składnia elementu <xref:System.Windows.Media.PathGeometry> umożliwia bardzo skomplikowanych i złożone regiony geometrycznych.  
  
 Bardziej złożone geometrii można utworzyć przy użyciu kombinacji <xref:System.Windows.Media.PathSegment> obiektów.  
  
 W następnym przykładzie użyto <xref:System.Windows.Media.BezierSegment>, <xref:System.Windows.Media.LineSegment>i <xref:System.Windows.Media.ArcSegment> do utworzenia kształtu. W przykładzie najpierw jest tworzony Beziera trzeciego stopnia krzywa jest definiując cztery punkty: punkt początkowy, który jest punktem końcowym poprzedniego segmentu, punkt końcowy (<xref:System.Windows.Media.BezierSegment.Point3%2A>), dwa punktów kontrolnych i (<xref:System.Windows.Media.BezierSegment.Point1%2A> i <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Punkty kontrolne dwóch krzywą Beziera trzeciego stopnia zachowują się jak pól, długotrwałego części co byłoby prostej kierunku, tworzenie krzywej. Pierwszy formant punktu, <xref:System.Windows.Media.BezierSegment.Point1%2A>, ma wpływ na początku części krzywej; drugi punkt kontrolny <xref:System.Windows.Media.BezierSegment.Point2%2A>, ma wpływ na końcowej części krzywej.  
  
 Przykład następnie dodaje <xref:System.Windows.Media.LineSegment>, który jest rysowana od poprzedniego punktu końcowego <xref:System.Windows.Media.BezierSegment> , poprzedzony punktu określonego przez jego <xref:System.Windows.Media.LineSegment> właściwości.  
  
 Przykład następnie dodaje <xref:System.Windows.Media.ArcSegment>, który jest rysowana od poprzedniego punktu końcowego <xref:System.Windows.Media.LineSegment> do punktu, określony przez jego <xref:System.Windows.Media.ArcSegment.Point%2A> właściwości. W przykładzie określono również łuku x i y-radius (<xref:System.Windows.Media.ArcSegment.Size%2A>), kąt obrotu (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), flagę wskazującą, jak duże powinny być kąt wynikowy łuk (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>), a wartość wskazującą, w jakim kierunku łuku (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). Poniższa ilustracja przedstawia kształt utworzone przez tego przykładu.  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Bardziej złożone geometrii można utworzyć za pomocą wielu <xref:System.Windows.Media.PathFigure> obiektów w ramach <xref:System.Windows.Media.PathGeometry>.  
  
 Poniższy przykład tworzy <xref:System.Windows.Media.PathGeometry> przy użyciu dwóch <xref:System.Windows.Media.PathFigure> obiektów, z których każdy zawiera wiele <xref:System.Windows.Media.PathSegment> obiektów.  <xref:System.Windows.Media.PathFigure> z powyższego przykładu i <xref:System.Windows.Media.PathFigure> z <xref:System.Windows.Media.PolyLineSegment> i <xref:System.Windows.Media.QuadraticBezierSegment> są używane.  A <xref:System.Windows.Media.PolyLineSegment> jest zdefiniowana za pomocą tablicy punktów i <xref:System.Windows.Media.QuadraticBezierSegment> jest zdefiniowana za pomocą punktu kontrolnego i punktu końcowego. Poniższa ilustracja przedstawia kształt utworzone przez tego przykładu.  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry z wieloma wynikami  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Podobnie jak <xref:System.Windows.Media.PathGeometry> klasy <xref:System.Windows.Media.StreamGeometry> definiuje złożonych kształtu geometrycznego, który może zawierać krzywych, łuki i linii. W odróżnieniu od <xref:System.Windows.Media.PathGeometry>, zawartość <xref:System.Windows.Media.StreamGeometry> obsługuje powiązanie danych, animacji lub modyfikacji. Użyj <xref:System.Windows.Media.StreamGeometry> niezbędne, aby opisać złożone typy geometryczne, ale nie chcesz koszty obsługi powiązań danych, animacji lub modyfikacji. Ze względu na jego wydajność <xref:System.Windows.Media.StreamGeometry> klasy jest dobrym wyborem dla opisu moduły definiowania układu.  
  
 Aby uzyskać przykład, zobacz [utworzyć kształt używając StreamGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Składni znacznikowania ścieżki  
 <xref:System.Windows.Media.PathGeometry> i <xref:System.Windows.Media.StreamGeometry> typy obsługi [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] atrybutu przy użyciu specjalnej serii przenoszenia o składni i narysuj poleceń. Aby uzyskać więcej informacji, zobacz [składni znacznikowania ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Złożone geometrii  
 Obiekty geometrii złożone można tworzyć przy użyciu <xref:System.Windows.Media.GeometryGroup>, <xref:System.Windows.Media.CombinedGeometry>, lub przez wywołanie statycznego <xref:System.Windows.Media.Geometry> metoda <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
-   <xref:System.Windows.Media.CombinedGeometry> Obiektu i <xref:System.Windows.Media.Geometry.Combine%2A> metoda wykonuje operację logiczną połączyć obszar zdefiniowany przez dwa geometrii. <xref:System.Windows.Media.Geometry> obiekty, które mają obszary są odrzucane. Tylko dwa <xref:System.Windows.Media.Geometry> obiekty mogą być połączone (mimo że te dwa geometrii może być również złożone geometrii).  
  
-   <xref:System.Windows.Media.GeometryGroup> Klasy tworzy połączenie <xref:System.Windows.Media.Geometry> obiektów zawiera bez łączenia ich obszaru. Dowolną liczbę <xref:System.Windows.Media.Geometry> obiekty mogą być dodawane do <xref:System.Windows.Media.GeometryGroup>. Aby uzyskać przykład, zobacz [Utwórz kształt złożony](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md).  
  
 Ponieważ nie wykonują operację łączenia, za pomocą <xref:System.Windows.Media.GeometryGroup> obiektów zapewnia korzyści w wydajności za pośrednictwem za pomocą <xref:System.Windows.Media.CombinedGeometry> obiektów lub <xref:System.Windows.Media.Geometry.Combine%2A> metody.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Połączone Geometrie  
 Poprzedniej sekcji, o których wspomniano <xref:System.Windows.Media.CombinedGeometry> obiektu i <xref:System.Windows.Media.Geometry.Combine%2A> metoda połączyć obszar zdefiniowany przez geometrii zawierają. <xref:System.Windows.Media.GeometryCombineMode> Wyliczenie Określa, jak są połączone geometrie. Możliwe wartości parametru <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> są właściwości: <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>, i <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 W poniższym przykładzie <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowana z trybem łączenia Unii.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są definiowane jako okręgów, tego samego serwera radius, ale z przesunięciem centra o 50.  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Wyniki Unii połączyć tryb](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 W poniższym przykładzie <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowana za pomocą trybu łączenia <xref:System.Windows.Media.GeometryCombineMode.Xor>.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są definiowane jako okręgów, tego samego serwera radius, ale z przesunięciem centra o 50.  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Wyniki Xor użycia trybu łączenia](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Aby uzyskać więcej przykładów, zobacz [Utwórz kształt złożony](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md) i [tworzenie geometrii połączone](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Funkcje freezable  
 Ponieważ dziedziczy on z <xref:System.Windows.Freezable> klasy <xref:System.Windows.Media.Geometry> klasy zapewniają kilka funkcji specjalnych: <xref:System.Windows.Media.Geometry> obiekty mogą być deklarowane jako [zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md), udostępnione wśród wielu obiektów, aby poprawić jest tylko do odczytu wydajność, sklonować i wprowadzone metodą o bezpiecznych wątkach. Aby uzyskać więcej informacji na temat różnych funkcji oferowanych przez <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Inne funkcje geometrii  
 <xref:System.Windows.Media.Geometry> Klasa udostępnia także metody przydatne narzędzie, takie jak następujące:  
  
-   <xref:System.Windows.Media.Geometry.GetArea%2A> -Są pobierane obszar <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.FillContains%2A> -Określa, czy geometrii zawiera inny <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.StrokeContains%2A> -Określa, czy obrysu <xref:System.Windows.Media.Geometry> zawiera określony punkt.  
  
 Zobacz <xref:System.Windows.Media.Geometry> klasy, aby uzyskać pełną listę jego metod.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Składnia znacznikowania ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)
- [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
