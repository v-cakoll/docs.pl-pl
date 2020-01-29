---
title: Przegląd kształtów i podstawowe informacje o rysowaniu
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
ms.openlocfilehash: dfdbf67d35cbb13e80d0c5184f165b0cc660e2ef
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731622"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="846b6-102">Przegląd Kształty i podstawowe rysowanie w WPF</span><span class="sxs-lookup"><span data-stu-id="846b6-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="846b6-103">Ten temat zawiera omówienie sposobu rysowania przy użyciu obiektów <xref:System.Windows.Shapes.Shape>.</span><span class="sxs-lookup"><span data-stu-id="846b6-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="846b6-104"><xref:System.Windows.Shapes.Shape> jest typem <xref:System.Windows.UIElement>, który umożliwia narysowanie kształtu na ekranie.</span><span class="sxs-lookup"><span data-stu-id="846b6-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="846b6-105">Ponieważ są to elementy interfejsu użytkownika, obiekty <xref:System.Windows.Shapes.Shape> mogą być używane wewnątrz elementów <xref:System.Windows.Controls.Panel> i większości formantów.</span><span class="sxs-lookup"><span data-stu-id="846b6-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="846b6-106">oferuje kilka warstw dostępu do usług graficznych i renderowania.</span><span class="sxs-lookup"><span data-stu-id="846b6-106">offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="846b6-107">W górnej warstwie obiekty <xref:System.Windows.Shapes.Shape> są łatwe w użyciu i zapewniają wiele przydatnych funkcji, takich jak układ i uczestnictwo w systemie zdarzeń [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="846b6-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  

<a name="shapes"></a>   
## <a name="shape-objects"></a><span data-ttu-id="846b6-108">Obiekty Shape</span><span class="sxs-lookup"><span data-stu-id="846b6-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="846b6-109">zawiera wiele gotowych do użycia obiektów <xref:System.Windows.Shapes.Shape>.</span><span class="sxs-lookup"><span data-stu-id="846b6-109">provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="846b6-110">Wszystkie obiekty kształtu dziedziczą z klasy <xref:System.Windows.Shapes.Shape>.</span><span class="sxs-lookup"><span data-stu-id="846b6-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="846b6-111">Dostępne obiekty kształtu obejmują <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>i <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="846b6-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="846b6-112"><xref:System.Windows.Shapes.Shape> obiekty współużytkują następujące typowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="846b6-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
- <span data-ttu-id="846b6-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Opisuje sposób malowania konturu kształtu.</span><span class="sxs-lookup"><span data-stu-id="846b6-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
- <span data-ttu-id="846b6-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: opisuje grubość konturu kształtu.</span><span class="sxs-lookup"><span data-stu-id="846b6-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
- <span data-ttu-id="846b6-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Opisuje sposób malowania wnętrza kształtu.</span><span class="sxs-lookup"><span data-stu-id="846b6-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
- <span data-ttu-id="846b6-116">Właściwości danych w celu określenia współrzędnych i wierzchołków mierzonych w pikselach niezależnych od urządzenia.</span><span class="sxs-lookup"><span data-stu-id="846b6-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="846b6-117">Ponieważ pochodzą one z <xref:System.Windows.UIElement>, obiekty Shape mogą być używane wewnątrz paneli i większości formantów.</span><span class="sxs-lookup"><span data-stu-id="846b6-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="846b6-118">Panel <xref:System.Windows.Controls.Canvas> jest szczególnie dobrym wyborem w przypadku tworzenia złożonych rysunków, ponieważ obsługuje pozycjonowanie bezwzględne jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="846b6-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="846b6-119">Klasa <xref:System.Windows.Shapes.Line> umożliwia narysowanie linii między dwoma punktami.</span><span class="sxs-lookup"><span data-stu-id="846b6-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="846b6-120">W poniższym przykładzie pokazano kilka sposobów określania współrzędnych linii i właściwości obrysu.</span><span class="sxs-lookup"><span data-stu-id="846b6-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="846b6-121">Na poniższej ilustracji przedstawiono renderowane <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="846b6-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="846b6-122">![Ilustracja przedstawiająca linię](./media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="846b6-122">![Line illustration](./media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="846b6-123">Chociaż Klasa <xref:System.Windows.Shapes.Line> udostępnia Właściwość <xref:System.Windows.Shapes.Shape.Fill%2A>, ustawienie jej nie ma żadnego efektu, ponieważ <xref:System.Windows.Shapes.Line> nie ma obszaru.</span><span class="sxs-lookup"><span data-stu-id="846b6-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="846b6-124">Innym typowym kształtem jest <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="846b6-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="846b6-125">Utwórz <xref:System.Windows.Shapes.Ellipse>, definiując właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> kształtu.</span><span class="sxs-lookup"><span data-stu-id="846b6-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="846b6-126">Aby narysować okrąg, określ <xref:System.Windows.Shapes.Ellipse>, których wartości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> są równe.</span><span class="sxs-lookup"><span data-stu-id="846b6-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="846b6-127">Na poniższej ilustracji przedstawiono przykład renderowanego <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="846b6-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="846b6-128">![Ilustracja przedstawiająca elipsę](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="846b6-128">![Ellipse illustration](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a><span data-ttu-id="846b6-129">Używanie ścieżek i geometrie</span><span class="sxs-lookup"><span data-stu-id="846b6-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="846b6-130">Klasa <xref:System.Windows.Shapes.Path> umożliwia rysowanie krzywych i złożonych kształtów.</span><span class="sxs-lookup"><span data-stu-id="846b6-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="846b6-131">Te krzywe i kształty są opisane przy użyciu <xref:System.Windows.Media.Geometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="846b6-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="846b6-132">Aby użyć <xref:System.Windows.Shapes.Path>, należy utworzyć <xref:System.Windows.Media.Geometry> i użyć go do ustawienia właściwości <xref:System.Windows.Shapes.Path.Data%2A> obiektu <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="846b6-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="846b6-133">Istnieje wiele obiektów <xref:System.Windows.Media.Geometry> do wyboru.</span><span class="sxs-lookup"><span data-stu-id="846b6-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="846b6-134">Klasy <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>i <xref:System.Windows.Media.EllipseGeometry> opisują stosunkowo proste kształty.</span><span class="sxs-lookup"><span data-stu-id="846b6-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="846b6-135">Aby utworzyć bardziej złożone kształty lub utworzyć krzywe, użyj <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="846b6-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="846b6-136">PathGeometry i PathSegments</span><span class="sxs-lookup"><span data-stu-id="846b6-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="846b6-137">obiekty <xref:System.Windows.Media.PathGeometry> składają się z co najmniej jednego obiektu <xref:System.Windows.Media.PathFigure>; Każda <xref:System.Windows.Media.PathFigure> reprezentuje inny "rysunek" lub "kształt".</span><span class="sxs-lookup"><span data-stu-id="846b6-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="846b6-138">Każda <xref:System.Windows.Media.PathFigure> składa się z jednego lub więcej obiektów <xref:System.Windows.Media.PathSegment>, z których każdy reprezentuje podłączoną część rysunku lub kształtu.</span><span class="sxs-lookup"><span data-stu-id="846b6-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="846b6-139">Typy segmentów obejmują następujące elementy: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>i <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="846b6-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="846b6-140">W poniższym przykładzie <xref:System.Windows.Shapes.Path> jest używany do rysowania krzywej Beziera kwadratu.</span><span class="sxs-lookup"><span data-stu-id="846b6-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="846b6-141">Na poniższej ilustracji przedstawiono renderowany kształt.</span><span class="sxs-lookup"><span data-stu-id="846b6-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="846b6-142">![Ilustracja przedstawiająca ścieżkę](./media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="846b6-142">![Path illustration](./media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="846b6-143">Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.PathGeometry> i innych klas <xref:System.Windows.Media.Geometry>, zobacz [Omówienie geometrii](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="846b6-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="846b6-144">Składnia języka XAML — skrócona</span><span class="sxs-lookup"><span data-stu-id="846b6-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="846b6-145">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]można także opisać <xref:System.Windows.Shapes.Path>za pomocą specjalnej składni skróconej.</span><span class="sxs-lookup"><span data-stu-id="846b6-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="846b6-146">W poniższym przykładzie Skrócona składnia jest używana do rysowania złożonego kształtu.</span><span class="sxs-lookup"><span data-stu-id="846b6-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="846b6-147">Na poniższej ilustracji przedstawiono renderowane <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="846b6-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="846b6-148">![Ilustracja przedstawiająca ścieżkę](./media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="846b6-148">![Path illustration](./media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="846b6-149">Ciąg atrybutu <xref:System.Windows.Shapes.Path.Data%2A> rozpoczyna się od polecenia "MoveTo" wskazywanego przez M, który ustanawia punkt początkowy dla ścieżki w układzie współrzędnych <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="846b6-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="846b6-150">parametry danych <xref:System.Windows.Shapes.Path> są rozróżniane wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="846b6-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="846b6-151">Wielka litera M wskazuje lokalizację bezwzględną dla nowego punktu bieżącego.</span><span class="sxs-lookup"><span data-stu-id="846b6-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="846b6-152">Małe litery m wskazują współrzędne względne.</span><span class="sxs-lookup"><span data-stu-id="846b6-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="846b6-153">Pierwszy segment jest zakrzywioną krzywą Beziera rozpoczynającą się o (100 200) i kończącą się na (400 175), narysowanym przy użyciu dwóch punktów kontrolnych (100, 25) i (400 350).</span><span class="sxs-lookup"><span data-stu-id="846b6-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="846b6-154">Ten segment jest wskazywany przez polecenie C w ciągu atrybutu <xref:System.Windows.Shapes.Path.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="846b6-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="846b6-155">Ponownie Wielka litera C wskazuje ścieżkę bezwzględną; Mała litera c wskazuje ścieżkę względną.</span><span class="sxs-lookup"><span data-stu-id="846b6-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="846b6-156">Drugi segment zaczyna się od bezwzględnej wartości "LineTo" polecenia H, które określa wiersz rysowany z poprzedniego punktu końcowego ścieżki podrzędnej (400 175) do nowego punktu końcowego (280 175).</span><span class="sxs-lookup"><span data-stu-id="846b6-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="846b6-157">Ponieważ jest to w poziomie polecenie "LineTo", określona wartość jest Współrzędna *x*.</span><span class="sxs-lookup"><span data-stu-id="846b6-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="846b6-158">Aby uzyskać pełną składnię ścieżki, zobacz Odwołanie <xref:System.Windows.Shapes.Path.Data%2A> i [Tworzenie kształtu przy użyciu PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="846b6-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a><span data-ttu-id="846b6-159">Malowanie kształtów</span><span class="sxs-lookup"><span data-stu-id="846b6-159">Painting Shapes</span></span>  
 <span data-ttu-id="846b6-160">obiekty <xref:System.Windows.Media.Brush> są używane do malowania <xref:System.Windows.Shapes.Shape.Stroke%2A> kształtu i <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="846b6-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="846b6-161">W poniższym przykładzie określono pociągnięcie i wypełnienie <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="846b6-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="846b6-162">Zwróć uwagę, że prawidłowe dane wejściowe właściwości pędzla mogą być słowami kluczowymi lub szesnastkowymi wartościami koloru.</span><span class="sxs-lookup"><span data-stu-id="846b6-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="846b6-163">Aby uzyskać więcej informacji na temat dostępnych słów kluczowych koloru, zobacz właściwości klasy <xref:System.Windows.Media.Colors> w przestrzeni nazw <xref:System.Windows.Media>.</span><span class="sxs-lookup"><span data-stu-id="846b6-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
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
  
 <span data-ttu-id="846b6-164">Na poniższej ilustracji przedstawiono renderowane <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="846b6-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="846b6-165">![Elipsa](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="846b6-165">![An ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="846b6-166">Alternatywnie można użyć składni elementu właściwości, aby jawnie utworzyć obiekt <xref:System.Windows.Media.SolidColorBrush>, aby malować kształt z pełnym kolorem.</span><span class="sxs-lookup"><span data-stu-id="846b6-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
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
  
 <span data-ttu-id="846b6-167">Na poniższej ilustracji przedstawiono renderowany kształt.</span><span class="sxs-lookup"><span data-stu-id="846b6-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="846b6-168">![Ilustracja przedstawiająca SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="846b6-168">![SolidColorBrush illustration](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="846b6-169">Możesz również malować obrys kształtu lub wypełnić kolorami gradientów, obrazów, wzorców i innych.</span><span class="sxs-lookup"><span data-stu-id="846b6-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="846b6-170">Aby uzyskać więcej informacji, zobacz [rysowanie z pełnymi kolorami i gradientami — Omówienie](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="846b6-170">For more information, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a><span data-ttu-id="846b6-171">Kształty rozciągane</span><span class="sxs-lookup"><span data-stu-id="846b6-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="846b6-172">Klasy <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>i <xref:System.Windows.Shapes.Rectangle> mają właściwość <xref:System.Windows.Shapes.Shape.Stretch%2A>.</span><span class="sxs-lookup"><span data-stu-id="846b6-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="846b6-173">Ta właściwość określa, jak zawartość obiektu <xref:System.Windows.Shapes.Shape> (kształt do rysowania) jest rozciągana w celu wypełnienia obszaru układu obiektu <xref:System.Windows.Shapes.Shape>.</span><span class="sxs-lookup"><span data-stu-id="846b6-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="846b6-174">Przestrzeń układu obiektu <xref:System.Windows.Shapes.Shape> jest ilością miejsca, do której <xref:System.Windows.Shapes.Shape> jest przydzielone przez system układu z powodu jawnego ustawienia <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> lub z powodu jego <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ustawień.</span><span class="sxs-lookup"><span data-stu-id="846b6-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="846b6-175">Aby uzyskać dodatkowe informacje na temat układu w Windows Presentation Foundation, zobacz Omówienie [układu](../advanced/layout.md) .</span><span class="sxs-lookup"><span data-stu-id="846b6-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="846b6-176">Właściwość rozciąganie przyjmuje jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="846b6-176">The Stretch property takes one of the following values:</span></span>  
  
- <span data-ttu-id="846b6-177"><xref:System.Windows.Media.Stretch.None>: zawartość obiektu <xref:System.Windows.Shapes.Shape> nie jest rozciągana.</span><span class="sxs-lookup"><span data-stu-id="846b6-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
- <span data-ttu-id="846b6-178"><xref:System.Windows.Media.Stretch.Fill>: zawartość obiektu <xref:System.Windows.Shapes.Shape> jest rozciągana w celu wypełnienia jego obszaru układu.</span><span class="sxs-lookup"><span data-stu-id="846b6-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="846b6-179">Współczynnik proporcji nie jest zachowywany.</span><span class="sxs-lookup"><span data-stu-id="846b6-179">Aspect ratio is not preserved.</span></span>  
  
- <span data-ttu-id="846b6-180"><xref:System.Windows.Media.Stretch.Uniform>: zawartość obiektu <xref:System.Windows.Shapes.Shape> jest rozciągana możliwie jak najwięcej, aby wypełnić jego przestrzeń układu przy zachowaniu oryginalnego współczynnika proporcji.</span><span class="sxs-lookup"><span data-stu-id="846b6-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
- <span data-ttu-id="846b6-181"><xref:System.Windows.Media.Stretch.UniformToFill>: zawartość obiektu <xref:System.Windows.Shapes.Shape> jest rozciągana w celu całkowitego wypełnienia jego obszaru układu, zachowując jego oryginalny współczynnik proporcji.</span><span class="sxs-lookup"><span data-stu-id="846b6-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="846b6-182">Należy pamiętać, że po rozciągnięciu zawartości obiektu <xref:System.Windows.Shapes.Shape>, kontur obiektu <xref:System.Windows.Shapes.Shape> zostanie namalowany po rozciągnięciu.</span><span class="sxs-lookup"><span data-stu-id="846b6-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="846b6-183">W poniższym przykładzie <xref:System.Windows.Shapes.Polygon> jest używany do rysowania bardzo małego trójkąta od (0, 0) do (od 0 do 1) do (1, 1).</span><span class="sxs-lookup"><span data-stu-id="846b6-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="846b6-184"><xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> obiektu <xref:System.Windows.Shapes.Polygon> są ustawione na 100, a jej Właściwość rozciągania ma wartość Fill.</span><span class="sxs-lookup"><span data-stu-id="846b6-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="846b6-185">W efekcie zawartość obiektu <xref:System.Windows.Shapes.Polygon> (trójkąt) są rozciągane w celu wypełnienia większej ilości miejsca.</span><span class="sxs-lookup"><span data-stu-id="846b6-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
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
## <a name="transforming-shapes"></a><span data-ttu-id="846b6-186">Przekształcanie kształtów</span><span class="sxs-lookup"><span data-stu-id="846b6-186">Transforming Shapes</span></span>  
 <span data-ttu-id="846b6-187">Klasa <xref:System.Windows.Media.Transform> zapewnia środki do przekształcania kształtów w płaszczyźnie dwuwymiarowej.</span><span class="sxs-lookup"><span data-stu-id="846b6-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="846b6-188">Różne typy transformacji obejmują rotację (<xref:System.Windows.Media.RotateTransform>), skalę (<xref:System.Windows.Media.ScaleTransform>), skośność (<xref:System.Windows.Media.SkewTransform>) i translację (<xref:System.Windows.Media.TranslateTransform>).</span><span class="sxs-lookup"><span data-stu-id="846b6-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="846b6-189">Typowa transformacja do zastosowania do kształtu jest rotacją.</span><span class="sxs-lookup"><span data-stu-id="846b6-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="846b6-190">Aby obrócić kształt, Utwórz <xref:System.Windows.Media.RotateTransform> i określ jego <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span><span class="sxs-lookup"><span data-stu-id="846b6-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="846b6-191"><xref:System.Windows.Media.RotateTransform.Angle%2A> 45 powoduje obrócenie elementu o 45 stopni w prawo; kąt 90 obraca element 90 stopni w prawo; i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="846b6-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="846b6-192">Ustaw właściwości <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A>, jeśli chcesz kontrolować punkt, w którym element jest obrócony.</span><span class="sxs-lookup"><span data-stu-id="846b6-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="846b6-193">Te wartości właściwości są wyrażane w przestrzeni współrzędnych elementu, który jest przekształcany.</span><span class="sxs-lookup"><span data-stu-id="846b6-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="846b6-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> mają wartości domyślne równe zero.</span><span class="sxs-lookup"><span data-stu-id="846b6-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="846b6-195">Na koniec zastosuj <xref:System.Windows.Media.RotateTransform> do elementu.</span><span class="sxs-lookup"><span data-stu-id="846b6-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="846b6-196">Jeśli nie chcesz, aby transformacja miała wpływ na układ, ustaw właściwość <xref:System.Windows.UIElement.RenderTransform%2A> kształtu.</span><span class="sxs-lookup"><span data-stu-id="846b6-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="846b6-197">W poniższym przykładzie <xref:System.Windows.Media.RotateTransform> jest używany do obracania kształtu 45 stopni wokół lewego górnego rogu kształtu (0, 0).</span><span class="sxs-lookup"><span data-stu-id="846b6-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="846b6-198">W następnym przykładzie inny kształt jest obrócony o 45 stopni, ale ten czas jest obracany o punkt (25, 50).</span><span class="sxs-lookup"><span data-stu-id="846b6-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="846b6-199">Na poniższej ilustracji przedstawiono wyniki zastosowania dwóch transformacji.</span><span class="sxs-lookup"><span data-stu-id="846b6-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="846b6-200">![45 stopni obrotów z różnymi punktami środkowymi](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="846b6-200">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="846b6-201">W poprzednich przykładach do każdego obiektu kształtu zastosowano pojedyncze przekształcenie.</span><span class="sxs-lookup"><span data-stu-id="846b6-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="846b6-202">Aby zastosować wiele przekształceń do kształtu (lub dowolnego innego elementu interfejsu użytkownika), użyj <xref:System.Windows.Media.TransformGroup>.</span><span class="sxs-lookup"><span data-stu-id="846b6-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846b6-203">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="846b6-203">See also</span></span>

- [<span data-ttu-id="846b6-204">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="846b6-204">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="846b6-205">Malowanie jednolitymi kolorami i gradientami — przegląd</span><span class="sxs-lookup"><span data-stu-id="846b6-205">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="846b6-206">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="846b6-206">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="846b6-207">Przewodnik: moja pierwsza aplikacja klasyczna WPF</span><span class="sxs-lookup"><span data-stu-id="846b6-207">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [<span data-ttu-id="846b6-208">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="846b6-208">Animation Overview</span></span>](animation-overview.md)
