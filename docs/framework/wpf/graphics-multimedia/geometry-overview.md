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
ms.openlocfilehash: ff42e59edd9d98b0b52dc3bdd3ace0c35df60878
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112378"
---
# <a name="geometry-overview"></a>Przegląd Geometria
W tym przeglądzie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> opisano sposób używania klas do opisywania kształtów. W tym temacie kontrastuje <xref:System.Windows.Media.Geometry> również <xref:System.Windows.Shapes.Shape> różnice między obiektami i elementami.  

<a name="wcpsdk_graphics_geometry_introduction"></a>
## <a name="what-is-a-geometry"></a>Co to jest geometria?  
 Klasa <xref:System.Windows.Media.Geometry> i klasy, które się z <xref:System.Windows.Media.EllipseGeometry>niej <xref:System.Windows.Media.PathGeometry>wywodzą, takie jak , i <xref:System.Windows.Media.CombinedGeometry>, umożliwiają opisanie geometrii kształtu 2D. Te geometryczne opisy mają wiele zastosowań, takich jak definiowanie kształtu do malowania na ekranie lub definiowanie regionów testu trafień i klipów. Można nawet użyć geometrii do zdefiniowania ścieżki animacji.  
  
 <xref:System.Windows.Media.Geometry>obiekty mogą być proste, takie jak prostokąty i okręgi, lub kompozytowe, utworzone z dwóch lub więcej obiektów geometrii.  Bardziej złożone geometrie można tworzyć <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.StreamGeometry> przy użyciu klas i, które umożliwiają opisywanie łuków i krzywych.  
  
 Ponieważ <xref:System.Windows.Media.Geometry> a jest <xref:System.Windows.Freezable>typem , <xref:System.Windows.Media.Geometry> obiekty zapewniają kilka specjalnych funkcji: mogą być zadeklarowane jako [zasoby,](../../../desktop-wpf/fundamentals/xaml-resources-define.md)współużytkowane przez wiele obiektów, wykonane tylko do odczytu w celu zwiększenia wydajności, sklonowane i wykonane wątku bezpieczne. Aby uzyskać więcej informacji na <xref:System.Windows.Freezable> temat różnych funkcji udostępnianych przez obiekty, zobacz [Omówienie obiektów freezable](../advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>
## <a name="geometries-vs-shapes"></a>Geometrie a kształty  
 Klasy <xref:System.Windows.Media.Geometry> <xref:System.Windows.Shapes.Shape> i klasy wydają się podobne, ponieważ oba <xref:System.Windows.Media.EllipseGeometry> opisują kształty 2D (porównaj i <xref:System.Windows.Shapes.Ellipse> na przykład), ale istnieją istotne różnice.  
  
 Po pierwsze, <xref:System.Windows.Media.Geometry> klasa dziedziczy <xref:System.Windows.Freezable> z <xref:System.Windows.Shapes.Shape> klasy, podczas <xref:System.Windows.FrameworkElement>gdy klasa dziedziczy z . Ponieważ są one <xref:System.Windows.Shapes.Shape> elementami, obiekty mogą renderować <xref:System.Windows.Media.Geometry> się i uczestniczyć w systemie układu, podczas gdy obiekty nie mogą.  
  
 Chociaż <xref:System.Windows.Shapes.Shape> obiekty są łatwiej dostępne <xref:System.Windows.Media.Geometry> do <xref:System.Windows.Media.Geometry> użytku niż obiekty, obiekty są bardziej wszechstronne. Podczas <xref:System.Windows.Shapes.Shape> gdy obiekt jest używany do renderowania grafiki 2D, <xref:System.Windows.Media.Geometry> obiekt może służyć do definiowania regionu geometrycznego dla grafiki 2D, definiowania regionu do przycinania lub definiowania regionu do testowania trafień, na przykład.  
  
### <a name="the-path-shape"></a>Kształt Ścieżka  
 Jeden <xref:System.Windows.Shapes.Shape>, <xref:System.Windows.Shapes.Path> klasa, faktycznie <xref:System.Windows.Media.Geometry> używa a do opisania jego zawartości. <xref:System.Windows.Shapes.Path.Data%2A> Ustawiając właściwość <xref:System.Windows.Shapes.Path> z <xref:System.Windows.Media.Geometry> a i <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Shape.Stroke%2A> ustawiając jego i <xref:System.Windows.Media.Geometry>właściwości, można renderować program .  
  
<a name="commonproperties"></a>
## <a name="common-properties-that-take-a-geometry"></a>Typowe właściwości, które przyjmują geometrię  
 W poprzednich sekcjach wspomniano, że obiekty Geometria mogą być używane z innymi obiektami do różnych celów, takich jak rysowanie kształtów, animowanie i przycinanie. W poniższej tabeli wymieniono kilka <xref:System.Windows.Media.Geometry> klas, które mają właściwości, które zajmują obiekt.  
  
|Typ|Właściwość|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>
## <a name="simple-geometry-types"></a>Proste typy geometrii  
 Klasą bazową dla wszystkich geometrii jest klasa <xref:System.Windows.Media.Geometry>abstrakcyjna .  Klasy, które pochodzą <xref:System.Windows.Media.Geometry> z klasy mogą być z grubsza pogrupowane w trzy kategorie: proste geometrie, geometrie ścieżki i geometrie kompozytowe.  
  
 Proste klasy geometrii <xref:System.Windows.Media.RectangleGeometry>obejmują <xref:System.Windows.Media.EllipseGeometry> <xref:System.Windows.Media.LineGeometry>i są używane do tworzenia podstawowych kształtów geometrycznych, takich jak linie, prostokąty i okręgi.  
  
- A <xref:System.Windows.Media.LineGeometry> jest definiowany przez określenie punktu początkowego linii i punktu końcowego.  
  
- A <xref:System.Windows.Media.RectangleGeometry> jest definiowany za pomocą struktury określającej <xref:System.Windows.Rect> jego względne położenie oraz wysokość i szerokość. Zaokrąglony prostokąt można <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> utworzyć, <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> ustawiając właściwości i.  
  
- An <xref:System.Windows.Media.EllipseGeometry> jest definiowany przez punkt środkowy, promień x i promień y.  Poniższe przykłady pokazują, jak utworzyć proste geometrie do renderowania i przycinania.  
  
 Te same kształty, jak również bardziej złożone kształty, mogą być tworzone przy użyciu <xref:System.Windows.Media.PathGeometry> lub przez połączenie obiektów geometrii razem, ale te klasy zapewniają prostszy sposób tworzenia tych podstawowych kształtów geometrycznych.  
  
 W poniższym przykładzie pokazano, <xref:System.Windows.Media.LineGeometry>jak utworzyć i renderować plik .  Jak wspomniano wcześniej, <xref:System.Windows.Media.Geometry> obiekt nie może narysować się, <xref:System.Windows.Shapes.Path> więc w przykładzie używa kształtu do renderowania linii.  Ponieważ wiersz nie ma obszaru, <xref:System.Windows.Shapes.Shape.Fill%2A> ustawienie <xref:System.Windows.Shapes.Path> właściwości nie miałoby wpływu; zamiast tego określono <xref:System.Windows.Shapes.Shape.Stroke%2A> <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> tylko właściwości i. Na poniższej ilustracji przedstawiono dane wyjściowe z przykładu.  
  
 ![LineGeometria](./media/graphicsmm-line.gif "graphicsmm_line")  
LineGeometria pobierana od (10,20) do (100 130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 W następnym przykładzie pokazano, <xref:System.Windows.Media.EllipseGeometry>jak utworzyć i renderować plik .  Przykłady <xref:System.Windows.Media.EllipseGeometry.Center%2A> ustawiają <xref:System.Windows.Media.EllipseGeometry> jest ustawiona `50,50` na punkt i x-promień i y-promień są ustawione na `50`, który tworzy okrąg o średnicy 100.  Wnętrze elipsy jest malowane przez przypisanie wartości do Właściwości Wypełnianie elementu <xref:System.Windows.Media.Brushes.Gold%2A>Path, w tym przypadku . Na poniższej ilustracji przedstawiono dane wyjściowe z przykładu.  
  
 ![ElipsaGeometria](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
ElipsaGeometria narysowana w (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 W poniższym przykładzie pokazano, <xref:System.Windows.Media.RectangleGeometry>jak utworzyć i renderować plik .  Położenie i wymiary prostokąta są definiowane <xref:System.Windows.Rect> przez strukturę. Położenie jest `50,50` i wysokość i `25`szerokość są zarówno , który tworzy kwadrat. Na poniższej ilustracji przedstawiono dane wyjściowe z przykładu.  
  
 ![RectangleGeometria](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry narysowana na 50,50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 W poniższym <xref:System.Windows.Media.EllipseGeometry> przykładzie pokazano, jak używać jako regionu klipu dla obrazu.  Obiekt <xref:System.Windows.Controls.Image> jest zdefiniowany <xref:System.Windows.FrameworkElement.Width%2A> z 200 <xref:System.Windows.FrameworkElement.Height%2A> i a 150.  Wartość <xref:System.Windows.Media.EllipseGeometry> <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> 100, <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> wartość 75 i <xref:System.Windows.Media.EllipseGeometry.Center%2A> wartość 100,75 jest ustawiona na <xref:System.Windows.UIElement.Clip%2A> właściwość obrazu.  Zostanie wyświetlona tylko część obrazu, która znajduje się w obszarze elipsy. Na poniższej ilustracji przedstawiono dane wyjściowe z przykładu.  
  
 ![Obraz z przycinaniem i bez niego](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Wiązypsgeometria używana do przycinania kontrolki obrazu  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>
## <a name="path-geometries"></a>Geometrie ścieżki  
 Klasa <xref:System.Windows.Media.PathGeometry> i jej lekki <xref:System.Windows.Media.StreamGeometry> odpowiednik, klasa, zapewniają środki do opisania wielu złożonych postaci składających się z łuków, krzywych i linii.  
  
 Sercem <xref:System.Windows.Media.PathGeometry> a jest zbiór <xref:System.Windows.Media.PathFigure> obiektów, tak nazwany, ponieważ każda postać opisuje <xref:System.Windows.Media.PathGeometry>dyskretny kształt w . Każdy <xref:System.Windows.Media.PathFigure> z nich składa się <xref:System.Windows.Media.PathSegment> z jednego lub więcej obiektów, z których każdy opisuje segment figury.  
  
 Istnieje wiele typów segmentów.  
  
|Typ segmentu|Opis|Przykład|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Tworzy łuk eliptyczny między dwoma punktami.|[Utwórz łuk eliptyczny](how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Tworzy krzywą beziera sześciennego między dwoma punktami.|[Utwórz krzywą beziera sześciennego](how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Tworzy linię między dwoma punktami.|[Tworzenie obiektu LineSegment w elemencie PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Tworzy serię sześciennych krzywych Beziera.|Zobacz <xref:System.Windows.Media.PolyBezierSegment> stronę tekstową.|  
|<xref:System.Windows.Media.PolyLineSegment>|Tworzy serię wierszy.|Zobacz <xref:System.Windows.Media.PolyLineSegment> stronę tekstową.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Tworzy serię kwadratowych krzywych Beziera.|Zobacz <xref:System.Windows.Media.PolyQuadraticBezierSegment> stronę.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Tworzy kwadratową krzywą Beziera.|[Utwórz krzywą beziera kwadratowego](how-to-create-a-quadratic-bezier-curve.md).|  
  
 Segmenty w <xref:System.Windows.Media.PathFigure> obrębie a są łączone w jeden kształt geometryczny, a punkt końcowy każdego segmentu jest punktem początkowym następnego segmentu. Właściwość <xref:System.Windows.Media.PathFigure.StartPoint%2A> a <xref:System.Windows.Media.PathFigure> określa punkt, z którego jest rysowany pierwszy segment. Każdy kolejny segment rozpoczyna się w punkcie końcowym poprzedniego segmentu. Na przykład pionową `10,50` linię `10,150` od do można <xref:System.Windows.Media.PathFigure.StartPoint%2A> zdefiniować, `10,50` ustawiając <xref:System.Windows.Media.LineSegment.Point%2A> właściwość i tworząc z ustawieniem `10,150` <xref:System.Windows.Media.LineSegment> właściwości .  
  
 Poniższy przykład tworzy <xref:System.Windows.Media.PathGeometry> prosty składa <xref:System.Windows.Media.PathFigure> się <xref:System.Windows.Media.LineSegment> z jednego z <xref:System.Windows.Shapes.Path> a i wyświetla go przy użyciu elementu. Obiekt <xref:System.Windows.Media.PathFigure> <xref:System.Windows.Media.PathFigure.StartPoint%2A> jest ustawiony i `10,20` a <xref:System.Windows.Media.LineSegment> jest zdefiniowany z `100,130`punktem końcowym . Na poniższej <xref:System.Windows.Media.PathGeometry> ilustracji przedstawiono utworzone w tym przykładzie.  
  
 ![LineGeometria](./media/graphicsmm-line.gif "graphicsmm_line")  
PathGeometry, który zawiera jeden LineSegment  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Warto porównać ten przykład z <xref:System.Windows.Media.LineGeometry> poprzednim przykładem.  Składnia używana dla <xref:System.Windows.Media.PathGeometry> a jest znacznie bardziej szczegółowa niż <xref:System.Windows.Media.LineGeometry>używana dla prostego , i <xref:System.Windows.Media.LineGeometry> może mieć większy sens, aby użyć klasy <xref:System.Windows.Media.PathGeometry> w tym przypadku, ale składnia pełne pozwala na bardzo skomplikowanych i złożonych regionów geometrycznych.  
  
 Bardziej złożone geometrie można tworzyć za <xref:System.Windows.Media.PathSegment> pomocą kombinacji obiektów.  
  
 W następnym przykładzie <xref:System.Windows.Media.BezierSegment>użyto kształtu , a <xref:System.Windows.Media.LineSegment>i do utworzenia. <xref:System.Windows.Media.ArcSegment> Przykład najpierw tworzy krzywą beziera sześciennego polega na zdefiniowaniu czterech punktów: punktu początkowego, który jest punktem końcowym poprzedniego segmentu, punktu końcowego (<xref:System.Windows.Media.BezierSegment.Point3%2A>i dwóch punktów kontrolnych (<xref:System.Windows.Media.BezierSegment.Point1%2A> i <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Dwa punkty kontrolne sześciennej krzywej Beziera zachowują się jak magnesy, przyciągając części tego, co w przeciwnym razie byłoby linią prostą w kierunku siebie, tworząc krzywą. Pierwszy punkt kontrolny <xref:System.Windows.Media.BezierSegment.Point1%2A>wpływa na początkową część krzywej; drugi punkt kontrolny <xref:System.Windows.Media.BezierSegment.Point2%2A>wpływa na końcową część krzywej.  
  
 W przykładzie <xref:System.Windows.Media.LineSegment>następnie dodaje , który jest rysowany <xref:System.Windows.Media.BezierSegment> między punktem końcowym poprzedniego, <xref:System.Windows.Media.LineSegment> który poprzedzał go do punktu określonego przez jego właściwości.  
  
 W przykładzie <xref:System.Windows.Media.ArcSegment>następnie dodaje , który jest rysowany <xref:System.Windows.Media.LineSegment> od punktu końcowego poprzedniego do punktu określonego przez jego <xref:System.Windows.Media.ArcSegment.Point%2A> właściwości. W przykładzie określono również kąt x- i y-radiu<xref:System.Windows.Media.ArcSegment.Size%2A>łuku<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>( ), kąt obrotu ( ), flagę wskazującą, jak duży powinien być kąt łuku wynikowego (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>) oraz wartość wskazującą, w którym kierunku łuk jest rysowany (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). Na poniższej ilustracji przedstawiono kształt utworzony w tym przykładzie.  
  
 ![A PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
A PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Jeszcze bardziej złożone geometrie można <xref:System.Windows.Media.PathFigure> tworzyć przy <xref:System.Windows.Media.PathGeometry>użyciu wielu obiektów w obrębie programu .  
  
 Poniższy przykład <xref:System.Windows.Media.PathGeometry> tworzy <xref:System.Windows.Media.PathFigure> z dwoma obiektami, <xref:System.Windows.Media.PathSegment> z których każdy zawiera wiele obiektów.  Z <xref:System.Windows.Media.PathFigure> powyższego przykładu <xref:System.Windows.Media.PathFigure> i <xref:System.Windows.Media.PolyLineSegment> z <xref:System.Windows.Media.QuadraticBezierSegment> a i a są używane.  A <xref:System.Windows.Media.PolyLineSegment> jest zdefiniowany za pomocą <xref:System.Windows.Media.QuadraticBezierSegment> tablicy punktów i jest zdefiniowany za pomocą punktu kontrolnego i punktu końcowego. Na poniższej ilustracji przedstawiono kształt utworzony w tym przykładzie.  
  
 ![A PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry z wieloma cyframi  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Podobnie <xref:System.Windows.Media.PathGeometry> jak klasa, a <xref:System.Windows.Media.StreamGeometry> definiuje złożony kształt geometryczny, który może zawierać krzywe, łuki i linie. W <xref:System.Windows.Media.PathGeometry>przeciwieństwie do , <xref:System.Windows.Media.StreamGeometry> zawartość nie obsługuje powiązania danych, animacji lub modyfikacji. <xref:System.Windows.Media.StreamGeometry> Użyj, gdy trzeba opisać złożoną geometrię, ale nie chcesz obciążenie obsługi powiązania danych, animacji lub modyfikacji. Ze względu na swoją <xref:System.Windows.Media.StreamGeometry> wydajność, klasa jest dobrym wyborem do opisywania adorners.  
  
 Na przykład zobacz [Tworzenie kształtu za pomocą streamgeometry .](how-to-create-a-shape-using-a-streamgeometry.md)  
  
### <a name="path-markup-syntax"></a>Składni znacznikowania ścieżki  
 <xref:System.Windows.Media.PathGeometry> Typy <xref:System.Windows.Media.StreamGeometry> i [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] typy obsługują składnię atrybutu przy użyciu specjalnej serii poleceń przenoszenia i rysowania. Aby uzyskać więcej informacji, zobacz [Składnia znaczników ścieżki](path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>
## <a name="composite-geometries"></a>Geometrie kompozytowe  
 <xref:System.Windows.Media.GeometryGroup>Obiekty geometrii złożonej można tworzyć <xref:System.Windows.Media.CombinedGeometry>za pomocą , <xref:System.Windows.Media.Geometry> a <xref:System.Windows.Media.Geometry.Combine%2A>lub wywołując metodę statyczną.  
  
- Obiekt <xref:System.Windows.Media.CombinedGeometry> i <xref:System.Windows.Media.Geometry.Combine%2A> metoda wykonuje operację logiczną, aby połączyć obszar zdefiniowany przez dwie geometrie. <xref:System.Windows.Media.Geometry>obiekty, które nie mają obszaru, są odrzucane. Można <xref:System.Windows.Media.Geometry> połączyć tylko dwa obiekty (chociaż te dwie geometrie mogą być również geometriami kompozytowymi).  
  
- Klasa <xref:System.Windows.Media.GeometryGroup> tworzy połączenie obiektów, <xref:System.Windows.Media.Geometry> które zawiera bez łączenia ich obszaru. <xref:System.Windows.Media.Geometry> Do <xref:System.Windows.Media.GeometryGroup>pliku . Na przykład zobacz [Tworzenie kształtu złożonego](how-to-create-a-composite-shape.md).  
  
 Ponieważ nie wykonują one operacji <xref:System.Windows.Media.GeometryGroup> kombinowania, przy <xref:System.Windows.Media.CombinedGeometry> użyciu <xref:System.Windows.Media.Geometry.Combine%2A> obiektów zapewnia korzyści wydajności przy użyciu obiektów lub metody.  
  
<a name="combindgeometriessection"></a>
## <a name="combined-geometries"></a>Połączone geometrie  
 W poprzedniej sekcji wspomniano <xref:System.Windows.Media.CombinedGeometry> o <xref:System.Windows.Media.Geometry.Combine%2A> obiekcie, a metoda łączy obszar zdefiniowany przez zawarte w nich geometrie. Wyliczenie <xref:System.Windows.Media.GeometryCombineMode> określa sposób łączenia geometrii. Możliwe wartości <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> dla właściwości <xref:System.Windows.Media.GeometryCombineMode.Union>to: <xref:System.Windows.Media.GeometryCombineMode.Exclude>, <xref:System.Windows.Media.GeometryCombineMode.Xor> <xref:System.Windows.Media.GeometryCombineMode.Intersect>, , i .  
  
 W poniższym przykładzie a <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany za pomocą trybu łączenia Unii.  Oba <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi o tym samym promieniu, ale z środkami przesuniętymi o 50.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Wyniki unijnego trybu łączenia](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 W poniższym przykładzie a <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowany z trybem łączenia . <xref:System.Windows.Media.GeometryCombineMode.Xor>  Oba <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są zdefiniowane jako okręgi o tym samym promieniu, ale z środkami przesuniętymi o 50.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Wyniki trybu kombajnu Xor](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Aby uzyskać dodatkowe przykłady, zobacz [Tworzenie kształtu złożonego](how-to-create-a-composite-shape.md) i [Tworzenie połączonej geometrii](how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Freezable Funkcje  
 Ponieważ dziedziczy z <xref:System.Windows.Freezable> klasy, <xref:System.Windows.Media.Geometry> klasa zapewnia kilka <xref:System.Windows.Media.Geometry> funkcji specjalnych: obiekty mogą być zadeklarowane jako [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md), współużytkowane przez wiele obiektów, wykonane tylko do odczytu w celu zwiększenia wydajności, sklonowane i wykonane wątku bezpieczne. Aby uzyskać więcej informacji na <xref:System.Windows.Freezable> temat różnych funkcji udostępnianych przez obiekty, zobacz [Omówienie obiektów freezable](../advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>
## <a name="other-geometry-features"></a>Inne funkcje geometrii  
 Klasa <xref:System.Windows.Media.Geometry> zawiera również przydatne metody narzędzia, takie jak:  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A>- Pobiera obszar <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A>- Określa, czy geometria <xref:System.Windows.Media.Geometry>zawiera inny .  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A>- Określa, czy obrys <xref:System.Windows.Media.Geometry> zawiera określony punkt.  
  
 Zobacz <xref:System.Windows.Media.Geometry> klasę, aby uzyskać pełną listę jego metod.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Składni znacznikowania ścieżki](path-markup-syntax.md)
- [Tematy in jakże](geometries-how-to-topics.md)
- [Przegląd Animacja](animation-overview.md)
- [Przegląd Kształty i podstawowe rysowanie w WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Przegląd Rysowanie obiektów](drawing-objects-overview.md)
