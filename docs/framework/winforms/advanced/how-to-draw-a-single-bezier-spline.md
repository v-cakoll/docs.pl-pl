---
title: 'Porady: Rysowanie pojedynczego B&#233;zier krzywymi składanymi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 9e91b63275c37fc0cdde5721fddd114e1bf2264e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-single-b233zier-spline"></a><span data-ttu-id="b6114-102">Porady: Rysowanie pojedynczego B&#233;zier krzywymi składanymi</span><span class="sxs-lookup"><span data-stu-id="b6114-102">How to: Draw a Single B&#233;zier Spline</span></span>
<span data-ttu-id="b6114-103">Krzywej Beziera jest definiowana za pomocą czterech punktów: punkt początkowy, punkty kontrolne dwóch i punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="b6114-103">A Bézier spline is defined by four points: a start point, two control points, and an endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6114-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6114-104">Example</span></span>  
 <span data-ttu-id="b6114-105">Poniższy przykład rysuje krzywej Beziera, punkt początkowy (10, 100) i punktu końcowego (200, 100).</span><span class="sxs-lookup"><span data-stu-id="b6114-105">The following example draws a Bézier spline with start point (10, 100) and endpoint (200, 100).</span></span> <span data-ttu-id="b6114-106">Formant wskazuje, czy (100, 10) i (150, 150).</span><span class="sxs-lookup"><span data-stu-id="b6114-106">The control points are (100, 10) and (150, 150).</span></span>  
  
 <span data-ttu-id="b6114-107">Na poniższej ilustracji przedstawiono wynikowy krzywej Beziera wraz z jego punkt początkowy, punkty kontrolne i punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b6114-107">The following illustration shows the resulting Bézier spline along with its start point, control points, and endpoint.</span></span> <span data-ttu-id="b6114-108">Na ilustracji przedstawiono również krzywej składanej wypukłych powłoki, czyli wielokąta sformułowany, łącząc się z czterech punktów z proste.</span><span class="sxs-lookup"><span data-stu-id="b6114-108">The illustration also shows the spline's convex hull, which is a polygon formed by connecting the four points with straight lines.</span></span>  
  
 <span data-ttu-id="b6114-109">![Beziera krzywej składanej](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span><span class="sxs-lookup"><span data-stu-id="b6114-109">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b6114-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b6114-110">Compiling the Code</span></span>  
 <span data-ttu-id="b6114-111">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b6114-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6114-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6114-112">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawBezier%2A>  
 [<span data-ttu-id="b6114-113">Krzywe Beziera w GDI+</span><span class="sxs-lookup"><span data-stu-id="b6114-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="b6114-114">Instrukcje: rysowanie sekwencji krzywych Beziera</span><span class="sxs-lookup"><span data-stu-id="b6114-114">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
