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
ms.openlocfilehash: d1e7e6eac775ca779fb68605adcc9bc2b9915e49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182451"
---
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="c17f5-102">Zarządzanie stanem obiektu graficznego</span><span class="sxs-lookup"><span data-stu-id="c17f5-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="c17f5-103">Klasa <xref:System.Drawing.Graphics> znajduje się w samym sercu GDI+.</span><span class="sxs-lookup"><span data-stu-id="c17f5-103">The <xref:System.Drawing.Graphics> class is at the heart of GDI+.</span></span> <span data-ttu-id="c17f5-104">Aby narysować cokolwiek, można <xref:System.Drawing.Graphics> uzyskać obiekt, ustawić <xref:System.Drawing.Graphics.DrawLine%2A>jego <xref:System.Drawing.Graphics.DrawImage%2A> <xref:System.Drawing.Graphics.DrawString%2A>właściwości i wywołać jego metody , , i tym podobne).</span><span class="sxs-lookup"><span data-stu-id="c17f5-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="c17f5-105">Poniższy przykład <xref:System.Drawing.Graphics.DrawRectangle%2A> wywołuje metodę <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c17f5-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c17f5-106">Pierwszy argument przekazany <xref:System.Drawing.Graphics.DrawRectangle%2A> do metody <xref:System.Drawing.Pen> jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="c17f5-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
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
  
## <a name="graphics-state"></a><span data-ttu-id="c17f5-107">Stan grafiki</span><span class="sxs-lookup"><span data-stu-id="c17f5-107">Graphics State</span></span>  
 <span data-ttu-id="c17f5-108">Obiekt <xref:System.Drawing.Graphics> nie tylko zapewnia metody rysowania, takie jak <xref:System.Drawing.Graphics.DrawLine%2A> i <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="c17f5-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="c17f5-109">Obiekt <xref:System.Drawing.Graphics> zachowuje również stan grafiki, który można podzielić na następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="c17f5-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
- <span data-ttu-id="c17f5-110">Ustawienia jakości</span><span class="sxs-lookup"><span data-stu-id="c17f5-110">Quality settings</span></span>  
  
- <span data-ttu-id="c17f5-111">Przekształcenia</span><span class="sxs-lookup"><span data-stu-id="c17f5-111">Transformations</span></span>  
  
- <span data-ttu-id="c17f5-112">Obszar przycinania</span><span class="sxs-lookup"><span data-stu-id="c17f5-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="c17f5-113">Ustawienia jakości</span><span class="sxs-lookup"><span data-stu-id="c17f5-113">Quality Settings</span></span>  
 <span data-ttu-id="c17f5-114">Obiekt <xref:System.Drawing.Graphics> ma kilka właściwości, które wpływają na jakość elementów, które są rysowane.</span><span class="sxs-lookup"><span data-stu-id="c17f5-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="c17f5-115">Na przykład można ustawić <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwość, aby określić typ antialiasing (jeśli istnieje) stosowane do tekstu.</span><span class="sxs-lookup"><span data-stu-id="c17f5-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="c17f5-116">Inne właściwości wpływające <xref:System.Drawing.Graphics.SmoothingMode%2A>na <xref:System.Drawing.Graphics.CompositingMode%2A> <xref:System.Drawing.Graphics.CompositingQuality%2A>jakość <xref:System.Drawing.Graphics.InterpolationMode%2A>to , , i .</span><span class="sxs-lookup"><span data-stu-id="c17f5-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="c17f5-117">Poniższy przykład rysuje dwie elipsy, jedną z <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> ustawionym trybem wygładzania, a druga z trybem wygładzania ustawionym na: <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed></span><span class="sxs-lookup"><span data-stu-id="c17f5-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
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
  
### <a name="transformations"></a><span data-ttu-id="c17f5-118">Przekształcenia</span><span class="sxs-lookup"><span data-stu-id="c17f5-118">Transformations</span></span>  
 <span data-ttu-id="c17f5-119">Obiekt <xref:System.Drawing.Graphics> zachowuje dwa przekształcenia (świat i strona), które są <xref:System.Drawing.Graphics> stosowane do wszystkich elementów rysowanych przez ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="c17f5-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c17f5-120">Wszelkie transformacji affine mogą być przechowywane w transformacji świata.</span><span class="sxs-lookup"><span data-stu-id="c17f5-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="c17f5-121">Przekształcenia afiniowe obejmują skalowanie, obracanie, odbijanie, pochylanie i tłumaczenie.</span><span class="sxs-lookup"><span data-stu-id="c17f5-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="c17f5-122">Transformacja strony może służyć do skalowania i zmiany jednostek (na przykład pikseli na cale).</span><span class="sxs-lookup"><span data-stu-id="c17f5-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="c17f5-123">Aby uzyskać więcej informacji, zobacz [Systemy współrzędnych i przekształcenia](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="c17f5-123">For more information, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="c17f5-124">Poniższy przykład ustawia przekształcenia świata <xref:System.Drawing.Graphics> i strony obiektu.</span><span class="sxs-lookup"><span data-stu-id="c17f5-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c17f5-125">Transformacja świata jest ustawiona na obrót o 30 stopni.</span><span class="sxs-lookup"><span data-stu-id="c17f5-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="c17f5-126">Transformacja strony jest ustawiona tak, aby <xref:System.Drawing.Graphics.DrawEllipse%2A> współrzędne przekazane do drugiego były traktowane jako milimetry zamiast pikseli.</span><span class="sxs-lookup"><span data-stu-id="c17f5-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="c17f5-127">Kod sprawia, że dwa <xref:System.Drawing.Graphics.DrawEllipse%2A> identyczne wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="c17f5-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="c17f5-128">Transformacja świata jest stosowana <xref:System.Drawing.Graphics.DrawEllipse%2A> do pierwszego wywołania, a oba przekształcenia (świat i strona) są stosowane do drugiego <xref:System.Drawing.Graphics.DrawEllipse%2A> wywołania.</span><span class="sxs-lookup"><span data-stu-id="c17f5-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
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
  
 <span data-ttu-id="c17f5-129">Na poniższej ilustracji przedstawiono dwie elipsy.</span><span class="sxs-lookup"><span data-stu-id="c17f5-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="c17f5-130">Należy zauważyć, że obrót o 30 stopni dotyczy początku układu współrzędnych (lewego górnego rogu obszaru klienta), a nie środkami elips.</span><span class="sxs-lookup"><span data-stu-id="c17f5-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="c17f5-131">Należy również zauważyć, że szerokość pióra 1 oznacza 1 piksel dla pierwszej elipsy i 1 milimetr dla drugiej elipsy.</span><span class="sxs-lookup"><span data-stu-id="c17f5-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 ![Ilustracja przedstawiająca dwie elipsy: obrót i szerokość pióra.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a><span data-ttu-id="c17f5-133">Region przycinania</span><span class="sxs-lookup"><span data-stu-id="c17f5-133">Clipping Region</span></span>  
 <span data-ttu-id="c17f5-134">Obiekt <xref:System.Drawing.Graphics> zachowuje region przycinania, który ma zastosowanie <xref:System.Drawing.Graphics> do wszystkich elementów rysowanych przez ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="c17f5-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c17f5-135">Region przycinania można ustawić, <xref:System.Drawing.Graphics.SetClip%2A> wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="c17f5-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="c17f5-136">Poniższy przykład tworzy region w kształcie plus, tworząc jedność dwóch prostokątów.</span><span class="sxs-lookup"><span data-stu-id="c17f5-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="c17f5-137">Ten region jest wyznaczony jako obszar <xref:System.Drawing.Graphics> przycinania obiektu.</span><span class="sxs-lookup"><span data-stu-id="c17f5-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c17f5-138">Następnie kod rysuje dwie linie, które są ograniczone do wnętrza regionu przycinania.</span><span class="sxs-lookup"><span data-stu-id="c17f5-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
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
  
 <span data-ttu-id="c17f5-139">Na poniższej ilustracji przedstawiono przycięte linie:</span><span class="sxs-lookup"><span data-stu-id="c17f5-139">The following illustration shows the clipped lines:</span></span>  
  
 ![Diagram przedstawiający ograniczony region klipu.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a><span data-ttu-id="c17f5-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c17f5-141">See also</span></span>

- [<span data-ttu-id="c17f5-142">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c17f5-142">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="c17f5-143">Używanie zagnieżdżonych kontenerów grafiki</span><span class="sxs-lookup"><span data-stu-id="c17f5-143">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)
