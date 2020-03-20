---
title: Kształty i podstawowy przegląd rysunku
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
ms.openlocfilehash: 44104bec478f1fbb10acc0e591af43ea95fecdc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141331"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Przegląd Kształty i podstawowe rysowanie w WPF
W tym temacie przedstawiono omówienie sposobu rysowania z <xref:System.Windows.Shapes.Shape> obiektami. A <xref:System.Windows.Shapes.Shape> jest typem, <xref:System.Windows.UIElement> który umożliwia rysowanie kształtu na ekranie. Ponieważ są one elementy <xref:System.Windows.Shapes.Shape> interfejsu użytkownika, <xref:System.Windows.Controls.Panel> obiekty mogą być używane wewnątrz elementów i większość formantów.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferuje kilka warstw dostępu do grafiki i usług renderowania. W górnej warstwie <xref:System.Windows.Shapes.Shape> obiekty są łatwe w użyciu i zapewniają wiele [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przydatnych funkcji, takich jak układ i uczestnictwo w systemie zdarzeń.  

<a name="shapes"></a>
## <a name="shape-objects"></a>Obiekty kształtu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wiele gotowych do <xref:System.Windows.Shapes.Shape> użycia obiektów.  Wszystkie obiekty kształtu <xref:System.Windows.Shapes.Shape> dziedziczą z klasy. Dostępne obiekty <xref:System.Windows.Shapes.Ellipse>kształtu to <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>, , i . <xref:System.Windows.Shapes.Shape>obiekty mają następujące wspólne właściwości.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: Opisuje sposób malowania konturu kształtu.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Opisuje grubość konturu kształtu.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: Opisuje sposób malowania wnętrza kształtu.  
  
- Właściwości danych do określania współrzędnych i wierzchołków, mierzone w pikselach niezależnych od urządzenia.  
  
 Ponieważ pochodzą one <xref:System.Windows.UIElement>od , obiekty kształtu mogą być używane wewnątrz paneli i większości formantów. Panel <xref:System.Windows.Controls.Canvas> jest szczególnie dobrym wyborem do tworzenia złożonych rysunków, ponieważ obsługuje bezwzględne pozycjonowanie obiektów podrzędnych.  
  
 Klasa <xref:System.Windows.Shapes.Line> umożliwia narysowanie linii między dwoma punktami. W poniższym przykładzie przedstawiono kilka sposobów określania współrzędnych linii i właściwości obrysu.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Na poniższej ilustracji <xref:System.Windows.Shapes.Line>przedstawiono renderowany plik .  
  
 ![Ilustracja liniowa](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Chociaż <xref:System.Windows.Shapes.Line> klasa zapewnia <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość, ustawienie nie ma <xref:System.Windows.Shapes.Line> wpływu, ponieważ a nie ma obszaru.  
  
 Innym wspólnym kształtem <xref:System.Windows.Shapes.Ellipse>jest .  Utwórz, <xref:System.Windows.Shapes.Ellipse> definiując kształt <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> i właściwości. Aby narysować okrąg, <xref:System.Windows.Shapes.Ellipse> należy określić, czyje <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> wartości są równe.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono <xref:System.Windows.Shapes.Ellipse>przykład renderowanego pliku .  
  
 ![Ilustracja elipsy](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>Korzystanie ze ścieżek i geometrii  
 Klasa <xref:System.Windows.Shapes.Path> umożliwia rysowanie krzywych i złożonych kształtów. Te krzywe i kształty <xref:System.Windows.Media.Geometry> są opisane za pomocą obiektów. Aby użyć <xref:System.Windows.Shapes.Path>programu , <xref:System.Windows.Media.Geometry> należy utworzyć i <xref:System.Windows.Shapes.Path> użyć <xref:System.Windows.Shapes.Path.Data%2A> go do ustawiania właściwości obiektu.  
  
 Istnieje wiele <xref:System.Windows.Media.Geometry> obiektów do wyboru. Klasy <xref:System.Windows.Media.LineGeometry> <xref:System.Windows.Media.RectangleGeometry>, <xref:System.Windows.Media.EllipseGeometry> i klasy opisują stosunkowo proste kształty. Aby utworzyć bardziej złożone kształty lub <xref:System.Windows.Media.PathGeometry>utworzyć krzywe, użyj pliku .  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry i PathSegments  
 <xref:System.Windows.Media.PathGeometry>obiekty składają się z <xref:System.Windows.Media.PathFigure> jednego lub więcej obiektów; każdy <xref:System.Windows.Media.PathFigure> reprezentuje inną "figurę" lub kształt. Każdy <xref:System.Windows.Media.PathFigure> z nich składa się <xref:System.Windows.Media.PathSegment> z jednego lub więcej obiektów, z których każdy reprezentuje połączoną część figury lub kształtu. Typy segmentów <xref:System.Windows.Media.LineSegment>są <xref:System.Windows.Media.BezierSegment>następujące: , i <xref:System.Windows.Media.ArcSegment>.  
  
 W poniższym przykładzie <xref:System.Windows.Shapes.Path> a służy do rysowania kwadratowej krzywej Beziera.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Na poniższej ilustracji przedstawiono renderowany kształt.  
  
 ![Ilustracja ścieżki](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Aby uzyskać <xref:System.Windows.Media.PathGeometry> więcej informacji <xref:System.Windows.Media.Geometry> na temat i innych klas, zobacz [Przegląd geometrii](geometry-overview.md).  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>Składnia skrócona XAML  
 W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]programze można również użyć specjalnej skróconej składni, aby opisać plik <xref:System.Windows.Shapes.Path>. W poniższym przykładzie skrócona składnia jest używana do rysowania złożonego kształtu.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Na poniższej ilustracji <xref:System.Windows.Shapes.Path>przedstawiono renderowany plik .  
  
 ![Ilustracja ścieżki](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 Ciąg <xref:System.Windows.Shapes.Path.Data%2A> atrybutu rozpoczyna się od polecenia "moveto", wskazanego przez M, które ustanawia punkt początkowy <xref:System.Windows.Controls.Canvas>ścieżki w układzie współrzędnych . <xref:System.Windows.Shapes.Path>parametry danych są rozróżniane wielkość liter. Stolica M wskazuje bezwzględną lokalizację dla nowego bieżącego punktu. Małe litery m wskazywałyby współrzędne względne. Pierwszy segment to sześcienna krzywa Beziera rozpoczynająca się od (100 200) i kończąca się na (400 175), narysowana przy użyciu dwóch punktów kontrolnych (100,25) i (400 350). Ten segment jest wskazywany <xref:System.Windows.Shapes.Path.Data%2A> przez polecenie C w ciągu atrybutu. Ponownie, stolica C wskazuje ścieżkę bezwzględną; małe litery c wskazywałyby względną ścieżkę.  
  
 Drugi segment rozpoczyna się bezwzględnym poziomym poleceniem "lineto" H, które określa linię narysowaną od punktu końcowego poprzedniej ścieżki podrzędnej (400 175) do nowego punktu końcowego (280 175). Ponieważ jest to poziome polecenie "lineto", określona wartość jest współrzędną *x.*  
  
 Aby zapoznać się ze składnią ścieżki pełnej, zobacz <xref:System.Windows.Shapes.Path.Data%2A> odwołanie i Tworzenie [kształtu przy użyciu ścieżkiGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>Malowanie kształtów  
 <xref:System.Windows.Media.Brush>obiekty są używane do malowania kształtu <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.Fill%2A>. W poniższym przykładzie określono obrys i wypełnienie. <xref:System.Windows.Shapes.Ellipse> Należy zauważyć, że prawidłowe dane wejściowe dla właściwości pędzla może być słowem kluczowym lub szesnastkowej wartości koloru. Aby uzyskać więcej informacji na temat dostępnych <xref:System.Windows.Media.Colors> słów kluczowych <xref:System.Windows.Media> kolorów, zobacz właściwości klasy w obszarze nazw.  
  
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
  
 Na poniższej ilustracji <xref:System.Windows.Shapes.Ellipse>przedstawiono renderowany plik .  
  
 ![Elipsę](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternatywnie można użyć składni elementu właściwości, aby <xref:System.Windows.Media.SolidColorBrush> jawnie utworzyć obiekt do malowania kształtu jednolitym kolorem.  
  
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
  
 Na poniższej ilustracji przedstawiono renderowany kształt.  
  
 ![Ilustracja SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Można również malować obrys kształtu lub wypełniać gradientami, obrazami, wzorami i innymi. Aby uzyskać więcej informacji, zobacz [Omówienie malowanie za pomocą jednolitych kolorów i gradientów](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a>Rozciągliwe kształty  
 , <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle> i klasy <xref:System.Windows.Shapes.Shape.Stretch%2A> wszystkie mają właściwość. Ta właściwość określa <xref:System.Windows.Shapes.Shape> sposób rozciągnięcia zawartości obiektu (kształtu do narysowania) w <xref:System.Windows.Shapes.Shape> celu wypełnienia przestrzeni układu obiektu. Obszar <xref:System.Windows.Shapes.Shape> układu obiektu to <xref:System.Windows.Shapes.Shape> ilość miejsca przydzielonego przez system układu, ze względu <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> na jawne <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ustawienie <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> lub ze względu na jego i ustawienia. Aby uzyskać dodatkowe informacje na temat układu w programie Windows Presentation Foundation, zobacz [Omówienie układu.](../advanced/layout.md)  
  
 Właściwość Stretch przyjmuje jedną z następujących wartości:  
  
- <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu nie jest rozciągnięta.  
  
- <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągnięta, aby wypełnić jego przestrzeń w układzie.  Współczynnik proporcji nie jest zachowywany.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągnięta w miarę możliwości, aby wypełnić jego przestrzeń w układzie, zachowując oryginalny współczynnik proporcji.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągnięta, aby całkowicie wypełnić jego przestrzeń w układzie, zachowując oryginalny współczynnik proporcji.  
  
 Należy zauważyć, <xref:System.Windows.Shapes.Shape> że gdy zawartość obiektu jest <xref:System.Windows.Shapes.Shape> rozciągnięta, kontur obiektu jest malowany po rozciąganiu.  
  
 W poniższym przykładzie a <xref:System.Windows.Shapes.Polygon> służy do rysowania bardzo małego trójkąta od (0,0) do (0,1) do (1,1). Obiekt <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.FrameworkElement.Width%2A> jest ustawiony <xref:System.Windows.FrameworkElement.Height%2A> na 100, a jego właściwość stretch jest ustawiona na Wypełnienie. W rezultacie zawartość <xref:System.Windows.Shapes.Polygon> obiektu (trójkąt) jest rozciągnięta, aby wypełnić większą przestrzeń.  
  
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
 Klasa <xref:System.Windows.Media.Transform> zapewnia środki do przekształcania kształtów w płaszczyźnie dwuwymiarowej.  Różne rodzaje transformacji obejmują<xref:System.Windows.Media.RotateTransform>obrót (<xref:System.Windows.Media.ScaleTransform>),<xref:System.Windows.Media.SkewTransform>skalę (<xref:System.Windows.Media.TranslateTransform>), pochylenie ( ) i tłumaczenie ( ).  
  
 Wspólne przekształcenie do zastosowania do kształtu jest obrotem.  Aby obrócić kształt, <xref:System.Windows.Media.RotateTransform> utwórz <xref:System.Windows.Media.RotateTransform.Angle%2A>i określ jego . An <xref:System.Windows.Media.RotateTransform.Angle%2A> z 45 obraca element 45 stopni w prawo; kąt 90 obraca element o 90 stopni w prawo; i tak dalej. Ustaw <xref:System.Windows.Media.RotateTransform.CenterX%2A> właściwości <xref:System.Windows.Media.RotateTransform.CenterY%2A> i, jeśli chcesz kontrolować punkt, o którym element jest obrócony. Te wartości właściwości są wyrażone w przestrzeni współrzędnych elementu, który jest przekształcany. <xref:System.Windows.Media.RotateTransform.CenterX%2A>i <xref:System.Windows.Media.RotateTransform.CenterY%2A> mają domyślne wartości zero. Na koniec zastosuj <xref:System.Windows.Media.RotateTransform> do elementu. Jeśli transformacja nie ma mieć wpływu na układ, <xref:System.Windows.UIElement.RenderTransform%2A> ustaw właściwość kształtu.  
  
 W poniższym przykładzie <xref:System.Windows.Media.RotateTransform> a służy do obracania kształtu o 45 stopni w lewym górnym rogu kształtu (0,0).  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 W następnym przykładzie inny kształt jest obracany o 45 stopni, ale tym razem jest obracany o punkt (25,50).  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Na poniższej ilustracji przedstawiono wyniki stosowania dwóch przekształceń.  
  
 ![Obrót 45 stopni z różnymi punktami środkowymi](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 W poprzednich przykładach do każdego obiektu kształtu zastosowano pojedyncze przekształcenie. Aby zastosować wiele przekształceń do kształtu (lub <xref:System.Windows.Media.TransformGroup>innego elementu interfejsu użytkownika), należy użyć pliku .  
  
## <a name="see-also"></a>Zobacz też

- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Przegląd Malowanie jednolitymi kolorami i gradientami](painting-with-solid-colors-and-gradients-overview.md)
- [Przegląd Geometria](geometry-overview.md)
- [Instruktaż: Moja pierwsza aplikacja komputerowa WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Przegląd Animacja](animation-overview.md)
