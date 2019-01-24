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
ms.openlocfilehash: 55cd3284f331e9793a0bb73f26ed16bbd99fa116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685653"
---
# <a name="graphics-paths-in-gdi"></a>Ścieżki grafiki w GDI+
Ścieżki są tworzone przez łączenie linii, prostokąty i krzywych proste. Jak pamiętamy z artykułu [Przegląd grafiki wektorowej](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) czy następujących podstawowych bloków konstrukcyjnych okazały się być najbardziej przydatne do rysowania obrazów:  
  
-   wiersze  
  
-   Prostokąty  
  
-   Wielokropek  
  
-   Łuki  
  
-   Wielokąty  
  
-   Krzywe kardynalne  
  
-   Krzywe Beziera  
  
 W GDI + <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt umożliwia zbieranie sekwencję te bloki konstrukcyjne w pojedynczą jednostkę. Całą sekwencję linii, prostokątów, wielokąty i krzywych następnie mogą być wystawiane przy użyciu jednego wywołania do <xref:System.Drawing.Graphics.DrawPath%2A> metody <xref:System.Drawing.Graphics> klasy. Poniższa ilustracja przedstawia ścieżki tworzone przez połączenie linii, łuk, krzywej Beziera i kardynalnej krzywej składanej.  
  
 ![Ścieżka](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>Przy użyciu ścieżki  
 <xref:System.Drawing.Drawing2D.GraphicsPath> Klasa udostępnia następujące metody do tworzenia sekwencji elementów, które mają być rysowane: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (na krzywe kardynalne), a <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>. Każda z tych metod jest przeciążona; oznacza to, że każda metoda obsługuje kilka list różnych parametrów. Na przykład jeden odmianą <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metoda otrzymuje czterech liczb całkowitych, a inna wersja <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metoda otrzymuje dwa <xref:System.Drawing.Point> obiektów.  
  
 Metody dodawania wierszy, prostokąty i krzywych Beziera na ścieżkę mają metody pomocnika w liczbie mnogiej, które dodać kilka elementów do ścieżki w pojedynczym wywołaniu: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, i <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>. Ponadto <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> metody mają metody pomocnika <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, zamkniętej krzywej lub koła, Dodaj do ścieżki.  
  
 Aby narysować ścieżkę, musisz mieć <xref:System.Drawing.Graphics> obiektu, <xref:System.Drawing.Pen> obiektu, a <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu. <xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawPath%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje atrybuty, takie jak szerokość i kolor linii służącej do renderowania ścieżki. <xref:System.Drawing.Drawing2D.GraphicsPath> Obiekt przechowuje sekwencji linii i krzywych, które tworzą ścieżki. <xref:System.Drawing.Pen> Obiektu i <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu są przekazywane jako argumenty <xref:System.Drawing.Graphics.DrawPath%2A> metody. Poniższy przykład pobiera ścieżki, która składa się z linii, elipsę i krzywej Beziera:  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 Poniższa ilustracja przedstawia ścieżkę.  
  
 ![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 Oprócz dodawania wierszy, prostokąty i krzywych do ścieżki, można dodać ścieżki do ścieżki. Dzięki temu można łączyć istniejące ścieżki w celu utworzenia dużych, złożonych ścieżki.  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 Istnieją dwa inne elementy, można dodać do ścieżki: ciągi i wycinków. Wykres kołowy to część wewnętrzne elipsy. Poniższy przykład tworzy ścieżkę z łuk, krzywa kardynalna, ciąg i wykres kołowy:  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 Poniższa ilustracja przedstawia ścieżkę. Należy zauważyć, że ścieżka nie ma połączenia; Łuk, krzywa kardynalna, parametry i kołowy są rozdzielone.  
  
 ![Ścieżki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Instrukcje: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
- [Konstruowanie i rysowanie ścieżek](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
