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
ms.openlocfilehash: 33a8954296a7e63637ad5e210fb30fba1a3fdd53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165116"
---
# <a name="open-and-closed-curves-in-gdi"></a>Krzywe otwarte i zamknięte w GDI+
Na poniższej ilustracji przedstawiono dwie krzywe: otwarty i jedną zamknięte.  
  
 ![Krzywe otwarte i zamknięte](./media/aboutgdip02-art24.gif "Aboutgdip02_art24")  
  
## <a name="managed-interface-for-curves"></a>Zarządzany interfejs dla krzywych  
 Zamknięte krzywych mają wewnętrzne i może zostać wypełniony przy użyciu pędzla. <xref:System.Drawing.Graphics> Klasy w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia następujące metody do wypełniania kształtów zamkniętych i krzywych: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, i <xref:System.Drawing.Graphics.FillRegion%2A>. Przy każdym wywołaniu jednej z następujących metod, należy przekazać jeden z typów określonych pędzla (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, lub <xref:System.Drawing.Drawing2D.PathGradientBrush>) jako argument.  
  
 <xref:System.Drawing.Graphics.FillPie%2A> Metody jest uzupełnieniem do <xref:System.Drawing.Graphics.DrawArc%2A> metody. Podobnie jak <xref:System.Drawing.Graphics.DrawArc%2A> metoda rysuje część zarys elipsy, <xref:System.Drawing.Graphics.FillPie%2A> metoda wypełni część wewnętrzne elipsy. Poniższy przykład łuk i wstawia odpowiednią część wewnętrzne elipsy:  
  
 [!code-csharp[LinesCurvesAndShapes#21](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 Na poniższej ilustracji przedstawiono łuk i wypełniony kołowy.  
  
 ![Krzywe otwarte i zamknięte](./media/aboutgdip02-art25.gif "Aboutgdip02_art25")  
  
 <xref:System.Drawing.Graphics.FillClosedCurve%2A> Metody jest uzupełnieniem do <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metody. Obie metody automatycznie Zamknij krzywej przez nawiązanie połączenia punktu początkowego punktu końcowego. Poniższy przykład pobiera krzywej, który przechodzi przez (0, 0), (60, 20) i (40, 50). Następnie krzywej zostaje automatycznie zamknięty, łącząc (40, 50) do punkt początkowy (0, 0), i wewnętrznych jest wypełniony jednolitym kolorem.  
  
 [!code-csharp[LinesCurvesAndShapes#22](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <xref:System.Drawing.Graphics.FillPath%2A> Metoda wypełni wnętrza osobnych części ścieżki. Jeśli fragment ścieżki nie tworzą zamkniętej krzywej lub kształtu, <xref:System.Drawing.Graphics.FillPath%2A> metoda automatycznie zamyka danego fragmentu ścieżkę przed jego wypełnianie. Poniższy przykład pobiera i wypełnia ścieżką, która składa się z łuk, krzywa kardynalna, ciąg i wykres kołowy:  
  
 [!code-csharp[LinesCurvesAndShapes#23](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 Poniższa ilustracja przedstawia ścieżki z lub bez wypełnienia kryjącego. Należy pamiętać, że tekst w ciągu jest opisane, ale nie jest wypełniony, przez <xref:System.Drawing.Graphics.DrawPath%2A> metody. Jest <xref:System.Drawing.Graphics.FillPath%2A> metodę, która umożliwia malowanie wnętrza znaków w ciągu.  
  
 ![Ciąg znaków w ścieżce](./media/aboutgdip02-art26.gif "Aboutgdip02_art26")  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [Linie, krzywe i kształty](lines-curves-and-shapes.md)
- [Instrukcje: Tworzenie obiektów graficznych do rysowania](how-to-create-graphics-objects-for-drawing.md)
- [Konstruowanie i rysowanie ścieżek](constructing-and-drawing-paths.md)
