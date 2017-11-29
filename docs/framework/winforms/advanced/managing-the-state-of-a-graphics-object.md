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
ms.openlocfilehash: 438243d16d8031d99e27993cadb44fd58bbec0b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="managing-the-state-of-a-graphics-object"></a>Zarządzanie stanem obiektu graficznego
<xref:System.Drawing.Graphics> Klasy jest istotą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Aby narysować niczego, należy uzyskać <xref:System.Drawing.Graphics> obiektu, ustawienia swoich właściwości i wywołanie metody <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>itp).  
  
 Następujące przykładowe wywołania <xref:System.Drawing.Graphics.DrawRectangle%2A> metody <xref:System.Drawing.Graphics> obiektu. Pierwszy argument przekazany do <xref:System.Drawing.Graphics.DrawRectangle%2A> jest metoda <xref:System.Drawing.Pen> obiektu.  
  
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
 A <xref:System.Drawing.Graphics> obiektu więcej niż podania rysowania metod, takich jak <xref:System.Drawing.Graphics.DrawLine%2A> i <xref:System.Drawing.Graphics.DrawRectangle%2A>. A <xref:System.Drawing.Graphics> obiektu również zachowuje swój stan grafiki, które można podzielić na następujące kategorie:  
  
-   Ustawienia jakości  
  
-   Przekształcenia  
  
-   Obszar przycinania  
  
### <a name="quality-settings"></a>Ustawienia jakości  
 A <xref:System.Drawing.Graphics> obiekt ma kilka właściwości wpływające na jakość elementy, które są rysowane. Na przykład można ustawić <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwości w celu określenia typu antialiasingu (jeśli istnieją) zastosowany do tekstu. Inne właściwości wpływające na jakości są <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, i <xref:System.Drawing.Graphics.InterpolationMode%2A>.  
  
 Poniższy przykład rysuje dwie elipsy, jeden z ustawioną tryb wygładzania <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> i jeden z ustawioną tryb wygładzania <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
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
 A <xref:System.Drawing.Graphics> obiektu obsługuje dwa przekształcenia (world i strony), które są stosowane do wszystkich elementów rysowane przez to <xref:System.Drawing.Graphics> obiektu. Dowolnego affine — przekształcenia mogą być przechowywane w transformacji świata. Affine — przekształcenia obejmują skalowanie, obracanie, odbijanie, pochylanie i tłumaczenia. Transformacja strony można skalować oraz zmiany jednostki (na przykład pikseli na cale). Aby uzyskać więcej informacji, zobacz [systemy i transformacje współrzędnych](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).  
  
 Poniższy przykład przedstawia transformacji świata i strony z <xref:System.Drawing.Graphics> obiektu. Transformacja świata wynosi 30 stopni. Transformacja strony ustawiono tak, aby współrzędne przekazany do drugiego <xref:System.Drawing.Graphics.DrawEllipse%2A> będzie traktowany jako milimetry zamiast pikseli. Kod wywołań dwie identyczne do <xref:System.Drawing.Graphics.DrawEllipse%2A> metody. Transformacja świata jest stosowany do pierwszego <xref:System.Drawing.Graphics.DrawEllipse%2A> wywołania i obu przekształcenia (world i strony) są stosowane do drugiego <xref:System.Drawing.Graphics.DrawEllipse%2A> wywołania.  
  
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
  
 Na poniższej ilustracji przedstawiono dwie elipsy. Należy pamiętać, że 30 stopni o pochodzenia współrzędnych (lewego górnego rogu obszaru klienckiego), nie na temat środkami wielokropek. Należy również zauważyć, że szerokość pióra 1 oznacza 1 piksela dla pierwszego elipsy i 1 milimetra drugi elipsy.  
  
 ![Elipsy](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")  
  
### <a name="clipping-region"></a>Obszar przycinania  
 A <xref:System.Drawing.Graphics> obiekt zachowuje obszar przycinania, która ma zastosowanie do wszystkich elementów rysowane przez to <xref:System.Drawing.Graphics> obiektu. Można ustawić obszaru przycinania przez wywołanie metody <xref:System.Drawing.Graphics.SetClip%2A> metody.  
  
 Poniższy przykład tworzy obszar w kształcie plus przez tworzenie złożenie dwóch prostokątów. Ten region jest wyznaczony jako regionu wycinka <xref:System.Drawing.Graphics> obiektu. Następnie kod pobiera dwa wiersze, które są ograniczone do wewnętrznych obszaru przycinania.  
  
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
  
 Na poniższej ilustracji przedstawiono przyciętą wierszy.  
  
 ![Ograniczone obszar przycinania](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")  
  
## <a name="see-also"></a>Zobacz też  
 [Grafika i rysowanie w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Używanie zagnieżdżonych kontenerów grafiki](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)
