---
title: B&#233;zier krzywe w GDI +
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: ff4e9eb18610b70c88e057d3d44020321bbb9f4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779275"
---
# <a name="b233zier-splines-in-gdi"></a><span data-ttu-id="f0ebd-102">B&#233;zier krzywe w GDI +</span><span class="sxs-lookup"><span data-stu-id="f0ebd-102">B&#233;zier Splines in GDI+</span></span>
<span data-ttu-id="f0ebd-103">Krzywej Beziera jest określony przez cztery punkty krzywej: dwa punkty końcowe (p1 i p2) i punkty kontrolne dwóch (c1 i c2).</span><span class="sxs-lookup"><span data-stu-id="f0ebd-103">A Bézier spline is a curve specified by four points: two end points (p1 and p2) and two control points (c1 and c2).</span></span> <span data-ttu-id="f0ebd-104">Krzywa rozpoczyna się od p1 i kończy się na p2.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-104">The curve begins at p1 and ends at p2.</span></span> <span data-ttu-id="f0ebd-105">Krzywa nie przechodzi przez punkty kontrolne, ale punktów kontrolnych pełnić rolę pól, ściągając krzywej w niektórych kierunkach i wywieranie wpływu na sposób, w jaki załamania krzywej.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-105">The curve does not pass through the control points, but the control points act as magnets, pulling the curve in certain directions and influencing the way the curve bends.</span></span> <span data-ttu-id="f0ebd-106">Poniższa ilustracja przedstawia krzywej Beziera, wraz z jej punktów końcowych i punkty kontrolne.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-106">The following illustration shows a Bézier curve along with its endpoints and control points.</span></span>  
  
 <span data-ttu-id="f0ebd-107">![Bezier Splines](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span><span class="sxs-lookup"><span data-stu-id="f0ebd-107">![Bezier Splines](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span></span>  
  
 <span data-ttu-id="f0ebd-108">Krzywa rozpoczyna się od p1 i jest przesuwany c1 punktu kontroli.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-108">The curve starts at p1 and moves toward the control point c1.</span></span> <span data-ttu-id="f0ebd-109">Tangens linii krzywej w p1 jest linią od p1 do c1.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-109">The tangent line to the curve at p1 is the line drawn from p1 to c1.</span></span> <span data-ttu-id="f0ebd-110">Stycznej wiersza na p2 punkt końcowy jest linią z c2 do p2.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-110">The tangent line at the endpoint p2 is the line drawn from c2 to p2.</span></span>  
  
## <a name="drawing-bzier-splines"></a><span data-ttu-id="f0ebd-111">Rysowanie krzywych Beziera</span><span class="sxs-lookup"><span data-stu-id="f0ebd-111">Drawing Bézier Splines</span></span>  
 <span data-ttu-id="f0ebd-112">Rysowanie krzywej Beziera, potrzebne jest wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Pen>.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-112">To draw a Bézier spline, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Pen>.</span></span> <span data-ttu-id="f0ebd-113">Wystąpienie <xref:System.Drawing.Graphics> klasa udostępnia <xref:System.Drawing.Graphics.DrawBezier%2A> metody i <xref:System.Drawing.Pen> przechowuje atrybuty, takie jak szerokość i kolor linii służącej do renderowania krzywej.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-113">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawBezier%2A> method, and the <xref:System.Drawing.Pen> stores attributes, such as width and color, of the line used to render the curve.</span></span> <span data-ttu-id="f0ebd-114"><xref:System.Drawing.Pen> Jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawBezier%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-114">The <xref:System.Drawing.Pen> is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawBezier%2A> method.</span></span> <span data-ttu-id="f0ebd-115">Pozostałe argumenty przekazywane do <xref:System.Drawing.Graphics.DrawBezier%2A> metody są punkty końcowe i punkty kontrolne.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-115">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawBezier%2A> method are the endpoints and the control points.</span></span> <span data-ttu-id="f0ebd-116">Poniższy przykład pobiera krzywej Beziera z początkowy (0, 0), kontrolować punkty (40, 20) i (80, 150), a końcowe (100, 10):</span><span class="sxs-lookup"><span data-stu-id="f0ebd-116">The following example draws a Bézier spline with starting point (0, 0), control points (40, 20) and (80, 150), and ending point (100, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#71](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 <span data-ttu-id="f0ebd-117">Na poniższej ilustracji przedstawiono krzywej, punktów kontrolnych i dwa wiersze stycznej.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-117">The following illustration shows the curve, the control points, and two tangent lines.</span></span>  
  
 <span data-ttu-id="f0ebd-118">![Bezier Splines](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span><span class="sxs-lookup"><span data-stu-id="f0ebd-118">![Bezier Splines](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span></span>  
  
 <span data-ttu-id="f0ebd-119">Krzywe Beziera pierwotnie opracowano w za Beziera Pierre w dziedzinie projektowania w przemysł samochodowy.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-119">Bézier splines were originally developed by Pierre Bézier for design in the automotive industry.</span></span> <span data-ttu-id="f0ebd-120">One od okazały się przydatne w wielu rodzajach CAD i są również używane do definiowania konturów czcionki.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-120">They have since proven to be useful in many types of computer-aided design and are also used to define the outlines of fonts.</span></span> <span data-ttu-id="f0ebd-121">Krzywe Beziera może przynieść szereg kształtów, niektóre z nich są wyświetlane na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="f0ebd-121">Bézier splines can yield a wide variety of shapes, some of which are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="f0ebd-122">![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span><span class="sxs-lookup"><span data-stu-id="f0ebd-122">![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ebd-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0ebd-123">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="f0ebd-124">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="f0ebd-124">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="f0ebd-125">Konstruowanie i rysowanie krzywych</span><span class="sxs-lookup"><span data-stu-id="f0ebd-125">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
- [<span data-ttu-id="f0ebd-126">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="f0ebd-126">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="f0ebd-127">Instrukcje: Tworzenie pióra</span><span class="sxs-lookup"><span data-stu-id="f0ebd-127">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
