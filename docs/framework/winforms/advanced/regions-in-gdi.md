---
title: Regiony w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
ms.openlocfilehash: 33d4f4ecca7b9d777fa4eab5b6d031de10f03ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956809"
---
# <a name="regions-in-gdi"></a><span data-ttu-id="ebabc-102">Regiony w GDI+</span><span class="sxs-lookup"><span data-stu-id="ebabc-102">Regions in GDI+</span></span>
<span data-ttu-id="ebabc-103">Region jest częścią obszaru wyświetlania na urządzeniach.</span><span class="sxs-lookup"><span data-stu-id="ebabc-103">A region is a portion of the display area of an output device.</span></span> <span data-ttu-id="ebabc-104">Regiony może być prosty (prostokąt pojedynczego) lub złożona (połączenia wielokąty i krzywych zamknięte).</span><span class="sxs-lookup"><span data-stu-id="ebabc-104">Regions can be simple (a single rectangle) or complex (a combination of polygons and closed curves).</span></span> <span data-ttu-id="ebabc-105">Na poniższej ilustracji przedstawiono dwa regiony: jeden wykonany z prostokąt i innych skonstruowany na podstawie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="ebabc-105">The following illustration shows two regions: one constructed from a rectangle, and the other constructed from a path.</span></span>  
  
 <span data-ttu-id="ebabc-106">![Regiony](./media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span><span class="sxs-lookup"><span data-stu-id="ebabc-106">![Regions](./media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span></span>  
  
## <a name="using-regions"></a><span data-ttu-id="ebabc-107">Używanie regionów</span><span class="sxs-lookup"><span data-stu-id="ebabc-107">Using Regions</span></span>  
 <span data-ttu-id="ebabc-108">Regiony są często używane do wycinka i testowania trafień.</span><span class="sxs-lookup"><span data-stu-id="ebabc-108">Regions are often used for clipping and hit testing.</span></span> <span data-ttu-id="ebabc-109">Wycinka polega na ograniczenie rysunku do region wyświetlacz, zwykle fragment, który musi zostać zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="ebabc-109">Clipping involves restricting drawing to a certain region of the display area, usually the portion that needs to be updated.</span></span> <span data-ttu-id="ebabc-110">Testowanie trafień sprawdza się, aby ustalić, czy kursor znajduje się w danym regionie ekranu po naciśnięciu przycisku myszy.</span><span class="sxs-lookup"><span data-stu-id="ebabc-110">Hit testing involves checking to determine whether the cursor is in a certain region of the screen when a mouse button is pressed.</span></span>  
  
 <span data-ttu-id="ebabc-111">Można skonstruować obszarem prostokąta lub ścieżki.</span><span class="sxs-lookup"><span data-stu-id="ebabc-111">You can construct a region from a rectangle or a path.</span></span> <span data-ttu-id="ebabc-112">Można również utworzyć złożone regionów, łącząc istniejących regionach.</span><span class="sxs-lookup"><span data-stu-id="ebabc-112">You can also create complex regions by combining existing regions.</span></span> <span data-ttu-id="ebabc-113"><xref:System.Drawing.Region> Klasa udostępnia następujące metody łączenia regionów: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, i <xref:System.Drawing.Region.Complement%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebabc-113">The <xref:System.Drawing.Region> class provides the following methods for combining regions: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, and <xref:System.Drawing.Region.Complement%2A>.</span></span>  
  
 <span data-ttu-id="ebabc-114">Część wspólną dwóch regionach to zestaw wszystkich punktów należących do obu regionach.</span><span class="sxs-lookup"><span data-stu-id="ebabc-114">The intersection of two regions is the set of all points belonging to both regions.</span></span> <span data-ttu-id="ebabc-115">Unia to zestaw wszystkich punktów należących do jednej lub drugiej lub obu regionach.</span><span class="sxs-lookup"><span data-stu-id="ebabc-115">The union is the set of all points belonging to one or the other or both regions.</span></span> <span data-ttu-id="ebabc-116">Uzupełnienie region to zestaw wszystkich punktów, które nie znajdują się w regionie.</span><span class="sxs-lookup"><span data-stu-id="ebabc-116">The complement of a region is the set of all points that are not in the region.</span></span> <span data-ttu-id="ebabc-117">Na poniższej ilustracji przedstawiono część wspólną i sumę dwóch regionach pokazano na poprzedniej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="ebabc-117">The following illustration shows the intersection and union of the two regions shown in the preceding illustration.</span></span>  
  
 <span data-ttu-id="ebabc-118">![Regiony](./media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span><span class="sxs-lookup"><span data-stu-id="ebabc-118">![Regions](./media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span></span>  
  
 <span data-ttu-id="ebabc-119"><xref:System.Drawing.Region.Xor%2A> Metody stosowane do pary regionów, tworzy obszar, który zawiera wszystkie punkty, które należą do jednego regionu lub innych, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="ebabc-119">The <xref:System.Drawing.Region.Xor%2A> method, applied to a pair of regions, produces a region that contains all points that belong to one region or the other, but not both.</span></span> <span data-ttu-id="ebabc-120"><xref:System.Drawing.Region.Exclude%2A> Metody stosowane do pary regionów, tworzy obszar, który zawiera wszystkie punkty w pierwszym regionie, które nie znajdują się w drugim regionie.</span><span class="sxs-lookup"><span data-stu-id="ebabc-120">The <xref:System.Drawing.Region.Exclude%2A> method, applied to a pair of regions, produces a region that contains all points in the first region that are not in the second region.</span></span> <span data-ttu-id="ebabc-121">Na poniższej ilustracji przedstawiono regionów, w wyniku zastosowania <xref:System.Drawing.Region.Xor%2A> i <xref:System.Drawing.Region.Exclude%2A> metod w dwóch regionach przedstawionych na początku tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ebabc-121">The following illustration shows the regions that result from applying the <xref:System.Drawing.Region.Xor%2A> and <xref:System.Drawing.Region.Exclude%2A> methods to the two regions shown at the beginning of this topic.</span></span>  
  
 <span data-ttu-id="ebabc-122">![Regiony](./media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span><span class="sxs-lookup"><span data-stu-id="ebabc-122">![Regions](./media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span></span>  
  
 <span data-ttu-id="ebabc-123">Aby wypełnić regionu, należy <xref:System.Drawing.Graphics> obiektu, <xref:System.Drawing.Brush> obiektu, a <xref:System.Drawing.Region> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ebabc-123">To fill a region, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Brush> object, and a <xref:System.Drawing.Region> object.</span></span> <span data-ttu-id="ebabc-124"><xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.FillRegion%2A> metody i <xref:System.Drawing.Brush> obiekt przechowuje atrybuty wypełnienia, takich jak kolor lub deseń.</span><span class="sxs-lookup"><span data-stu-id="ebabc-124">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.FillRegion%2A> method, and the <xref:System.Drawing.Brush> object stores attributes of the fill, such as color or pattern.</span></span> <span data-ttu-id="ebabc-125">Poniższy przykład wypełnia obszar jednolitym kolorem.</span><span class="sxs-lookup"><span data-stu-id="ebabc-125">The following example fills a region with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#61](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="ebabc-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebabc-126">See also</span></span>

- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [<span data-ttu-id="ebabc-127">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="ebabc-127">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="ebabc-128">Używanie regionów</span><span class="sxs-lookup"><span data-stu-id="ebabc-128">Using Regions</span></span>](using-regions.md)
