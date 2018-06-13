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
ms.openlocfilehash: 3ac6b9b651e65a45612cf2bd8ff17990c5cfba0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525850"
---
# <a name="polygons-in-gdi"></a>Wielokąty w GDI+
Wielokąt jest zamknięty kształt z co najmniej trzech stronach proste. Na przykład trójkąt ma wielokąta z trzech stron, prostokąt jest wielokąta z czterech stron, a pięciobok wielokąta z pięcioma stron. Na poniższej ilustracji przedstawiono kilka wielokątów.  
  
 ![Wielokąty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")  
  
## <a name="drawing-a-polygon"></a>Rysowanie wielokąta  
 Aby narysować wielokąt, należy <xref:System.Drawing.Graphics> obiektu, <xref:System.Drawing.Pen> obiekt a tablica <xref:System.Drawing.Point> (lub <xref:System.Drawing.PointF>) obiektów. <xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.DrawPolygon%2A> metody. <xref:System.Drawing.Pen> Obiekt przechowuje atrybuty, takie jak szerokości i koloru linii używany do renderowania wielokąta i tablica <xref:System.Drawing.Point> obiektów przechowuje punkty połączenia za pomocą linii prostych. <xref:System.Drawing.Pen> Obiekt a tablica <xref:System.Drawing.Point> obiekty są przekazywane jako argumenty do <xref:System.Drawing.Graphics.DrawPolygon%2A> metody. Poniższy przykład rysuje dwustronnych trzech wielokąta. Należy pamiętać, że są tylko trzy punkty w `myPointArray`: (0, 0), (50, 30) i (30, 60). <xref:System.Drawing.Graphics.DrawPolygon%2A> Metody jest automatycznie zamykany wielokąta za pomocą rysowania linii z (30, 60) do punktu początkowego (0, 0).  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 Na poniższej ilustracji przedstawiono wielokąta.  
  
 ![Wielokąt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Instrukcje: tworzenie pióra](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
