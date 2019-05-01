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
ms.openlocfilehash: 765df4bcd3cef83e624ad8b11676696b95f7d035
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792366"
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="a88c6-102">Typy systemów współrzędnych</span><span class="sxs-lookup"><span data-stu-id="a88c6-102">Types of Coordinate Systems</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="a88c6-103">używa trzech przestrzeni współrzędnych: świata, strony i urządzeń.</span><span class="sxs-lookup"><span data-stu-id="a88c6-103">uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="a88c6-104">Współrzędne świata są współrzędne używane do modelowania określonego świata graficznego i współrzędne, które są przekazywane do metody w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a88c6-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="a88c6-105">Współrzędne strony można znaleźć w układzie współrzędnych używana przez powierzchnię rysunku, na przykład jako formularz lub formant.</span><span class="sxs-lookup"><span data-stu-id="a88c6-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="a88c6-106">Współrzędne urządzenia są współrzędne używane przez urządzenie fizyczne rysowania, takie jak ekran, lub arkusz papieru.</span><span class="sxs-lookup"><span data-stu-id="a88c6-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="a88c6-107">Podczas wywoływania `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, punkty, które są przekazywane do <xref:System.Drawing.Graphics.DrawLine%2A> metody —`(0, 0)` i `(160, 80)`— znajdują się w przestrzeni współrzędnych świata.</span><span class="sxs-lookup"><span data-stu-id="a88c6-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="a88c6-108">Przed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można narysować linię na ekranie, współrzędne przechodzą przez sekwencję transformacji.</span><span class="sxs-lookup"><span data-stu-id="a88c6-108">Before [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="a88c6-109">Jeden przekształcenia, nazywane transformacji świata konwertuje współrzędne świata na współrzędne strony, a inny przekształcenia, o nazwie przekształcenie strony konwertuje współrzędne strony współrzędnych urządzenia.</span><span class="sxs-lookup"><span data-stu-id="a88c6-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="a88c6-110">Transformacje i systemów współrzędnych</span><span class="sxs-lookup"><span data-stu-id="a88c6-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="a88c6-111">Załóżmy, że chcesz pracować z współrzędnych pochodzenia w treści obszaru klienta, a nie w lewym górnym rogu.</span><span class="sxs-lookup"><span data-stu-id="a88c6-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="a88c6-112">Powiedz, na przykład, ma punkt początkowy za 100 pikseli od lewej krawędzi obszaru klienta i 50 pikseli od górnej krawędzi obszaru klienta.</span><span class="sxs-lookup"><span data-stu-id="a88c6-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="a88c6-113">Poniższa ilustracja przedstawia układ współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a88c6-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="a88c6-114">![System współrzędnych](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="a88c6-114">![Coordinate System](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="a88c6-115">Podczas wywoływania `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, Pobierz wiersz pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="a88c6-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="a88c6-116">![System współrzędnych](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="a88c6-116">![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="a88c6-117">Współrzędne punktów końcowych linii w trzech przestrzeni współrzędnych są następujące:</span><span class="sxs-lookup"><span data-stu-id="a88c6-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a88c6-118">Świata</span><span class="sxs-lookup"><span data-stu-id="a88c6-118">World</span></span>|<span data-ttu-id="a88c6-119">(0, 0) do (160, 80)</span><span class="sxs-lookup"><span data-stu-id="a88c6-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="a88c6-120">Strona</span><span class="sxs-lookup"><span data-stu-id="a88c6-120">Page</span></span>|<span data-ttu-id="a88c6-121">(100, 50) na (260, 130)</span><span class="sxs-lookup"><span data-stu-id="a88c6-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="a88c6-122">Urządzenie</span><span class="sxs-lookup"><span data-stu-id="a88c6-122">Device</span></span>|<span data-ttu-id="a88c6-123">(100, 50) na (260, 130)</span><span class="sxs-lookup"><span data-stu-id="a88c6-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="a88c6-124">Należy pamiętać, że przestrzeni współrzędnych strony ma pochodzenia w lewym górnym rogu obszaru klienckiego; zawsze będzie to wymagane.</span><span class="sxs-lookup"><span data-stu-id="a88c6-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="a88c6-125">Należy również zauważyć, że ponieważ jednostka miary jest piksel, urządzenia współrzędne są takie same jak współrzędnych strony.</span><span class="sxs-lookup"><span data-stu-id="a88c6-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="a88c6-126">Jeśli ustawisz jednostka miary na coś innego niż pikseli (na przykład, w calach) współrzędnych urządzenia może się różnić od współrzędne strony.</span><span class="sxs-lookup"><span data-stu-id="a88c6-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="a88c6-127">Transformacji świata, który mapuje współrzędne świata na współrzędne strony, są przechowywane w <xref:System.Drawing.Graphics.Transform%2A> właściwość <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="a88c6-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="a88c6-128">W powyższym przykładzie transformacji świata jest 100 jednostek tłumaczenia, w kierunku x i 50 jednostek w kierunku y.</span><span class="sxs-lookup"><span data-stu-id="a88c6-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="a88c6-129">W poniższym przykładzie ustawiono transformacji świata z <xref:System.Drawing.Graphics> obiektu, a następnie używa, <xref:System.Drawing.Graphics> obiektu, aby narysować linię pokazano na poprzednim rysunku:</span><span class="sxs-lookup"><span data-stu-id="a88c6-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="a88c6-130">Przekształcenie strony mapuje współrzędne strony współrzędnych urządzenia.</span><span class="sxs-lookup"><span data-stu-id="a88c6-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="a88c6-131"><xref:System.Drawing.Graphics> Klasa udostępnia <xref:System.Drawing.Graphics.PageUnit%2A> i <xref:System.Drawing.Graphics.PageScale%2A> właściwości do manipulowania przekształcenie strony.</span><span class="sxs-lookup"><span data-stu-id="a88c6-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="a88c6-132"><xref:System.Drawing.Graphics> Klasa udostępnia także dwie właściwości tylko do odczytu, <xref:System.Drawing.Graphics.DpiX%2A> i <xref:System.Drawing.Graphics.DpiY%2A>, badania poziome i pionowe punktów na cal, urządzenia.</span><span class="sxs-lookup"><span data-stu-id="a88c6-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="a88c6-133">Możesz użyć <xref:System.Drawing.Graphics.PageUnit%2A> właściwość <xref:System.Drawing.Graphics> klasy, aby określić jednostki miar innych niż piksela.</span><span class="sxs-lookup"><span data-stu-id="a88c6-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a88c6-134">Nie można ustawić <xref:System.Drawing.Graphics.PageUnit%2A> właściwości <xref:System.Drawing.GraphicsUnit.World>, ponieważ to nie jest jednostką fizycznych i spowodują wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a88c6-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="a88c6-135">Poniższy przykład pobiera wiersz z (0, 0) do (2, 1), gdzie punkt, (2, 1) jest cala 2 z prawej strony oraz 1 cal w dół od punktu (0, 0):</span><span class="sxs-lookup"><span data-stu-id="a88c6-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  <span data-ttu-id="a88c6-136">Jeśli nie określisz szerokość pióra podczas konstruowania pióra, poprzedni przykład będzie rysowanie linii, o szerokości 1 cal.</span><span class="sxs-lookup"><span data-stu-id="a88c6-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="a88c6-137">W drugim argumencie można określić szerokość pióra <xref:System.Drawing.Pen> Konstruktor:</span><span class="sxs-lookup"><span data-stu-id="a88c6-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="a88c6-138">Przy założeniu, że urządzenia wyświetlającego ma 96 punktów na cal w kierunku poziomym i 96 punktów na cal w kierunku pionowym, punkty końcowe wiersza w poprzednim przykładzie mają następujące współrzędne w trzech przestrzeni współrzędnych:</span><span class="sxs-lookup"><span data-stu-id="a88c6-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a88c6-139">Świata</span><span class="sxs-lookup"><span data-stu-id="a88c6-139">World</span></span>|<span data-ttu-id="a88c6-140">(0, 0) do (2, 1)</span><span class="sxs-lookup"><span data-stu-id="a88c6-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="a88c6-141">Strona</span><span class="sxs-lookup"><span data-stu-id="a88c6-141">Page</span></span>|<span data-ttu-id="a88c6-142">(0, 0) do (2, 1)</span><span class="sxs-lookup"><span data-stu-id="a88c6-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="a88c6-143">Urządzenie</span><span class="sxs-lookup"><span data-stu-id="a88c6-143">Device</span></span>|<span data-ttu-id="a88c6-144">(0, 0, aby (192, 96)</span><span class="sxs-lookup"><span data-stu-id="a88c6-144">(0, 0, to (192, 96)</span></span>|  
  
 <span data-ttu-id="a88c6-145">Uwaga: ponieważ pochodzenia przestrzeni współrzędnych świata znajduje się w lewym górnym rogu obszaru klienta, współrzędne strony są takie same jak współrzędnych świata.</span><span class="sxs-lookup"><span data-stu-id="a88c6-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="a88c6-146">Można połączyć przekształcenia world i strony, aby uzyskać różne efekty.</span><span class="sxs-lookup"><span data-stu-id="a88c6-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="a88c6-147">Na przykład załóżmy, że chcesz użyć cala jako jednostka miary i chcesz, aby pochodzenia swoje współrzędnych za 2 cala od lewej krawędzi obszaru klienta i 1/2 cala od góry obszaru klienta.</span><span class="sxs-lookup"><span data-stu-id="a88c6-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="a88c6-148">W poniższym przykładzie ustawiono Przekształcanie świata i strony <xref:System.Drawing.Graphics> obiektu, a następnie rysuje linię z (0, 0) do (2, 1):</span><span class="sxs-lookup"><span data-stu-id="a88c6-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="a88c6-149">Na poniższej ilustracji przedstawiono wiersza i układ współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a88c6-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="a88c6-150">![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="a88c6-150">![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="a88c6-151">Przy założeniu, że urządzenia wyświetlającego ma 96 punktów na cal w kierunku poziomym i 96 punktów na cal w kierunku pionowym, punkty końcowe wiersza w poprzednim przykładzie mają następujące współrzędne w trzech przestrzeni współrzędnych:</span><span class="sxs-lookup"><span data-stu-id="a88c6-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a88c6-152">Świata</span><span class="sxs-lookup"><span data-stu-id="a88c6-152">World</span></span>|<span data-ttu-id="a88c6-153">(0, 0) do (2, 1)</span><span class="sxs-lookup"><span data-stu-id="a88c6-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="a88c6-154">Strona</span><span class="sxs-lookup"><span data-stu-id="a88c6-154">Page</span></span>|<span data-ttu-id="a88c6-155">(2, 0,5) do (4, 1.5)</span><span class="sxs-lookup"><span data-stu-id="a88c6-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="a88c6-156">Urządzenie</span><span class="sxs-lookup"><span data-stu-id="a88c6-156">Device</span></span>|<span data-ttu-id="a88c6-157">(192, 48) do (384, 144)</span><span class="sxs-lookup"><span data-stu-id="a88c6-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a88c6-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a88c6-158">See also</span></span>

- [<span data-ttu-id="a88c6-159">Systemy i przekształcenia współrzędnych</span><span class="sxs-lookup"><span data-stu-id="a88c6-159">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="a88c6-160">Macierzowe przedstawienie przekształcenia</span><span class="sxs-lookup"><span data-stu-id="a88c6-160">Matrix Representation of Transformations</span></span>](matrix-representation-of-transformations.md)
