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
ms.openlocfilehash: 31fec6d0d3769251d21783b4657d00b06431e942
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="vector-graphics-overview"></a>Przegląd grafiki wektorowej
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Rysuje linii, prostokątów i innych kształtów w układzie współrzędnych. Można wybrać spośród różnych systemów współrzędnych, ale domyślny układ współrzędnych ma źródła w lewym górnym rogu z wskazanie osi y skierowany w dół i prawej osi x. Jednostka miary w układzie współrzędnych domyślny jest piksela.  
  
## <a name="the-building-blocks-of-gdi"></a>Bloki konstrukcyjne GDI +  
 ![Grafika wektorowa](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.gif "AboutGdip02_Art01")  
  
 Monitor komputera tworzy wyświetlanie na tablicy regularnej kropek nazywane elementami obrazu lub pikselach. Liczba pikseli na ekranie są wyświetlane zmienia się z jednego monitora do następnego i zwykle można skonfigurować liczbę pikseli, które są wyświetlane na poszczególnych monitora w pewnym stopniu przez użytkownika.  
  
 ![Grafika wektorowa](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.gif "AboutGdip02_Art02")  
  
 Jeśli używasz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do rysowania linii, prostokąta lub krzywej, podaj niektóre najważniejsze informacje na temat elementu, który ma być rysowany. Na przykład można określić wiersz, zapewniając dwa punkty i prostokąt można określić, podając punkt, wysokości i szerokości. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] działa w połączeniu z oprogramowaniem sterownik ekranu do określenia, które pikseli musi być włączona do wyświetlenia linii, prostokąta lub krzywej. Na poniższej ilustracji przedstawiono pikseli, które są włączone, aby wyświetlić wiersz z punktu (4, 2) w punkcie (12, 8).  
  
 ![Grafika wektorowa](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.gif "AboutGdip02_Art03")  
  
 Wraz z upływem czasu niektóre podstawowe bloki konstrukcyjne okazały się najbardziej przydatny w przypadku tworzenia obrazów dwuwymiarową. Te bloki konstrukcyjne, które są obsługiwane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], podano w poniższej liście:  
  
-   wiersze  
  
-   Prostokątów  
  
-   Wielokropek  
  
-   Łuki  
  
-   Wielokąty  
  
-   Krzywe kardynalne  
  
-   krzywe Beziera  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a>Metody do rysowania obiektu grafiki  
 <xref:System.Drawing.Graphics> Klasy w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia następujące metody rysowanie elementów na poprzedniej liście: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (dla kardynalne), a <xref:System.Drawing.Graphics.DrawBezier%2A>. Każda z tych metod jest przeciążony; oznacza to, że każda metoda obsługuje kilka list innym parametrem. Na przykład, jeden odmianą <xref:System.Drawing.Graphics.DrawLine%2A> metoda <xref:System.Drawing.Pen> i czterech liczb całkowitych, podczas zmiany innego obiektu <xref:System.Drawing.Graphics.DrawLine%2A> odbiera — metoda <xref:System.Drawing.Pen> obiektu i dwa <xref:System.Drawing.Point> obiektów.  
  
 Metody na rysowanie linii, prostokątów i krzywych Beziera mają pomocnika mnogiej metody kilka elementów w pojedynczym wywołaniu: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, i <xref:System.Drawing.Graphics.DrawBeziers%2A>. Ponadto <xref:System.Drawing.Graphics.DrawCurve%2A> metoda ma metodę Pomocnika <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, że punktu krzywej przez nawiązanie połączenia punktu końcowego krzywej początkowej zostanie zamknięty.  
  
 Wszystkie metody rysowania <xref:System.Drawing.Graphics> klasy pracy w połączeniu z <xref:System.Drawing.Pen> obiektu. Aby narysować niczego, należy utworzyć co najmniej dwa obiekty: <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu. <xref:System.Drawing.Pen> Obiekt przechowuje atrybuty, takie jak szerokość linii i kolor elementu, który ma być rysowany. <xref:System.Drawing.Pen> Przekazano obiekt jako jeden z argumentów metody rysowania. Na przykład, jeden odmianą <xref:System.Drawing.Graphics.DrawLine%2A> metoda <xref:System.Drawing.Pen> obiektu i czterech liczb całkowitych, jak pokazano w poniższym przykładzie rysuje prostokąt o szerokości 100, wysokości 50 i lewym górnym rogu (20, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Instrukcje: tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
