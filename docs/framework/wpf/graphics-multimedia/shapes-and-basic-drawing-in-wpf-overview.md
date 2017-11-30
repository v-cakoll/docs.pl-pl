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
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="bba56-102">Przegląd Kształty i podstawowe rysowanie w WPF</span><span class="sxs-lookup"><span data-stu-id="bba56-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="bba56-103">Ten temat zawiera omówienie sposobu Rysowanie za pomocą <xref:System.Windows.Shapes.Shape> obiektów.</span><span class="sxs-lookup"><span data-stu-id="bba56-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="bba56-104">A <xref:System.Windows.Shapes.Shape> jest typem <xref:System.Windows.UIElement> umożliwiająca narysować kształt do ekranu.</span><span class="sxs-lookup"><span data-stu-id="bba56-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="bba56-105">Ponieważ są one elementy interfejsu użytkownika <xref:System.Windows.Shapes.Shape> obiekty mogą być używane wewnątrz <xref:System.Windows.Controls.Panel> elementów i większość formantów.</span><span class="sxs-lookup"><span data-stu-id="bba56-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="bba56-106">oferuje kilka warstw dostępu do usługi renderowania i grafiki.</span><span class="sxs-lookup"><span data-stu-id="bba56-106"> offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="bba56-107">W górnej warstwie <xref:System.Windows.Shapes.Shape> obiekty są łatwe w użyciu i podaj wielu przydatnych funkcji, takich jak układ i udział w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zdarzeń systemu.</span><span class="sxs-lookup"><span data-stu-id="bba56-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a><span data-ttu-id="bba56-108">Obiekty kształtu</span><span class="sxs-lookup"><span data-stu-id="bba56-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="bba56-109">udostępnia wiele gotowych do użycia <xref:System.Windows.Shapes.Shape> obiektów.</span><span class="sxs-lookup"><span data-stu-id="bba56-109"> provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="bba56-110">Wszystkie obiekty kształtu dziedziczyć <xref:System.Windows.Shapes.Shape> klasy.</span><span class="sxs-lookup"><span data-stu-id="bba56-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="bba56-111">Kształt dostępne obiekty obejmują <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, i <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="bba56-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="bba56-112"><xref:System.Windows.Shapes.Shape>obiekty współużytkują wspólne następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="bba56-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
-   <span data-ttu-id="bba56-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: W tym artykule opisano sposób jest rysowane konturu kształtu.</span><span class="sxs-lookup"><span data-stu-id="bba56-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
-   <span data-ttu-id="bba56-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: W tym artykule opisano Grubość konturu kształtu.</span><span class="sxs-lookup"><span data-stu-id="bba56-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
-   <span data-ttu-id="bba56-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: W tym artykule opisano sposób jest rysowane wewnątrz kształtu.</span><span class="sxs-lookup"><span data-stu-id="bba56-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
-   <span data-ttu-id="bba56-116">Właściwości danych, aby określić współrzędne i wierzchołki, podawana w pikselach niezależnych od urządzenia.</span><span class="sxs-lookup"><span data-stu-id="bba56-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="bba56-117">Ponieważ pochodzą one od <xref:System.Windows.UIElement>, kształtu obiekty mogą być używane wewnątrz paneli i większość formantów.</span><span class="sxs-lookup"><span data-stu-id="bba56-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="bba56-118"><xref:System.Windows.Controls.Canvas> Panel jest szczególnie użyteczna do tworzenia złożonych rysunki, ponieważ obsługuje on bezwzględny jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="bba56-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="bba56-119"><xref:System.Windows.Shapes.Line> Klasa pozwala na rysowanie linii między dwoma punktami.</span><span class="sxs-lookup"><span data-stu-id="bba56-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="bba56-120">Poniższy przykład przedstawia kilka sposobów, aby określić właściwości obrysu i współrzędnych wiersza.</span><span class="sxs-lookup"><span data-stu-id="bba56-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="bba56-121">Na poniższej ilustracji przedstawiono renderowanych <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="bba56-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="bba56-122">![Wiersz ilustracji](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="bba56-122">![Line illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="bba56-123">Mimo że <xref:System.Windows.Shapes.Line> klasy podaj <xref:System.Windows.Shapes.Shape.Fill%2A> ustawienia jego właściwości nie obowiązuje, ponieważ <xref:System.Windows.Shapes.Line> ma bez obszaru.</span><span class="sxs-lookup"><span data-stu-id="bba56-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="bba56-124">Inny kształt wspólnej jest <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="bba56-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="bba56-125">Utwórz <xref:System.Windows.Shapes.Ellipse> , definiując kształtu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bba56-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="bba56-126">Aby narysować okrąg, określ <xref:System.Windows.Shapes.Ellipse> których <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> wartości są równe.</span><span class="sxs-lookup"><span data-stu-id="bba56-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="bba56-127">Na poniższej ilustracji przedstawiono przykład renderowanych <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="bba56-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="bba56-128">![Ilustracja przedstawiająca elipsę](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="bba56-128">![Ellipse illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a><span data-ttu-id="bba56-129">Przy użyciu ścieżki i mają geometrię</span><span class="sxs-lookup"><span data-stu-id="bba56-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="bba56-130"><xref:System.Windows.Shapes.Path> Klasa umożliwia rysowanie krzywych i kształtów złożonych.</span><span class="sxs-lookup"><span data-stu-id="bba56-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="bba56-131">Te krzywych i kształtów są opisane przy użyciu <xref:System.Windows.Media.Geometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="bba56-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="bba56-132">Aby użyć <xref:System.Windows.Shapes.Path>, możesz utworzyć <xref:System.Windows.Media.Geometry> i użyj jej do ustawienia <xref:System.Windows.Shapes.Path> obiektu <xref:System.Windows.Shapes.Path.Data%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bba56-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="bba56-133">Istnieją różne <xref:System.Windows.Media.Geometry> obiekty do wyboru.</span><span class="sxs-lookup"><span data-stu-id="bba56-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="bba56-134"><xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, I <xref:System.Windows.Media.EllipseGeometry> klas definiujących kształty stosunkowo proste.</span><span class="sxs-lookup"><span data-stu-id="bba56-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="bba56-135">Aby utworzyć bardziej złożoną kształtów lub krzywych, należy użyć <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="bba56-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="bba56-136">PathGeometry i PathSegments</span><span class="sxs-lookup"><span data-stu-id="bba56-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="bba56-137"><xref:System.Windows.Media.PathGeometry>obiekty składają się z co najmniej jeden <xref:System.Windows.Media.PathFigure> obiektów; każda <xref:System.Windows.Media.PathFigure> reprezentuje różne "rysunek" lub kształtu.</span><span class="sxs-lookup"><span data-stu-id="bba56-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="bba56-138">Każdy <xref:System.Windows.Media.PathFigure> sam składa się z co najmniej jednego <xref:System.Windows.Media.PathSegment> obiekty, każdy reprezentuje połączony fragment rysunku lub kształtu.</span><span class="sxs-lookup"><span data-stu-id="bba56-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="bba56-139">Są następujące typy segmentu: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, i <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="bba56-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="bba56-140">W poniższym przykładzie <xref:System.Windows.Shapes.Path> jest używany do rysowania kwadratową krzywą Beziera.</span><span class="sxs-lookup"><span data-stu-id="bba56-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="bba56-141">Na poniższej ilustracji przedstawiono renderowanych kształtu.</span><span class="sxs-lookup"><span data-stu-id="bba56-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="bba56-142">![Ilustracja przedstawiająca ścieżkę](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="bba56-142">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="bba56-143">Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.PathGeometry> i innych <xref:System.Windows.Media.Geometry> klas, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bba56-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="bba56-144">Pojęcie skracane składni języka XAML</span><span class="sxs-lookup"><span data-stu-id="bba56-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="bba56-145">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można także użyć do opisania specjalnej składni skróconej <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="bba56-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="bba56-146">W poniższym przykładzie składni skróconej używany do rysowania złożonego kształtu.</span><span class="sxs-lookup"><span data-stu-id="bba56-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="bba56-147">Na poniższej ilustracji przedstawiono renderowanych <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="bba56-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="bba56-148">![Ilustracja przedstawiająca ścieżkę](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="bba56-148">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="bba56-149"><xref:System.Windows.Shapes.Path.Data%2A> Ciąg atrybutu rozpoczyna się przy użyciu polecenia "moveto", wskazane przez M, która określa punkt początkowy dla ścieżki w układzie współrzędnych <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="bba56-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="bba56-150"><xref:System.Windows.Shapes.Path>Parametry danych jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="bba56-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="bba56-151">Wielka litera M wskazuje bezwzględny lokalizacji dla nowego punktu bieżącego.</span><span class="sxs-lookup"><span data-stu-id="bba56-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="bba56-152">Małe litery m wskazuje współrzędnych względnych.</span><span class="sxs-lookup"><span data-stu-id="bba56-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="bba56-153">Pierwszy segment jest sześcienny początku krzywej Beziera na (100,200) i koniec (400,175), rysowane przy użyciu dwóch kontroli punktów (100,25) i (400,350).</span><span class="sxs-lookup"><span data-stu-id="bba56-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="bba56-154">Ten segment jest określane przez polecenie C w <xref:System.Windows.Shapes.Path.Data%2A> atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="bba56-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="bba56-155">Ponownie Wielka litera C wskazuje ścieżką bezwzględną; małe litery c wskazuje ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="bba56-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="bba56-156">Drugi segment rozpocznie się za pomocą wiersza polecenia bezwzględny poziome "lineto" H, który określa linią z poprzednim podrzędną punktu końcowego (400,175) do nowego punktu końcowego (280,175).</span><span class="sxs-lookup"><span data-stu-id="bba56-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="bba56-157">Polecenie poziome "lineto", dlatego jest wybrana *x*-współrzędną.</span><span class="sxs-lookup"><span data-stu-id="bba56-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="bba56-158">Pełną ścieżkę składni, zobacz <xref:System.Windows.Shapes.Path.Data%2A> odwołania i [tworzenie kształtu przy użyciu PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="bba56-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a><span data-ttu-id="bba56-159">Kształty malowania</span><span class="sxs-lookup"><span data-stu-id="bba56-159">Painting Shapes</span></span>  
 <span data-ttu-id="bba56-160"><xref:System.Windows.Media.Brush>obiekty służą do malowania kształtu <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="bba56-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="bba56-161">W poniższym przykładzie, obrysu i wypełnienie <xref:System.Windows.Shapes.Ellipse> zostały określone.</span><span class="sxs-lookup"><span data-stu-id="bba56-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="bba56-162">Należy zauważyć, że prawidłowe wartości wejściowe pędzla właściwości mogą być słowo kluczowe lub szesnastkowej wartości koloru.</span><span class="sxs-lookup"><span data-stu-id="bba56-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="bba56-163">Aby uzyskać więcej informacji na temat słów kluczowych dostępny kolor, zobacz właściwości <xref:System.Windows.Media.Colors> klasy w <xref:System.Windows.Media> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bba56-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
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
  
 <span data-ttu-id="bba56-164">Na poniższej ilustracji przedstawiono renderowanych <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="bba56-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="bba56-165">![Elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="bba56-165">![An ellipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="bba56-166">Można również można użyć składni elementu właściwości można jawnie utworzyć <xref:System.Windows.Media.SolidColorBrush> obiektu namalować kształtów jednolitym kolorem.</span><span class="sxs-lookup"><span data-stu-id="bba56-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
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
  
 <span data-ttu-id="bba56-167">Na poniższej ilustracji przedstawiono renderowanych kształtu.</span><span class="sxs-lookup"><span data-stu-id="bba56-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="bba56-168">![Ilustracja SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="bba56-168">![SolidColorBrush illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="bba56-169">Umożliwia malowanie obrysu lub wypełnienia gradientów, obrazy, wzorców i kształtu.</span><span class="sxs-lookup"><span data-stu-id="bba56-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="bba56-170">Aby uzyskać więcej informacji, zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bba56-170">For more information, see the [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a><span data-ttu-id="bba56-171">Kształty regulowanej długości</span><span class="sxs-lookup"><span data-stu-id="bba56-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="bba56-172"><xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, I <xref:System.Windows.Shapes.Rectangle> klasy mają <xref:System.Windows.Shapes.Shape.Stretch%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bba56-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="bba56-173">Ta właściwość określa, jak <xref:System.Windows.Shapes.Shape> zawartość obiektu (kształt do narysowania) jest rozciągany tak, aby wypełnić <xref:System.Windows.Shapes.Shape> obiektu układu miejsca.</span><span class="sxs-lookup"><span data-stu-id="bba56-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="bba56-174">A <xref:System.Windows.Shapes.Shape> ilość miejsca jest obiektu układu miejsca <xref:System.Windows.Shapes.Shape> został przydzielony przez system układu z powodu albo jawne <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> ustawienie lub z powodu jego <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> ustawienia.</span><span class="sxs-lookup"><span data-stu-id="bba56-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="bba56-175">Aby uzyskać dodatkowe informacje na układ w systemie Windows Presentation Foundation, zobacz [układu](../../../../docs/framework/wpf/advanced/layout.md) omówienie.</span><span class="sxs-lookup"><span data-stu-id="bba56-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../../../../docs/framework/wpf/advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="bba56-176">Właściwość Stretch przyjmuje jeden z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="bba56-176">The Stretch property takes one of the following values:</span></span>  
  
-   <span data-ttu-id="bba56-177"><xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu nie jest rozciągana.</span><span class="sxs-lookup"><span data-stu-id="bba56-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
-   <span data-ttu-id="bba56-178"><xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągany w celu wypełnienia miejsca jego układu.</span><span class="sxs-lookup"><span data-stu-id="bba56-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="bba56-179">Współczynnik proporcji nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="bba56-179">Aspect ratio is not preserved.</span></span>  
  
-   <span data-ttu-id="bba56-180"><xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu są rozciągany tak jak to możliwe do wypełnienia miejsca jego układ, zachowując jego oryginalny współczynnik proporcji.</span><span class="sxs-lookup"><span data-stu-id="bba56-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
-   <span data-ttu-id="bba56-181"><xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Zawartość obiektu jest rozciągany tak, aby wypełnić miejsca jego układ, zachowując jego oryginalny współczynnik proporcji.</span><span class="sxs-lookup"><span data-stu-id="bba56-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="bba56-182">Należy zauważyć, że gdy <xref:System.Windows.Shapes.Shape> zawartość obiektu jest rozciągany tak, <xref:System.Windows.Shapes.Shape> obiektu jest rysowane po rozciąganie.</span><span class="sxs-lookup"><span data-stu-id="bba56-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="bba56-183">W poniższym przykładzie <xref:System.Windows.Shapes.Polygon> używany do rysowania bardzo mały trójkąt z (0,0) (0,1) (1,1).</span><span class="sxs-lookup"><span data-stu-id="bba56-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="bba56-184"><xref:System.Windows.Shapes.Polygon> Obiektu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> są ustawione na 100, a jego właściwość stretch jest ustawiona na wartość Fill.</span><span class="sxs-lookup"><span data-stu-id="bba56-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="bba56-185">W związku z tym <xref:System.Windows.Shapes.Polygon> zawartość obiektu (trójkąt) są rozciągany w celu wypełnienia większych miejsca.</span><span class="sxs-lookup"><span data-stu-id="bba56-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
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
## <a name="transforming-shapes"></a><span data-ttu-id="bba56-186">Przekształcanie kształtów</span><span class="sxs-lookup"><span data-stu-id="bba56-186">Transforming Shapes</span></span>  
 <span data-ttu-id="bba56-187"><xref:System.Windows.Media.Transform> Klasa udostępnia środki do przekształcania kształtów w dwuwymiarowego rzutu.</span><span class="sxs-lookup"><span data-stu-id="bba56-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="bba56-188">Różne typy przekształcania obejmują obrotu (<xref:System.Windows.Media.RotateTransform>), skali (<xref:System.Windows.Media.ScaleTransform>), pochylenia (<xref:System.Windows.Media.SkewTransform>), a translacja (<xref:System.Windows.Media.TranslateTransform>).</span><span class="sxs-lookup"><span data-stu-id="bba56-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="bba56-189">Typowe przekształcenie do zastosowania do kształtu jest obrotu.</span><span class="sxs-lookup"><span data-stu-id="bba56-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="bba56-190">Obracanie kształtu, należy utworzyć <xref:System.Windows.Media.RotateTransform> i określ jej <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span><span class="sxs-lookup"><span data-stu-id="bba56-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="bba56-191"><xref:System.Windows.Media.RotateTransform.Angle%2A> 45 obraca element 45 stopni w prawo; pod kątem 90 obraca element 90 stopni w prawo; i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="bba56-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="bba56-192">Ustaw <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości, jeśli chcesz kontrolować punktu o tym, które jest obracana elementu.</span><span class="sxs-lookup"><span data-stu-id="bba56-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="bba56-193">Wartości tych właściwości są wyrażane w układzie współrzędnych elementu transformacji.</span><span class="sxs-lookup"><span data-stu-id="bba56-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="bba56-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A>i <xref:System.Windows.Media.RotateTransform.CenterY%2A> mają przypisane wartości domyślne o wartości zero.</span><span class="sxs-lookup"><span data-stu-id="bba56-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="bba56-195">Na koniec zastosować <xref:System.Windows.Media.RotateTransform> do elementu.</span><span class="sxs-lookup"><span data-stu-id="bba56-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="bba56-196">Jeśli nie chcesz transformacji do mają wpływ na układ, ustaw kształtu <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bba56-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="bba56-197">W poniższym przykładzie <xref:System.Windows.Media.RotateTransform> służy do Obrót o 45 stopni kształtu, o kształtu lewym górnym rogu (0,0).</span><span class="sxs-lookup"><span data-stu-id="bba56-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="bba56-198">W następnym przykładzie innego kształtu jest obrócony o 45 stopni, ale tym razem go obraca się wokół punktu (25,50).</span><span class="sxs-lookup"><span data-stu-id="bba56-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="bba56-199">Na poniższej ilustracji przedstawiono wyniki dwóch transformacji.</span><span class="sxs-lookup"><span data-stu-id="bba56-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="bba56-200">![obrotów 45 stopni z różnymi punktami](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="bba56-200">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="bba56-201">W poprzednich przykładach transformacji pojedynczego została zastosowana do każdego obiektu kształtu.</span><span class="sxs-lookup"><span data-stu-id="bba56-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="bba56-202">Aby zastosować kilka przekształceń do kształtu (lub innego elementu interfejsu użytkownika), należy użyć <xref:System.Windows.Media.TransformGroup>.</span><span class="sxs-lookup"><span data-stu-id="bba56-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bba56-203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bba56-203">See Also</span></span>  
 [<span data-ttu-id="bba56-204">Grafika 2W i utworzenia obrazu</span><span class="sxs-lookup"><span data-stu-id="bba56-204">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="bba56-205">Malowanie pełnych kolorów i gradientów — omówienie</span><span class="sxs-lookup"><span data-stu-id="bba56-205">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="bba56-206">Omówienie geometrii</span><span class="sxs-lookup"><span data-stu-id="bba56-206">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="bba56-207">Wskazówki: Pierwszy WPF pulpitu aplikację</span><span class="sxs-lookup"><span data-stu-id="bba56-207">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [<span data-ttu-id="bba56-208">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="bba56-208">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
