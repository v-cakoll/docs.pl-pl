---
title: 'Instrukcje: Rysowanie krzywych kardynalnych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 2f03177bf97936a2ca9558972d4d82fa3e07463c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204955"
---
# <a name="how-to-draw-cardinal-splines"></a><span data-ttu-id="41098-102">Instrukcje: Rysowanie krzywych kardynalnych</span><span class="sxs-lookup"><span data-stu-id="41098-102">How to: Draw Cardinal Splines</span></span>
<span data-ttu-id="41098-103">Krzywa kardynalna jest płynnie przechodzący przez podany zestaw punktów krzywej.</span><span class="sxs-lookup"><span data-stu-id="41098-103">A cardinal spline is a curve that passes smoothly through a given set of points.</span></span> <span data-ttu-id="41098-104">Aby narysować kardynalna, należy utworzyć <xref:System.Drawing.Graphics> i przekazać adres tablica wskazuje <xref:System.Drawing.Graphics.DrawCurve%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="41098-104">To draw a cardinal spline, create a <xref:System.Drawing.Graphics> object and pass the address of an array of points to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span>  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a><span data-ttu-id="41098-105">Rysowanie krzywej składanej Kardynalną w kształcie dzwonka</span><span class="sxs-lookup"><span data-stu-id="41098-105">Drawing a Bell-Shaped Cardinal Spline</span></span>  
  
-   <span data-ttu-id="41098-106">Poniższy przykład pobiera w kształcie dzwonka kardynalna przechodzący przez pięć punktów wyznaczonym.</span><span class="sxs-lookup"><span data-stu-id="41098-106">The following example draws a bell-shaped cardinal spline that passes through five designated points.</span></span> <span data-ttu-id="41098-107">Na poniższej ilustracji przedstawiono krzywej i pięć punktów.</span><span class="sxs-lookup"><span data-stu-id="41098-107">The following illustration shows the curve and five points.</span></span>  
  
     ![Diagram przedstawiający kardynalnej krzywej składanej w kształcie dzwonka.](./media/how-to-draw-cardinal-splines/bell-shaped-cardinal-spline.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a><span data-ttu-id="41098-109">Rysowanie zamkniętej krzywej kardynalnej</span><span class="sxs-lookup"><span data-stu-id="41098-109">Drawing a Closed Cardinal Spline</span></span>  
  
-   <span data-ttu-id="41098-110">Użyj <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metody <xref:System.Drawing.Graphics> klasy, aby narysować zamkniętej krzywej kardynalnej.</span><span class="sxs-lookup"><span data-stu-id="41098-110">Use the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method of the <xref:System.Drawing.Graphics> class to draw a closed cardinal spline.</span></span> <span data-ttu-id="41098-111">W zamkniętej krzywej kardynalnej krzywej kontynuuje do ostatniego punktu w macierzy i nawiązuje połączenie z pierwszym punktem w tablicy.</span><span class="sxs-lookup"><span data-stu-id="41098-111">In a closed cardinal spline, the curve continues through the last point in the array and connects with the first point in the array.</span></span> <span data-ttu-id="41098-112">Poniższy przykład pobiera zamknięte kardynalna przechodzący przez sześć wyznaczonym punktów.</span><span class="sxs-lookup"><span data-stu-id="41098-112">The following example draws a closed cardinal spline that passes through six designated points.</span></span> <span data-ttu-id="41098-113">Poniższa ilustracja przedstawia zamkniętej krzywej składanej wraz z sześciu pól:</span><span class="sxs-lookup"><span data-stu-id="41098-113">The following illustration shows the closed spline along with the six points:</span></span>  
  
 ![Diagram przedstawiający zamkniętej krzywej kardynalnej.](./media/how-to-draw-cardinal-splines/closed-cardinal-spine.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a><span data-ttu-id="41098-115">Zmiana odcinek łącznika krzywej składanej kardynalnych</span><span class="sxs-lookup"><span data-stu-id="41098-115">Changing the Bend of a Cardinal Spline</span></span>  
  
-   <span data-ttu-id="41098-116">Zmiana sposobu kardynalna załamania przez przekazanie argumentu napięcie <xref:System.Drawing.Graphics.DrawCurve%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="41098-116">Change the way a cardinal spline bends by passing a tension argument to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span> <span data-ttu-id="41098-117">Poniższy przykład pobiera trzy kardynalne, które przechodzą przez ten sam zestaw punktów.</span><span class="sxs-lookup"><span data-stu-id="41098-117">The following example draws three cardinal splines that pass through the same set of points.</span></span> <span data-ttu-id="41098-118">Poniższa ilustracja przedstawia trzy krzywe wraz z wartościami napięcie.</span><span class="sxs-lookup"><span data-stu-id="41098-118">The following illustration shows the three splines along with their tension values.</span></span> <span data-ttu-id="41098-119">Należy pamiętać, że gdy naciągnięcie wynosi 0, punkty są połączone liniami proste.</span><span class="sxs-lookup"><span data-stu-id="41098-119">Note that when the tension is 0, the points are connected by straight lines.</span></span>  
  
 ![Diagram przedstawiający trzy krzywe kardynalne.](./media/how-to-draw-cardinal-splines/three-cardinal-splines.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41098-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="41098-121">Compiling the Code</span></span>  
 <span data-ttu-id="41098-122">Powyższych przykładach są skonstruowane do użycia za pomocą interfejsu Windows Forms i wymagają one <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="41098-122">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41098-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41098-123">See also</span></span>

- [<span data-ttu-id="41098-124">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="41098-124">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="41098-125">Konstruowanie i rysowanie krzywych</span><span class="sxs-lookup"><span data-stu-id="41098-125">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
