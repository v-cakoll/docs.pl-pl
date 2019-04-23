---
title: Przegląd grafiki wektorowej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
ms.openlocfilehash: d424254839db6c403bafe779f475c0e344918a5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087966"
---
# <a name="vector-graphics-overview"></a>Przegląd grafiki wektorowej
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Rysuje linie, prostokąty i inne kształty w układzie współrzędnych. Można wybrać spośród różnych systemów współrzędnych, ale w układzie współrzędnych domyślna ma pochodzenia w lewym górnym rogu z osi x, wskazując i prawej osi y skierowany w dół. Jednostka miary w układzie współrzędnych domyślny jest piksela.  
  
## <a name="the-building-blocks-of-gdi"></a>Bloki konstrukcyjne GDI +  
 ![Grafika wektorowa](./media/aboutgdip02-art01.gif "AboutGdip02_Art01")  
  
 Monitor komputera tworzy jej wyświetlanie na prostokątne tablicę kropki, nazywane elementami obrazu lub pikselach. Liczbę pikseli, które są wyświetlane na ekranie różni się od jednego monitora do następnego i zazwyczaj można skonfigurować liczbę pikseli, wyświetlanymi na monitorze poszczególnych do pewnego stopnia przez użytkownika.  
  
 ![Grafika wektorowa](./media/aboutgdip02-art02.gif "AboutGdip02_Art02")  
  
 Kiedy używasz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Aby narysować linię, prostokąta lub krzywą, podaj niektórych kluczowych informacji na temat elementu do narysowania. Na przykład można określić wiersz, zapewniając dwa punkty i prostokąt można określić, podając punkt, wysokość i szerokość. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] działa w połączeniu z oprogramowanie sterownik ekranu w celu ustalenia, które piksele muszą być włączone do wyświetlenia w wierszu, prostokąta lub krzywej. Poniższa ilustracja przedstawia piksele, które są włączone, aby wyświetlić wiersz z punktu (4, 2) w punkcie (12, 8).  
  
 ![Grafika wektorowa](./media/aboutgdip02-art03.gif "AboutGdip02_Art03")  
  
 Wraz z upływem czasu niektórych podstawowych bloków konstrukcyjnych okazały się być najbardziej przydatne do tworzenia obrazów dwuwymiarową. Te bloki konstrukcyjne, w których są obsługiwane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], są podane w poniższej liście:  
  
-   wiersze  
  
-   Prostokąty  
  
-   Wielokropek  
  
-   Łuki  
  
-   Wielokąty  
  
-   Krzywe kardynalne  
  
-   krzywe Beziera  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a>Metody Rysowanie obiektów grafiki  
 <xref:System.Drawing.Graphics> Klasy w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia następujące metody rysowania elementów na poprzedniej liście: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (na krzywe kardynalne), a <xref:System.Drawing.Graphics.DrawBezier%2A>. Każda z tych metod jest przeciążona; oznacza to, że każda metoda obsługuje kilka list różnych parametrów. Na przykład jeden odmianą <xref:System.Drawing.Graphics.DrawLine%2A> metoda otrzymuje <xref:System.Drawing.Pen> obiektu i czterech liczb całkowitych, podczas inna wersja <xref:System.Drawing.Graphics.DrawLine%2A> metoda otrzymuje <xref:System.Drawing.Pen> obiektu a dwa <xref:System.Drawing.Point> obiektów.  
  
 Metody do rysowania linii, prostokąty i krzywych Beziera mają metody pomocnika w liczbie mnogiej, które Rysowanie kilka elementów w jednym wywołaniu: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, i <xref:System.Drawing.Graphics.DrawBeziers%2A>. Ponadto <xref:System.Drawing.Graphics.DrawCurve%2A> metoda ma metodę Pomocnika <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, że punkt krzywej przez nawiązanie połączenia punktu końcowego krzywej początkowy zostanie zamknięty.  
  
 Wszystkie metody rysowania <xref:System.Drawing.Graphics> klasy działa w połączeniu z <xref:System.Drawing.Pen> obiektu. Aby narysować niczego, należy utworzyć co najmniej dwa obiekty: <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Pen> Obiekt przechowuje atrybuty, takie jak szerokość i kolor elementu do narysowania. <xref:System.Drawing.Pen> Obiekt jest przekazywany jako jeden z argumentów metody rysowania. Na przykład jeden odmianą <xref:System.Drawing.Graphics.DrawLine%2A> metoda otrzymuje <xref:System.Drawing.Pen> obiektu i czterech liczb całkowitych, jak pokazano w poniższym przykładzie, który rysuje prostokąt o szerokości 100, o wysokości od 50 do lewego górnego rogu (20, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#11](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Linie, krzywe i kształty](lines-curves-and-shapes.md)
- [Instrukcje: Tworzenie obiektów graficznych do rysowania](how-to-create-graphics-objects-for-drawing.md)
