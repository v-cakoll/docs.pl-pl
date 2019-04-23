---
title: Stosowanie antyaliasingu do linii i krzywych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
ms.openlocfilehash: cbc9033f18f1ab255862c8f8e2891aa9b68cf8d6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078501"
---
# <a name="antialiasing-with-lines-and-curves"></a><span data-ttu-id="ade31-102">Stosowanie antyaliasingu do linii i krzywych</span><span class="sxs-lookup"><span data-stu-id="ade31-102">Antialiasing with Lines and Curves</span></span>
<span data-ttu-id="ade31-103">Kiedy używasz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Aby narysować linię, podaj punkt początkowy i końcowy punkt wiersza, ale nie należy podać wszystkie informacje dotyczące poszczególnych pikseli w wierszu.</span><span class="sxs-lookup"><span data-stu-id="ade31-103">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, you provide the starting point and ending point of the line, but you do not have to provide any information about the individual pixels on the line.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="ade31-104">działa w połączeniu z oprogramowanie sterownik ekranu w celu ustalenia, które piksele zostanie włączona, aby wyświetlić wiersz na urządzeniu określonego.</span><span class="sxs-lookup"><span data-stu-id="ade31-104">works in conjunction with the display driver software to determine which pixels will be turned on to show the line on a particular display device.</span></span>  
  
## <a name="aliasing"></a><span data-ttu-id="ade31-105">Tworzenie aliasów</span><span class="sxs-lookup"><span data-stu-id="ade31-105">Aliasing</span></span>  
 <span data-ttu-id="ade31-106">Należy wziąć pod uwagę bezpośrednio czerwoną linię, która przechodzi z punktu (4, 2) w punkcie (16, 10).</span><span class="sxs-lookup"><span data-stu-id="ade31-106">Consider the straight red line that goes from the point (4, 2) to the point (16, 10).</span></span> <span data-ttu-id="ade31-107">Założono w układzie współrzędnych pochodzenia w lewym górnym rogu i to jednostka miary piksela.</span><span class="sxs-lookup"><span data-stu-id="ade31-107">Assume the coordinate system has its origin in the upper-left corner and that the unit of measure is the pixel.</span></span> <span data-ttu-id="ade31-108">Również założono osi x punktów w dół po prawej stronie i punktach osi y.</span><span class="sxs-lookup"><span data-stu-id="ade31-108">Also assume that the x-axis points to the right and the y-axis points down.</span></span> <span data-ttu-id="ade31-109">Na poniższej ilustracji przedstawiono rozszerzonej czerwoną linią rysowana na tle różnych kolorach.</span><span class="sxs-lookup"><span data-stu-id="ade31-109">The following illustration shows an enlarged view of the red line drawn on a multicolored background.</span></span>  
  
 <span data-ttu-id="ade31-110">![Wiersz, bez antialiasingu](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span><span class="sxs-lookup"><span data-stu-id="ade31-110">![Line, no antialiasing](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span></span>  
  
 <span data-ttu-id="ade31-111">Czerwony pikseli, używany do renderowania wiersza są nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="ade31-111">The red pixels used to render the line are opaque.</span></span> <span data-ttu-id="ade31-112">W wierszu nie ma bez częściowo przezroczyste pikseli.</span><span class="sxs-lookup"><span data-stu-id="ade31-112">There are no partially transparent pixels in the line.</span></span> <span data-ttu-id="ade31-113">Tego typu linii renderowania udostępnia wiersz nieregularne wygląd, a wiersz wygląda nieco takich jak klatka schodowa.</span><span class="sxs-lookup"><span data-stu-id="ade31-113">This type of line rendering gives the line a jagged appearance, and the line looks somewhat like a staircase.</span></span> <span data-ttu-id="ade31-114">Ta technika reprezentować linii z klatka schodowa nazywa się tworzenie aliasów; klatka schodowa jest aliasem dla teoretycznych wiersza.</span><span class="sxs-lookup"><span data-stu-id="ade31-114">This technique of representing a line with a staircase is called aliasing; the staircase is an alias for the theoretical line.</span></span>  
  
## <a name="antialiasing"></a><span data-ttu-id="ade31-115">Antyaliasing</span><span class="sxs-lookup"><span data-stu-id="ade31-115">Antialiasing</span></span>  
 <span data-ttu-id="ade31-116">Bardziej zaawansowanych technik do renderowania linię pociąga za sobą przy użyciu częściowo przezroczyste piksele wraz z nieprzezroczyste pikseli.</span><span class="sxs-lookup"><span data-stu-id="ade31-116">A more sophisticated technique for rendering a line involves using partially transparent pixels along with opaque pixels.</span></span> <span data-ttu-id="ade31-117">Pikseli są ustawione na czerwony czysty, lub do niektórych programu blend czerwony i kolor tła zależności od tego, jak blisko są do wiersza.</span><span class="sxs-lookup"><span data-stu-id="ade31-117">Pixels are set to pure red, or to some blend of red and the background color, depending on how close they are to the line.</span></span> <span data-ttu-id="ade31-118">Tego rodzaju renderowania nosi nazwę antialiasingu i wyników w wierszu, który ludzkiego oka uświadamia sobie, jak bardziej bezproblemowe.</span><span class="sxs-lookup"><span data-stu-id="ade31-118">This type of rendering is called antialiasing and results in a line that the human eye perceives as more smooth.</span></span> <span data-ttu-id="ade31-119">Poniższa ilustracja przedstawia, jak niektórych pikseli są mieszane w tle do wyprodukowania antialiased linii.</span><span class="sxs-lookup"><span data-stu-id="ade31-119">The following illustration shows how certain pixels are blended with the background to produce an antialiased line.</span></span>  
  
 <span data-ttu-id="ade31-120">![Antyaliasingu do linii](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span><span class="sxs-lookup"><span data-stu-id="ade31-120">![Antialiasing a Line](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span></span>  
  
 <span data-ttu-id="ade31-121">Antyaliasing, nazywany również wygładzanie, można zastosować również na krzywe.</span><span class="sxs-lookup"><span data-stu-id="ade31-121">Antialiasing, also called smoothing, can also be applied to curves.</span></span> <span data-ttu-id="ade31-122">Na poniższej ilustracji przedstawiono rozszerzonej wygładzone elipsy.</span><span class="sxs-lookup"><span data-stu-id="ade31-122">The following illustration shows an enlarged view of a smoothed ellipse.</span></span>  
  
 <span data-ttu-id="ade31-123">![Antyaliasing krzywych](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span><span class="sxs-lookup"><span data-stu-id="ade31-123">![Antialiasing Curves](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span></span>  
  
 <span data-ttu-id="ade31-124">Poniższa ilustracja przedstawia ten sam elipsy w rzeczywisty rozmiar, jeden raz bez antialiasingu i drugi raz antialiasingu.</span><span class="sxs-lookup"><span data-stu-id="ade31-124">The following illustration shows the same ellipse in its actual size, once without antialiasing and once with antialiasing.</span></span>  
  
 <span data-ttu-id="ade31-125">![Przykład antialiasingu](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span><span class="sxs-lookup"><span data-stu-id="ade31-125">![Antialiasing example](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span></span>  
  
 <span data-ttu-id="ade31-126">Rysowanie linii i krzywych, których stosowanie antyaliasingu do, Utwórz wystąpienie obiektu <xref:System.Drawing.Graphics> klasy i ustaw jego <xref:System.Drawing.Graphics.SmoothingMode%2A> właściwości <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> lub <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span><span class="sxs-lookup"><span data-stu-id="ade31-126">To draw lines and curves that use antialiasing, create an instance of the <xref:System.Drawing.Graphics> class and set its <xref:System.Drawing.Graphics.SmoothingMode%2A> property to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> or <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span></span> <span data-ttu-id="ade31-127">Następnie wywołać jedną z metod rysowania tego samego <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="ade31-127">Then call one of the drawing methods of that same <xref:System.Drawing.Graphics> class.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#81](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a><span data-ttu-id="ade31-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ade31-128">See also</span></span>

- <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>
- [<span data-ttu-id="ade31-129">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="ade31-129">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="ade31-130">Instrukcje: Stosowanie antyaliasingu do tekstu</span><span class="sxs-lookup"><span data-stu-id="ade31-130">How to: Use Antialiasing with Text</span></span>](how-to-use-antialiasing-with-text.md)
