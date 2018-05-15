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
ms.openlocfilehash: 2e247ec2bcd57c2fb2f5c32f61d38a2e7a267ff1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="b233zier-splines-in-gdi"></a><span data-ttu-id="f2414-102">B&#233;zier krzywe w GDI +</span><span class="sxs-lookup"><span data-stu-id="f2414-102">B&#233;zier Splines in GDI+</span></span>
<span data-ttu-id="f2414-103">Krzywej Beziera jest określony przez cztery punkty krzywej: dwa punkty końcowe (p1 i p2) i punkty kontrolne dwóch (c1 i c2).</span><span class="sxs-lookup"><span data-stu-id="f2414-103">A Bézier spline is a curve specified by four points: two end points (p1 and p2) and two control points (c1 and c2).</span></span> <span data-ttu-id="f2414-104">Krzywej zaczyna się od p1 i kończy się na p2.</span><span class="sxs-lookup"><span data-stu-id="f2414-104">The curve begins at p1 and ends at p2.</span></span> <span data-ttu-id="f2414-105">Krzywej nie przechodzi przez punkty kontrolne, ale punktów kontrolnych pełnienie pól, ściąganie krzywej w niektórych kierunkach i mające wpływ na sposób załamania krzywej.</span><span class="sxs-lookup"><span data-stu-id="f2414-105">The curve does not pass through the control points, but the control points act as magnets, pulling the curve in certain directions and influencing the way the curve bends.</span></span> <span data-ttu-id="f2414-106">Na poniższej ilustracji przedstawiono krzywej Beziera, wraz z jego punktów końcowych i punkty kontrolne.</span><span class="sxs-lookup"><span data-stu-id="f2414-106">The following illustration shows a Bézier curve along with its endpoints and control points.</span></span>  
  
 <span data-ttu-id="f2414-107">![Krzywe Beziera](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span><span class="sxs-lookup"><span data-stu-id="f2414-107">![Bezier Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span></span>  
  
 <span data-ttu-id="f2414-108">Krzywej rozpoczyna się od p1 i przenosi kierunku c1 punktu kontroli.</span><span class="sxs-lookup"><span data-stu-id="f2414-108">The curve starts at p1 and moves toward the control point c1.</span></span> <span data-ttu-id="f2414-109">Stycznej wiersz na krzywą na p1 jest rysowane z p1 c1 wiersza.</span><span class="sxs-lookup"><span data-stu-id="f2414-109">The tangent line to the curve at p1 is the line drawn from p1 to c1.</span></span> <span data-ttu-id="f2414-110">Stycznej wiersza na p2 punktu końcowego jest rysowane z c2 p2 wiersza.</span><span class="sxs-lookup"><span data-stu-id="f2414-110">The tangent line at the endpoint p2 is the line drawn from c2 to p2.</span></span>  
  
## <a name="drawing-bzier-splines"></a><span data-ttu-id="f2414-111">Rysowanie krzywych Beziera</span><span class="sxs-lookup"><span data-stu-id="f2414-111">Drawing Bézier Splines</span></span>  
 <span data-ttu-id="f2414-112">Rysowanie krzywej Beziera, potrzebujesz wystąpienia <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Pen>.</span><span class="sxs-lookup"><span data-stu-id="f2414-112">To draw a Bézier spline, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Pen>.</span></span> <span data-ttu-id="f2414-113">Wystąpienie <xref:System.Drawing.Graphics> klasa udostępnia <xref:System.Drawing.Graphics.DrawBezier%2A> metody i <xref:System.Drawing.Pen> przechowuje atrybuty, takie jak szerokości i koloru linii służącej do renderowania krzywej.</span><span class="sxs-lookup"><span data-stu-id="f2414-113">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawBezier%2A> method, and the <xref:System.Drawing.Pen> stores attributes, such as width and color, of the line used to render the curve.</span></span> <span data-ttu-id="f2414-114"><xref:System.Drawing.Pen> Jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawBezier%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f2414-114">The <xref:System.Drawing.Pen> is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawBezier%2A> method.</span></span> <span data-ttu-id="f2414-115">Pozostałe argumenty przekazane do <xref:System.Drawing.Graphics.DrawBezier%2A> metody są punkty końcowe i punkty kontrolne.</span><span class="sxs-lookup"><span data-stu-id="f2414-115">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawBezier%2A> method are the endpoints and the control points.</span></span> <span data-ttu-id="f2414-116">Poniższy przykład rysuje krzywej Beziera, z punkt (0, 0), początkowy kontroli punktów (40, 20) i (80, 150) i końcowe (100, 10):</span><span class="sxs-lookup"><span data-stu-id="f2414-116">The following example draws a Bézier spline with starting point (0, 0), control points (40, 20) and (80, 150), and ending point (100, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 <span data-ttu-id="f2414-117">Na poniższej ilustracji przedstawiono krzywej, punkty kontrolne i dwa wiersze stycznej.</span><span class="sxs-lookup"><span data-stu-id="f2414-117">The following illustration shows the curve, the control points, and two tangent lines.</span></span>  
  
 <span data-ttu-id="f2414-118">![Krzywe Beziera](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span><span class="sxs-lookup"><span data-stu-id="f2414-118">![Bezier Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span></span>  
  
 <span data-ttu-id="f2414-119">Krzywe Beziera pierwotnie zostały opracowane przez Beziera Pierre dla projektu w branży motoryzacyjnych.</span><span class="sxs-lookup"><span data-stu-id="f2414-119">Bézier splines were originally developed by Pierre Bézier for design in the automotive industry.</span></span> <span data-ttu-id="f2414-120">Ponieważ okazały się użyteczne w wielu rodzajów CAD, a także są używane do definiowania konturów czcionki.</span><span class="sxs-lookup"><span data-stu-id="f2414-120">They have since proven to be useful in many types of computer-aided design and are also used to define the outlines of fonts.</span></span> <span data-ttu-id="f2414-121">Krzywe Beziera umożliwia uzyskanie szerokiej gamy kształtów, niektóre z nich są wyświetlane na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="f2414-121">Bézier splines can yield a wide variety of shapes, some of which are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="f2414-122">![Ścieżki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span><span class="sxs-lookup"><span data-stu-id="f2414-122">![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2414-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2414-123">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="f2414-124">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="f2414-124">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="f2414-125">Konstruowanie i rysowanie krzywych</span><span class="sxs-lookup"><span data-stu-id="f2414-125">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)  
 [<span data-ttu-id="f2414-126">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="f2414-126">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="f2414-127">Instrukcje: tworzenie pióra</span><span class="sxs-lookup"><span data-stu-id="f2414-127">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
