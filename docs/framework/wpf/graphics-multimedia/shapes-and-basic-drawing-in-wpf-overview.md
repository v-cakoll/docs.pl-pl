---
title: "Przegląd Kształty i podstawowe rysowanie w WPF"
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
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 134f42da7e4366d4d5bb971aaf26b2a3b57a4c1c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Przegląd Kształty i podstawowe rysowanie w WPF
Ten temat zawiera omówienie sposobu Rysowanie za pomocą <xref:System.Windows.Shapes.Shape> obiektów. A <xref:System.Windows.Shapes.Shape> jest typem <xref:System.Windows.UIElement> umożliwiająca narysować kształt do ekranu. Ponieważ są one elementy interfejsu użytkownika <xref:System.Windows.Shapes.Shape> obiekty mogą być używane wewnątrz <xref:System.Windows.Controls.Panel> elementów i większość formantów.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferuje kilka warstw dostępu do usługi renderowania i grafiki. W górnej warstwie <xref:System.Windows.Shapes.Shape> obiekty są łatwe w użyciu i podaj wielu przydatnych funkcji, takich jak układ i udział w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zdarzeń systemu.  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a>Obiekty kształtu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia wiele gotowych do użycia <xref:System.Windows.Shapes.Shape> obiektów.  Wszystkie obiekty kształtu dziedziczyć <xref:System.Windows.Shapes.Shape> klasy. Kształt dostępne obiekty obejmują <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, i <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Shapes.Shape>obiekty współużytkują wspólne następujące właściwości.  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>: W tym artykule opisano sposób jest rysowane konturu kształtu.  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: W tym artykule opisano Grubość konturu kształtu.  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>: W tym artykule opisano sposób jest rysowane wewnątrz kształtu.  
  
-   Właściwości danych, aby określić współrzędne i wierzchołki, podawana w pikselach niezależnych od urządzenia.  
  
 Ponieważ pochodzą one od <xref:System.Windows.UIElement>, kształtu obiekty mogą być używane wewnątrz paneli i większość formantów. <xref:System.Windows.Controls.Canvas> Panel jest szczególnie użyteczna do tworzenia złożonych rysunki, ponieważ obsługuje on bezwzględny jego obiektów podrzędnych.  
  
 <xref:System.Windows.Shapes.Line> Klasa pozwala na rysowanie linii między dwoma punktami. Poniższy przykład przedstawia kilka sposobów, aby określić właściwości obrysu i współrzędnych wiersza.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Na poniższej ilustracji przedstawiono renderowanych <xref:System.Windows.Shapes.Line>.  
  
 ![Wiersz ilustracji](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Mimo że <xref:System.Windows.Shapes.Line> klasy podaj <xref:System.Windows.Shapes.Shape.Fill%2A> ustawienia jego właściwości nie obowiązuje, ponieważ <xref:System.Windows.Shapes.Line> ma bez obszaru.  
  
 Inny kształt wspólnej jest <xref:System.Windows.Shapes.Ellipse>.  Utwórz <xref:System.Windows.Shapes.Ellipse> , definiując kształtu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości. Aby narysować okrąg, określ <xref:System.Windows.Shapes.Ellipse> których <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> wartości są równe.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono przykład renderowanych <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Ilustracja przedstawiająca elipsę](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>Przy użyciu ścieżki i mają geometrię  
 <xref:System.Windows.Shapes.Path> Klasa umożliwia rysowanie krzywych i kształtów złożonych. Te krzywych i kształtów są opisane przy użyciu <xref:System.Windows.Media.Geometry> obiektów. Aby użyć <xref:System.Windows.Shapes.Path>, możesz utworzyć <xref:System.Windows.Media.Geometry> i użyj jej do ustawienia <xref:System.Windows.Shapes.Path> obiektu <xref:System.Windows.Shapes.Path.Data%2A> właściwości.  
  
 Istnieją różne <xref:System.Windows.Media.Geometry> obiekty do wyboru. <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, I <xref:System.Windows.Media.EllipseGeometry> klas definiujących kształty stosunkowo proste. Aby utworzyć bardziej złożoną kształtów lub krzywych, należy użyć <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry i PathSegments  
 <xref:System.Windows.Media.PathGeometry>obiekty składają się z co najmniej jeden <xref:System.Windows.Media.PathFigure> obiektów; każda <xref:System.Windows.Media.PathFigure> reprezentuje różne "rysunek" lub kształtu. Każdy <xref:System.Windows.Media.PathFigure> sam składa się z co najmniej jednego <xref:System.Windows.Media.PathSegment> obiekty, każdy reprezentuje połączony fragment rysunku lub kształtu. Są następujące typy segmentu: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, i <xref:System.Windows.Media.ArcSegment>.  
  
 W poniższym przykładzie <xref:System.Windows.Shapes.Path> jest używany do rysowania kwadratową krzywą Beziera.  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Na poniższej ilustracji przedstawiono renderowanych kształtu.  
  
 ![Ilustracja przedstawiająca ścieżkę](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.PathGeometry> i innych <xref:System.Windows.Media.Geometry> klas, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>Pojęcie skracane składni języka XAML  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można także użyć do opisania specjalnej składni skróconej <xref:System.Windows.Shapes.Path>. W poniższym przykładzie składni skróconej używany do rysowania złożonego kształtu.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Na poniższej ilustracji przedstawiono renderowanych <xref:System.Windows.Shapes.Path>.  
  
 ![Ilustracja przedstawiająca ścieżkę](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A> Ciąg atrybutu rozpoczyna się przy użyciu polecenia "moveto", wskazane przez M, która określa punkt początkowy dla ścieżki w układzie współrzędnych <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Shapes.Path>Parametry danych jest rozróżniana wielkość liter. Wielka litera M wskazuje bezwzględny lokalizacji dla nowego punktu bieżącego. Małe litery m wskazuje współrzędnych względnych. Pierwszy segment jest sześcienny początku krzywej Beziera na (100,200) i koniec (400,175), rysowane przy użyciu dwóch kontroli punktów (100,25) i (400,350). Ten segment jest określane przez polecenie C w <xref:System.Windows.Shapes.Path.Data%2A> atrybut ciągu. Ponownie Wielka litera C wskazuje ścieżką bezwzględną; małe litery c wskazuje ścieżki względnej.  
  
 Drugi segment rozpocznie się za pomocą wiersza polecenia bezwzględny poziome "lineto" H, który określa linią z poprzednim podrzędną punktu końcowego (400,175) do nowego punktu końcowego (280,175). Polecenie poziome "lineto", dlatego jest wybrana *x*-współrzędną.  
  
 Pełną ścieżkę składni, zobacz <xref:System.Windows.Shapes.Path.Data%2A> odwołania i [tworzenie kształtu przy użyciu PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>Kształty malowania  
 <xref:System.Windows.Media.Brush>obiekty służą do malowania kształtu <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.Fill%2A>. W poniższym przykładzie, obrysu i wypełnienie <xref:System.Windows.Shapes.Ellipse> zostały określone. Należy zauważyć, że prawidłowe wartości wejściowe pędzla właściwości mogą być słowo kluczowe lub szesnastkowej wartości koloru. Aby uzyskać więcej informacji na temat słów kluczowych dostępny kolor, zobacz właściwości <xref:System.Windows.Media.Colors> klasy w <xref:System.Windows.Media> przestrzeni nazw.  
  
```  
<Canvas Background="LightGray">   
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 Na poniższej ilustracji przedstawiono renderowanych <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Można również można użyć składni elementu właściwości można jawnie utworzyć <xref:System.Windows.Media.SolidColorBrush> obiektu namalować kształtów jednolitym kolorem.  
  
```  
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"   
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 Na poniższej ilustracji przedstawiono renderowanych kształtu.  
  
 ![Ilustracja SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Umożliwia malowanie obrysu lub wypełnienia gradientów, obrazy, wzorców i kształtu. Aby uzyskać więcej informacji, zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>Kształty regulowanej długości  
 <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, I <xref:System.Windows.Shapes.Rectangle> klasy mają <xref:System.Windows.Shapes.Shape.Stretch%2A> właściwości. Ta właściwość określa, jak <xref:System.Windows.Shapes.Shape> zawartość obiektu (kształt do narysowania) jest rozciągany tak, aby wypełnić <xref:System.Windows.Shapes.Shape> obiektu układu miejsca. A <xref:System.Windows.Shapes.Shape> ilość miejsca jest obiektu układu miejsca <xref:System.Windows.Shapes.Shape> został przydzielony przez system układu z powodu albo jawne <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> ustawienie lub z powodu jego <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ustawienia. Aby uzyskać dodatkowe informacje na układ w systemie Windows Presentation Foundation, zobacz [układu](../../../../docs/framework/wpf/advanced/layout.md) omówienie.  
  
 Właściwość Stretch przyjmuje jeden z następujących wartości:  
  
-   <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu nie jest rozciągana.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągany w celu wypełnienia miejsca jego układu.  Współczynnik proporcji nie są zachowywane.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu są rozciągany tak jak to możliwe do wypełnienia miejsca jego układ, zachowując jego oryginalny współczynnik proporcji.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągany tak, aby wypełnić miejsca jego układ, zachowując jego oryginalny współczynnik proporcji.  
  
 Należy zauważyć, że gdy <xref:System.Windows.Shapes.Shape> zawartość obiektu jest rozciągany tak, <xref:System.Windows.Shapes.Shape> obiektu jest rysowane po rozciąganie.  
  
 W poniższym przykładzie <xref:System.Windows.Shapes.Polygon> używany do rysowania bardzo mały trójkąt z (0,0) (0,1) (1,1). <xref:System.Windows.Shapes.Polygon> Obiektu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> są ustawione na 100, a jego właściwość stretch jest ustawiona na wartość Fill. W związku z tym <xref:System.Windows.Shapes.Polygon> zawartość obiektu (trójkąt) są rozciągany w celu wypełnienia większych miejsca.  
  
```  
...  
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
...  
```  
  
```  
...  
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
...  
```  
  
<a name="transforms"></a>   
## <a name="transforming-shapes"></a>Przekształcanie kształtów  
 <xref:System.Windows.Media.Transform> Klasa udostępnia środki do przekształcania kształtów w dwuwymiarowego rzutu.  Różne typy przekształcania obejmują obrotu (<xref:System.Windows.Media.RotateTransform>), skali (<xref:System.Windows.Media.ScaleTransform>), pochylenia (<xref:System.Windows.Media.SkewTransform>), a translacja (<xref:System.Windows.Media.TranslateTransform>).  
  
 Typowe przekształcenie do zastosowania do kształtu jest obrotu.  Obracanie kształtu, należy utworzyć <xref:System.Windows.Media.RotateTransform> i określ jej <xref:System.Windows.Media.RotateTransform.Angle%2A>. <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 obraca element 45 stopni w prawo; pod kątem 90 obraca element 90 stopni w prawo; i tak dalej. Ustaw <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości, jeśli chcesz kontrolować punktu o tym, które jest obracana elementu. Wartości tych właściwości są wyrażane w układzie współrzędnych elementu transformacji. <xref:System.Windows.Media.RotateTransform.CenterX%2A>i <xref:System.Windows.Media.RotateTransform.CenterY%2A> mają przypisane wartości domyślne o wartości zero. Na koniec zastosować <xref:System.Windows.Media.RotateTransform> do elementu. Jeśli nie chcesz transformacji do mają wpływ na układ, ustaw kształtu <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.  
  
 W poniższym przykładzie <xref:System.Windows.Media.RotateTransform> służy do Obrót o 45 stopni kształtu, o kształtu lewym górnym rogu (0,0).  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 W następnym przykładzie innego kształtu jest obrócony o 45 stopni, ale tym razem go obraca się wokół punktu (25,50).  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Na poniższej ilustracji przedstawiono wyniki dwóch transformacji.  
  
 ![obrotów 45 stopni z różnymi punktami](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 W poprzednich przykładach transformacji pojedynczego została zastosowana do każdego obiektu kształtu. Aby zastosować kilka przekształceń do kształtu (lub innego elementu interfejsu użytkownika), należy użyć <xref:System.Windows.Media.TransformGroup>.  
  
## <a name="see-also"></a>Zobacz też  
 [Grafika 2W i utworzenia obrazu](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Malowanie pełnych kolorów i gradientów — omówienie](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Wskazówki: Pierwszy WPF pulpitu aplikację](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
