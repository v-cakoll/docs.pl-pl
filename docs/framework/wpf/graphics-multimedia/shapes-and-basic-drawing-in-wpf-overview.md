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
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="b4803-103">Przegląd Kształty i podstawowe rysowanie w WPF</span><span class="sxs-lookup"><span data-stu-id="b4803-103">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="b4803-104">Ten temat zawiera omówienie sposobu rysowania z <xref:System.Windows.Shapes.Shape> obiektami.</span><span class="sxs-lookup"><span data-stu-id="b4803-104">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="b4803-105">A <xref:System.Windows.Shapes.Shape> to typ <xref:System.Windows.UIElement> , który umożliwia narysowanie kształtu na ekranie.</span><span class="sxs-lookup"><span data-stu-id="b4803-105">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="b4803-106">Ponieważ są to elementy interfejsu użytkownika, <xref:System.Windows.Shapes.Shape> obiekty mogą być używane wewnątrz <xref:System.Windows.Controls.Panel> elementów i większości formantów.</span><span class="sxs-lookup"><span data-stu-id="b4803-106">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="b4803-107">oferuje kilka warstw dostępu do usług graficznych i renderowania.</span><span class="sxs-lookup"><span data-stu-id="b4803-107">offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="b4803-108">W górnej warstwie <xref:System.Windows.Shapes.Shape> obiekty są łatwe w użyciu i zapewniają wiele przydatnych funkcji, takich jak układ i uczestnictwo w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systemie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b4803-108">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  

<a name="shapes"></a>
## <a name="shape-objects"></a><span data-ttu-id="b4803-109">Obiekty Shape</span><span class="sxs-lookup"><span data-stu-id="b4803-109">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="b4803-110">zawiera wiele gotowych do użycia <xref:System.Windows.Shapes.Shape> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b4803-110">provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="b4803-111">Wszystkie obiekty kształtu dziedziczą z <xref:System.Windows.Shapes.Shape> klasy.</span><span class="sxs-lookup"><span data-stu-id="b4803-111">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="b4803-112">Dostępne obiekty kształtu obejmują <xref:System.Windows.Shapes.Ellipse> , <xref:System.Windows.Shapes.Line> ,,, <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline> , i <xref:System.Windows.Shapes.Rectangle> .</span><span class="sxs-lookup"><span data-stu-id="b4803-112">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="b4803-113"><xref:System.Windows.Shapes.Shape>obiekty współużytkują następujące typowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="b4803-113"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
- <span data-ttu-id="b4803-114"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Opisuje sposób malowania konturu kształtu.</span><span class="sxs-lookup"><span data-stu-id="b4803-114"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
- <span data-ttu-id="b4803-115"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Opisuje grubość konturu kształtu.</span><span class="sxs-lookup"><span data-stu-id="b4803-115"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
- <span data-ttu-id="b4803-116"><xref:System.Windows.Shapes.Shape.Fill%2A>: Opisuje sposób malowania wnętrza kształtu.</span><span class="sxs-lookup"><span data-stu-id="b4803-116"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
- <span data-ttu-id="b4803-117">Właściwości danych w celu określenia współrzędnych i wierzchołków mierzonych w pikselach niezależnych od urządzenia.</span><span class="sxs-lookup"><span data-stu-id="b4803-117">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="b4803-118">Ponieważ pochodzą one od <xref:System.Windows.UIElement> , obiekty Shape mogą być używane wewnątrz paneli i większości formantów.</span><span class="sxs-lookup"><span data-stu-id="b4803-118">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="b4803-119"><xref:System.Windows.Controls.Canvas>Panel jest szczególnie dobrym wyborem w przypadku tworzenia złożonych rysunków, ponieważ obsługuje pozycjonowanie bezwzględne jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b4803-119">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="b4803-120"><xref:System.Windows.Shapes.Line>Klasa umożliwia narysowanie linii między dwoma punktami.</span><span class="sxs-lookup"><span data-stu-id="b4803-120">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="b4803-121">W poniższym przykładzie pokazano kilka sposobów określania współrzędnych linii i właściwości obrysu.</span><span class="sxs-lookup"><span data-stu-id="b4803-121">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="b4803-122">Na poniższej ilustracji przedstawiono renderowane <xref:System.Windows.Shapes.Line> .</span><span class="sxs-lookup"><span data-stu-id="b4803-122">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="b4803-123">![Ilustracja przedstawiająca linię](./media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="b4803-123">![Line illustration](./media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="b4803-124">Chociaż <xref:System.Windows.Shapes.Line> Klasa udostępnia <xref:System.Windows.Shapes.Shape.Fill%2A> Właściwość, ustawienie nie ma żadnego efektu, ponieważ nie <xref:System.Windows.Shapes.Line> ma żadnego obszaru.</span><span class="sxs-lookup"><span data-stu-id="b4803-124">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="b4803-125">Innym wspólnym kształtem jest <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="b4803-125">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="b4803-126">Utwórz obiekt <xref:System.Windows.Shapes.Ellipse> przez zdefiniowanie kształtu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b4803-126">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="b4803-127">Aby narysować okrąg, określ, <xref:System.Windows.Shapes.Ellipse> którego <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> wartości są równe.</span><span class="sxs-lookup"><span data-stu-id="b4803-127">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="b4803-128">Na poniższej ilustracji przedstawiono przykład renderowanego elementu <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="b4803-128">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="b4803-129">![Ilustracja przedstawiająca elipsę](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="b4803-129">![Ellipse illustration](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a><span data-ttu-id="b4803-130">Używanie ścieżek i geometrie</span><span class="sxs-lookup"><span data-stu-id="b4803-130">Using Paths and Geometries</span></span>  
 <span data-ttu-id="b4803-131"><xref:System.Windows.Shapes.Path>Klasa umożliwia rysowanie krzywych i złożonych kształtów.</span><span class="sxs-lookup"><span data-stu-id="b4803-131">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="b4803-132">Te krzywe i kształty są opisane przy użyciu <xref:System.Windows.Media.Geometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b4803-132">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="b4803-133">Aby użyć <xref:System.Windows.Shapes.Path> , należy utworzyć <xref:System.Windows.Media.Geometry> i użyć go do ustawienia <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Path.Data%2A> właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="b4803-133">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="b4803-134">Istnieje wiele <xref:System.Windows.Media.Geometry> obiektów do wyboru.</span><span class="sxs-lookup"><span data-stu-id="b4803-134">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="b4803-135"><xref:System.Windows.Media.LineGeometry>Klasy, <xref:System.Windows.Media.RectangleGeometry> i <xref:System.Windows.Media.EllipseGeometry> opisują stosunkowo proste kształty.</span><span class="sxs-lookup"><span data-stu-id="b4803-135">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="b4803-136">Aby utworzyć bardziej złożone kształty lub utworzyć krzywe, użyj <xref:System.Windows.Media.PathGeometry> .</span><span class="sxs-lookup"><span data-stu-id="b4803-136">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="b4803-137">PathGeometry i PathSegments</span><span class="sxs-lookup"><span data-stu-id="b4803-137">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="b4803-138"><xref:System.Windows.Media.PathGeometry>obiekty składają się z co najmniej jednego <xref:System.Windows.Media.PathFigure> obiektu; każdy <xref:System.Windows.Media.PathFigure> reprezentuje inny "rysunek" lub kształt.</span><span class="sxs-lookup"><span data-stu-id="b4803-138"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="b4803-139">Każda <xref:System.Windows.Media.PathFigure> z nich składa się z co najmniej jednego <xref:System.Windows.Media.PathSegment> obiektu, z których każdy reprezentuje podłączoną część rysunku lub kształtu.</span><span class="sxs-lookup"><span data-stu-id="b4803-139">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="b4803-140">Typy segmentów obejmują następujące elementy: <xref:System.Windows.Media.LineSegment> , <xref:System.Windows.Media.BezierSegment> , i <xref:System.Windows.Media.ArcSegment> .</span><span class="sxs-lookup"><span data-stu-id="b4803-140">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="b4803-141">W poniższym przykładzie <xref:System.Windows.Shapes.Path> jest używany do rysowania krzywej Beziera kwadratu.</span><span class="sxs-lookup"><span data-stu-id="b4803-141">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="b4803-142">Na poniższej ilustracji przedstawiono renderowany kształt.</span><span class="sxs-lookup"><span data-stu-id="b4803-142">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="b4803-143">![Ilustracja przedstawiająca ścieżkę](./media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="b4803-143">![Path illustration](./media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="b4803-144">Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.PathGeometry> i innych <xref:System.Windows.Media.Geometry> klas, zobacz [Omówienie geometrii](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b4803-144">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="b4803-145">Składnia języka XAML — skrócona</span><span class="sxs-lookup"><span data-stu-id="b4803-145">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="b4803-146">W programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] można również użyć specjalnej składni skróconej do opisania <xref:System.Windows.Shapes.Path> .</span><span class="sxs-lookup"><span data-stu-id="b4803-146">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="b4803-147">W poniższym przykładzie Skrócona składnia jest używana do rysowania złożonego kształtu.</span><span class="sxs-lookup"><span data-stu-id="b4803-147">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="b4803-148">Na poniższej ilustracji przedstawiono renderowane <xref:System.Windows.Shapes.Path> .</span><span class="sxs-lookup"><span data-stu-id="b4803-148">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="b4803-149">![Ilustracja przedstawiająca ścieżkę](./media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="b4803-149">![Path illustration](./media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="b4803-150"><xref:System.Windows.Shapes.Path.Data%2A>Ciąg atrybutu zaczyna się od polecenia "MoveTo" wskazanego przez M, które określa punkt początkowy dla ścieżki w układzie współrzędnych <xref:System.Windows.Controls.Canvas> .</span><span class="sxs-lookup"><span data-stu-id="b4803-150">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="b4803-151"><xref:System.Windows.Shapes.Path>w parametrach danych jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="b4803-151"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="b4803-152">Wielka litera M wskazuje lokalizację bezwzględną dla nowego punktu bieżącego.</span><span class="sxs-lookup"><span data-stu-id="b4803-152">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="b4803-153">Małe litery m wskazują współrzędne względne.</span><span class="sxs-lookup"><span data-stu-id="b4803-153">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="b4803-154">Pierwszy segment jest zakrzywioną krzywą Beziera rozpoczynającą się o (100 200) i kończącą się na (400 175), narysowanym przy użyciu dwóch punktów kontrolnych (100, 25) i (400 350).</span><span class="sxs-lookup"><span data-stu-id="b4803-154">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="b4803-155">Ten segment jest wskazywany przez polecenie C w <xref:System.Windows.Shapes.Path.Data%2A> ciągu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b4803-155">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="b4803-156">Ponownie Wielka litera C wskazuje ścieżkę bezwzględną; Mała litera c wskazuje ścieżkę względną.</span><span class="sxs-lookup"><span data-stu-id="b4803-156">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="b4803-157">Drugi segment zaczyna się od bezwzględnej wartości "LineTo" polecenia H, które określa wiersz rysowany z poprzedniego punktu końcowego ścieżki podrzędnej (400 175) do nowego punktu końcowego (280 175).</span><span class="sxs-lookup"><span data-stu-id="b4803-157">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="b4803-158">Ponieważ jest to w poziomie polecenie "LineTo", określona wartość jest Współrzędna *x*.</span><span class="sxs-lookup"><span data-stu-id="b4803-158">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="b4803-159">Aby uzyskać pełną składnię ścieżki, zobacz <xref:System.Windows.Shapes.Path.Data%2A> odwołanie i [Tworzenie kształtu przy użyciu PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="b4803-159">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a><span data-ttu-id="b4803-160">Malowanie kształtów</span><span class="sxs-lookup"><span data-stu-id="b4803-160">Painting Shapes</span></span>  
 <span data-ttu-id="b4803-161"><xref:System.Windows.Media.Brush>obiekty są używane do malowania kształtu <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.Fill%2A> .</span><span class="sxs-lookup"><span data-stu-id="b4803-161"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="b4803-162">W poniższym przykładzie pociągnięcia i wypełnienia <xref:System.Windows.Shapes.Ellipse> są określone.</span><span class="sxs-lookup"><span data-stu-id="b4803-162">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="b4803-163">Zwróć uwagę, że prawidłowe dane wejściowe właściwości pędzla mogą być słowami kluczowymi lub szesnastkowymi wartościami koloru.</span><span class="sxs-lookup"><span data-stu-id="b4803-163">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="b4803-164">Aby uzyskać więcej informacji na temat dostępnych słów kluczowych koloru, zobacz właściwości <xref:System.Windows.Media.Colors> klasy w <xref:System.Windows.Media> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b4803-164">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
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
  
 <span data-ttu-id="b4803-165">Na poniższej ilustracji przedstawiono renderowane <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="b4803-165">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="b4803-166">![Elipsa](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="b4803-166">![An ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="b4803-167">Alternatywnie, można użyć składni elementu właściwości, aby jawnie utworzyć <xref:System.Windows.Media.SolidColorBrush> obiekt, aby malować kształt z pełnym kolorem.</span><span class="sxs-lookup"><span data-stu-id="b4803-167">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
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
  
 <span data-ttu-id="b4803-168">Na poniższej ilustracji przedstawiono renderowany kształt.</span><span class="sxs-lookup"><span data-stu-id="b4803-168">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="b4803-169">![Ilustracja przedstawiająca SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="b4803-169">![SolidColorBrush illustration](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="b4803-170">Możesz również malować obrys kształtu lub wypełnić kolorami gradientów, obrazów, wzorców i innych.</span><span class="sxs-lookup"><span data-stu-id="b4803-170">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="b4803-171">Aby uzyskać więcej informacji, zobacz [rysowanie z pełnymi kolorami i gradientami — Omówienie](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b4803-171">For more information, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a><span data-ttu-id="b4803-172">Kształty rozciągane</span><span class="sxs-lookup"><span data-stu-id="b4803-172">Stretchable Shapes</span></span>  
 <span data-ttu-id="b4803-173"><xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon> Wszystkie klasy,,, <xref:System.Windows.Shapes.Polyline> i <xref:System.Windows.Shapes.Rectangle> mają <xref:System.Windows.Shapes.Shape.Stretch%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="b4803-173">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="b4803-174">Ta właściwość określa, w jaki sposób <xref:System.Windows.Shapes.Shape> zawartość obiektu (kształt do rysowania) jest rozciągana w celu wypełnienia <xref:System.Windows.Shapes.Shape> obszaru układu obiektu.</span><span class="sxs-lookup"><span data-stu-id="b4803-174">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="b4803-175"><xref:System.Windows.Shapes.Shape>Przestrzeń układu obiektu to ilość miejsca <xref:System.Windows.Shapes.Shape> przydzielonego przez system układu ze względu na <xref:System.Windows.FrameworkElement.Width%2A> ustawienie jawne i <xref:System.Windows.FrameworkElement.Height%2A> lub z powodu jego <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ustawień i.</span><span class="sxs-lookup"><span data-stu-id="b4803-175">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="b4803-176">Aby uzyskać dodatkowe informacje na temat układu w Windows Presentation Foundation, zobacz Omówienie [układu](../advanced/layout.md) .</span><span class="sxs-lookup"><span data-stu-id="b4803-176">For additional information on layout in Windows Presentation Foundation, see [Layout](../advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="b4803-177">Właściwość rozciąganie przyjmuje jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="b4803-177">The Stretch property takes one of the following values:</span></span>  
  
- <span data-ttu-id="b4803-178"><xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu nie jest rozciągana.</span><span class="sxs-lookup"><span data-stu-id="b4803-178"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
- <span data-ttu-id="b4803-179"><xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągana w celu wypełnienia jego obszaru układu.</span><span class="sxs-lookup"><span data-stu-id="b4803-179"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="b4803-180">Współczynnik proporcji nie jest zachowywany.</span><span class="sxs-lookup"><span data-stu-id="b4803-180">Aspect ratio is not preserved.</span></span>  
  
- <span data-ttu-id="b4803-181"><xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągana jak najwięcej, aby wypełnić jego przestrzeń układu przy zachowaniu oryginalnego współczynnika proporcji.</span><span class="sxs-lookup"><span data-stu-id="b4803-181"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
- <span data-ttu-id="b4803-182"><xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągana w celu całkowitego wypełnienia jego obszaru układu, zachowując jego oryginalny współczynnik proporcji.</span><span class="sxs-lookup"><span data-stu-id="b4803-182"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="b4803-183">Należy pamiętać, że po <xref:System.Windows.Shapes.Shape> rozciągnięciu zawartości obiektu <xref:System.Windows.Shapes.Shape> Konspekt obiektu jest malowany po rozciągnięciu.</span><span class="sxs-lookup"><span data-stu-id="b4803-183">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="b4803-184">W poniższym przykładzie <xref:System.Windows.Shapes.Polygon> jest używany do rysowania bardzo małego trójkąta od (0, 0) do (od 0 do 1) do (1, 1).</span><span class="sxs-lookup"><span data-stu-id="b4803-184">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="b4803-185"><xref:System.Windows.Shapes.Polygon>Obiekt i ma <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> ustawioną wartość 100, a jego właściwość rozciągania ma wartość Fill.</span><span class="sxs-lookup"><span data-stu-id="b4803-185">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="b4803-186">W efekcie <xref:System.Windows.Shapes.Polygon> zawartość obiektu (trójkąt) jest rozciągana w celu wypełnienia większej ilości miejsca.</span><span class="sxs-lookup"><span data-stu-id="b4803-186">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
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
## <a name="transforming-shapes"></a><span data-ttu-id="b4803-187">Przekształcanie kształtów</span><span class="sxs-lookup"><span data-stu-id="b4803-187">Transforming Shapes</span></span>  
 <span data-ttu-id="b4803-188"><xref:System.Windows.Media.Transform>Klasa zapewnia środki do przekształcania kształtów w płaszczyźnie dwuwymiarowej.</span><span class="sxs-lookup"><span data-stu-id="b4803-188">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="b4803-189">Różne typy transformacji obejmują rotację ( <xref:System.Windows.Media.RotateTransform> ), skalę ( <xref:System.Windows.Media.ScaleTransform> ), skośność ( <xref:System.Windows.Media.SkewTransform> ) i translację ( <xref:System.Windows.Media.TranslateTransform> ).</span><span class="sxs-lookup"><span data-stu-id="b4803-189">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="b4803-190">Typowa transformacja do zastosowania do kształtu jest rotacją.</span><span class="sxs-lookup"><span data-stu-id="b4803-190">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="b4803-191">Aby obrócić kształt, Utwórz <xref:System.Windows.Media.RotateTransform> i określ jego <xref:System.Windows.Media.RotateTransform.Angle%2A> .</span><span class="sxs-lookup"><span data-stu-id="b4803-191">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="b4803-192">Do <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 obraca element 45 stopni w prawo; kąt 90 obraca element o wartości 90 stopni w prawo i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b4803-192">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="b4803-193">Ustaw <xref:System.Windows.Media.RotateTransform.CenterX%2A> właściwości i, <xref:System.Windows.Media.RotateTransform.CenterY%2A> Jeśli chcesz kontrolować punkt, w którym element jest obrócony.</span><span class="sxs-lookup"><span data-stu-id="b4803-193">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="b4803-194">Te wartości właściwości są wyrażane w przestrzeni współrzędnych elementu, który jest przekształcany.</span><span class="sxs-lookup"><span data-stu-id="b4803-194">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="b4803-195"><xref:System.Windows.Media.RotateTransform.CenterX%2A>i <xref:System.Windows.Media.RotateTransform.CenterY%2A> mają wartości domyślne równe zero.</span><span class="sxs-lookup"><span data-stu-id="b4803-195"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="b4803-196">Na koniec zastosuj <xref:System.Windows.Media.RotateTransform> do elementu.</span><span class="sxs-lookup"><span data-stu-id="b4803-196">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="b4803-197">Jeśli nie chcesz, aby transformacja miała wpływ na układ, ustaw właściwość kształtu <xref:System.Windows.UIElement.RenderTransform%2A> .</span><span class="sxs-lookup"><span data-stu-id="b4803-197">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="b4803-198">W poniższym przykładzie <xref:System.Windows.Media.RotateTransform> jest używany do obracania kształtu 45 stopni wokół lewego górnego rogu kształtu (0, 0).</span><span class="sxs-lookup"><span data-stu-id="b4803-198">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="b4803-199">W następnym przykładzie inny kształt jest obrócony o 45 stopni, ale ten czas jest obracany o punkt (25, 50).</span><span class="sxs-lookup"><span data-stu-id="b4803-199">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="b4803-200">Na poniższej ilustracji przedstawiono wyniki zastosowania dwóch transformacji.</span><span class="sxs-lookup"><span data-stu-id="b4803-200">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="b4803-201">![45 stopni obrotów z różnymi punktami środkowymi](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="b4803-201">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="b4803-202">W poprzednich przykładach do każdego obiektu kształtu zastosowano pojedyncze przekształcenie.</span><span class="sxs-lookup"><span data-stu-id="b4803-202">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="b4803-203">Aby zastosować wiele przekształceń do kształtu (lub dowolnego innego elementu interfejsu użytkownika), użyj <xref:System.Windows.Media.TransformGroup> .</span><span class="sxs-lookup"><span data-stu-id="b4803-203">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4803-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4803-204">See also</span></span>

- [<span data-ttu-id="b4803-205">Grafika 2D i obrazowanie</span><span class="sxs-lookup"><span data-stu-id="b4803-205">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="b4803-206">Przegląd Malowanie jednolitymi kolorami i gradientami</span><span class="sxs-lookup"><span data-stu-id="b4803-206">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="b4803-207">Przegląd Geometria</span><span class="sxs-lookup"><span data-stu-id="b4803-207">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="b4803-208">Przewodnik: moja pierwsza aplikacja klasyczna WPF</span><span class="sxs-lookup"><span data-stu-id="b4803-208">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [<span data-ttu-id="b4803-209">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="b4803-209">Animation Overview</span></span>](animation-overview.md)
