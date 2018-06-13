---
title: Krzywe otwarte i zamknięte w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
ms.openlocfilehash: 47f420184ac384ab11054d1cc3e767ab7f618234
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527151"
---
# <a name="open-and-closed-curves-in-gdi"></a>Krzywe otwarte i zamknięte w GDI+
Na poniższej ilustracji przedstawiono dwie krzywe: otwarty i jedną zamknięte.  
  
 ![Krzywe otwarte i zamknięte](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")  
  
## <a name="managed-interface-for-curves"></a>Zarządzanego interfejsu dla krzywych  
 Zamknięte krzywych mają wewnętrzne i może zostać wypełniony przy użyciu pędzla. <xref:System.Drawing.Graphics> Klasy w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia następujące metody do wypełniania krzywe i kształty zamknięte: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, i <xref:System.Drawing.Graphics.FillRegion%2A>. Zawsze, gdy wywoływana jednej z tych metod, trzeba przekazać jeden z typów określonych pędzla (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, lub <xref:System.Drawing.Drawing2D.PathGradientBrush>) jako argumentu.  
  
 <xref:System.Drawing.Graphics.FillPie%2A> Jest metoda pomocnika do <xref:System.Drawing.Graphics.DrawArc%2A> metody. Podobnie jak <xref:System.Drawing.Graphics.DrawArc%2A> metody rysuje część konturu elipsy <xref:System.Drawing.Graphics.FillPie%2A> metody wypełnia część wewnątrz elipsy. W poniższym przykładzie łuk i wypełnia odpowiednich części wewnątrz elipsy:  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 Na poniższej ilustracji przedstawiono łuk i kołowy wypełnione.  
  
 ![Krzywe otwarte i zamknięte](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")  
  
 <xref:System.Drawing.Graphics.FillClosedCurve%2A> Jest metoda pomocnika do <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metody. Obie metody automatycznie zamknąć krzywą przez połączenie punktu końcowego do punktu początkowego. Poniższy przykład rysuje krzywej, który przechodzi przez (0, 0), (60, 20) i (40, 50). Następnie krzywej zostaje automatycznie zamknięty, nawiązując połączenie (40, 50) do punktu początkowego (0, 0), a wewnętrzny jest wypełniony jednolitym kolorem.  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <xref:System.Drawing.Graphics.FillPath%2A> Metody wypełnia wnętrza oddzielnych części ścieżki. Jeśli część ścieżki nie tworzą zamkniętej krzywej lub kształt <xref:System.Drawing.Graphics.FillPath%2A> metody jest automatycznie zamykany tej części ścieżki przed jego wypełniania. Rysuje, wypełnia ścieżki, która składa się z łuk, kardynalnej krzywej składanej ciągu i wykres kołowy w następującym przykładzie:  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 Na poniższej ilustracji przedstawiono ścieżki z włączonymi i wyłączonymi wypełnieniem. Należy pamiętać, że tekst w ciągu jest opisane, ale nie jest wypełniony, przez <xref:System.Drawing.Graphics.DrawPath%2A> metody. Jest <xref:System.Drawing.Graphics.FillPath%2A> metodę, która umożliwia malowanie wnętrza znaków w ciągu.  
  
 ![Ciąg ścieżki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Instrukcje: tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Konstruowanie i rysowanie ścieżek](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
