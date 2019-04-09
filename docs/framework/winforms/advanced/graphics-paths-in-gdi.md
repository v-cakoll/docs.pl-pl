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
ms.openlocfilehash: c9a43065210f5ef0fffcae01cc7eb88349696b6b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140507"
---
# <a name="graphics-paths-in-gdi"></a><span data-ttu-id="fdd1d-102">Ścieżki grafiki w GDI+</span><span class="sxs-lookup"><span data-stu-id="fdd1d-102">Graphics Paths in GDI+</span></span>
<span data-ttu-id="fdd1d-103">Ścieżki są tworzone przez łączenie linii, prostokąty i krzywych proste.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-103">Paths are formed by combining lines, rectangles, and simple curves.</span></span> <span data-ttu-id="fdd1d-104">Jak pamiętamy z artykułu [Przegląd grafiki wektorowej](vector-graphics-overview.md) czy następujących podstawowych bloków konstrukcyjnych okazały się być najbardziej przydatne do rysowania obrazów:</span><span class="sxs-lookup"><span data-stu-id="fdd1d-104">Recall from the [Vector Graphics Overview](vector-graphics-overview.md) that the following basic building blocks have proven to be the most useful for drawing pictures:</span></span>  
  
-   <span data-ttu-id="fdd1d-105">wiersze</span><span class="sxs-lookup"><span data-stu-id="fdd1d-105">Lines</span></span>  
  
-   <span data-ttu-id="fdd1d-106">Prostokąty</span><span class="sxs-lookup"><span data-stu-id="fdd1d-106">Rectangles</span></span>  
  
-   <span data-ttu-id="fdd1d-107">Wielokropek</span><span class="sxs-lookup"><span data-stu-id="fdd1d-107">Ellipses</span></span>  
  
-   <span data-ttu-id="fdd1d-108">Łuki</span><span class="sxs-lookup"><span data-stu-id="fdd1d-108">Arcs</span></span>  
  
-   <span data-ttu-id="fdd1d-109">Wielokąty</span><span class="sxs-lookup"><span data-stu-id="fdd1d-109">Polygons</span></span>  
  
-   <span data-ttu-id="fdd1d-110">Krzywe kardynalne</span><span class="sxs-lookup"><span data-stu-id="fdd1d-110">Cardinal splines</span></span>  
  
-   <span data-ttu-id="fdd1d-111">Krzywe Beziera</span><span class="sxs-lookup"><span data-stu-id="fdd1d-111">Bézier splines</span></span>  
  
 <span data-ttu-id="fdd1d-112">W GDI + <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt umożliwia zbieranie sekwencję te bloki konstrukcyjne w pojedynczą jednostkę.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-112">In GDI+, the <xref:System.Drawing.Drawing2D.GraphicsPath> object allows you to collect a sequence of these building blocks into a single unit.</span></span> <span data-ttu-id="fdd1d-113">Całą sekwencję linii, prostokątów, wielokąty i krzywych następnie mogą być wystawiane przy użyciu jednego wywołania do <xref:System.Drawing.Graphics.DrawPath%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-113">The entire sequence of lines, rectangles, polygons, and curves can then be drawn with one call to the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="fdd1d-114">Poniższa ilustracja przedstawia ścieżki tworzone przez połączenie linii, łuk, krzywej Beziera i kardynalnej krzywej składanej.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-114">The following illustration shows a path created by combining a line, an arc, a Bézier spline, and a cardinal spline.</span></span>  
  
 <span data-ttu-id="fdd1d-115">![Ścieżka](./media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span><span class="sxs-lookup"><span data-stu-id="fdd1d-115">![Path](./media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span></span>  
  
## <a name="using-a-path"></a><span data-ttu-id="fdd1d-116">Przy użyciu ścieżki</span><span class="sxs-lookup"><span data-stu-id="fdd1d-116">Using a Path</span></span>  
 <span data-ttu-id="fdd1d-117"><xref:System.Drawing.Drawing2D.GraphicsPath> Klasa udostępnia następujące metody do tworzenia sekwencji elementów, które mają być rysowane: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (na krzywe kardynalne), a <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-117">The <xref:System.Drawing.Drawing2D.GraphicsPath> class provides the following methods for creating a sequence of items to be drawn: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (for cardinal splines), and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span></span> <span data-ttu-id="fdd1d-118">Każda z tych metod jest przeciążona; oznacza to, że każda metoda obsługuje kilka list różnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-118">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="fdd1d-119">Na przykład jeden odmianą <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metoda otrzymuje czterech liczb całkowitych, a inna wersja <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metoda otrzymuje dwa <xref:System.Drawing.Point> obiektów.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-119">For example, one variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives four integers, and another variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="fdd1d-120">Metody dodawania wierszy, prostokąty i krzywych Beziera na ścieżkę mają metody pomocnika w liczbie mnogiej, które dodać kilka elementów do ścieżki w pojedynczym wywołaniu: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, i <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-120">The methods for adding lines, rectangles, and Bézier splines to a path have plural companion methods that add several items to the path in a single call: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span></span> <span data-ttu-id="fdd1d-121">Ponadto <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> metody mają metody pomocnika <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, zamkniętej krzywej lub koła, Dodaj do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-121">Also, the <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> methods have companion methods, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, that add a closed curve or pie to the path.</span></span>  
  
 <span data-ttu-id="fdd1d-122">Aby narysować ścieżkę, musisz mieć <xref:System.Drawing.Graphics> obiektu, <xref:System.Drawing.Pen> obiektu, a <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-122">To draw a path, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="fdd1d-123"><xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawPath%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak szerokość i kolor linii służącej do renderowania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-123">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPath%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the path.</span></span> <span data-ttu-id="fdd1d-124"><xref:System.Drawing.Drawing2D.GraphicsPath> Obiekt przechowuje sekwencji linii i krzywych, które tworzą ścieżki.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-124">The <xref:System.Drawing.Drawing2D.GraphicsPath> object stores the sequence of lines and curves that make up the path.</span></span> <span data-ttu-id="fdd1d-125"><xref:System.Drawing.Pen> Obiektu i <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu są przekazywane jako argumenty <xref:System.Drawing.Graphics.DrawPath%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-125">The <xref:System.Drawing.Pen> object and the <xref:System.Drawing.Drawing2D.GraphicsPath> object are passed as arguments to the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="fdd1d-126">Poniższy przykład pobiera ścieżki, która składa się z linii, elipsę i krzywej Beziera:</span><span class="sxs-lookup"><span data-stu-id="fdd1d-126">The following example draws a path that consists of a line, an ellipse, and a Bézier spline:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#101](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 <span data-ttu-id="fdd1d-127">Poniższa ilustracja przedstawia ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-127">The following illustration shows the path.</span></span>  
  
 <span data-ttu-id="fdd1d-128">![Path](./media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span><span class="sxs-lookup"><span data-stu-id="fdd1d-128">![Path](./media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span></span>  
  
 <span data-ttu-id="fdd1d-129">Oprócz dodawania wierszy, prostokąty i krzywych do ścieżki, można dodać ścieżki do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-129">In addition to adding lines, rectangles, and curves to a path, you can add paths to a path.</span></span> <span data-ttu-id="fdd1d-130">Dzięki temu można łączyć istniejące ścieżki w celu utworzenia dużych, złożonych ścieżki.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-130">This allows you to combine existing paths to form large, complex paths.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#102](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 <span data-ttu-id="fdd1d-131">Istnieją dwa inne elementy, można dodać do ścieżki: ciągi i wycinków.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-131">There are two other items you can add to a path: strings and pies.</span></span> <span data-ttu-id="fdd1d-132">Wykres kołowy to część wewnętrzne elipsy.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-132">A pie is a portion of the interior of an ellipse.</span></span> <span data-ttu-id="fdd1d-133">Poniższy przykład tworzy ścieżkę z łuk, krzywa kardynalna, ciąg i wykres kołowy:</span><span class="sxs-lookup"><span data-stu-id="fdd1d-133">The following example creates a path from an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#103](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 <span data-ttu-id="fdd1d-134">Poniższa ilustracja przedstawia ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-134">The following illustration shows the path.</span></span> <span data-ttu-id="fdd1d-135">Należy zauważyć, że ścieżka nie ma połączenia; Łuk, krzywa kardynalna, parametry i kołowy są rozdzielone.</span><span class="sxs-lookup"><span data-stu-id="fdd1d-135">Note that a path does not have to be connected; the arc, cardinal spline, string, and pie are separated.</span></span>  
  
 <span data-ttu-id="fdd1d-136">![Ścieżki](./media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span><span class="sxs-lookup"><span data-stu-id="fdd1d-136">![Paths](./media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd1d-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdd1d-137">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [<span data-ttu-id="fdd1d-138">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="fdd1d-138">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="fdd1d-139">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="fdd1d-139">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="fdd1d-140">Konstruowanie i rysowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="fdd1d-140">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
