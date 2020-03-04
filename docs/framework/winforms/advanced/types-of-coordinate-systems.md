---
title: Typy systemów współrzędnych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: bbb0d4908d4a281499336d262c653d7b72f3ccdc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159809"
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="0e5fc-102">Typy systemów współrzędnych</span><span class="sxs-lookup"><span data-stu-id="0e5fc-102">Types of Coordinate Systems</span></span>
<span data-ttu-id="0e5fc-103">Interfejs GDI+ używa trzech przestrzeni współrzędnych: świecie, strony i urządzenia.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-103">GDI+ uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="0e5fc-104">Współrzędne świata są współrzędnymi używanymi do modelowania określonego świata grafiki i są współrzędnymi przekazywanymi do metod w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="0e5fc-105">Współrzędne strony odwołują się do układu współrzędnych używanego przez powierzchnię rysowania, taką jak formularz lub kontrolka.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="0e5fc-106">Współrzędne urządzenia są współrzędnymi używanymi przez urządzenie fizyczne, na przykład na ekranie lub arkuszu papieru.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="0e5fc-107">Po nadaniu wywołania `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`punkty przekazane do metody <xref:System.Drawing.Graphics.DrawLine%2A> —`(0, 0)` i `(160, 80)`— znajdują się na świecie współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="0e5fc-108">Zanim GDI+ będzie mógł narysować linię na ekranie, współrzędne przechodzą przez sekwencję transformacji.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-108">Before GDI+ can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="0e5fc-109">Jedną transformację, nazywaną transformację światową, konwertuje współrzędne świata na współrzędne strony, a inna transformacja, nazywana przekształceniem strony, konwertuje współrzędne strony na współrzędne urządzenia.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="0e5fc-110">Transformacje i systemy współrzędnych</span><span class="sxs-lookup"><span data-stu-id="0e5fc-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="0e5fc-111">Załóżmy, że chcesz korzystać z układu współrzędnych, który ma swoją zawartość w treści obszaru klienta, a nie w lewym górnym rogu.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="0e5fc-112">Załóżmy na przykład, że źródło ma mieć 100 pikseli od lewej krawędzi obszaru klienta i 50 pikseli od góry obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="0e5fc-113">Na poniższej ilustracji przedstawiono układ współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="0e5fc-114">![System współrzędnych](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="0e5fc-114">![Coordinate System](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="0e5fc-115">Po nadaniu wywołania `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`uzyskasz wiersz przedstawiony na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="0e5fc-116">![System współrzędnych](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="0e5fc-116">![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="0e5fc-117">Współrzędne punkty końcowe linii w trzech miejscach współrzędnych są następujące:</span><span class="sxs-lookup"><span data-stu-id="0e5fc-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e5fc-118">Międzynarodowa</span><span class="sxs-lookup"><span data-stu-id="0e5fc-118">World</span></span>|<span data-ttu-id="0e5fc-119">(od 0 do 0) do (160, 80)</span><span class="sxs-lookup"><span data-stu-id="0e5fc-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="0e5fc-120">Stronic</span><span class="sxs-lookup"><span data-stu-id="0e5fc-120">Page</span></span>|<span data-ttu-id="0e5fc-121">(100, 50) do (260, 130)</span><span class="sxs-lookup"><span data-stu-id="0e5fc-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="0e5fc-122">Urządzenie</span><span class="sxs-lookup"><span data-stu-id="0e5fc-122">Device</span></span>|<span data-ttu-id="0e5fc-123">(100, 50) do (260, 130)</span><span class="sxs-lookup"><span data-stu-id="0e5fc-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="0e5fc-124">Należy zauważyć, że obszar współrzędnej strony ma swój początek w lewym górnym rogu obszaru klienckiego. zawsze będzie to miało zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="0e5fc-125">Należy również zauważyć, że ponieważ jednostka miary jest pikselem, współrzędne urządzenia są takie same jak współrzędne strony.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="0e5fc-126">Jeśli ustawisz jednostkę miary na coś innego niż piksele (na przykład centymetry), współrzędne urządzenia będą różnić się od współrzędnej strony.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="0e5fc-127">Transformacja świata, która mapuje współrzędne świata na współrzędne strony, jest utrzymywana we właściwości <xref:System.Drawing.Graphics.Transform%2A> klasy <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="0e5fc-128">W poprzednim przykładzie transformacja świata jest jednostką translacji 100 w kierunku x i 50 jednostek w kierunku y.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="0e5fc-129">Poniższy przykład ustawia światową transformację obiektu <xref:System.Drawing.Graphics>, a następnie używa tego obiektu <xref:System.Drawing.Graphics> do rysowania linii pokazanej na poprzednim rysunku:</span><span class="sxs-lookup"><span data-stu-id="0e5fc-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="0e5fc-130">Transformacja strony mapuje współrzędne strony na współrzędne urządzeń.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="0e5fc-131">Klasa <xref:System.Drawing.Graphics> udostępnia właściwości <xref:System.Drawing.Graphics.PageUnit%2A> i <xref:System.Drawing.Graphics.PageScale%2A> na potrzeby manipulowania transformację strony.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="0e5fc-132">Klasa <xref:System.Drawing.Graphics> udostępnia również dwie właściwości tylko do odczytu, <xref:System.Drawing.Graphics.DpiX%2A> i <xref:System.Drawing.Graphics.DpiY%2A>do badania w poziomie i w pionie na cal urządzenia wyświetlającego.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="0e5fc-133">Aby określić jednostkę miary inną niż piksel, można użyć właściwości <xref:System.Drawing.Graphics.PageUnit%2A> klasy <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e5fc-134">Nie można ustawić właściwości <xref:System.Drawing.Graphics.PageUnit%2A> na <xref:System.Drawing.GraphicsUnit.World>, ponieważ nie jest to jednostka fizyczna i spowoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="0e5fc-135">Poniższy przykład rysuje linię od (0, 0) do (2, 1), gdzie punkt (2, 1) jest 2 cala po prawej i 1 cal w dół od punktu (0, 0):</span><span class="sxs-lookup"><span data-stu-id="0e5fc-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
> <span data-ttu-id="0e5fc-136">Jeśli nie określisz szerokości pióra podczas tworzenia pióra, w poprzednim przykładzie zostanie narysowana linia o szerokości jednego cala.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="0e5fc-137">Możesz określić szerokość pióra w drugim argumencie konstruktora <xref:System.Drawing.Pen>:</span><span class="sxs-lookup"><span data-stu-id="0e5fc-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="0e5fc-138">Jeśli założono, że urządzenie wyświetlające ma 96 punktów na cal w kierunku poziomym i 96 punktów na cal w kierunku pionowym, punkty końcowe wiersza w poprzednim przykładzie mają następujące współrzędne w trzech miejscach współrzędnych:</span><span class="sxs-lookup"><span data-stu-id="0e5fc-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e5fc-139">Międzynarodowa</span><span class="sxs-lookup"><span data-stu-id="0e5fc-139">World</span></span>|<span data-ttu-id="0e5fc-140">(od 0 do 0) do (2, 1)</span><span class="sxs-lookup"><span data-stu-id="0e5fc-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="0e5fc-141">Stronic</span><span class="sxs-lookup"><span data-stu-id="0e5fc-141">Page</span></span>|<span data-ttu-id="0e5fc-142">(od 0 do 0) do (2, 1)</span><span class="sxs-lookup"><span data-stu-id="0e5fc-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="0e5fc-143">Urządzenie</span><span class="sxs-lookup"><span data-stu-id="0e5fc-143">Device</span></span>|<span data-ttu-id="0e5fc-144">(od 0 do 0) do (192, 96)</span><span class="sxs-lookup"><span data-stu-id="0e5fc-144">(0, 0) to (192, 96)</span></span>|  
  
 <span data-ttu-id="0e5fc-145">Należy zauważyć, że ze względu na to, że początek przestrzeni współrzędnych świata znajduje się w lewym górnym rogu obszaru klienta, współrzędne strony są takie same jak współrzędne świata.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="0e5fc-146">Możesz połączyć przekształcenia światowe i strony, aby osiągnąć różne efekty.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="0e5fc-147">Załóżmy na przykład, że chcesz użyć cali jako jednostki miary, i chcesz, aby początkowa część układu współrzędnych była równa 2 cala od lewej krawędzi obszaru klienckiego i 1/2 cala od góry obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="0e5fc-148">Poniższy przykład ustawia przekształcenia na świecie i na stronie obiektu <xref:System.Drawing.Graphics>, a następnie rysuje linię od (0, 0) do (2, 1):</span><span class="sxs-lookup"><span data-stu-id="0e5fc-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="0e5fc-149">Poniższa ilustracja przedstawia układ linii i układu współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="0e5fc-150">![System współrzędnych](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="0e5fc-150">![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="0e5fc-151">Jeśli założono, że urządzenie wyświetlające ma 96 punktów na cal w kierunku poziomym i 96 punktów na cal w kierunku pionowym, punkty końcowe wiersza w poprzednim przykładzie mają następujące współrzędne w trzech miejscach współrzędnych:</span><span class="sxs-lookup"><span data-stu-id="0e5fc-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e5fc-152">Międzynarodowa</span><span class="sxs-lookup"><span data-stu-id="0e5fc-152">World</span></span>|<span data-ttu-id="0e5fc-153">(od 0 do 0) do (2, 1)</span><span class="sxs-lookup"><span data-stu-id="0e5fc-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="0e5fc-154">Stronic</span><span class="sxs-lookup"><span data-stu-id="0e5fc-154">Page</span></span>|<span data-ttu-id="0e5fc-155">(2, 0,5) do (4, 1,5)</span><span class="sxs-lookup"><span data-stu-id="0e5fc-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="0e5fc-156">Urządzenie</span><span class="sxs-lookup"><span data-stu-id="0e5fc-156">Device</span></span>|<span data-ttu-id="0e5fc-157">(192, 48) do (384, 144)</span><span class="sxs-lookup"><span data-stu-id="0e5fc-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e5fc-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e5fc-158">See also</span></span>

- [<span data-ttu-id="0e5fc-159">Systemy i przekształcenia współrzędnych</span><span class="sxs-lookup"><span data-stu-id="0e5fc-159">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="0e5fc-160">Macierzowe przedstawienie przekształcenia</span><span class="sxs-lookup"><span data-stu-id="0e5fc-160">Matrix Representation of Transformations</span></span>](matrix-representation-of-transformations.md)
