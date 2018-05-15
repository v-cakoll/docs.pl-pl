---
title: Ścieżki grafiki w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: 66d30b949fbfe8190b9e2ae2ea7896ac36bf0bac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="graphics-paths-in-gdi"></a><span data-ttu-id="a5b15-102">Ścieżki grafiki w GDI+</span><span class="sxs-lookup"><span data-stu-id="a5b15-102">Graphics Paths in GDI+</span></span>
<span data-ttu-id="a5b15-103">Ścieżki jest tworzony przez połączenie linii, prostokątów i krzywych proste.</span><span class="sxs-lookup"><span data-stu-id="a5b15-103">Paths are formed by combining lines, rectangles, and simple curves.</span></span> <span data-ttu-id="a5b15-104">Wycofaj z [Przegląd grafiki wektorowej](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) czy następujących podstawowych bloków konstrukcyjnych okazały się najbardziej przydatny w przypadku rysowania obrazów:</span><span class="sxs-lookup"><span data-stu-id="a5b15-104">Recall from the [Vector Graphics Overview](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) that the following basic building blocks have proven to be the most useful for drawing pictures:</span></span>  
  
-   <span data-ttu-id="a5b15-105">wiersze</span><span class="sxs-lookup"><span data-stu-id="a5b15-105">Lines</span></span>  
  
-   <span data-ttu-id="a5b15-106">Prostokątów</span><span class="sxs-lookup"><span data-stu-id="a5b15-106">Rectangles</span></span>  
  
-   <span data-ttu-id="a5b15-107">Wielokropek</span><span class="sxs-lookup"><span data-stu-id="a5b15-107">Ellipses</span></span>  
  
-   <span data-ttu-id="a5b15-108">Łuki</span><span class="sxs-lookup"><span data-stu-id="a5b15-108">Arcs</span></span>  
  
-   <span data-ttu-id="a5b15-109">Wielokąty</span><span class="sxs-lookup"><span data-stu-id="a5b15-109">Polygons</span></span>  
  
-   <span data-ttu-id="a5b15-110">Krzywe kardynalne</span><span class="sxs-lookup"><span data-stu-id="a5b15-110">Cardinal splines</span></span>  
  
-   <span data-ttu-id="a5b15-111">Krzywe Beziera</span><span class="sxs-lookup"><span data-stu-id="a5b15-111">Bézier splines</span></span>  
  
 <span data-ttu-id="a5b15-112">W GDI + <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu umożliwia zbieranie sekwencję te bloki konstrukcyjne w pojedynczą jednostkę.</span><span class="sxs-lookup"><span data-stu-id="a5b15-112">In GDI+, the <xref:System.Drawing.Drawing2D.GraphicsPath> object allows you to collect a sequence of these building blocks into a single unit.</span></span> <span data-ttu-id="a5b15-113">Można następnie narysowania całej sekwencji wierszy, prostokąty wielokątów i krzywych z jednego wywołania <xref:System.Drawing.Graphics.DrawPath%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="a5b15-113">The entire sequence of lines, rectangles, polygons, and curves can then be drawn with one call to the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="a5b15-114">Na poniższej ilustracji przedstawiono ścieżki tworzone przez połączenie linii, łuku krzywej Beziera i kardynalnej krzywej składanej.</span><span class="sxs-lookup"><span data-stu-id="a5b15-114">The following illustration shows a path created by combining a line, an arc, a Bézier spline, and a cardinal spline.</span></span>  
  
 <span data-ttu-id="a5b15-115">![Ścieżka](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span><span class="sxs-lookup"><span data-stu-id="a5b15-115">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span></span>  
  
## <a name="using-a-path"></a><span data-ttu-id="a5b15-116">Przy użyciu ścieżki</span><span class="sxs-lookup"><span data-stu-id="a5b15-116">Using a Path</span></span>  
 <span data-ttu-id="a5b15-117"><xref:System.Drawing.Drawing2D.GraphicsPath> Klasy udostępnia następujące metody tworzenia sekwencję elementów, które mają być rysowane: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (dla kardynalne), i <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5b15-117">The <xref:System.Drawing.Drawing2D.GraphicsPath> class provides the following methods for creating a sequence of items to be drawn: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (for cardinal splines), and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span></span> <span data-ttu-id="a5b15-118">Każda z tych metod jest przeciążony; oznacza to, że każda metoda obsługuje kilka list innym parametrem.</span><span class="sxs-lookup"><span data-stu-id="a5b15-118">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="a5b15-119">Na przykład, jeden odmianą <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metody otrzymuje czterech liczb całkowitych i inna odmiana <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metody otrzymuje dwa <xref:System.Drawing.Point> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a5b15-119">For example, one variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives four integers, and another variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="a5b15-120">Metody dodawania wierszy, prostokąty i krzywych Beziera na ścieżkę mają metody pomocnika w liczbie mnogiej, które dodać kilka elementów na ścieżkę w pojedynczym wywołaniu: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, i <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5b15-120">The methods for adding lines, rectangles, and Bézier splines to a path have plural companion methods that add several items to the path in a single call: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span></span> <span data-ttu-id="a5b15-121">Ponadto <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> metody mają metody pomocnika <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, dodaje zamkniętej krzywej lub kołowy do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="a5b15-121">Also, the <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> methods have companion methods, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, that add a closed curve or pie to the path.</span></span>  
  
 <span data-ttu-id="a5b15-122">Aby narysować ścieżkę, należy <xref:System.Drawing.Graphics> obiektu <xref:System.Drawing.Pen> obiektu, a <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a5b15-122">To draw a path, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="a5b15-123"><xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.DrawPath%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak szerokość i kolor używany do renderowania ścieżki wiersza.</span><span class="sxs-lookup"><span data-stu-id="a5b15-123">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPath%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the path.</span></span> <span data-ttu-id="a5b15-124"><xref:System.Drawing.Drawing2D.GraphicsPath> Obiekt przechowuje sekwencji linii i krzywych, które składają się na ścieżce.</span><span class="sxs-lookup"><span data-stu-id="a5b15-124">The <xref:System.Drawing.Drawing2D.GraphicsPath> object stores the sequence of lines and curves that make up the path.</span></span> <span data-ttu-id="a5b15-125"><xref:System.Drawing.Pen> Obiektu i <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu są przekazywane jako argumenty do <xref:System.Drawing.Graphics.DrawPath%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a5b15-125">The <xref:System.Drawing.Pen> object and the <xref:System.Drawing.Drawing2D.GraphicsPath> object are passed as arguments to the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="a5b15-126">Poniższy przykład rysuje ścieżki, która składa się z linii, elipsy i krzywej Beziera:</span><span class="sxs-lookup"><span data-stu-id="a5b15-126">The following example draws a path that consists of a line, an ellipse, and a Bézier spline:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 <span data-ttu-id="a5b15-127">Na poniższej ilustracji przedstawiono ścieżki.</span><span class="sxs-lookup"><span data-stu-id="a5b15-127">The following illustration shows the path.</span></span>  
  
 <span data-ttu-id="a5b15-128">![Ścieżka](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span><span class="sxs-lookup"><span data-stu-id="a5b15-128">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span></span>  
  
 <span data-ttu-id="a5b15-129">Oprócz dodania linii, prostokątów i krzywych do ścieżki, można dodać ścieżek do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="a5b15-129">In addition to adding lines, rectangles, and curves to a path, you can add paths to a path.</span></span> <span data-ttu-id="a5b15-130">Dzięki temu można połączyć istniejące ścieżki do tworzenia ścieżek dużych, złożonych.</span><span class="sxs-lookup"><span data-stu-id="a5b15-130">This allows you to combine existing paths to form large, complex paths.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 <span data-ttu-id="a5b15-131">Istnieją dwa inne elementy można dodać do ścieżki: ciągów i ciast.</span><span class="sxs-lookup"><span data-stu-id="a5b15-131">There are two other items you can add to a path: strings and pies.</span></span> <span data-ttu-id="a5b15-132">Wykres kołowy jest częścią wewnątrz elipsy.</span><span class="sxs-lookup"><span data-stu-id="a5b15-132">A pie is a portion of the interior of an ellipse.</span></span> <span data-ttu-id="a5b15-133">Poniższy przykład tworzy ścieżki z łuk, kardynalnej krzywej składanej ciągu i wykres kołowy:</span><span class="sxs-lookup"><span data-stu-id="a5b15-133">The following example creates a path from an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 <span data-ttu-id="a5b15-134">Na poniższej ilustracji przedstawiono ścieżki.</span><span class="sxs-lookup"><span data-stu-id="a5b15-134">The following illustration shows the path.</span></span> <span data-ttu-id="a5b15-135">Należy pamiętać, że ścieżki nie ma zostać połączona; Łuk, kardynalnej krzywej składanej, ciągu i koła są rozdzielone.</span><span class="sxs-lookup"><span data-stu-id="a5b15-135">Note that a path does not have to be connected; the arc, cardinal spline, string, and pie are separated.</span></span>  
  
 <span data-ttu-id="a5b15-136">![Ścieżki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span><span class="sxs-lookup"><span data-stu-id="a5b15-136">![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b15-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5b15-137">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [<span data-ttu-id="a5b15-138">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="a5b15-138">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="a5b15-139">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="a5b15-139">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="a5b15-140">Konstruowanie i rysowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="a5b15-140">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
