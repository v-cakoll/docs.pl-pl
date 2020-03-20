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
# <a name="managing-the-state-of-a-graphics-object"></a>Zarządzanie stanem obiektu graficznego
Klasa <xref:System.Drawing.Graphics> znajduje się w samym sercu GDI+. Aby narysować cokolwiek, można <xref:System.Drawing.Graphics> uzyskać obiekt, ustawić <xref:System.Drawing.Graphics.DrawLine%2A>jego <xref:System.Drawing.Graphics.DrawImage%2A> <xref:System.Drawing.Graphics.DrawString%2A>właściwości i wywołać jego metody , , i tym podobne).  
  
 Poniższy przykład <xref:System.Drawing.Graphics.DrawRectangle%2A> wywołuje metodę <xref:System.Drawing.Graphics> obiektu. Pierwszy argument przekazany <xref:System.Drawing.Graphics.DrawRectangle%2A> do metody <xref:System.Drawing.Pen> jest obiektem.  
  
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
  
## <a name="graphics-state"></a>Stan grafiki  
 Obiekt <xref:System.Drawing.Graphics> nie tylko zapewnia metody rysowania, takie jak <xref:System.Drawing.Graphics.DrawLine%2A> i <xref:System.Drawing.Graphics.DrawRectangle%2A>. Obiekt <xref:System.Drawing.Graphics> zachowuje również stan grafiki, który można podzielić na następujące kategorie:  
  
- Ustawienia jakości  
  
- Przekształcenia  
  
- Obszar przycinania  
  
### <a name="quality-settings"></a>Ustawienia jakości  
 Obiekt <xref:System.Drawing.Graphics> ma kilka właściwości, które wpływają na jakość elementów, które są rysowane. Na przykład można ustawić <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwość, aby określić typ antialiasing (jeśli istnieje) stosowane do tekstu. Inne właściwości wpływające <xref:System.Drawing.Graphics.SmoothingMode%2A>na <xref:System.Drawing.Graphics.CompositingMode%2A> <xref:System.Drawing.Graphics.CompositingQuality%2A>jakość <xref:System.Drawing.Graphics.InterpolationMode%2A>to , , i .  
  
 Poniższy przykład rysuje dwie elipsy, jedną z <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> ustawionym trybem wygładzania, a druga z trybem wygładzania ustawionym na: <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>  
  
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
  
### <a name="transformations"></a>Przekształcenia  
 Obiekt <xref:System.Drawing.Graphics> zachowuje dwa przekształcenia (świat i strona), które są <xref:System.Drawing.Graphics> stosowane do wszystkich elementów rysowanych przez ten obiekt. Wszelkie transformacji affine mogą być przechowywane w transformacji świata. Przekształcenia afiniowe obejmują skalowanie, obracanie, odbijanie, pochylanie i tłumaczenie. Transformacja strony może służyć do skalowania i zmiany jednostek (na przykład pikseli na cale). Aby uzyskać więcej informacji, zobacz [Systemy współrzędnych i przekształcenia](coordinate-systems-and-transformations.md).  
  
 Poniższy przykład ustawia przekształcenia świata <xref:System.Drawing.Graphics> i strony obiektu. Transformacja świata jest ustawiona na obrót o 30 stopni. Transformacja strony jest ustawiona tak, aby <xref:System.Drawing.Graphics.DrawEllipse%2A> współrzędne przekazane do drugiego były traktowane jako milimetry zamiast pikseli. Kod sprawia, że dwa <xref:System.Drawing.Graphics.DrawEllipse%2A> identyczne wywołania metody. Transformacja świata jest stosowana <xref:System.Drawing.Graphics.DrawEllipse%2A> do pierwszego wywołania, a oba przekształcenia (świat i strona) są stosowane do drugiego <xref:System.Drawing.Graphics.DrawEllipse%2A> wywołania.  
  
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
  
 Na poniższej ilustracji przedstawiono dwie elipsy. Należy zauważyć, że obrót o 30 stopni dotyczy początku układu współrzędnych (lewego górnego rogu obszaru klienta), a nie środkami elips. Należy również zauważyć, że szerokość pióra 1 oznacza 1 piksel dla pierwszej elipsy i 1 milimetr dla drugiej elipsy.  
  
 ![Ilustracja przedstawiająca dwie elipsy: obrót i szerokość pióra.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>Region przycinania  
 Obiekt <xref:System.Drawing.Graphics> zachowuje region przycinania, który ma zastosowanie <xref:System.Drawing.Graphics> do wszystkich elementów rysowanych przez ten obiekt. Region przycinania można ustawić, <xref:System.Drawing.Graphics.SetClip%2A> wywołując metodę.  
  
 Poniższy przykład tworzy region w kształcie plus, tworząc jedność dwóch prostokątów. Ten region jest wyznaczony jako obszar <xref:System.Drawing.Graphics> przycinania obiektu. Następnie kod rysuje dwie linie, które są ograniczone do wnętrza regionu przycinania.  
  
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
  
 Na poniższej ilustracji przedstawiono przycięte linie:  
  
 ![Diagram przedstawiający ograniczony region klipu.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>Zobacz też

- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Używanie zagnieżdżonych kontenerów grafiki](using-nested-graphics-containers.md)
