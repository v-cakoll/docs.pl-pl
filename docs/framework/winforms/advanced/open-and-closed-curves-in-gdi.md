---
title: Krzywe otwarte i zamknięte w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
ms.openlocfilehash: 8581b5f8d774a91d17dcfe93f801d87394f28c0b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735211"
---
# <a name="open-and-closed-curves-in-gdi"></a><span data-ttu-id="df299-102">Krzywe otwarte i zamknięte w GDI+</span><span class="sxs-lookup"><span data-stu-id="df299-102">Open and Closed Curves in GDI+</span></span>
<span data-ttu-id="df299-103">Na poniższej ilustracji przedstawiono dwie krzywe: otwarty i jedną zamknięte.</span><span class="sxs-lookup"><span data-stu-id="df299-103">The following illustration shows two curves: one open and one closed.</span></span>  
  
 <span data-ttu-id="df299-104">![Krzywe otwarte i zamknięte](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span><span class="sxs-lookup"><span data-stu-id="df299-104">![Open & Closed curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span></span>  
  
## <a name="managed-interface-for-curves"></a><span data-ttu-id="df299-105">Zarządzany interfejs dla krzywych</span><span class="sxs-lookup"><span data-stu-id="df299-105">Managed Interface for Curves</span></span>  
 <span data-ttu-id="df299-106">Zamknięte krzywych mają wewnętrzne i może zostać wypełniony przy użyciu pędzla.</span><span class="sxs-lookup"><span data-stu-id="df299-106">Closed curves have an interior and therefore can be filled with a brush.</span></span> <span data-ttu-id="df299-107"><xref:System.Drawing.Graphics> Klasy w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia następujące metody do wypełniania kształtów zamkniętych i krzywych: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, i <xref:System.Drawing.Graphics.FillRegion%2A>.</span><span class="sxs-lookup"><span data-stu-id="df299-107">The <xref:System.Drawing.Graphics> class in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the following methods for filling closed shapes and curves: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, and <xref:System.Drawing.Graphics.FillRegion%2A>.</span></span> <span data-ttu-id="df299-108">Przy każdym wywołaniu jednej z następujących metod, należy przekazać jeden z typów określonych pędzla (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, lub <xref:System.Drawing.Drawing2D.PathGradientBrush>) jako argument.</span><span class="sxs-lookup"><span data-stu-id="df299-108">Whenever you call one of these methods, you must pass one of the specific brush types (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, or <xref:System.Drawing.Drawing2D.PathGradientBrush>) as an argument.</span></span>  
  
 <span data-ttu-id="df299-109"><xref:System.Drawing.Graphics.FillPie%2A> Metody jest uzupełnieniem do <xref:System.Drawing.Graphics.DrawArc%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="df299-109">The <xref:System.Drawing.Graphics.FillPie%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawArc%2A> method.</span></span> <span data-ttu-id="df299-110">Podobnie jak <xref:System.Drawing.Graphics.DrawArc%2A> metoda rysuje część zarys elipsy, <xref:System.Drawing.Graphics.FillPie%2A> metoda wypełni część wewnętrzne elipsy.</span><span class="sxs-lookup"><span data-stu-id="df299-110">Just as the <xref:System.Drawing.Graphics.DrawArc%2A> method draws a portion of the outline of an ellipse, the <xref:System.Drawing.Graphics.FillPie%2A> method fills a portion of the interior of an ellipse.</span></span> <span data-ttu-id="df299-111">Poniższy przykład łuk i wstawia odpowiednią część wewnętrzne elipsy:</span><span class="sxs-lookup"><span data-stu-id="df299-111">The following example draws an arc and fills the corresponding portion of the interior of the ellipse:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 <span data-ttu-id="df299-112">Na poniższej ilustracji przedstawiono łuk i wypełniony kołowy.</span><span class="sxs-lookup"><span data-stu-id="df299-112">The following illustration shows the arc and the filled pie.</span></span>  
  
 <span data-ttu-id="df299-113">![Krzywe otwarte i zamknięte](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span><span class="sxs-lookup"><span data-stu-id="df299-113">![Open & Closed curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span></span>  
  
 <span data-ttu-id="df299-114"><xref:System.Drawing.Graphics.FillClosedCurve%2A> Metody jest uzupełnieniem do <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="df299-114">The <xref:System.Drawing.Graphics.FillClosedCurve%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method.</span></span> <span data-ttu-id="df299-115">Obie metody automatycznie Zamknij krzywej przez nawiązanie połączenia punktu początkowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="df299-115">Both methods automatically close the curve by connecting the ending point to the starting point.</span></span> <span data-ttu-id="df299-116">Poniższy przykład pobiera krzywej, który przechodzi przez (0, 0), (60, 20) i (40, 50).</span><span class="sxs-lookup"><span data-stu-id="df299-116">The following example draws a curve that passes through (0, 0), (60, 20), and (40, 50).</span></span> <span data-ttu-id="df299-117">Następnie krzywej zostaje automatycznie zamknięty, łącząc (40, 50) do punkt początkowy (0, 0), i wewnętrznych jest wypełniony jednolitym kolorem.</span><span class="sxs-lookup"><span data-stu-id="df299-117">Then, the curve is automatically closed by connecting (40, 50) to the starting point (0, 0), and the interior is filled with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <span data-ttu-id="df299-118"><xref:System.Drawing.Graphics.FillPath%2A> Metoda wypełni wnętrza osobnych części ścieżki.</span><span class="sxs-lookup"><span data-stu-id="df299-118">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the interiors of the separate pieces of a path.</span></span> <span data-ttu-id="df299-119">Jeśli fragment ścieżki nie tworzą zamkniętej krzywej lub kształtu, <xref:System.Drawing.Graphics.FillPath%2A> metoda automatycznie zamyka danego fragmentu ścieżkę przed jego wypełnianie.</span><span class="sxs-lookup"><span data-stu-id="df299-119">If a piece of a path doesn't form a closed curve or shape, the <xref:System.Drawing.Graphics.FillPath%2A> method automatically closes that piece of the path before filling it.</span></span> <span data-ttu-id="df299-120">Poniższy przykład pobiera i wypełnia ścieżką, która składa się z łuk, krzywa kardynalna, ciąg i wykres kołowy:</span><span class="sxs-lookup"><span data-stu-id="df299-120">The following example draws and fills a path that consists of an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 <span data-ttu-id="df299-121">Poniższa ilustracja przedstawia ścieżki z lub bez wypełnienia kryjącego.</span><span class="sxs-lookup"><span data-stu-id="df299-121">The following illustration shows the path with and without the solid fill.</span></span> <span data-ttu-id="df299-122">Należy pamiętać, że tekst w ciągu jest opisane, ale nie jest wypełniony, przez <xref:System.Drawing.Graphics.DrawPath%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="df299-122">Note that the text in the string is outlined, but not filled, by the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="df299-123">Jest <xref:System.Drawing.Graphics.FillPath%2A> metodę, która umożliwia malowanie wnętrza znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="df299-123">It is the <xref:System.Drawing.Graphics.FillPath%2A> method that paints the interiors of the characters in the string.</span></span>  
  
 <span data-ttu-id="df299-124">![Ciąg znaków w ścieżce](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span><span class="sxs-lookup"><span data-stu-id="df299-124">![String in a path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df299-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df299-125">See also</span></span>
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [<span data-ttu-id="df299-126">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="df299-126">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [<span data-ttu-id="df299-127">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="df299-127">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="df299-128">Konstruowanie i rysowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="df299-128">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
