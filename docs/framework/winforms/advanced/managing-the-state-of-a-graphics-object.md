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
ms.openlocfilehash: 8fc92bf84def50bed54a054ae634a8a08c8835c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936893"
---
# <a name="managing-the-state-of-a-graphics-object"></a>Zarządzanie stanem obiektu graficznego
<xref:System.Drawing.Graphics> Klasy to serce [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Aby narysować niczego, należy uzyskać <xref:System.Drawing.Graphics> obiektu, ustaw jej właściwości i wywołać jego metody <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>i tym podobne).  
  
 Poniższy przykład wywołuje <xref:System.Drawing.Graphics.DrawRectangle%2A> metody <xref:System.Drawing.Graphics> obiektu. Pierwszy argument przekazany do <xref:System.Drawing.Graphics.DrawRectangle%2A> metodą jest <xref:System.Drawing.Pen> obiektu.  
  
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
 A <xref:System.Drawing.Graphics> obiektu więcej niż zapewnia rysowania metod, takich jak <xref:System.Drawing.Graphics.DrawLine%2A> i <xref:System.Drawing.Graphics.DrawRectangle%2A>. A <xref:System.Drawing.Graphics> obiekt przechowuje również stanu grafiki, które można podzielić na następujące kategorie:  
  
- Ustawienia jakości  
  
- Przekształcenia  
  
- Obszar przycinania  
  
### <a name="quality-settings"></a>Ustawienia jakości  
 A <xref:System.Drawing.Graphics> obiekt ma kilka właściwości, które mają wpływ na jakość elementy, które są rysowane. Na przykład można ustawić <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwości w celu określenia typu antialiasingu (jeśli istnieje) zastosowane do tekstu. Inne właściwości, które mają wpływ na jakość są <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, i <xref:System.Drawing.Graphics.InterpolationMode%2A>.  
  
 Poniższy przykładowy kod rysuje dwa elipsy, jeden z tryb wygładzania równa <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> i jeden z tryb wygładzania równa <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
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
 A <xref:System.Drawing.Graphics> obiekt przechowuje dwa przekształceń (świecie i strony), które są stosowane do wszystkich elementów rysowane przez to <xref:System.Drawing.Graphics> obiektu. Dowolnego affine — przekształcenia mogą być przechowywane w transformacji świata. Affine — przekształcenia obejmują skalowanie, obracanie, odzwierciedlanie, pochylanie i tłumaczenia. Przekształcenie strony może służyć skalowanie oraz zmiany jednostki (na przykład, w pikselach cm). Aby uzyskać więcej informacji, zobacz [systemy i przekształcenia współrzędnych](coordinate-systems-and-transformations.md).  
  
 W poniższym przykładzie ustawiono Przekształcanie świata i strony <xref:System.Drawing.Graphics> obiektu. Transformacja świata jest ustawiona na 30 stopni. Przekształcenie strony jest ustawiony tak, aby współrzędne przekazany do drugiego <xref:System.Drawing.Graphics.DrawEllipse%2A> będzie traktowane jako milimetry zamiast pikseli. Kod sprawia, że dwa identyczne wywołania <xref:System.Drawing.Graphics.DrawEllipse%2A> metody. Transformacja świata jest stosowana do pierwszego <xref:System.Drawing.Graphics.DrawEllipse%2A> wywołania i zarówno przekształcenia (świecie i strony), które są stosowane do drugiego <xref:System.Drawing.Graphics.DrawEllipse%2A> wywołania.  
  
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
  
 Poniższa ilustracja przedstawia dwie elipsy. Należy pamiętać, że 30 stopni o pochodzenia w układzie współrzędnych (lewym górnym rogu obszaru klienta), nie o centra wielokropek. Należy również zauważyć, że szerokość pióra 1 oznacza, że 1 piksel w pierwszym elipsy i 1 milimetra drugi elipsy.  
  
 ![Ilustracja przedstawiająca dwie elipsy: szerokość rotacji i Pióro.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>Obszar przycinania  
 A <xref:System.Drawing.Graphics> obiekt zachowuje obszaru przycinania, która ma zastosowanie do wszystkich elementów rysowane przez to <xref:System.Drawing.Graphics> obiektu. Możesz ustawić obszaru przycinania, wywołując <xref:System.Drawing.Graphics.SetClip%2A> metody.  
  
 Poniższy przykład tworzy obszar ukształtowane plus tworzymy sumę dwóch prostokątów. Ten region jest wyznaczony jako region wycinka <xref:System.Drawing.Graphics> obiektu. Następnie kod rysuje dwa wiersze, które są ograniczone do wewnętrznego obszaru przycinania.  
  
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
  
 Poniższa ilustracja przedstawia obciętych wiersze:  
  
 ![Diagram przedstawiający ograniczony obszar przycinania.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>Zobacz także

- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Używanie zagnieżdżonych kontenerów grafiki](using-nested-graphics-containers.md)
