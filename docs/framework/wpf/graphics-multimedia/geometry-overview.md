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
ms.openlocfilehash: f45c13e1af9bc2d1f75da11b13a2c03936b136c1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455010"
---
# <a name="geometry-overview"></a>Przegląd Geometria
W tym omówieniu opisano sposób użycia klas <xref:System.Windows.Media.Geometry> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] do opisywania kształtów. W tym temacie opisano również różnice między obiektami <xref:System.Windows.Media.Geometry> i <xref:System.Windows.Shapes.Shape> elementów.  

<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>Co to jest geometria?  
 Klasa <xref:System.Windows.Media.Geometry> i klasy, które pochodzą z niej, takie jak <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>i <xref:System.Windows.Media.CombinedGeometry>, umożliwiają opisywanie geometrii kształtu 2-D. Te opisy geometryczne mają wiele celów, takich jak Definiowanie kształtu do malowania na ekranie lub Definiowanie trafień i regionów klipów. Można nawet użyć geometrii do definiowania ścieżki animacji.  
  
 obiekty <xref:System.Windows.Media.Geometry> mogą być proste, takie jak prostokąty i okręgi lub złożone, utworzone na podstawie dwóch lub więcej obiektów geometrycznych.  Bardziej złożone geometrie można utworzyć przy użyciu klas <xref:System.Windows.Media.PathGeometry> i <xref:System.Windows.Media.StreamGeometry>, które umożliwiają opisywanie łuków i krzywych.  
  
 Ponieważ <xref:System.Windows.Media.Geometry> jest typem <xref:System.Windows.Freezable>, obiekty <xref:System.Windows.Media.Geometry> zapewniają kilka specjalnych funkcji: mogą być deklarowane jako [zasoby](../../../desktop-wpf/fundamentals/xaml-resources-define.md), współużytkowane przez wiele obiektów, przeznaczone tylko do odczytu w celu poprawy wydajności, klonowania i zabezpieczania wątków. Aby uzyskać więcej informacji o różnych funkcjach zapewnianych przez <xref:System.Windows.Freezable> obiektów, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Geometrie a Shapes  
 Klasy <xref:System.Windows.Media.Geometry> i <xref:System.Windows.Shapes.Shape> wyglądają podobnie jak w przypadku dwóch kształtów (Porównaj <xref:System.Windows.Media.EllipseGeometry> i <xref:System.Windows.Shapes.Ellipse> na przykład), ale istnieją istotne różnice.  
  
 Dla jednej klasy <xref:System.Windows.Media.Geometry> dziedziczy z klasy <xref:System.Windows.Freezable>, podczas gdy Klasa <xref:System.Windows.Shapes.Shape> dziedziczy z <xref:System.Windows.FrameworkElement>. Ponieważ są to elementy, <xref:System.Windows.Shapes.Shape> obiekty mogą same renderować i uczestniczyć w systemie układu, podczas gdy obiekty <xref:System.Windows.Media.Geometry> nie mogą.  
  
 Chociaż obiekty <xref:System.Windows.Shapes.Shape> są bardziej łatwo użyteczne niż obiekty <xref:System.Windows.Media.Geometry>, <xref:System.Windows.Media.Geometry> obiekty są bardziej uniwersalne. Gdy obiekt <xref:System.Windows.Shapes.Shape> jest używany do renderowania grafiki 2-D, obiekt <xref:System.Windows.Media.Geometry> może służyć do definiowania regionu geometrycznego dla grafiki 2-D, definiowania regionu przycinania lub definiowania regionu na potrzeby testowania trafień, na przykład.  
  
### <a name="the-path-shape"></a>Kształt ścieżki  
 Jeden <xref:System.Windows.Shapes.Shape>, Klasa <xref:System.Windows.Shapes.Path>, faktycznie używa <xref:System.Windows.Media.Geometry> do opisywania jego zawartości. Ustawiając właściwość <xref:System.Windows.Shapes.Path.Data%2A> <xref:System.Windows.Shapes.Path> za pomocą <xref:System.Windows.Media.Geometry> i ustawiając jej właściwości <xref:System.Windows.Shapes.Shape.Fill%2A> i <xref:System.Windows.Shapes.Shape.Stroke%2A>, można renderować <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Wspólne właściwości, które mają geometrię  
 Powyższe sekcje wymienione w tym, że obiekty geometryczne mogą być używane z innymi obiektami do różnych celów, takich jak rysowanie kształtów, animowanie i przycinanie. W poniższej tabeli wymieniono kilka klas, które mają właściwości, które pobierają <xref:System.Windows.Media.Geometry> obiektu.  
  
|Typ|Właściwość|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Proste typy geometrii  
 Klasa bazowa dla wszystkich geometrie jest klasą abstrakcyjną <xref:System.Windows.Media.Geometry>.  Klasy, które pochodzą z klasy <xref:System.Windows.Media.Geometry>, mogą być w przybliżeniu pogrupowane w trzy kategorie: proste geometrie, Path geometrie i Composite geometrie.  
  
 Proste klasy geometrii obejmują <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>i <xref:System.Windows.Media.EllipseGeometry> i są używane do tworzenia podstawowych kształtów geometrycznych, takich jak linie, prostokąty i okręgi.  
  
- <xref:System.Windows.Media.LineGeometry> jest definiowana przez określenie punktu początkowego wiersza i punktu końcowego.  
  
- <xref:System.Windows.Media.RectangleGeometry> jest definiowana przy użyciu struktury <xref:System.Windows.Rect>, która określa jego położenie względne oraz jego wysokość i szerokość. Prostokąt zaokrąglony można utworzyć przez ustawienie właściwości <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>.  
  
- <xref:System.Windows.Media.EllipseGeometry> jest definiowana przez punkt centralny, x-RADIUS i y-RADIUS.  W poniższych przykładach pokazano, jak utworzyć prostą geometrie do renderowania i przycinania.  
  
 Te same kształty, a także bardziej złożone kształty, można utworzyć przy użyciu <xref:System.Windows.Media.PathGeometry> lub łącząc obiekty geometryczne ze sobą, ale te klasy zapewniają prostszy sposób tworzenia podstawowych kształtów geometrycznych.  
  
 Poniższy przykład pokazuje, jak utworzyć i renderować <xref:System.Windows.Media.LineGeometry>.  Jak wspomniano wcześniej, obiekt <xref:System.Windows.Media.Geometry> nie może narysować samego siebie, więc przykład używa kształtu <xref:System.Windows.Shapes.Path> do renderowania wiersza.  Ponieważ linia nie ma obszaru, ustawienie właściwości <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Path> nie będzie miało żadnego efektu; Zamiast tego są określone tylko właściwości <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>. Na poniższej ilustracji przedstawiono dane wyjściowe z przykładu.  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
LineGeometry od (10, 20) do (100 130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 W następnym przykładzie pokazano, jak utworzyć i renderować <xref:System.Windows.Media.EllipseGeometry>.  Przykłady ustawiają <xref:System.Windows.Media.EllipseGeometry.Center%2A> <xref:System.Windows.Media.EllipseGeometry> jest ustawiony na `50,50`, a wartości x-RADIUS i y-RADIUS są ustawiane na `50`, co tworzy okrąg o średnicy 100.  Wnętrze elipsy jest rysowane przez przypisanie wartości do właściwości Fill elementu Path, w tym przypadku <xref:System.Windows.Media.Brushes.Gold%2A>. Na poniższej ilustracji przedstawiono dane wyjściowe z przykładu.  
  
 ![EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
EllipseGeometry narysowana o (50, 50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 Poniższy przykład pokazuje, jak utworzyć i renderować <xref:System.Windows.Media.RectangleGeometry>.  Pozycja i wymiary prostokąta są definiowane przez strukturę <xref:System.Windows.Rect>. Pozycja jest `50,50`, a wysokość i szerokość są `25`, które tworzą kwadrat. Na poniższej ilustracji przedstawiono dane wyjściowe z przykładu.  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry narysowana o 50, 50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.EllipseGeometry> jako regionu klipu obrazu.  Obiekt <xref:System.Windows.Controls.Image> jest zdefiniowany za pomocą <xref:System.Windows.FrameworkElement.Width%2A> 200 i <xref:System.Windows.FrameworkElement.Height%2A> 150.  <xref:System.Windows.Media.EllipseGeometry> z wartością <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> 100, <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> wartością 75 i <xref:System.Windows.Media.EllipseGeometry.Center%2A> wartością 100, 75 jest ustawiona na Właściwość <xref:System.Windows.UIElement.Clip%2A> obrazu.  Zostanie wyświetlona tylko część obrazu znajdująca się w obszarze elipsy. Na poniższej ilustracji przedstawiono dane wyjściowe z przykładu.  
  
 ![Obraz z przycinaniem i bez](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
EllipseGeometry używany do wycinania kontrolki obrazu  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Geometrie ścieżki  
 Klasa <xref:System.Windows.Media.PathGeometry> i jej lekki odpowiednik, Klasa <xref:System.Windows.Media.StreamGeometry>, udostępniają metody opisujące wiele złożonych liczb składających się z łuków, krzywych i linii.  
  
 W przypadku <xref:System.Windows.Media.PathGeometry> jest kolekcją obiektów <xref:System.Windows.Media.PathFigure>, dlatego nazwane, ponieważ każda ilustracja opisuje dyskretny kształt w <xref:System.Windows.Media.PathGeometry>. Każda <xref:System.Windows.Media.PathFigure> składa się z jednego lub kilku obiektów <xref:System.Windows.Media.PathSegment>, z których każdy opisuje segment rysunku.  
  
 Istnieje wiele typów segmentów.  
  
|Typ segmentu|Opis|Przykład|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Tworzy Łuk eliptyczny między dwoma punktami.|[Utwórz Łuk eliptyczny](how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Tworzy zaokrągloną krzywą Beziera między dwoma punktami.|[Utworzenie krzywej Beziera w postaci sześciennej](how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Tworzy linię między dwoma punktami.|[Tworzenie obiektu LineSegment w elemencie PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Tworzy serię wielowartościowych krzywych Beziera.|Zobacz stronę typu <xref:System.Windows.Media.PolyBezierSegment>.|  
|<xref:System.Windows.Media.PolyLineSegment>|Tworzy serię wierszy.|Zobacz stronę typu <xref:System.Windows.Media.PolyLineSegment>.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Tworzy serię krzywych Beziera kwadratowego.|Zobacz stronę <xref:System.Windows.Media.PolyQuadraticBezierSegment>.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Tworzy krzywą Beziera kwadratu.|[Utwórz krzywą Beziera kwadratowego](how-to-create-a-quadratic-bezier-curve.md).|  
  
 Segmenty w <xref:System.Windows.Media.PathFigure> są łączone w jeden kształt geometryczny z punktem końcowym każdego segmentu w punkcie początkowym następnego segmentu. Właściwość <xref:System.Windows.Media.PathFigure.StartPoint%2A> <xref:System.Windows.Media.PathFigure> określa punkt, z którego jest rysowany pierwszy segment. Każdy kolejny segment zaczyna się od punktu końcowego poprzedniego segmentu. Na przykład pionowa linia z `10,50` do `10,150` może być zdefiniowana przez ustawienie właściwości <xref:System.Windows.Media.PathFigure.StartPoint%2A> na `10,50` i utworzenie <xref:System.Windows.Media.LineSegment> z ustawieniem <xref:System.Windows.Media.LineSegment.Point%2A> właściwości `10,150`.  
  
 Poniższy przykład tworzy prosty <xref:System.Windows.Media.PathGeometry> składający się z pojedynczego <xref:System.Windows.Media.PathFigure> z <xref:System.Windows.Media.LineSegment> i wyświetla go przy użyciu elementu <xref:System.Windows.Shapes.Path>. <xref:System.Windows.Media.PathFigure.StartPoint%2A> obiektu <xref:System.Windows.Media.PathFigure> jest ustawiona na `10,20` i <xref:System.Windows.Media.LineSegment> jest definiowana z punktem końcowym `100,130`. Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.PathGeometry> utworzone w tym przykładzie.  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
PathGeometry zawierający pojedynczy LineSegment  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Jest to bardzo zróżnicowane w tym przykładzie z powyższym przykładem <xref:System.Windows.Media.LineGeometry>.  Składnia używana dla <xref:System.Windows.Media.PathGeometry> jest znacznie bardziej pełna niż użyta w przypadku prostej <xref:System.Windows.Media.LineGeometry>. w takim przypadku może być wygodniejsze użycie klasy <xref:System.Windows.Media.LineGeometry>, ale Pełna składnia <xref:System.Windows.Media.PathGeometry> zezwala na bardzo Intricate i złożone regiony geometryczne.  
  
 Bardziej złożone geometrie można utworzyć przy użyciu kombinacji obiektów <xref:System.Windows.Media.PathSegment>.  
  
 W następnym przykładzie zastosowano <xref:System.Windows.Media.BezierSegment>, <xref:System.Windows.Media.LineSegment>i <xref:System.Windows.Media.ArcSegment> do utworzenia kształtu. W przykładzie najpierw tworzona jest dwukierunkowa krzywa Beziera, definiując cztery punkty: punkt początkowy, który jest punktem końcowym poprzedniego segmentu, punkt końcowy (<xref:System.Windows.Media.BezierSegment.Point3%2A>) i dwa punkty kontrolne (<xref:System.Windows.Media.BezierSegment.Point1%2A> i <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Dwa punkty kontrolne zakrzywionej krzywej Beziera zachowują się jak magnets, co pociąga za sobą, że w przeciwnym razie będzie to linia prosta prowadząca do siebie. Pierwszy punkt kontrolny, <xref:System.Windows.Media.BezierSegment.Point1%2A>, ma wpływ na początkową część krzywej; drugi punkt kontrolny, <xref:System.Windows.Media.BezierSegment.Point2%2A>, wpływa na końcową część krzywej.  
  
 Przykład dodaje <xref:System.Windows.Media.LineSegment>, który jest rysowany między punktem końcowym poprzedniej <xref:System.Windows.Media.BezierSegment>, który poprzedza do punktu określonego przez jego właściwość <xref:System.Windows.Media.LineSegment>.  
  
 Przykład dodaje <xref:System.Windows.Media.ArcSegment>, który jest rysowany od punktu końcowego poprzedniego <xref:System.Windows.Media.LineSegment> do punktu określonego przez jego właściwość <xref:System.Windows.Media.ArcSegment.Point%2A>. W przykładzie określono również wartość x-i y-promieniowy łuku (<xref:System.Windows.Media.ArcSegment.Size%2A>), kąt obrotu (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), flagę wskazującą, jak duży kąt powstającego łuku powinien być (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>), i wartości wskazujące kierunek rysowania łuku (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). Na poniższej ilustracji przedstawiono kształt utworzony w tym przykładzie.  
  
 ![PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Jeszcze bardziej złożone geometrie można utworzyć przy użyciu wielu obiektów <xref:System.Windows.Media.PathFigure> w <xref:System.Windows.Media.PathGeometry>.  
  
 Poniższy przykład tworzy <xref:System.Windows.Media.PathGeometry> z dwoma obiektami <xref:System.Windows.Media.PathFigure>, z których każdy zawiera wiele obiektów <xref:System.Windows.Media.PathSegment>.  <xref:System.Windows.Media.PathFigure> z powyższego przykładu i <xref:System.Windows.Media.PathFigure> z <xref:System.Windows.Media.PolyLineSegment> i <xref:System.Windows.Media.QuadraticBezierSegment> są używane.  <xref:System.Windows.Media.PolyLineSegment> jest zdefiniowana z tablicą punktów, a <xref:System.Windows.Media.QuadraticBezierSegment> jest definiowana z punktem kontrolnym i punktem końcowym. Na poniższej ilustracji przedstawiono kształt utworzony w tym przykładzie.  
  
 ![PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry z wieloma ilustracjami  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Podobnie jak w przypadku klasy <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.StreamGeometry> definiuje złożony kształt geometryczny, który może zawierać krzywe, łuki i linie. W przeciwieństwie do <xref:System.Windows.Media.PathGeometry>, zawartość <xref:System.Windows.Media.StreamGeometry> nie obsługuje powiązań danych, animacji ani modyfikacji. Użyj <xref:System.Windows.Media.StreamGeometry>, gdy zachodzi potrzeba opisania złożonej geometrii, ale nie chcesz obciążać powiązania danych, animacji ani modyfikacji. Ze względu na jego wydajność Klasa <xref:System.Windows.Media.StreamGeometry> jest dobrym wyborem do opisywania modułów definiowania układu.  
  
 Aby zapoznać się z przykładem, zobacz [Tworzenie kształtu przy użyciu StreamGeometry](how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Składni znacznikowania ścieżki  
 Typy <xref:System.Windows.Media.PathGeometry> i <xref:System.Windows.Media.StreamGeometry> obsługują składnię atrybutów [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] za pomocą specjalnej serii poleceń Move i Draw. Aby uzyskać więcej informacji, zobacz [Path Markup Syntax](path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Geometrie złożony  
 Złożone obiekty geometryczne mogą być tworzone przy użyciu <xref:System.Windows.Media.GeometryGroup>, <xref:System.Windows.Media.CombinedGeometry>lub przez wywołanie metody statycznej <xref:System.Windows.Media.Geometry> <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
- Obiekt <xref:System.Windows.Media.CombinedGeometry> i Metoda <xref:System.Windows.Media.Geometry.Combine%2A> wykonuje operację logiczną, aby połączyć obszar zdefiniowany przez dwa geometrie. obiekty <xref:System.Windows.Media.Geometry>, które nie mają obszaru są odrzucane. Można łączyć tylko dwa obiekty <xref:System.Windows.Media.Geometry> (Chociaż te dwie geometrie mogą być również złożonymi geometrie).  
  
- Klasa <xref:System.Windows.Media.GeometryGroup> tworzy Amalgamation obiektów <xref:System.Windows.Media.Geometry>, które zawiera, bez łączenia ich obszaru. Do <xref:System.Windows.Media.GeometryGroup>można dodać dowolną liczbę obiektów <xref:System.Windows.Media.Geometry>. Aby zapoznać się z przykładem, zobacz [Tworzenie kształtu złożonego](how-to-create-a-composite-shape.md).  
  
 Ponieważ nie wykonują operacji łączenia, korzystanie z <xref:System.Windows.Media.GeometryGroup> obiektów zapewnia wydajność w porównaniu z użyciem obiektów <xref:System.Windows.Media.CombinedGeometry> lub metody <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Połączone geometrie  
 W poprzedniej sekcji wymienionej w obiekcie <xref:System.Windows.Media.CombinedGeometry> i metody <xref:System.Windows.Media.Geometry.Combine%2A> łączą obszar zdefiniowany przez geometrie, które zawierają. Wyliczenie <xref:System.Windows.Media.GeometryCombineMode> określa, w jaki sposób są połączone geometrie. Możliwe wartości właściwości <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> to: <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>i <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 W poniższym przykładzie <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany przy użyciu trybu łączenia Unii.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>, jak i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako koła tego samego promienia, ale z przesunięciami centrów do 50.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Wyniki trybu łączenia z Unią](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 W poniższym przykładzie <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowana z trybem łączenia <xref:System.Windows.Media.GeometryCombineMode.Xor>.  Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>, jak i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako koła tego samego promienia, ale z przesunięciami centrów do 50.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Wyniki trybu łączenia XOR](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Aby uzyskać więcej przykładów, zobacz [Tworzenie złożonego kształtu](how-to-create-a-composite-shape.md) i [Tworzenie połączonej geometrii](how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Funkcje freezable  
 Ponieważ dziedziczy on z klasy <xref:System.Windows.Freezable>, Klasa <xref:System.Windows.Media.Geometry> udostępnia kilka specjalnych funkcji: obiekty <xref:System.Windows.Media.Geometry> mogą być deklarowane jako [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md), współdzielone przez wiele obiektów, wykonywane tylko do odczytu w celu zwiększenia wydajności, sklonowane i wykonane bezpieczny wątkowo. Aby uzyskać więcej informacji o różnych funkcjach zapewnianych przez <xref:System.Windows.Freezable> obiektów, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Inne funkcje geometrii  
 Klasa <xref:System.Windows.Media.Geometry> udostępnia również przydatne metody narzędziowe, takie jak:  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A> — Pobiera obszar <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A> — określa, czy geometria zawiera inną <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A> — określa, czy pociągnięcia <xref:System.Windows.Media.Geometry> zawiera określony punkt.  
  
 Zapoznaj się z klasą <xref:System.Windows.Media.Geometry>, aby zapoznać się z pełną listą metod.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Składnia znacznikowania ścieżki](path-markup-syntax.md)
- [Tematy z instrukcjami](geometries-how-to-topics.md)
- [Animacja — przegląd](animation-overview.md)
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](shapes-and-basic-drawing-in-wpf-overview.md)
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
