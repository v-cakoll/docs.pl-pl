---
title: 'Instrukcje: Rysowanie pojedynczej B&#233;zier z krzywymi składanymi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 0731595dc25b1afb4b3dbcc7eedbfb92ef32d267
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58126282"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a><span data-ttu-id="b78ac-102">Instrukcje: Rysowanie pojedynczej B&#233;zier z krzywymi składanymi</span><span class="sxs-lookup"><span data-stu-id="b78ac-102">How to: Draw a Single B&#233;zier Spline</span></span>
<span data-ttu-id="b78ac-103">Krzywej Beziera jest definiowany przez cztery punkty: punkt początkowy, punktów kontrolnych dwóch i punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="b78ac-103">A Bézier spline is defined by four points: a start point, two control points, and an endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b78ac-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b78ac-104">Example</span></span>  
 <span data-ttu-id="b78ac-105">Poniższy przykład pobiera krzywej Beziera punkt początkowy (10, 100) i punkt końcowy (200, 100).</span><span class="sxs-lookup"><span data-stu-id="b78ac-105">The following example draws a Bézier spline with start point (10, 100) and endpoint (200, 100).</span></span> <span data-ttu-id="b78ac-106">Kontrolka wskazuje, czy (100, 10) i (150, 150).</span><span class="sxs-lookup"><span data-stu-id="b78ac-106">The control points are (100, 10) and (150, 150).</span></span>  
  
 <span data-ttu-id="b78ac-107">Poniższa ilustracja przedstawia wynikowy Beziera wraz z jego punkt początkowy, punktów kontrolnych i punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b78ac-107">The following illustration shows the resulting Bézier spline along with its start point, control points, and endpoint.</span></span> <span data-ttu-id="b78ac-108">Na ilustracji pokazano również krzywej składanej wypukłe kadłuba, czyli wielokąta sformułowany, łącząc cztery punkty za pomocą prostych wierszy.</span><span class="sxs-lookup"><span data-stu-id="b78ac-108">The illustration also shows the spline's convex hull, which is a polygon formed by connecting the four points with straight lines.</span></span>  
  
 ![Ilustracja Krzywa Beziera.](./media/how-to-draw-a-single-bezier-spline/bezier-spline-illustration.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b78ac-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b78ac-110">Compiling the Code</span></span>  
 <span data-ttu-id="b78ac-111">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b78ac-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b78ac-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b78ac-112">See also</span></span>
- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [<span data-ttu-id="b78ac-113">Krzywe Beziera w GDI+</span><span class="sxs-lookup"><span data-stu-id="b78ac-113">Bézier Splines in GDI+</span></span>](bezier-splines-in-gdi.md)
- [<span data-ttu-id="b78ac-114">Instrukcje: Rysowanie sekwencji krzywych Beziera</span><span class="sxs-lookup"><span data-stu-id="b78ac-114">How to: Draw a Sequence of Bézier Splines</span></span>](how-to-draw-a-sequence-of-bezier-splines.md)
