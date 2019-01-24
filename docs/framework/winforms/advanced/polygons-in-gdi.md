---
title: Wielokąty w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
ms.openlocfilehash: 94f18b3150a5c953f2e886f644ec5cfaabd786fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511514"
---
# <a name="polygons-in-gdi"></a>Wielokąty w GDI+
Wielokąt jest kształt zamknięty przy użyciu co najmniej trzech stronach proste. Na przykład trójkąt jest Wielokąt przy użyciu trzech stronach prostokątowi Wielokąt przy użyciu czterech bokach i pięciobok jest wielokąta z pięciu stron. Poniższa ilustracja przedstawia kilka wielokątów.  
  
 ![Polygons](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")  
  
## <a name="drawing-a-polygon"></a>Rysowanie wielokąta  
 Aby narysować wielokąt, musisz mieć <xref:System.Drawing.Graphics> obiektu <xref:System.Drawing.Pen> obiekt i tablica <xref:System.Drawing.Point> (lub <xref:System.Drawing.PointF>) obiektów. <xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawPolygon%2A> metody. <xref:System.Drawing.Pen> Obiekt przechowuje atrybuty, takie jak szerokość i kolor linii, używany do renderowania wielokąta i tablica <xref:System.Drawing.Point> obiektów przechowuje punktów połączenia linii prostych. <xref:System.Drawing.Pen> Obiekt i tablica <xref:System.Drawing.Point> obiekty są przekazywane jako argumenty <xref:System.Drawing.Graphics.DrawPolygon%2A> metody. Poniższy przykład pobiera wielokąta dwustronna trzy. Należy zauważyć, że istnieje tylko dla trzech punktów w `myPointArray`: (0, 0), (50, 30) i (30, 60). <xref:System.Drawing.Graphics.DrawPolygon%2A> Metoda automatycznie zamyka wielokąta za pomocą rysowania linii z (30, 60) do punkt początkowy (0, 0).  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 Poniższa ilustracja przedstawia wielokąta.  
  
 ![Polygon](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Instrukcje: Tworzenie pióra](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
