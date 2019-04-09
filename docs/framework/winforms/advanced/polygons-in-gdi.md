---
title: Wielokąty w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
ms.openlocfilehash: 2b1e3d387e4d056d9187c54dcef560544206c370
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132629"
---
# <a name="polygons-in-gdi"></a><span data-ttu-id="66956-102">Wielokąty w GDI+</span><span class="sxs-lookup"><span data-stu-id="66956-102">Polygons in GDI+</span></span>
<span data-ttu-id="66956-103">Wielokąt jest kształt zamknięty przy użyciu co najmniej trzech stronach proste.</span><span class="sxs-lookup"><span data-stu-id="66956-103">A polygon is a closed shape with three or more straight sides.</span></span> <span data-ttu-id="66956-104">Na przykład trójkąt jest Wielokąt przy użyciu trzech stronach prostokątowi Wielokąt przy użyciu czterech bokach i pięciobok jest wielokąta z pięciu stron.</span><span class="sxs-lookup"><span data-stu-id="66956-104">For example, a triangle is a polygon with three sides, a rectangle is a polygon with four sides, and a pentagon is a polygon with five sides.</span></span> <span data-ttu-id="66956-105">Poniższa ilustracja przedstawia kilka wielokątów.</span><span class="sxs-lookup"><span data-stu-id="66956-105">The following illustration shows several polygons.</span></span>  
  
 <span data-ttu-id="66956-106">![Polygons](./media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span><span class="sxs-lookup"><span data-stu-id="66956-106">![Polygons](./media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span></span>  
  
## <a name="drawing-a-polygon"></a><span data-ttu-id="66956-107">Rysowanie wielokąta</span><span class="sxs-lookup"><span data-stu-id="66956-107">Drawing a Polygon</span></span>  
 <span data-ttu-id="66956-108">Aby narysować wielokąt, musisz mieć <xref:System.Drawing.Graphics> obiektu <xref:System.Drawing.Pen> obiekt i tablica <xref:System.Drawing.Point> (lub <xref:System.Drawing.PointF>) obiektów.</span><span class="sxs-lookup"><span data-stu-id="66956-108">To draw a polygon, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and an array of <xref:System.Drawing.Point> (or <xref:System.Drawing.PointF>) objects.</span></span> <span data-ttu-id="66956-109"><xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawPolygon%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="66956-109">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="66956-110"><xref:System.Drawing.Pen> Obiekt przechowuje atrybuty, takie jak szerokość i kolor linii, używany do renderowania wielokąta i tablica <xref:System.Drawing.Point> obiektów przechowuje punktów połączenia linii prostych.</span><span class="sxs-lookup"><span data-stu-id="66956-110">The <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the polygon, and the array of <xref:System.Drawing.Point> objects stores the points to be connected by straight lines.</span></span> <span data-ttu-id="66956-111"><xref:System.Drawing.Pen> Obiekt i tablica <xref:System.Drawing.Point> obiekty są przekazywane jako argumenty <xref:System.Drawing.Graphics.DrawPolygon%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="66956-111">The <xref:System.Drawing.Pen> object and the array of <xref:System.Drawing.Point> objects are passed as arguments to the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="66956-112">Poniższy przykład pobiera wielokąta dwustronna trzy.</span><span class="sxs-lookup"><span data-stu-id="66956-112">The following example draws a three-sided polygon.</span></span> <span data-ttu-id="66956-113">Należy zauważyć, że istnieje tylko dla trzech punktów w `myPointArray`: (0, 0), (50, 30) i (30, 60).</span><span class="sxs-lookup"><span data-stu-id="66956-113">Note that there are only three points in `myPointArray`: (0, 0), (50, 30), and (30, 60).</span></span> <span data-ttu-id="66956-114"><xref:System.Drawing.Graphics.DrawPolygon%2A> Metoda automatycznie zamyka wielokąta za pomocą rysowania linii z (30, 60) do punkt początkowy (0, 0).</span><span class="sxs-lookup"><span data-stu-id="66956-114">The <xref:System.Drawing.Graphics.DrawPolygon%2A> method automatically closes the polygon by drawing a line from (30, 60) back to the starting point (0, 0).</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#111](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 <span data-ttu-id="66956-115">Poniższa ilustracja przedstawia wielokąta.</span><span class="sxs-lookup"><span data-stu-id="66956-115">The following illustration shows the polygon.</span></span>  
  
 <span data-ttu-id="66956-116">![Polygon](./media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span><span class="sxs-lookup"><span data-stu-id="66956-116">![Polygon](./media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66956-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66956-117">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="66956-118">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="66956-118">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="66956-119">Instrukcje: Tworzenie pióra</span><span class="sxs-lookup"><span data-stu-id="66956-119">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
