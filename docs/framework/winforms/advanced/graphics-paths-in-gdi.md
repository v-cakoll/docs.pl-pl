---
title: Ścieżki grafiki w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: 66d30b949fbfe8190b9e2ae2ea7896ac36bf0bac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523892"
---
# <a name="graphics-paths-in-gdi"></a>Ścieżki grafiki w GDI+
Ścieżki jest tworzony przez połączenie linii, prostokątów i krzywych proste. Wycofaj z [Przegląd grafiki wektorowej](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) czy następujących podstawowych bloków konstrukcyjnych okazały się najbardziej przydatny w przypadku rysowania obrazów:  
  
-   wiersze  
  
-   Prostokątów  
  
-   Wielokropek  
  
-   Łuki  
  
-   Wielokąty  
  
-   Krzywe kardynalne  
  
-   Krzywe Beziera  
  
 W GDI + <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu umożliwia zbieranie sekwencję te bloki konstrukcyjne w pojedynczą jednostkę. Można następnie narysowania całej sekwencji wierszy, prostokąty wielokątów i krzywych z jednego wywołania <xref:System.Drawing.Graphics.DrawPath%2A> metody <xref:System.Drawing.Graphics> klasy. Na poniższej ilustracji przedstawiono ścieżki tworzone przez połączenie linii, łuku krzywej Beziera i kardynalnej krzywej składanej.  
  
 ![Ścieżka](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>Przy użyciu ścieżki  
 <xref:System.Drawing.Drawing2D.GraphicsPath> Klasy udostępnia następujące metody tworzenia sekwencję elementów, które mają być rysowane: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (dla kardynalne), i <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>. Każda z tych metod jest przeciążony; oznacza to, że każda metoda obsługuje kilka list innym parametrem. Na przykład, jeden odmianą <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metody otrzymuje czterech liczb całkowitych i inna odmiana <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metody otrzymuje dwa <xref:System.Drawing.Point> obiektów.  
  
 Metody dodawania wierszy, prostokąty i krzywych Beziera na ścieżkę mają metody pomocnika w liczbie mnogiej, które dodać kilka elementów na ścieżkę w pojedynczym wywołaniu: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, i <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>. Ponadto <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> metody mają metody pomocnika <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, dodaje zamkniętej krzywej lub kołowy do ścieżki.  
  
 Aby narysować ścieżkę, należy <xref:System.Drawing.Graphics> obiektu <xref:System.Drawing.Pen> obiektu, a <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu. <xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.DrawPath%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak szerokość i kolor używany do renderowania ścieżki wiersza. <xref:System.Drawing.Drawing2D.GraphicsPath> Obiekt przechowuje sekwencji linii i krzywych, które składają się na ścieżce. <xref:System.Drawing.Pen> Obiektu i <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu są przekazywane jako argumenty do <xref:System.Drawing.Graphics.DrawPath%2A> metody. Poniższy przykład rysuje ścieżki, która składa się z linii, elipsy i krzywej Beziera:  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 Na poniższej ilustracji przedstawiono ścieżki.  
  
 ![Ścieżka](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 Oprócz dodania linii, prostokątów i krzywych do ścieżki, można dodać ścieżek do ścieżki. Dzięki temu można połączyć istniejące ścieżki do tworzenia ścieżek dużych, złożonych.  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 Istnieją dwa inne elementy można dodać do ścieżki: ciągów i ciast. Wykres kołowy jest częścią wewnątrz elipsy. Poniższy przykład tworzy ścieżki z łuk, kardynalnej krzywej składanej ciągu i wykres kołowy:  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 Na poniższej ilustracji przedstawiono ścieżki. Należy pamiętać, że ścieżki nie ma zostać połączona; Łuk, kardynalnej krzywej składanej, ciągu i koła są rozdzielone.  
  
 ![Ścieżki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Instrukcje: tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Konstruowanie i rysowanie ścieżek](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
