---
title: 'Porady: rysowanie krzywych kardynalnych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 3ad06eb28e1d8e6b5d5f4a77e545f174d8a68d9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525063"
---
# <a name="how-to-draw-cardinal-splines"></a><span data-ttu-id="00e66-102">Porady: rysowanie krzywych kardynalnych</span><span class="sxs-lookup"><span data-stu-id="00e66-102">How to: Draw Cardinal Splines</span></span>
<span data-ttu-id="00e66-103">Kardynalnej krzywej składanej jest krzywą płynnie przechodzi przez podany zestaw punktów.</span><span class="sxs-lookup"><span data-stu-id="00e66-103">A cardinal spline is a curve that passes smoothly through a given set of points.</span></span> <span data-ttu-id="00e66-104">Do rysowania kardynalnej krzywej składanej, Utwórz <xref:System.Drawing.Graphics> obiektu i przekazać adres tablicę punkty <xref:System.Drawing.Graphics.DrawCurve%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="00e66-104">To draw a cardinal spline, create a <xref:System.Drawing.Graphics> object and pass the address of an array of points to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span>  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a><span data-ttu-id="00e66-105">Rysowanie w kształcie dzwonka krzywej kardynalnej</span><span class="sxs-lookup"><span data-stu-id="00e66-105">Drawing a Bell-Shaped Cardinal Spline</span></span>  
  
-   <span data-ttu-id="00e66-106">Poniższy przykład rysuje w kształcie dzwonka kardynalnej krzywej składanej który przechodzi przez pięć punktów wyznaczonych.</span><span class="sxs-lookup"><span data-stu-id="00e66-106">The following example draws a bell-shaped cardinal spline that passes through five designated points.</span></span> <span data-ttu-id="00e66-107">Na poniższej ilustracji przedstawiono krzywej i pięć punktów.</span><span class="sxs-lookup"><span data-stu-id="00e66-107">The following illustration shows the curve and five points.</span></span>  
  
     <span data-ttu-id="00e66-108">![Kardynalnej krzywej składanej](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")</span><span class="sxs-lookup"><span data-stu-id="00e66-108">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a><span data-ttu-id="00e66-109">Rysowanie zamkniętej krzywej kardynalnej</span><span class="sxs-lookup"><span data-stu-id="00e66-109">Drawing a Closed Cardinal Spline</span></span>  
  
-   <span data-ttu-id="00e66-110">Użyj <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metody <xref:System.Drawing.Graphics> klasy do zamkniętej krzywej kardynalnej rysowania.</span><span class="sxs-lookup"><span data-stu-id="00e66-110">Use the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method of the <xref:System.Drawing.Graphics> class to draw a closed cardinal spline.</span></span> <span data-ttu-id="00e66-111">W zamkniętej krzywej kardynalnej krzywej będzie kontynuowane do ostatniego punktu w macierzy i nawiązanie połączenia z pierwszego punktu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="00e66-111">In a closed cardinal spline, the curve continues through the last point in the array and connects with the first point in the array.</span></span> <span data-ttu-id="00e66-112">Poniższy przykład rysuje zamkniętego kardynalnej krzywej składanej, który przechodzi przez sześć wyznaczonych punktów.</span><span class="sxs-lookup"><span data-stu-id="00e66-112">The following example draws a closed cardinal spline that passes through six designated points.</span></span> <span data-ttu-id="00e66-113">Na poniższej ilustracji przedstawiono zamkniętej krzywej składanej wraz z sześciu punktów.</span><span class="sxs-lookup"><span data-stu-id="00e66-113">The following illustration shows the closed spline along with the six points.</span></span>  
  
 <span data-ttu-id="00e66-114">![Kardynalnej krzywej składanej](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")</span><span class="sxs-lookup"><span data-stu-id="00e66-114">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a><span data-ttu-id="00e66-115">Zmiana odcinek łącznika kardynalnej krzywej składanej</span><span class="sxs-lookup"><span data-stu-id="00e66-115">Changing the Bend of a Cardinal Spline</span></span>  
  
-   <span data-ttu-id="00e66-116">Zmień sposób kardynalnej krzywej składanej załamania przekazując argument naprężenia <xref:System.Drawing.Graphics.DrawCurve%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="00e66-116">Change the way a cardinal spline bends by passing a tension argument to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span> <span data-ttu-id="00e66-117">Poniższy przykład rysuje trzy kardynalne, które przechodzą przez ten sam zestaw punktów.</span><span class="sxs-lookup"><span data-stu-id="00e66-117">The following example draws three cardinal splines that pass through the same set of points.</span></span> <span data-ttu-id="00e66-118">Na poniższej ilustracji przedstawiono trzy krzywe wraz z wartościami naprężenia.</span><span class="sxs-lookup"><span data-stu-id="00e66-118">The following illustration shows the three splines along with their tension values.</span></span> <span data-ttu-id="00e66-119">Należy pamiętać, że gdy naciągnięcie ma wartość 0, punkty są połączone liniami proste.</span><span class="sxs-lookup"><span data-stu-id="00e66-119">Note that when the tension is 0, the points are connected by straight lines.</span></span>  
  
 <span data-ttu-id="00e66-120">![Kardynalnej krzywej składanej](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")</span><span class="sxs-lookup"><span data-stu-id="00e66-120">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="00e66-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="00e66-121">Compiling the Code</span></span>  
 <span data-ttu-id="00e66-122">Powyższych przykładach są przeznaczone do użytku z formularzy systemu Windows, a potrzebują <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="00e66-122">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e66-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00e66-123">See Also</span></span>  
 [<span data-ttu-id="00e66-124">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="00e66-124">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="00e66-125">Konstruowanie i rysowanie krzywych</span><span class="sxs-lookup"><span data-stu-id="00e66-125">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
