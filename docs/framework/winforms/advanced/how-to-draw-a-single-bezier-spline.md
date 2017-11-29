---
title: "Porady: Rysowanie pojedynczego B &#233; zier krzywej składanej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ebdba9e01824cc764a6ab759da049add180ba83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-single-b233zier-spline"></a><span data-ttu-id="c2165-102">Porady: Rysowanie pojedynczego B &#233; zier krzywej składanej</span><span class="sxs-lookup"><span data-stu-id="c2165-102">How to: Draw a Single B&#233;zier Spline</span></span>
<span data-ttu-id="c2165-103">Krzywej Beziera jest definiowana za pomocą czterech punktów: punkt początkowy, punkty kontrolne dwóch i punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="c2165-103">A Bézier spline is defined by four points: a start point, two control points, and an endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2165-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2165-104">Example</span></span>  
 <span data-ttu-id="c2165-105">Poniższy przykład rysuje krzywej Beziera, punkt początkowy (10, 100) i punktu końcowego (200, 100).</span><span class="sxs-lookup"><span data-stu-id="c2165-105">The following example draws a Bézier spline with start point (10, 100) and endpoint (200, 100).</span></span> <span data-ttu-id="c2165-106">Formant wskazuje, czy (100, 10) i (150, 150).</span><span class="sxs-lookup"><span data-stu-id="c2165-106">The control points are (100, 10) and (150, 150).</span></span>  
  
 <span data-ttu-id="c2165-107">Na poniższej ilustracji przedstawiono wynikowy krzywej Beziera wraz z jego punkt początkowy, punkty kontrolne i punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c2165-107">The following illustration shows the resulting Bézier spline along with its start point, control points, and endpoint.</span></span> <span data-ttu-id="c2165-108">Na ilustracji przedstawiono również krzywej składanej wypukłych powłoki, czyli wielokąta sformułowany, łącząc się z czterech punktów z proste.</span><span class="sxs-lookup"><span data-stu-id="c2165-108">The illustration also shows the spline's convex hull, which is a polygon formed by connecting the four points with straight lines.</span></span>  
  
 <span data-ttu-id="c2165-109">![Beziera krzywej składanej](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span><span class="sxs-lookup"><span data-stu-id="c2165-109">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c2165-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c2165-110">Compiling the Code</span></span>  
 <span data-ttu-id="c2165-111">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c2165-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2165-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2165-112">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawBezier%2A>  
 [<span data-ttu-id="c2165-113">Krzywe Beziera w GDI +</span><span class="sxs-lookup"><span data-stu-id="c2165-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="c2165-114">Porady: Rysowanie sekwencji krzywych Beziera</span><span class="sxs-lookup"><span data-stu-id="c2165-114">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
