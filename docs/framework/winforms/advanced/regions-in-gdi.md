---
title: Regiony w GDI+
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
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0525e7b58353909d41e5367aa52a17aa56bcd77c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="regions-in-gdi"></a><span data-ttu-id="289a9-102">Regiony w GDI+</span><span class="sxs-lookup"><span data-stu-id="289a9-102">Regions in GDI+</span></span>
<span data-ttu-id="289a9-103">Region jest częścią obszaru wyświetlania urządzenia wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="289a9-103">A region is a portion of the display area of an output device.</span></span> <span data-ttu-id="289a9-104">Regiony może być prosty (pojedynczy prostokąt) lub złożonych (kombinacja wielokątów i krzywych zamknięte).</span><span class="sxs-lookup"><span data-stu-id="289a9-104">Regions can be simple (a single rectangle) or complex (a combination of polygons and closed curves).</span></span> <span data-ttu-id="289a9-105">Na poniższej ilustracji przedstawiono dwóch regionach: jeden utworzone na podstawie prostokąt i innych utworzone na podstawie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="289a9-105">The following illustration shows two regions: one constructed from a rectangle, and the other constructed from a path.</span></span>  
  
 <span data-ttu-id="289a9-106">![Regiony](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span><span class="sxs-lookup"><span data-stu-id="289a9-106">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span></span>  
  
## <a name="using-regions"></a><span data-ttu-id="289a9-107">Używanie regionów</span><span class="sxs-lookup"><span data-stu-id="289a9-107">Using Regions</span></span>  
 <span data-ttu-id="289a9-108">Regiony są często używane na wycinka i testowanie trafień.</span><span class="sxs-lookup"><span data-stu-id="289a9-108">Regions are often used for clipping and hit testing.</span></span> <span data-ttu-id="289a9-109">Wycinka obejmuje ograniczanie rysunku do regionu obszaru wyświetlania zwykle fragment, który musi zostać zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="289a9-109">Clipping involves restricting drawing to a certain region of the display area, usually the portion that needs to be updated.</span></span> <span data-ttu-id="289a9-110">Testowanie trafień obejmuje sprawdzanie, czy kursor jest w danym regionie ekranu po naciśnięciu przycisku myszy.</span><span class="sxs-lookup"><span data-stu-id="289a9-110">Hit testing involves checking to determine whether the cursor is in a certain region of the screen when a mouse button is pressed.</span></span>  
  
 <span data-ttu-id="289a9-111">Można utworzyć obszarem prostokąta lub ścieżki.</span><span class="sxs-lookup"><span data-stu-id="289a9-111">You can construct a region from a rectangle or a path.</span></span> <span data-ttu-id="289a9-112">Można też utworzyć złożonych regionów, łącząc istniejący regionów.</span><span class="sxs-lookup"><span data-stu-id="289a9-112">You can also create complex regions by combining existing regions.</span></span> <span data-ttu-id="289a9-113"><xref:System.Drawing.Region> Klasa udostępnia następujące metody łączenie regionów: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, i <xref:System.Drawing.Region.Complement%2A>.</span><span class="sxs-lookup"><span data-stu-id="289a9-113">The <xref:System.Drawing.Region> class provides the following methods for combining regions: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, and <xref:System.Drawing.Region.Complement%2A>.</span></span>  
  
 <span data-ttu-id="289a9-114">Część wspólną dwóch regionach jest zestaw wszystkich punktów należących do obu regionów.</span><span class="sxs-lookup"><span data-stu-id="289a9-114">The intersection of two regions is the set of all points belonging to both regions.</span></span> <span data-ttu-id="289a9-115">Unia jest zestaw wszystkich punktów należących do jednej lub drugiej lub obu regionów.</span><span class="sxs-lookup"><span data-stu-id="289a9-115">The union is the set of all points belonging to one or the other or both regions.</span></span> <span data-ttu-id="289a9-116">Uzupełnienie regionu jest zestaw wszystkich punktów, które nie znajdują się w regionie.</span><span class="sxs-lookup"><span data-stu-id="289a9-116">The complement of a region is the set of all points that are not in the region.</span></span> <span data-ttu-id="289a9-117">Na poniższej ilustracji przedstawiono przecięcia i złożenie dwóch regionach, pokazane na powyższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="289a9-117">The following illustration shows the intersection and union of the two regions shown in the preceding illustration.</span></span>  
  
 <span data-ttu-id="289a9-118">![Regiony](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span><span class="sxs-lookup"><span data-stu-id="289a9-118">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span></span>  
  
 <span data-ttu-id="289a9-119"><xref:System.Drawing.Region.Xor%2A> Metody stosowane do pary regionów, tworzy region, który zawiera wszystkie punkty, które należą do jednego regionu lub innych, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="289a9-119">The <xref:System.Drawing.Region.Xor%2A> method, applied to a pair of regions, produces a region that contains all points that belong to one region or the other, but not both.</span></span> <span data-ttu-id="289a9-120"><xref:System.Drawing.Region.Exclude%2A> Metody stosowane do pary regionów, tworzy region, który zawiera wszystkie punkty w regionie pierwszy, które nie znajdują się w drugim regionu.</span><span class="sxs-lookup"><span data-stu-id="289a9-120">The <xref:System.Drawing.Region.Exclude%2A> method, applied to a pair of regions, produces a region that contains all points in the first region that are not in the second region.</span></span> <span data-ttu-id="289a9-121">Na poniższej ilustracji przedstawiono regionów, w wyniku zastosowania <xref:System.Drawing.Region.Xor%2A> i <xref:System.Drawing.Region.Exclude%2A> metody do dwóch regionach pokazywane na początku tego tematu.</span><span class="sxs-lookup"><span data-stu-id="289a9-121">The following illustration shows the regions that result from applying the <xref:System.Drawing.Region.Xor%2A> and <xref:System.Drawing.Region.Exclude%2A> methods to the two regions shown at the beginning of this topic.</span></span>  
  
 <span data-ttu-id="289a9-122">![Regiony](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span><span class="sxs-lookup"><span data-stu-id="289a9-122">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span></span>  
  
 <span data-ttu-id="289a9-123">Aby wypełnić region, należy <xref:System.Drawing.Graphics> obiektu, <xref:System.Drawing.Brush> obiektu, a <xref:System.Drawing.Region> obiektu.</span><span class="sxs-lookup"><span data-stu-id="289a9-123">To fill a region, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Brush> object, and a <xref:System.Drawing.Region> object.</span></span> <span data-ttu-id="289a9-124"><xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.FillRegion%2A> metody i <xref:System.Drawing.Brush> obiekt przechowuje atrybuty wypełnienia, takie jak kolor lub deseń.</span><span class="sxs-lookup"><span data-stu-id="289a9-124">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.FillRegion%2A> method, and the <xref:System.Drawing.Brush> object stores attributes of the fill, such as color or pattern.</span></span> <span data-ttu-id="289a9-125">Poniższy przykład wypełnia region jednolitym kolorem.</span><span class="sxs-lookup"><span data-stu-id="289a9-125">The following example fills a region with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="289a9-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="289a9-126">See Also</span></span>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [<span data-ttu-id="289a9-127">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="289a9-127">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="289a9-128">Używanie regionów</span><span class="sxs-lookup"><span data-stu-id="289a9-128">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
