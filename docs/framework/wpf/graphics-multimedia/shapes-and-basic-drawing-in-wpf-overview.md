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
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="5a007-102">Przegląd Kształty i podstawowe rysowanie w WPF</span><span class="sxs-lookup"><span data-stu-id="5a007-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="5a007-103">W tym temacie przedstawiono omówienie sposobu rysowania z <xref:System.Windows.Shapes.Shape> obiektami.</span><span class="sxs-lookup"><span data-stu-id="5a007-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="5a007-104">A <xref:System.Windows.Shapes.Shape> jest typem, <xref:System.Windows.UIElement> który umożliwia rysowanie kształtu na ekranie.</span><span class="sxs-lookup"><span data-stu-id="5a007-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="5a007-105">Ponieważ są one elementy <xref:System.Windows.Shapes.Shape> interfejsu użytkownika, <xref:System.Windows.Controls.Panel> obiekty mogą być używane wewnątrz elementów i większość formantów.</span><span class="sxs-lookup"><span data-stu-id="5a007-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="5a007-106">oferuje kilka warstw dostępu do grafiki i usług renderowania.</span><span class="sxs-lookup"><span data-stu-id="5a007-106">offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="5a007-107">W górnej warstwie <xref:System.Windows.Shapes.Shape> obiekty są łatwe w użyciu i zapewniają wiele [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przydatnych funkcji, takich jak układ i uczestnictwo w systemie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5a007-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  

<a name="shapes"></a>
## <a name="shape-objects"></a><span data-ttu-id="5a007-108">Obiekty kształtu</span><span class="sxs-lookup"><span data-stu-id="5a007-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="5a007-109">zawiera wiele gotowych do <xref:System.Windows.Shapes.Shape> użycia obiektów.</span><span class="sxs-lookup"><span data-stu-id="5a007-109">provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="5a007-110">Wszystkie obiekty kształtu <xref:System.Windows.Shapes.Shape> dziedziczą z klasy.</span><span class="sxs-lookup"><span data-stu-id="5a007-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="5a007-111">Dostępne obiekty <xref:System.Windows.Shapes.Ellipse>kształtu to <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>, , i .</span><span class="sxs-lookup"><span data-stu-id="5a007-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="5a007-112"><xref:System.Windows.Shapes.Shape>obiekty mają następujące wspólne właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a007-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
- <span data-ttu-id="5a007-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Opisuje sposób malowania konturu kształtu.</span><span class="sxs-lookup"><span data-stu-id="5a007-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
- <span data-ttu-id="5a007-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Opisuje grubość konturu kształtu.</span><span class="sxs-lookup"><span data-stu-id="5a007-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
- <span data-ttu-id="5a007-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Opisuje sposób malowania wnętrza kształtu.</span><span class="sxs-lookup"><span data-stu-id="5a007-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
- <span data-ttu-id="5a007-116">Właściwości danych do określania współrzędnych i wierzchołków, mierzone w pikselach niezależnych od urządzenia.</span><span class="sxs-lookup"><span data-stu-id="5a007-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="5a007-117">Ponieważ pochodzą one <xref:System.Windows.UIElement>od , obiekty kształtu mogą być używane wewnątrz paneli i większości formantów.</span><span class="sxs-lookup"><span data-stu-id="5a007-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="5a007-118">Panel <xref:System.Windows.Controls.Canvas> jest szczególnie dobrym wyborem do tworzenia złożonych rysunków, ponieważ obsługuje bezwzględne pozycjonowanie obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5a007-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="5a007-119">Klasa <xref:System.Windows.Shapes.Line> umożliwia narysowanie linii między dwoma punktami.</span><span class="sxs-lookup"><span data-stu-id="5a007-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="5a007-120">W poniższym przykładzie przedstawiono kilka sposobów określania współrzędnych linii i właściwości obrysu.</span><span class="sxs-lookup"><span data-stu-id="5a007-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="5a007-121">Na poniższej ilustracji <xref:System.Windows.Shapes.Line>przedstawiono renderowany plik .</span><span class="sxs-lookup"><span data-stu-id="5a007-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="5a007-122">![Ilustracja liniowa](./media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="5a007-122">![Line illustration](./media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="5a007-123">Chociaż <xref:System.Windows.Shapes.Line> klasa zapewnia <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość, ustawienie nie ma <xref:System.Windows.Shapes.Line> wpływu, ponieważ a nie ma obszaru.</span><span class="sxs-lookup"><span data-stu-id="5a007-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="5a007-124">Innym wspólnym kształtem <xref:System.Windows.Shapes.Ellipse>jest .</span><span class="sxs-lookup"><span data-stu-id="5a007-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="5a007-125">Utwórz, <xref:System.Windows.Shapes.Ellipse> definiując kształt <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> i właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a007-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="5a007-126">Aby narysować okrąg, <xref:System.Windows.Shapes.Ellipse> należy określić, czyje <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> wartości są równe.</span><span class="sxs-lookup"><span data-stu-id="5a007-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="5a007-127">Na poniższej ilustracji przedstawiono <xref:System.Windows.Shapes.Ellipse>przykład renderowanego pliku .</span><span class="sxs-lookup"><span data-stu-id="5a007-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="5a007-128">![Ilustracja elipsy](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="5a007-128">![Ellipse illustration](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a><span data-ttu-id="5a007-129">Korzystanie ze ścieżek i geometrii</span><span class="sxs-lookup"><span data-stu-id="5a007-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="5a007-130">Klasa <xref:System.Windows.Shapes.Path> umożliwia rysowanie krzywych i złożonych kształtów.</span><span class="sxs-lookup"><span data-stu-id="5a007-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="5a007-131">Te krzywe i kształty <xref:System.Windows.Media.Geometry> są opisane za pomocą obiektów.</span><span class="sxs-lookup"><span data-stu-id="5a007-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="5a007-132">Aby użyć <xref:System.Windows.Shapes.Path>programu , <xref:System.Windows.Media.Geometry> należy utworzyć i <xref:System.Windows.Shapes.Path> użyć <xref:System.Windows.Shapes.Path.Data%2A> go do ustawiania właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="5a007-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="5a007-133">Istnieje wiele <xref:System.Windows.Media.Geometry> obiektów do wyboru.</span><span class="sxs-lookup"><span data-stu-id="5a007-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="5a007-134">Klasy <xref:System.Windows.Media.LineGeometry> <xref:System.Windows.Media.RectangleGeometry>, <xref:System.Windows.Media.EllipseGeometry> i klasy opisują stosunkowo proste kształty.</span><span class="sxs-lookup"><span data-stu-id="5a007-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="5a007-135">Aby utworzyć bardziej złożone kształty lub <xref:System.Windows.Media.PathGeometry>utworzyć krzywe, użyj pliku .</span><span class="sxs-lookup"><span data-stu-id="5a007-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="5a007-136">PathGeometry i PathSegments</span><span class="sxs-lookup"><span data-stu-id="5a007-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="5a007-137"><xref:System.Windows.Media.PathGeometry>obiekty składają się z <xref:System.Windows.Media.PathFigure> jednego lub więcej obiektów; każdy <xref:System.Windows.Media.PathFigure> reprezentuje inną "figurę" lub kształt.</span><span class="sxs-lookup"><span data-stu-id="5a007-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="5a007-138">Każdy <xref:System.Windows.Media.PathFigure> z nich składa się <xref:System.Windows.Media.PathSegment> z jednego lub więcej obiektów, z których każdy reprezentuje połączoną część figury lub kształtu.</span><span class="sxs-lookup"><span data-stu-id="5a007-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="5a007-139">Typy segmentów <xref:System.Windows.Media.LineSegment>są <xref:System.Windows.Media.BezierSegment>następujące: , i <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="5a007-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="5a007-140">W poniższym przykładzie <xref:System.Windows.Shapes.Path> a służy do rysowania kwadratowej krzywej Beziera.</span><span class="sxs-lookup"><span data-stu-id="5a007-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="5a007-141">Na poniższej ilustracji przedstawiono renderowany kształt.</span><span class="sxs-lookup"><span data-stu-id="5a007-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="5a007-142">![Ilustracja ścieżki](./media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="5a007-142">![Path illustration](./media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="5a007-143">Aby uzyskać <xref:System.Windows.Media.PathGeometry> więcej informacji <xref:System.Windows.Media.Geometry> na temat i innych klas, zobacz [Przegląd geometrii](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5a007-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="5a007-144">Składnia skrócona XAML</span><span class="sxs-lookup"><span data-stu-id="5a007-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="5a007-145">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]programze można również użyć specjalnej skróconej składni, aby opisać plik <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="5a007-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="5a007-146">W poniższym przykładzie skrócona składnia jest używana do rysowania złożonego kształtu.</span><span class="sxs-lookup"><span data-stu-id="5a007-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="5a007-147">Na poniższej ilustracji <xref:System.Windows.Shapes.Path>przedstawiono renderowany plik .</span><span class="sxs-lookup"><span data-stu-id="5a007-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="5a007-148">![Ilustracja ścieżki](./media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="5a007-148">![Path illustration](./media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="5a007-149">Ciąg <xref:System.Windows.Shapes.Path.Data%2A> atrybutu rozpoczyna się od polecenia "moveto", wskazanego przez M, które ustanawia punkt początkowy <xref:System.Windows.Controls.Canvas>ścieżki w układzie współrzędnych .</span><span class="sxs-lookup"><span data-stu-id="5a007-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="5a007-150"><xref:System.Windows.Shapes.Path>parametry danych są rozróżniane wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="5a007-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="5a007-151">Stolica M wskazuje bezwzględną lokalizację dla nowego bieżącego punktu.</span><span class="sxs-lookup"><span data-stu-id="5a007-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="5a007-152">Małe litery m wskazywałyby współrzędne względne.</span><span class="sxs-lookup"><span data-stu-id="5a007-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="5a007-153">Pierwszy segment to sześcienna krzywa Beziera rozpoczynająca się od (100 200) i kończąca się na (400 175), narysowana przy użyciu dwóch punktów kontrolnych (100,25) i (400 350).</span><span class="sxs-lookup"><span data-stu-id="5a007-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="5a007-154">Ten segment jest wskazywany <xref:System.Windows.Shapes.Path.Data%2A> przez polecenie C w ciągu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5a007-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="5a007-155">Ponownie, stolica C wskazuje ścieżkę bezwzględną; małe litery c wskazywałyby względną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="5a007-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="5a007-156">Drugi segment rozpoczyna się bezwzględnym poziomym poleceniem "lineto" H, które określa linię narysowaną od punktu końcowego poprzedniej ścieżki podrzędnej (400 175) do nowego punktu końcowego (280 175).</span><span class="sxs-lookup"><span data-stu-id="5a007-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="5a007-157">Ponieważ jest to poziome polecenie "lineto", określona wartość jest współrzędną *x.*</span><span class="sxs-lookup"><span data-stu-id="5a007-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="5a007-158">Aby zapoznać się ze składnią ścieżki pełnej, zobacz <xref:System.Windows.Shapes.Path.Data%2A> odwołanie i Tworzenie [kształtu przy użyciu ścieżkiGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="5a007-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a><span data-ttu-id="5a007-159">Malowanie kształtów</span><span class="sxs-lookup"><span data-stu-id="5a007-159">Painting Shapes</span></span>  
 <span data-ttu-id="5a007-160"><xref:System.Windows.Media.Brush>obiekty są używane do malowania kształtu <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a007-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="5a007-161">W poniższym przykładzie określono obrys i wypełnienie. <xref:System.Windows.Shapes.Ellipse></span><span class="sxs-lookup"><span data-stu-id="5a007-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="5a007-162">Należy zauważyć, że prawidłowe dane wejściowe dla właściwości pędzla może być słowem kluczowym lub szesnastkowej wartości koloru.</span><span class="sxs-lookup"><span data-stu-id="5a007-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="5a007-163">Aby uzyskać więcej informacji na temat dostępnych <xref:System.Windows.Media.Colors> słów kluczowych <xref:System.Windows.Media> kolorów, zobacz właściwości klasy w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="5a007-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
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
  
 <span data-ttu-id="5a007-164">Na poniższej ilustracji <xref:System.Windows.Shapes.Ellipse>przedstawiono renderowany plik .</span><span class="sxs-lookup"><span data-stu-id="5a007-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="5a007-165">![Elipsę](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="5a007-165">![An ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="5a007-166">Alternatywnie można użyć składni elementu właściwości, aby <xref:System.Windows.Media.SolidColorBrush> jawnie utworzyć obiekt do malowania kształtu jednolitym kolorem.</span><span class="sxs-lookup"><span data-stu-id="5a007-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
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
  
 <span data-ttu-id="5a007-167">Na poniższej ilustracji przedstawiono renderowany kształt.</span><span class="sxs-lookup"><span data-stu-id="5a007-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="5a007-168">![Ilustracja SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="5a007-168">![SolidColorBrush illustration](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="5a007-169">Można również malować obrys kształtu lub wypełniać gradientami, obrazami, wzorami i innymi.</span><span class="sxs-lookup"><span data-stu-id="5a007-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="5a007-170">Aby uzyskać więcej informacji, zobacz [Omówienie malowanie za pomocą jednolitych kolorów i gradientów](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5a007-170">For more information, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a><span data-ttu-id="5a007-171">Rozciągliwe kształty</span><span class="sxs-lookup"><span data-stu-id="5a007-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="5a007-172">, <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle> i klasy <xref:System.Windows.Shapes.Shape.Stretch%2A> wszystkie mają właściwość.</span><span class="sxs-lookup"><span data-stu-id="5a007-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="5a007-173">Ta właściwość określa <xref:System.Windows.Shapes.Shape> sposób rozciągnięcia zawartości obiektu (kształtu do narysowania) w <xref:System.Windows.Shapes.Shape> celu wypełnienia przestrzeni układu obiektu.</span><span class="sxs-lookup"><span data-stu-id="5a007-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="5a007-174">Obszar <xref:System.Windows.Shapes.Shape> układu obiektu to <xref:System.Windows.Shapes.Shape> ilość miejsca przydzielonego przez system układu, ze względu <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> na jawne <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ustawienie <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> lub ze względu na jego i ustawienia.</span><span class="sxs-lookup"><span data-stu-id="5a007-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="5a007-175">Aby uzyskać dodatkowe informacje na temat układu w programie Windows Presentation Foundation, zobacz [Omówienie układu.](../advanced/layout.md)</span><span class="sxs-lookup"><span data-stu-id="5a007-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="5a007-176">Właściwość Stretch przyjmuje jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="5a007-176">The Stretch property takes one of the following values:</span></span>  
  
- <span data-ttu-id="5a007-177"><xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu nie jest rozciągnięta.</span><span class="sxs-lookup"><span data-stu-id="5a007-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
- <span data-ttu-id="5a007-178"><xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągnięta, aby wypełnić jego przestrzeń w układzie.</span><span class="sxs-lookup"><span data-stu-id="5a007-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="5a007-179">Współczynnik proporcji nie jest zachowywany.</span><span class="sxs-lookup"><span data-stu-id="5a007-179">Aspect ratio is not preserved.</span></span>  
  
- <span data-ttu-id="5a007-180"><xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągnięta w miarę możliwości, aby wypełnić jego przestrzeń w układzie, zachowując oryginalny współczynnik proporcji.</span><span class="sxs-lookup"><span data-stu-id="5a007-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
- <span data-ttu-id="5a007-181"><xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągnięta, aby całkowicie wypełnić jego przestrzeń w układzie, zachowując oryginalny współczynnik proporcji.</span><span class="sxs-lookup"><span data-stu-id="5a007-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="5a007-182">Należy zauważyć, <xref:System.Windows.Shapes.Shape> że gdy zawartość obiektu jest <xref:System.Windows.Shapes.Shape> rozciągnięta, kontur obiektu jest malowany po rozciąganiu.</span><span class="sxs-lookup"><span data-stu-id="5a007-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="5a007-183">W poniższym przykładzie a <xref:System.Windows.Shapes.Polygon> służy do rysowania bardzo małego trójkąta od (0,0) do (0,1) do (1,1).</span><span class="sxs-lookup"><span data-stu-id="5a007-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="5a007-184">Obiekt <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.FrameworkElement.Width%2A> jest ustawiony <xref:System.Windows.FrameworkElement.Height%2A> na 100, a jego właściwość stretch jest ustawiona na Wypełnienie.</span><span class="sxs-lookup"><span data-stu-id="5a007-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="5a007-185">W rezultacie zawartość <xref:System.Windows.Shapes.Polygon> obiektu (trójkąt) jest rozciągnięta, aby wypełnić większą przestrzeń.</span><span class="sxs-lookup"><span data-stu-id="5a007-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
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
## <a name="transforming-shapes"></a><span data-ttu-id="5a007-186">Przekształcanie kształtów</span><span class="sxs-lookup"><span data-stu-id="5a007-186">Transforming Shapes</span></span>  
 <span data-ttu-id="5a007-187">Klasa <xref:System.Windows.Media.Transform> zapewnia środki do przekształcania kształtów w płaszczyźnie dwuwymiarowej.</span><span class="sxs-lookup"><span data-stu-id="5a007-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="5a007-188">Różne rodzaje transformacji obejmują<xref:System.Windows.Media.RotateTransform>obrót (<xref:System.Windows.Media.ScaleTransform>),<xref:System.Windows.Media.SkewTransform>skalę (<xref:System.Windows.Media.TranslateTransform>), pochylenie ( ) i tłumaczenie ( ).</span><span class="sxs-lookup"><span data-stu-id="5a007-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="5a007-189">Wspólne przekształcenie do zastosowania do kształtu jest obrotem.</span><span class="sxs-lookup"><span data-stu-id="5a007-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="5a007-190">Aby obrócić kształt, <xref:System.Windows.Media.RotateTransform> utwórz <xref:System.Windows.Media.RotateTransform.Angle%2A>i określ jego .</span><span class="sxs-lookup"><span data-stu-id="5a007-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="5a007-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> z 45 obraca element 45 stopni w prawo; kąt 90 obraca element o 90 stopni w prawo; i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="5a007-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="5a007-192">Ustaw <xref:System.Windows.Media.RotateTransform.CenterX%2A> właściwości <xref:System.Windows.Media.RotateTransform.CenterY%2A> i, jeśli chcesz kontrolować punkt, o którym element jest obrócony.</span><span class="sxs-lookup"><span data-stu-id="5a007-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="5a007-193">Te wartości właściwości są wyrażone w przestrzeni współrzędnych elementu, który jest przekształcany.</span><span class="sxs-lookup"><span data-stu-id="5a007-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="5a007-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A>i <xref:System.Windows.Media.RotateTransform.CenterY%2A> mają domyślne wartości zero.</span><span class="sxs-lookup"><span data-stu-id="5a007-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="5a007-195">Na koniec zastosuj <xref:System.Windows.Media.RotateTransform> do elementu.</span><span class="sxs-lookup"><span data-stu-id="5a007-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="5a007-196">Jeśli transformacja nie ma mieć wpływu na układ, <xref:System.Windows.UIElement.RenderTransform%2A> ustaw właściwość kształtu.</span><span class="sxs-lookup"><span data-stu-id="5a007-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="5a007-197">W poniższym przykładzie <xref:System.Windows.Media.RotateTransform> a służy do obracania kształtu o 45 stopni w lewym górnym rogu kształtu (0,0).</span><span class="sxs-lookup"><span data-stu-id="5a007-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="5a007-198">W następnym przykładzie inny kształt jest obracany o 45 stopni, ale tym razem jest obracany o punkt (25,50).</span><span class="sxs-lookup"><span data-stu-id="5a007-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="5a007-199">Na poniższej ilustracji przedstawiono wyniki stosowania dwóch przekształceń.</span><span class="sxs-lookup"><span data-stu-id="5a007-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="5a007-200">![Obrót 45 stopni z różnymi punktami środkowymi](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="5a007-200">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="5a007-201">W poprzednich przykładach do każdego obiektu kształtu zastosowano pojedyncze przekształcenie.</span><span class="sxs-lookup"><span data-stu-id="5a007-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="5a007-202">Aby zastosować wiele przekształceń do kształtu (lub <xref:System.Windows.Media.TransformGroup>innego elementu interfejsu użytkownika), należy użyć pliku .</span><span class="sxs-lookup"><span data-stu-id="5a007-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a007-203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a007-203">See also</span></span>

- [<span data-ttu-id="5a007-204">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="5a007-204">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="5a007-205">Przegląd Malowanie jednolitymi kolorami i gradientami</span><span class="sxs-lookup"><span data-stu-id="5a007-205">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="5a007-206">Przegląd Geometria</span><span class="sxs-lookup"><span data-stu-id="5a007-206">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="5a007-207">Instruktaż: Moja pierwsza aplikacja komputerowa WPF</span><span class="sxs-lookup"><span data-stu-id="5a007-207">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [<span data-ttu-id="5a007-208">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="5a007-208">Animation Overview</span></span>](animation-overview.md)
