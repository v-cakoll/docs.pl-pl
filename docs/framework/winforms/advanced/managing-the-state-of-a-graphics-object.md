---
title: "Zarządzanie stanem obiektu graficznego"
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
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a9514d845580bfe921fefa5f4a249c5a905d03d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="5e308-102">Zarządzanie stanem obiektu graficznego</span><span class="sxs-lookup"><span data-stu-id="5e308-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="5e308-103"><xref:System.Drawing.Graphics> Klasy jest istotą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e308-103">The <xref:System.Drawing.Graphics> class is at the heart of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="5e308-104">Aby narysować niczego, należy uzyskać <xref:System.Drawing.Graphics> obiektu, ustawienia swoich właściwości i wywołanie metody <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>itp).</span><span class="sxs-lookup"><span data-stu-id="5e308-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="5e308-105">Następujące przykładowe wywołania <xref:System.Drawing.Graphics.DrawRectangle%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5e308-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="5e308-106">Pierwszy argument przekazany do <xref:System.Drawing.Graphics.DrawRectangle%2A> jest metoda <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5e308-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
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
  
## <a name="graphics-state"></a><span data-ttu-id="5e308-107">Stan grafiki</span><span class="sxs-lookup"><span data-stu-id="5e308-107">Graphics State</span></span>  
 <span data-ttu-id="5e308-108">A <xref:System.Drawing.Graphics> obiektu więcej niż podania rysowania metod, takich jak <xref:System.Drawing.Graphics.DrawLine%2A> i <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="5e308-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="5e308-109">A <xref:System.Drawing.Graphics> obiektu również zachowuje swój stan grafiki, które można podzielić na następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="5e308-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
-   <span data-ttu-id="5e308-110">Ustawienia jakości</span><span class="sxs-lookup"><span data-stu-id="5e308-110">Quality settings</span></span>  
  
-   <span data-ttu-id="5e308-111">Przekształcenia</span><span class="sxs-lookup"><span data-stu-id="5e308-111">Transformations</span></span>  
  
-   <span data-ttu-id="5e308-112">Obszar przycinania</span><span class="sxs-lookup"><span data-stu-id="5e308-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="5e308-113">Ustawienia jakości</span><span class="sxs-lookup"><span data-stu-id="5e308-113">Quality Settings</span></span>  
 <span data-ttu-id="5e308-114">A <xref:System.Drawing.Graphics> obiekt ma kilka właściwości wpływające na jakość elementy, które są rysowane.</span><span class="sxs-lookup"><span data-stu-id="5e308-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="5e308-115">Na przykład można ustawić <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwości w celu określenia typu antialiasingu (jeśli istnieją) zastosowany do tekstu.</span><span class="sxs-lookup"><span data-stu-id="5e308-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="5e308-116">Inne właściwości wpływające na jakości są <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, i <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="5e308-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="5e308-117">Poniższy przykład rysuje dwie elipsy, jeden z ustawioną tryb wygładzania <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> i jeden z ustawioną tryb wygładzania <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span><span class="sxs-lookup"><span data-stu-id="5e308-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
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
  
### <a name="transformations"></a><span data-ttu-id="5e308-118">Przekształcenia</span><span class="sxs-lookup"><span data-stu-id="5e308-118">Transformations</span></span>  
 <span data-ttu-id="5e308-119">A <xref:System.Drawing.Graphics> obiektu obsługuje dwa przekształcenia (world i strony), które są stosowane do wszystkich elementów rysowane przez to <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5e308-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="5e308-120">Dowolnego affine — przekształcenia mogą być przechowywane w transformacji świata.</span><span class="sxs-lookup"><span data-stu-id="5e308-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="5e308-121">Affine — przekształcenia obejmują skalowanie, obracanie, odbijanie, pochylanie i tłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="5e308-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="5e308-122">Transformacja strony można skalować oraz zmiany jednostki (na przykład pikseli na cale).</span><span class="sxs-lookup"><span data-stu-id="5e308-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="5e308-123">Aby uzyskać więcej informacji, zobacz [systemy i transformacje współrzędnych](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="5e308-123">For more information, see [Coordinate Systems and Transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="5e308-124">Poniższy przykład przedstawia transformacji świata i strony z <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5e308-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="5e308-125">Transformacja świata wynosi 30 stopni.</span><span class="sxs-lookup"><span data-stu-id="5e308-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="5e308-126">Transformacja strony ustawiono tak, aby współrzędne przekazany do drugiego <xref:System.Drawing.Graphics.DrawEllipse%2A> będzie traktowany jako milimetry zamiast pikseli.</span><span class="sxs-lookup"><span data-stu-id="5e308-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="5e308-127">Kod wywołań dwie identyczne do <xref:System.Drawing.Graphics.DrawEllipse%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5e308-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="5e308-128">Transformacja świata jest stosowany do pierwszego <xref:System.Drawing.Graphics.DrawEllipse%2A> wywołania i obu przekształcenia (world i strony) są stosowane do drugiego <xref:System.Drawing.Graphics.DrawEllipse%2A> wywołania.</span><span class="sxs-lookup"><span data-stu-id="5e308-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
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
  
 <span data-ttu-id="5e308-129">Na poniższej ilustracji przedstawiono dwie elipsy.</span><span class="sxs-lookup"><span data-stu-id="5e308-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="5e308-130">Należy pamiętać, że 30 stopni o pochodzenia współrzędnych (lewego górnego rogu obszaru klienckiego), nie na temat środkami wielokropek.</span><span class="sxs-lookup"><span data-stu-id="5e308-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="5e308-131">Należy również zauważyć, że szerokość pióra 1 oznacza 1 piksela dla pierwszego elipsy i 1 milimetra drugi elipsy.</span><span class="sxs-lookup"><span data-stu-id="5e308-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 <span data-ttu-id="5e308-132">![Elipsy](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")</span><span class="sxs-lookup"><span data-stu-id="5e308-132">![Ovals](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")</span></span>  
  
### <a name="clipping-region"></a><span data-ttu-id="5e308-133">Obszar przycinania</span><span class="sxs-lookup"><span data-stu-id="5e308-133">Clipping Region</span></span>  
 <span data-ttu-id="5e308-134">A <xref:System.Drawing.Graphics> obiekt zachowuje obszar przycinania, która ma zastosowanie do wszystkich elementów rysowane przez to <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5e308-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="5e308-135">Można ustawić obszaru przycinania przez wywołanie metody <xref:System.Drawing.Graphics.SetClip%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5e308-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="5e308-136">Poniższy przykład tworzy obszar w kształcie plus przez tworzenie złożenie dwóch prostokątów.</span><span class="sxs-lookup"><span data-stu-id="5e308-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="5e308-137">Ten region jest wyznaczony jako regionu wycinka <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5e308-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="5e308-138">Następnie kod pobiera dwa wiersze, które są ograniczone do wewnętrznych obszaru przycinania.</span><span class="sxs-lookup"><span data-stu-id="5e308-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
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
  
 <span data-ttu-id="5e308-139">Na poniższej ilustracji przedstawiono przyciętą wierszy.</span><span class="sxs-lookup"><span data-stu-id="5e308-139">The following illustration shows the clipped lines.</span></span>  
  
 <span data-ttu-id="5e308-140">![Ograniczone obszar przycinania](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")</span><span class="sxs-lookup"><span data-stu-id="5e308-140">![Limited Clip Region](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e308-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e308-141">See Also</span></span>  
 [<span data-ttu-id="5e308-142">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e308-142">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="5e308-143">Używanie zagnieżdżonych kontenerów grafiki</span><span class="sxs-lookup"><span data-stu-id="5e308-143">Using Nested Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)
