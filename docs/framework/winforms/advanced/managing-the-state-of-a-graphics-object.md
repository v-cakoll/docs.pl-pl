---
title: Zarządzanie stanem obiektu graficznego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
ms.openlocfilehash: fc961b59dabc2f7f123b792e7e45a4ff3b535fc1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717625"
---
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="3d1be-102">Zarządzanie stanem obiektu graficznego</span><span class="sxs-lookup"><span data-stu-id="3d1be-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="3d1be-103"><xref:System.Drawing.Graphics> Klasy to serce [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d1be-103">The <xref:System.Drawing.Graphics> class is at the heart of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="3d1be-104">Aby narysować niczego, należy uzyskać <xref:System.Drawing.Graphics> obiektu, ustaw jej właściwości i wywołać jego metody <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>i tym podobne).</span><span class="sxs-lookup"><span data-stu-id="3d1be-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="3d1be-105">Poniższy przykład wywołuje <xref:System.Drawing.Graphics.DrawRectangle%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d1be-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="3d1be-106">Pierwszy argument przekazany do <xref:System.Drawing.Graphics.DrawRectangle%2A> metodą jest <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d1be-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## <a name="graphics-state"></a><span data-ttu-id="3d1be-107">Stan grafiki</span><span class="sxs-lookup"><span data-stu-id="3d1be-107">Graphics State</span></span>  
 <span data-ttu-id="3d1be-108">A <xref:System.Drawing.Graphics> obiektu więcej niż zapewnia rysowania metod, takich jak <xref:System.Drawing.Graphics.DrawLine%2A> i <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d1be-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="3d1be-109">A <xref:System.Drawing.Graphics> obiekt przechowuje również stanu grafiki, które można podzielić na następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="3d1be-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
-   <span data-ttu-id="3d1be-110">Ustawienia jakości</span><span class="sxs-lookup"><span data-stu-id="3d1be-110">Quality settings</span></span>  
  
-   <span data-ttu-id="3d1be-111">Przekształcenia</span><span class="sxs-lookup"><span data-stu-id="3d1be-111">Transformations</span></span>  
  
-   <span data-ttu-id="3d1be-112">Obszar przycinania</span><span class="sxs-lookup"><span data-stu-id="3d1be-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="3d1be-113">Ustawienia jakości</span><span class="sxs-lookup"><span data-stu-id="3d1be-113">Quality Settings</span></span>  
 <span data-ttu-id="3d1be-114">A <xref:System.Drawing.Graphics> obiekt ma kilka właściwości, które mają wpływ na jakość elementy, które są rysowane.</span><span class="sxs-lookup"><span data-stu-id="3d1be-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="3d1be-115">Na przykład można ustawić <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwości w celu określenia typu antialiasingu (jeśli istnieje) zastosowane do tekstu.</span><span class="sxs-lookup"><span data-stu-id="3d1be-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="3d1be-116">Inne właściwości, które mają wpływ na jakość są <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, i <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d1be-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="3d1be-117">Poniższy przykładowy kod rysuje dwa elipsy, jeden z tryb wygładzania równa <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> i jeden z tryb wygładzania równa <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span><span class="sxs-lookup"><span data-stu-id="3d1be-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### <a name="transformations"></a><span data-ttu-id="3d1be-118">Przekształcenia</span><span class="sxs-lookup"><span data-stu-id="3d1be-118">Transformations</span></span>  
 <span data-ttu-id="3d1be-119">A <xref:System.Drawing.Graphics> obiekt przechowuje dwa przekształceń (świecie i strony), które są stosowane do wszystkich elementów rysowane przez to <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d1be-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="3d1be-120">Dowolnego affine — przekształcenia mogą być przechowywane w transformacji świata.</span><span class="sxs-lookup"><span data-stu-id="3d1be-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="3d1be-121">Affine — przekształcenia obejmują skalowanie, obracanie, odzwierciedlanie, pochylanie i tłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="3d1be-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="3d1be-122">Przekształcenie strony może służyć skalowanie oraz zmiany jednostki (na przykład, w pikselach cm).</span><span class="sxs-lookup"><span data-stu-id="3d1be-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="3d1be-123">Aby uzyskać więcej informacji, zobacz [systemy i przekształcenia współrzędnych](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="3d1be-123">For more information, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="3d1be-124">W poniższym przykładzie ustawiono Przekształcanie świata i strony <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d1be-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="3d1be-125">Transformacja świata jest ustawiona na 30 stopni.</span><span class="sxs-lookup"><span data-stu-id="3d1be-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="3d1be-126">Przekształcenie strony jest ustawiony tak, aby współrzędne przekazany do drugiego <xref:System.Drawing.Graphics.DrawEllipse%2A> będzie traktowane jako milimetry zamiast pikseli.</span><span class="sxs-lookup"><span data-stu-id="3d1be-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="3d1be-127">Kod sprawia, że dwa identyczne wywołania <xref:System.Drawing.Graphics.DrawEllipse%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3d1be-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="3d1be-128">Transformacja świata jest stosowana do pierwszego <xref:System.Drawing.Graphics.DrawEllipse%2A> wywołania i zarówno przekształcenia (świecie i strony), które są stosowane do drugiego <xref:System.Drawing.Graphics.DrawEllipse%2A> wywołania.</span><span class="sxs-lookup"><span data-stu-id="3d1be-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);   
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 <span data-ttu-id="3d1be-129">Poniższa ilustracja przedstawia dwie elipsy.</span><span class="sxs-lookup"><span data-stu-id="3d1be-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="3d1be-130">Należy pamiętać, że 30 stopni o pochodzenia w układzie współrzędnych (lewym górnym rogu obszaru klienta), nie o centra wielokropek.</span><span class="sxs-lookup"><span data-stu-id="3d1be-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="3d1be-131">Należy również zauważyć, że szerokość pióra 1 oznacza, że 1 piksel w pierwszym elipsy i 1 milimetra drugi elipsy.</span><span class="sxs-lookup"><span data-stu-id="3d1be-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 <span data-ttu-id="3d1be-132">![Ovals](./media/csgraphicsascon1.png "csgraphicsascon1")</span><span class="sxs-lookup"><span data-stu-id="3d1be-132">![Ovals](./media/csgraphicsascon1.png "csgraphicsascon1")</span></span>  
  
### <a name="clipping-region"></a><span data-ttu-id="3d1be-133">Obszar przycinania</span><span class="sxs-lookup"><span data-stu-id="3d1be-133">Clipping Region</span></span>  
 <span data-ttu-id="3d1be-134">A <xref:System.Drawing.Graphics> obiekt zachowuje obszaru przycinania, która ma zastosowanie do wszystkich elementów rysowane przez to <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d1be-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="3d1be-135">Możesz ustawić obszaru przycinania, wywołując <xref:System.Drawing.Graphics.SetClip%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3d1be-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="3d1be-136">Poniższy przykład tworzy obszar ukształtowane plus tworzymy sumę dwóch prostokątów.</span><span class="sxs-lookup"><span data-stu-id="3d1be-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="3d1be-137">Ten region jest wyznaczony jako region wycinka <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d1be-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="3d1be-138">Następnie kod rysuje dwa wiersze, które są ograniczone do wewnętrznego obszaru przycinania.</span><span class="sxs-lookup"><span data-stu-id="3d1be-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](New Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);    
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));    
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 <span data-ttu-id="3d1be-139">Poniższa ilustracja przedstawia obciętych wierszy.</span><span class="sxs-lookup"><span data-stu-id="3d1be-139">The following illustration shows the clipped lines.</span></span>  
  
 <span data-ttu-id="3d1be-140">![Ograniczone obszar przycinania](./media/graphicsascon2.png "graphicsascon2")</span><span class="sxs-lookup"><span data-stu-id="3d1be-140">![Limited Clip Region](./media/graphicsascon2.png "graphicsascon2")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d1be-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d1be-141">See also</span></span>
- [<span data-ttu-id="3d1be-142">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d1be-142">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="3d1be-143">Używanie zagnieżdżonych kontenerów grafiki</span><span class="sxs-lookup"><span data-stu-id="3d1be-143">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)
