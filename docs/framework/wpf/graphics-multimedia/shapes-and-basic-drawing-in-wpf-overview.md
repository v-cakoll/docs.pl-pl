---
title: Przegląd kształtów i podstawowe informacje o rysowaniu
description: Wzbogacaj interfejs użytkownika za pomocą gotowych do użycia kształtów i kilku warstw usług renderowania w Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 41d8f2b87232740c8945bd6a6099aa86dbe77bc6
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853695"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Przegląd Kształty i podstawowe rysowanie w WPF
Ten temat zawiera omówienie sposobu rysowania z <xref:System.Windows.Shapes.Shape> obiektami. A <xref:System.Windows.Shapes.Shape> to typ <xref:System.Windows.UIElement> , który umożliwia narysowanie kształtu na ekranie. Ponieważ są to elementy interfejsu użytkownika, <xref:System.Windows.Shapes.Shape> obiekty mogą być używane wewnątrz <xref:System.Windows.Controls.Panel> elementów i większości formantów.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferuje kilka warstw dostępu do usług graficznych i renderowania. W górnej warstwie <xref:System.Windows.Shapes.Shape> obiekty są łatwe w użyciu i zapewniają wiele przydatnych funkcji, takich jak układ i uczestnictwo w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systemie zdarzeń.  

<a name="shapes"></a>
## <a name="shape-objects"></a>Obiekty Shape  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wiele gotowych do użycia <xref:System.Windows.Shapes.Shape> obiektów.  Wszystkie obiekty kształtu dziedziczą z <xref:System.Windows.Shapes.Shape> klasy. Dostępne obiekty kształtu obejmują <xref:System.Windows.Shapes.Ellipse> , <xref:System.Windows.Shapes.Line> ,,, <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline> , i <xref:System.Windows.Shapes.Rectangle> . <xref:System.Windows.Shapes.Shape>obiekty współużytkują następujące typowe właściwości.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: Opisuje sposób malowania konturu kształtu.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Opisuje grubość konturu kształtu.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: Opisuje sposób malowania wnętrza kształtu.  
  
- Właściwości danych w celu określenia współrzędnych i wierzchołków mierzonych w pikselach niezależnych od urządzenia.  
  
 Ponieważ pochodzą one od <xref:System.Windows.UIElement> , obiekty Shape mogą być używane wewnątrz paneli i większości formantów. <xref:System.Windows.Controls.Canvas>Panel jest szczególnie dobrym wyborem w przypadku tworzenia złożonych rysunków, ponieważ obsługuje pozycjonowanie bezwzględne jego obiektów podrzędnych.  
  
 <xref:System.Windows.Shapes.Line>Klasa umożliwia narysowanie linii między dwoma punktami. W poniższym przykładzie pokazano kilka sposobów określania współrzędnych linii i właściwości obrysu.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Na poniższej ilustracji przedstawiono renderowane <xref:System.Windows.Shapes.Line> .  
  
 ![Ilustracja przedstawiająca linię](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Chociaż <xref:System.Windows.Shapes.Line> Klasa udostępnia <xref:System.Windows.Shapes.Shape.Fill%2A> Właściwość, ustawienie nie ma żadnego efektu, ponieważ nie <xref:System.Windows.Shapes.Line> ma żadnego obszaru.  
  
 Innym wspólnym kształtem jest <xref:System.Windows.Shapes.Ellipse> .  Utwórz obiekt <xref:System.Windows.Shapes.Ellipse> przez zdefiniowanie kształtu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości. Aby narysować okrąg, określ, <xref:System.Windows.Shapes.Ellipse> którego <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> wartości są równe.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono przykład renderowanego elementu <xref:System.Windows.Shapes.Ellipse> .  
  
 ![Ilustracja przedstawiająca elipsę](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>Używanie ścieżek i geometrie  
 <xref:System.Windows.Shapes.Path>Klasa umożliwia rysowanie krzywych i złożonych kształtów. Te krzywe i kształty są opisane przy użyciu <xref:System.Windows.Media.Geometry> obiektów. Aby użyć <xref:System.Windows.Shapes.Path> , należy utworzyć <xref:System.Windows.Media.Geometry> i użyć go do ustawienia <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Path.Data%2A> właściwości obiektu.  
  
 Istnieje wiele <xref:System.Windows.Media.Geometry> obiektów do wyboru. <xref:System.Windows.Media.LineGeometry>Klasy, <xref:System.Windows.Media.RectangleGeometry> i <xref:System.Windows.Media.EllipseGeometry> opisują stosunkowo proste kształty. Aby utworzyć bardziej złożone kształty lub utworzyć krzywe, użyj <xref:System.Windows.Media.PathGeometry> .  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry i PathSegments  
 <xref:System.Windows.Media.PathGeometry>obiekty składają się z co najmniej jednego <xref:System.Windows.Media.PathFigure> obiektu; każdy <xref:System.Windows.Media.PathFigure> reprezentuje inny "rysunek" lub kształt. Każda <xref:System.Windows.Media.PathFigure> z nich składa się z co najmniej jednego <xref:System.Windows.Media.PathSegment> obiektu, z których każdy reprezentuje podłączoną część rysunku lub kształtu. Typy segmentów obejmują następujące elementy: <xref:System.Windows.Media.LineSegment> , <xref:System.Windows.Media.BezierSegment> , i <xref:System.Windows.Media.ArcSegment> .  
  
 W poniższym przykładzie <xref:System.Windows.Shapes.Path> jest używany do rysowania krzywej Beziera kwadratu.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Na poniższej ilustracji przedstawiono renderowany kształt.  
  
 ![Ilustracja przedstawiająca ścieżkę](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.PathGeometry> i innych <xref:System.Windows.Media.Geometry> klas, zobacz [Omówienie geometrii](geometry-overview.md).  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>Składnia języka XAML — skrócona  
 W programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] można również użyć specjalnej składni skróconej do opisania <xref:System.Windows.Shapes.Path> . W poniższym przykładzie Skrócona składnia jest używana do rysowania złożonego kształtu.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Na poniższej ilustracji przedstawiono renderowane <xref:System.Windows.Shapes.Path> .  
  
 ![Ilustracja przedstawiająca ścieżkę](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A>Ciąg atrybutu zaczyna się od polecenia "MoveTo" wskazanego przez M, które określa punkt początkowy dla ścieżki w układzie współrzędnych <xref:System.Windows.Controls.Canvas> . <xref:System.Windows.Shapes.Path>w parametrach danych jest rozróżniana wielkość liter. Wielka litera M wskazuje lokalizację bezwzględną dla nowego punktu bieżącego. Małe litery m wskazują współrzędne względne. Pierwszy segment jest zakrzywioną krzywą Beziera rozpoczynającą się o (100 200) i kończącą się na (400 175), narysowanym przy użyciu dwóch punktów kontrolnych (100, 25) i (400 350). Ten segment jest wskazywany przez polecenie C w <xref:System.Windows.Shapes.Path.Data%2A> ciągu atrybutu. Ponownie Wielka litera C wskazuje ścieżkę bezwzględną; Mała litera c wskazuje ścieżkę względną.  
  
 Drugi segment zaczyna się od bezwzględnej wartości "LineTo" polecenia H, które określa wiersz rysowany z poprzedniego punktu końcowego ścieżki podrzędnej (400 175) do nowego punktu końcowego (280 175). Ponieważ jest to w poziomie polecenie "LineTo", określona wartość jest Współrzędna *x*.  
  
 Aby uzyskać pełną składnię ścieżki, zobacz <xref:System.Windows.Shapes.Path.Data%2A> odwołanie i [Tworzenie kształtu przy użyciu PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>Malowanie kształtów  
 <xref:System.Windows.Media.Brush>obiekty są używane do malowania kształtu <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.Fill%2A> . W poniższym przykładzie pociągnięcia i wypełnienia <xref:System.Windows.Shapes.Ellipse> są określone. Zwróć uwagę, że prawidłowe dane wejściowe właściwości pędzla mogą być słowami kluczowymi lub szesnastkowymi wartościami koloru. Aby uzyskać więcej informacji na temat dostępnych słów kluczowych koloru, zobacz właściwości <xref:System.Windows.Media.Colors> klasy w <xref:System.Windows.Media> przestrzeni nazw.  
  
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
  
 Na poniższej ilustracji przedstawiono renderowane <xref:System.Windows.Shapes.Ellipse> .  
  
 ![Elipsa](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternatywnie, można użyć składni elementu właściwości, aby jawnie utworzyć <xref:System.Windows.Media.SolidColorBrush> obiekt, aby malować kształt z pełnym kolorem.  
  
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
  
 ![Ilustracja przedstawiająca SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Możesz również malować obrys kształtu lub wypełnić kolorami gradientów, obrazów, wzorców i innych. Aby uzyskać więcej informacji, zobacz [rysowanie z pełnymi kolorami i gradientami — Omówienie](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a>Kształty rozciągane  
 <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon> Wszystkie klasy,,, <xref:System.Windows.Shapes.Polyline> i <xref:System.Windows.Shapes.Rectangle> mają <xref:System.Windows.Shapes.Shape.Stretch%2A> Właściwość. Ta właściwość określa, w jaki sposób <xref:System.Windows.Shapes.Shape> zawartość obiektu (kształt do rysowania) jest rozciągana w celu wypełnienia <xref:System.Windows.Shapes.Shape> obszaru układu obiektu. <xref:System.Windows.Shapes.Shape>Przestrzeń układu obiektu to ilość miejsca <xref:System.Windows.Shapes.Shape> przydzielonego przez system układu ze względu na <xref:System.Windows.FrameworkElement.Width%2A> ustawienie jawne i <xref:System.Windows.FrameworkElement.Height%2A> lub z powodu jego <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ustawień i. Aby uzyskać dodatkowe informacje na temat układu w Windows Presentation Foundation, zobacz Omówienie [układu](../advanced/layout.md) .  
  
 Właściwość rozciąganie przyjmuje jedną z następujących wartości:  
  
- <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu nie jest rozciągana.  
  
- <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągana w celu wypełnienia jego obszaru układu.  Współczynnik proporcji nie jest zachowywany.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągana jak najwięcej, aby wypełnić jego przestrzeń układu przy zachowaniu oryginalnego współczynnika proporcji.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągana w celu całkowitego wypełnienia jego obszaru układu, zachowując jego oryginalny współczynnik proporcji.  
  
 Należy pamiętać, że po <xref:System.Windows.Shapes.Shape> rozciągnięciu zawartości obiektu <xref:System.Windows.Shapes.Shape> Konspekt obiektu jest malowany po rozciągnięciu.  
  
 W poniższym przykładzie <xref:System.Windows.Shapes.Polygon> jest używany do rysowania bardzo małego trójkąta od (0, 0) do (od 0 do 1) do (1, 1). <xref:System.Windows.Shapes.Polygon>Obiekt i ma <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> ustawioną wartość 100, a jego właściwość rozciągania ma wartość Fill. W efekcie <xref:System.Windows.Shapes.Polygon> zawartość obiektu (trójkąt) jest rozciągana w celu wypełnienia większej ilości miejsca.  
  
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
 <xref:System.Windows.Media.Transform>Klasa zapewnia środki do przekształcania kształtów w płaszczyźnie dwuwymiarowej.  Różne typy transformacji obejmują rotację ( <xref:System.Windows.Media.RotateTransform> ), skalę ( <xref:System.Windows.Media.ScaleTransform> ), skośność ( <xref:System.Windows.Media.SkewTransform> ) i translację ( <xref:System.Windows.Media.TranslateTransform> ).  
  
 Typowa transformacja do zastosowania do kształtu jest rotacją.  Aby obrócić kształt, Utwórz <xref:System.Windows.Media.RotateTransform> i określ jego <xref:System.Windows.Media.RotateTransform.Angle%2A> . Do <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 obraca element 45 stopni w prawo; kąt 90 obraca element o wartości 90 stopni w prawo i tak dalej. Ustaw <xref:System.Windows.Media.RotateTransform.CenterX%2A> właściwości i, <xref:System.Windows.Media.RotateTransform.CenterY%2A> Jeśli chcesz kontrolować punkt, w którym element jest obrócony. Te wartości właściwości są wyrażane w przestrzeni współrzędnych elementu, który jest przekształcany. <xref:System.Windows.Media.RotateTransform.CenterX%2A>i <xref:System.Windows.Media.RotateTransform.CenterY%2A> mają wartości domyślne równe zero. Na koniec zastosuj <xref:System.Windows.Media.RotateTransform> do elementu. Jeśli nie chcesz, aby transformacja miała wpływ na układ, ustaw właściwość kształtu <xref:System.Windows.UIElement.RenderTransform%2A> .  
  
 W poniższym przykładzie <xref:System.Windows.Media.RotateTransform> jest używany do obracania kształtu 45 stopni wokół lewego górnego rogu kształtu (0, 0).  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 W następnym przykładzie inny kształt jest obrócony o 45 stopni, ale ten czas jest obracany o punkt (25, 50).  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Na poniższej ilustracji przedstawiono wyniki zastosowania dwóch transformacji.  
  
 ![45 stopni obrotów z różnymi punktami środkowymi](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 W poprzednich przykładach do każdego obiektu kształtu zastosowano pojedyncze przekształcenie. Aby zastosować wiele przekształceń do kształtu (lub dowolnego innego elementu interfejsu użytkownika), użyj <xref:System.Windows.Media.TransformGroup> .  
  
## <a name="see-also"></a>Zobacz też

- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Przegląd Malowanie jednolitymi kolorami i gradientami](painting-with-solid-colors-and-gradients-overview.md)
- [Przegląd Geometria](geometry-overview.md)
- [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Przegląd Animacja](animation-overview.md)
