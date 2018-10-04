---
title: Przegląd Kształty i podstawowe rysowanie w WPF
ms.date: 03/30/2017
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
ms.openlocfilehash: 47df352c3b001f088f34ea057b34698efc4f4b53
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778104"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Przegląd Kształty i podstawowe rysowanie w WPF
Ten temat zawiera omówienie sposobu Rysowanie za pomocą <xref:System.Windows.Shapes.Shape> obiektów. A <xref:System.Windows.Shapes.Shape> jest typem <xref:System.Windows.UIElement> pozwala narysować kształt na ekranie. Ponieważ są one elementy interfejsu użytkownika <xref:System.Windows.Shapes.Shape> obiekty mogą być używane wewnątrz <xref:System.Windows.Controls.Panel> elementów i większości kontrolek.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferuje kilka warstw dostępu do grafiki i renderowania usług. W górnej warstwie <xref:System.Windows.Shapes.Shape> obiekty są łatwe w użyciu i zapewnia wiele przydatnych funkcji, takie jak układ i udział w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] system zdarzeń.  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a>Obiekty kształtów  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia wiele gotowych do użycia <xref:System.Windows.Shapes.Shape> obiektów.  Wszystkie obiekty kształtów dziedziczyć <xref:System.Windows.Shapes.Shape> klasy. Kształt dostępne obiekty zawierają <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, i <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Shapes.Shape> obiekty mają następujące wspólne właściwości.  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>: W tym artykule opisano sposób jest malowane kontur figury.  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: W tym artykule opisano Grubość konturu tego kształtu.  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>: W tym artykule opisano sposób jest malowane wnętrze figury.  
  
-   Właściwości danych, aby określić współrzędne i wierzchołki, podawana w pikselach niezależnych od urządzenia.  
  
 Ponieważ pochodzą one od <xref:System.Windows.UIElement>, obiekty kształtów można używać wewnątrz paneli i większość formantów. <xref:System.Windows.Controls.Canvas> Panel jest szczególnie dobrym wyborem dla tworzenia rysunki złożone, ponieważ obsługuje on pozycjonowanie absolutne jego obiektów podrzędnych.  
  
 <xref:System.Windows.Shapes.Line> Klasy umożliwia narysuj linię między dwoma punktami. Poniższy przykład pokazuje kilka sposobów, aby określić współrzędne wiersza i właściwości pociągnięcia.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Na poniższej ilustracji przedstawiono renderowanych <xref:System.Windows.Shapes.Line>.  
  
 ![Wiersz ilustracji](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Mimo że <xref:System.Windows.Shapes.Line> klasa dostarczać <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość, ustawienie nie obowiązuje, ponieważ <xref:System.Windows.Shapes.Line> ma bez obszaru.  
  
 Jest innym kształcie wspólnej <xref:System.Windows.Shapes.Ellipse>.  Tworzenie <xref:System.Windows.Shapes.Ellipse> , definiując kształtu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości. Aby narysować okrąg, należy określić <xref:System.Windows.Shapes.Ellipse> którego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> wartości są równe.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono przykład renderowanych <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Ilustracja przedstawiająca elipsę](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>Przy użyciu ścieżek i geometrii  
 <xref:System.Windows.Shapes.Path> Klasy umożliwia rysowanie krzywych i kształtów złożonych. Te krzywe i kształty są opisane za pomocą <xref:System.Windows.Media.Geometry> obiektów. Aby użyć <xref:System.Windows.Shapes.Path>, tworzenia <xref:System.Windows.Media.Geometry> i użyj go, aby ustawić <xref:System.Windows.Shapes.Path> obiektu <xref:System.Windows.Shapes.Path.Data%2A> właściwości.  
  
 Istnieją różne <xref:System.Windows.Media.Geometry> obiektów do wybrania. <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, I <xref:System.Windows.Media.EllipseGeometry> klasy opisują kształty stosunkowo proste. Aby utworzyć bardziej złożonych kształtów lub krzywych, należy użyć <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry — i PathSegments  
 <xref:System.Windows.Media.PathGeometry> obiekty składają się z co najmniej jeden <xref:System.Windows.Media.PathFigure> obiektów; każdy <xref:System.Windows.Media.PathFigure> reprezentuje różne "rysunek" lub kształtu. Każdy <xref:System.Windows.Media.PathFigure> sam składa się z co najmniej jeden <xref:System.Windows.Media.PathSegment> obiektów, każdy reprezentuje połączone część rysunek lub kształtu. Segment typy obejmują następujące elementy: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, i <xref:System.Windows.Media.ArcSegment>.  
  
 W poniższym przykładzie <xref:System.Windows.Shapes.Path> używany do rysowania krzywą Beziera drugiego stopnia.  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Na poniższej ilustracji przedstawiono renderowanych kształtu.  
  
 ![Ilustracja przedstawiająca ścieżkę](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.PathGeometry> , a druga <xref:System.Windows.Media.Geometry> klas, zobacz [Przegląd Geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>XAML skróconej składni  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można także użyć specjalnej składni skrócona do opisania <xref:System.Windows.Shapes.Path>. W poniższym przykładzie służy skróconej składni, aby narysować kształt złożony.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Na poniższej ilustracji przedstawiono renderowanych <xref:System.Windows.Shapes.Path>.  
  
 ![Ilustracja przedstawiająca ścieżkę](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A> Ciągu atrybutu rozpocznie się za pomocą polecenia "moveto" wskazywanym przez M, która ustanawia punkt początkowy dla ścieżki w układzie współrzędnych <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Shapes.Path> Parametry danych jest rozróżniana wielkość liter. Wielka litera M wskazuje bezwzględna lokalizacji dla nowego punktu bieżącego. Mała litera m wskazuje współrzędnych względnych. Pierwszy segment jest trzeciego stopnia początku krzywej Beziera na (100,200) i kończąc na (400,175), rysowane przy użyciu dwóch kontrolować punkty (100,25) i (400,350). Ten segment jest wskazywane za pomocą polecenia języka C w <xref:System.Windows.Shapes.Path.Data%2A> atrybut ciągu. Ponownie wielkiej litery C wskazuje ścieżkę bezwzględną; małe litery c wskazuje ścieżkę względną.  
  
 Drugi segment rozpoczyna się za pomocą polecenia poziomy bezwzględny "lineto" H, który określa linią z podrzędną poprzedniego punktu końcowego (400,175) do nowego punktu końcowego (280,175). Ponieważ polecenia poziomy "lineto", określona wartość jest *x*-koordynacji.  
  
 Informacje na temat składni pełną ścieżkę, zobacz <xref:System.Windows.Shapes.Path.Data%2A> odwołania i [Utwórz kształt używając PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>Malowanie kształtów  
 <xref:System.Windows.Media.Brush> obiekty służą do rysowania kształtów <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.Fill%2A>. W poniższym przykładzie, obrysu i wypełnienie <xref:System.Windows.Shapes.Ellipse> zostały określone. Należy pamiętać, że prawidłowych danych wejściowych dla właściwości pędzla może być słowo kluczowe lub szesnastkowej wartości koloru. Aby uzyskać więcej informacji na temat słów kluczowych dostępnych kolorów, zobacz właściwości <xref:System.Windows.Media.Colors> klasy w <xref:System.Windows.Media> przestrzeni nazw.  
  
```xaml
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
  
 Alternatywnie można użyć składni elementu właściwości jawnie utworzyć <xref:System.Windows.Media.SolidColorBrush> obiekt do rysowania kształtów jednolitym kolorem.  
  
```xaml
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
  
 Poniższa ilustracja przedstawia renderowanych kształtu.  
  
 ![Ilustracja SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Umożliwia malowanie wypełnienia przy użyciu gradientów, obrazy, wzorców i lub obrys kształtu. Aby uzyskać więcej informacji, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>Kształty rozciągalne  
 <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, I <xref:System.Windows.Shapes.Rectangle> wszystkich klas <xref:System.Windows.Shapes.Shape.Stretch%2A> właściwości. Ta właściwość określa, jak <xref:System.Windows.Shapes.Shape> zawartość obiektu (kształt do narysowania) jest rozciągany tak, aby wypełnić <xref:System.Windows.Shapes.Shape> miejsca układ obiektu. A <xref:System.Windows.Shapes.Shape> ilość miejsca jest miejsca układ obiektu <xref:System.Windows.Shapes.Shape> jest przydzielany przez system układu z powodu albo jawnie <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> ustawienie lub z powodu jego <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ustawienia. Aby uzyskać dodatkowe informacje na temat układu w oprogramowaniu Windows Presentation Foundation, zobacz [układ](../../../../docs/framework/wpf/advanced/layout.md) Przegląd.  
  
 Właściwości rozciągania ma jedną z następujących wartości:  
  
-   <xref:System.Windows.Media.Stretch.None><xref:System.Windows.Shapes.Shape> Zawartość obiektu nie jest rozciągana.  
  
-   <xref:System.Windows.Media.Stretch.Fill><xref:System.Windows.Shapes.Shape> Konfiguracji zawartości obiektu do wypełnienia jego układu przestrzeni.  Współczynnik proporcji nie są zachowywane.  
  
-   <xref:System.Windows.Media.Stretch.Uniform><xref:System.Windows.Shapes.Shape> Zawartość obiektu konfiguracji jak najszerzej w celu wypełnienia jego układu przestrzeni, zachowując jego oryginalny współczynnik proporcji.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill><xref:System.Windows.Shapes.Shape> Zawartość obiektu konfiguracji Aby całkowicie wypełnić jego układu przestrzeni, zachowując jego oryginalny współczynnik proporcji.  
  
 Należy zauważyć, że gdy <xref:System.Windows.Shapes.Shape> konfiguracji zawartość obiektu <xref:System.Windows.Shapes.Shape> kontur obiektu jest malowane po rozciąganie.  
  
 W poniższym przykładzie <xref:System.Windows.Shapes.Polygon> używany do rysowania bardzo małego trójkąta z (0,0) (0,1) (1,1). <xref:System.Windows.Shapes.Polygon> Obiektu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> są ustawione na 100, a jego właściwości rozciągania do wypełnienia. W rezultacie <xref:System.Windows.Shapes.Polygon> zawartość obiektu ("trójkąt") czy rozciągnięte do wypełnienia większą przestrzeń.  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
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
```

<a name="transforms"></a>   
## <a name="transforming-shapes"></a>Przekształcanie kształtów  
 <xref:System.Windows.Media.Transform> Klasy zapewnia sposób przekształcania kształty w dwuwymiarowej płaszczyzny.  Różne rodzaje przekształcania obejmują obrót (<xref:System.Windows.Media.RotateTransform>), skalowanie (<xref:System.Windows.Media.ScaleTransform>), niesymetryczność (<xref:System.Windows.Media.SkewTransform>) i tłumaczenie (<xref:System.Windows.Media.TranslateTransform>).  
  
 Typowe przekształcenie do zastosowania do kształtu jest obrotu.  Aby obrócić kształt znajdujący się, Utwórz <xref:System.Windows.Media.RotateTransform> i określ jej <xref:System.Windows.Media.RotateTransform.Angle%2A>. <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 obraca element 45 stopni w prawo; pod kątem 90 obraca element o 90 stopni zgodnie ze wskazówkami zegara; i tak dalej. Ustaw <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości, jeśli chcesz kontrolować punkt o tym, które jest obracana elementu. Wartości tych właściwości są wyrażane w układzie współrzędnych elementu przekształcanego. <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> mają przypisane wartości domyślne o wartości zero. Na koniec Zastosuj <xref:System.Windows.Media.RotateTransform> do elementu. Jeśli nie chcesz, aby przekształcania wpływ na układ, ustaw kształtu <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.  
  
 W poniższym przykładzie <xref:System.Windows.Media.RotateTransform> służy do obracania kształtu o 45 stopni o kształtu lewym górnym rogu (0,0).  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 W następnym przykładzie innym kształcie jest obracany 45 stopni, ale tym razem go obraca się wokół punktu (25,50).  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Poniższa ilustracja przedstawia wyniki dwóch transformacji.  
  
 ![Obroty 45 stopni z różnymi punktami](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 W poprzednich przykładach przekształcenia pojedynczego została zastosowana do każdego obiektu kształtu. Aby zastosować wiele przekształceń do kształtu (lub innego elementu interfejsu użytkownika), należy użyć <xref:System.Windows.Media.TransformGroup>.  
  
## <a name="see-also"></a>Zobacz też  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Geometria — przegląd](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
