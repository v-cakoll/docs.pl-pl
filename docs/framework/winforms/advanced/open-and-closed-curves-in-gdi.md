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
ms.openlocfilehash: 47f420184ac384ab11054d1cc3e767ab7f618234
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527151"
---
# <a name="open-and-closed-curves-in-gdi"></a><span data-ttu-id="f262a-102">Krzywe otwarte i zamknięte w GDI+</span><span class="sxs-lookup"><span data-stu-id="f262a-102">Open and Closed Curves in GDI+</span></span>
<span data-ttu-id="f262a-103">Na poniższej ilustracji przedstawiono dwie krzywe: otwarty i jedną zamknięte.</span><span class="sxs-lookup"><span data-stu-id="f262a-103">The following illustration shows two curves: one open and one closed.</span></span>  
  
 <span data-ttu-id="f262a-104">![Krzywe otwarte i zamknięte](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span><span class="sxs-lookup"><span data-stu-id="f262a-104">![Open & Closed curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span></span>  
  
## <a name="managed-interface-for-curves"></a><span data-ttu-id="f262a-105">Zarządzanego interfejsu dla krzywych</span><span class="sxs-lookup"><span data-stu-id="f262a-105">Managed Interface for Curves</span></span>  
 <span data-ttu-id="f262a-106">Zamknięte krzywych mają wewnętrzne i może zostać wypełniony przy użyciu pędzla.</span><span class="sxs-lookup"><span data-stu-id="f262a-106">Closed curves have an interior and therefore can be filled with a brush.</span></span> <span data-ttu-id="f262a-107"><xref:System.Drawing.Graphics> Klasy w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia następujące metody do wypełniania krzywe i kształty zamknięte: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, i <xref:System.Drawing.Graphics.FillRegion%2A>.</span><span class="sxs-lookup"><span data-stu-id="f262a-107">The <xref:System.Drawing.Graphics> class in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the following methods for filling closed shapes and curves: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, and <xref:System.Drawing.Graphics.FillRegion%2A>.</span></span> <span data-ttu-id="f262a-108">Zawsze, gdy wywoływana jednej z tych metod, trzeba przekazać jeden z typów określonych pędzla (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, lub <xref:System.Drawing.Drawing2D.PathGradientBrush>) jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="f262a-108">Whenever you call one of these methods, you must pass one of the specific brush types (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, or <xref:System.Drawing.Drawing2D.PathGradientBrush>) as an argument.</span></span>  
  
 <span data-ttu-id="f262a-109"><xref:System.Drawing.Graphics.FillPie%2A> Jest metoda pomocnika do <xref:System.Drawing.Graphics.DrawArc%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f262a-109">The <xref:System.Drawing.Graphics.FillPie%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawArc%2A> method.</span></span> <span data-ttu-id="f262a-110">Podobnie jak <xref:System.Drawing.Graphics.DrawArc%2A> metody rysuje część konturu elipsy <xref:System.Drawing.Graphics.FillPie%2A> metody wypełnia część wewnątrz elipsy.</span><span class="sxs-lookup"><span data-stu-id="f262a-110">Just as the <xref:System.Drawing.Graphics.DrawArc%2A> method draws a portion of the outline of an ellipse, the <xref:System.Drawing.Graphics.FillPie%2A> method fills a portion of the interior of an ellipse.</span></span> <span data-ttu-id="f262a-111">W poniższym przykładzie łuk i wypełnia odpowiednich części wewnątrz elipsy:</span><span class="sxs-lookup"><span data-stu-id="f262a-111">The following example draws an arc and fills the corresponding portion of the interior of the ellipse:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 <span data-ttu-id="f262a-112">Na poniższej ilustracji przedstawiono łuk i kołowy wypełnione.</span><span class="sxs-lookup"><span data-stu-id="f262a-112">The following illustration shows the arc and the filled pie.</span></span>  
  
 <span data-ttu-id="f262a-113">![Krzywe otwarte i zamknięte](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span><span class="sxs-lookup"><span data-stu-id="f262a-113">![Open & Closed curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span></span>  
  
 <span data-ttu-id="f262a-114"><xref:System.Drawing.Graphics.FillClosedCurve%2A> Jest metoda pomocnika do <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f262a-114">The <xref:System.Drawing.Graphics.FillClosedCurve%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method.</span></span> <span data-ttu-id="f262a-115">Obie metody automatycznie zamknąć krzywą przez połączenie punktu końcowego do punktu początkowego.</span><span class="sxs-lookup"><span data-stu-id="f262a-115">Both methods automatically close the curve by connecting the ending point to the starting point.</span></span> <span data-ttu-id="f262a-116">Poniższy przykład rysuje krzywej, który przechodzi przez (0, 0), (60, 20) i (40, 50).</span><span class="sxs-lookup"><span data-stu-id="f262a-116">The following example draws a curve that passes through (0, 0), (60, 20), and (40, 50).</span></span> <span data-ttu-id="f262a-117">Następnie krzywej zostaje automatycznie zamknięty, nawiązując połączenie (40, 50) do punktu początkowego (0, 0), a wewnętrzny jest wypełniony jednolitym kolorem.</span><span class="sxs-lookup"><span data-stu-id="f262a-117">Then, the curve is automatically closed by connecting (40, 50) to the starting point (0, 0), and the interior is filled with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <span data-ttu-id="f262a-118"><xref:System.Drawing.Graphics.FillPath%2A> Metody wypełnia wnętrza oddzielnych części ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f262a-118">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the interiors of the separate pieces of a path.</span></span> <span data-ttu-id="f262a-119">Jeśli część ścieżki nie tworzą zamkniętej krzywej lub kształt <xref:System.Drawing.Graphics.FillPath%2A> metody jest automatycznie zamykany tej części ścieżki przed jego wypełniania.</span><span class="sxs-lookup"><span data-stu-id="f262a-119">If a piece of a path doesn't form a closed curve or shape, the <xref:System.Drawing.Graphics.FillPath%2A> method automatically closes that piece of the path before filling it.</span></span> <span data-ttu-id="f262a-120">Rysuje, wypełnia ścieżki, która składa się z łuk, kardynalnej krzywej składanej ciągu i wykres kołowy w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f262a-120">The following example draws and fills a path that consists of an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 <span data-ttu-id="f262a-121">Na poniższej ilustracji przedstawiono ścieżki z włączonymi i wyłączonymi wypełnieniem.</span><span class="sxs-lookup"><span data-stu-id="f262a-121">The following illustration shows the path with and without the solid fill.</span></span> <span data-ttu-id="f262a-122">Należy pamiętać, że tekst w ciągu jest opisane, ale nie jest wypełniony, przez <xref:System.Drawing.Graphics.DrawPath%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f262a-122">Note that the text in the string is outlined, but not filled, by the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="f262a-123">Jest <xref:System.Drawing.Graphics.FillPath%2A> metodę, która umożliwia malowanie wnętrza znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="f262a-123">It is the <xref:System.Drawing.Graphics.FillPath%2A> method that paints the interiors of the characters in the string.</span></span>  
  
 <span data-ttu-id="f262a-124">![Ciąg ścieżki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span><span class="sxs-lookup"><span data-stu-id="f262a-124">![String in a path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f262a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f262a-125">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [<span data-ttu-id="f262a-126">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="f262a-126">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="f262a-127">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="f262a-127">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="f262a-128">Konstruowanie i rysowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="f262a-128">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
