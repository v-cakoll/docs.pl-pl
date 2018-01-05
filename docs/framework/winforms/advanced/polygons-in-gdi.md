---
title: "Wielokąty w GDI+"
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
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26068ab72473a541b1f16aeb2a1f0d43ec7a7313
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="polygons-in-gdi"></a><span data-ttu-id="3f7cc-102">Wielokąty w GDI+</span><span class="sxs-lookup"><span data-stu-id="3f7cc-102">Polygons in GDI+</span></span>
<span data-ttu-id="3f7cc-103">Wielokąt jest zamknięty kształt z co najmniej trzech stronach proste.</span><span class="sxs-lookup"><span data-stu-id="3f7cc-103">A polygon is a closed shape with three or more straight sides.</span></span> <span data-ttu-id="3f7cc-104">Na przykład trójkąt ma wielokąta z trzech stron, prostokąt jest wielokąta z czterech stron, a pięciobok wielokąta z pięcioma stron.</span><span class="sxs-lookup"><span data-stu-id="3f7cc-104">For example, a triangle is a polygon with three sides, a rectangle is a polygon with four sides, and a pentagon is a polygon with five sides.</span></span> <span data-ttu-id="3f7cc-105">Na poniższej ilustracji przedstawiono kilka wielokątów.</span><span class="sxs-lookup"><span data-stu-id="3f7cc-105">The following illustration shows several polygons.</span></span>  
  
 <span data-ttu-id="3f7cc-106">![Wielokąty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span><span class="sxs-lookup"><span data-stu-id="3f7cc-106">![Polygons](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span></span>  
  
## <a name="drawing-a-polygon"></a><span data-ttu-id="3f7cc-107">Rysowanie wielokąta</span><span class="sxs-lookup"><span data-stu-id="3f7cc-107">Drawing a Polygon</span></span>  
 <span data-ttu-id="3f7cc-108">Aby narysować wielokąt, należy <xref:System.Drawing.Graphics> obiektu, <xref:System.Drawing.Pen> obiekt a tablica <xref:System.Drawing.Point> (lub <xref:System.Drawing.PointF>) obiektów.</span><span class="sxs-lookup"><span data-stu-id="3f7cc-108">To draw a polygon, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and an array of <xref:System.Drawing.Point> (or <xref:System.Drawing.PointF>) objects.</span></span> <span data-ttu-id="3f7cc-109"><xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.DrawPolygon%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3f7cc-109">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="3f7cc-110"><xref:System.Drawing.Pen> Obiekt przechowuje atrybuty, takie jak szerokości i koloru linii używany do renderowania wielokąta i tablica <xref:System.Drawing.Point> obiektów przechowuje punkty połączenia za pomocą linii prostych.</span><span class="sxs-lookup"><span data-stu-id="3f7cc-110">The <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the polygon, and the array of <xref:System.Drawing.Point> objects stores the points to be connected by straight lines.</span></span> <span data-ttu-id="3f7cc-111"><xref:System.Drawing.Pen> Obiekt a tablica <xref:System.Drawing.Point> obiekty są przekazywane jako argumenty do <xref:System.Drawing.Graphics.DrawPolygon%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3f7cc-111">The <xref:System.Drawing.Pen> object and the array of <xref:System.Drawing.Point> objects are passed as arguments to the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="3f7cc-112">Poniższy przykład rysuje dwustronnych trzech wielokąta.</span><span class="sxs-lookup"><span data-stu-id="3f7cc-112">The following example draws a three-sided polygon.</span></span> <span data-ttu-id="3f7cc-113">Należy pamiętać, że są tylko trzy punkty w `myPointArray`: (0, 0), (50, 30) i (30, 60).</span><span class="sxs-lookup"><span data-stu-id="3f7cc-113">Note that there are only three points in `myPointArray`: (0, 0), (50, 30), and (30, 60).</span></span> <span data-ttu-id="3f7cc-114"><xref:System.Drawing.Graphics.DrawPolygon%2A> Metody jest automatycznie zamykany wielokąta za pomocą rysowania linii z (30, 60) do punktu początkowego (0, 0).</span><span class="sxs-lookup"><span data-stu-id="3f7cc-114">The <xref:System.Drawing.Graphics.DrawPolygon%2A> method automatically closes the polygon by drawing a line from (30, 60) back to the starting point (0, 0).</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 <span data-ttu-id="3f7cc-115">Na poniższej ilustracji przedstawiono wielokąta.</span><span class="sxs-lookup"><span data-stu-id="3f7cc-115">The following illustration shows the polygon.</span></span>  
  
 <span data-ttu-id="3f7cc-116">![Wielokąt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span><span class="sxs-lookup"><span data-stu-id="3f7cc-116">![Polygon](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7cc-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f7cc-117">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="3f7cc-118">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="3f7cc-118">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="3f7cc-119">Instrukcje: tworzenie pióra</span><span class="sxs-lookup"><span data-stu-id="3f7cc-119">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
