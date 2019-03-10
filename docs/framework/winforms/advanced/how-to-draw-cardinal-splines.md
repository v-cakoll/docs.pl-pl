---
title: 'Instrukcje: Rysowanie krzywych kardynalnych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 687143273a07acba4b4d60acb1be25eee165b91d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710488"
---
# <a name="how-to-draw-cardinal-splines"></a>Instrukcje: Rysowanie krzywych kardynalnych
Krzywa kardynalna jest płynnie przechodzący przez podany zestaw punktów krzywej. Aby narysować kardynalna, należy utworzyć <xref:System.Drawing.Graphics> i przekazać adres tablica wskazuje <xref:System.Drawing.Graphics.DrawCurve%2A> metody.  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a>Rysowanie krzywej składanej Kardynalną w kształcie dzwonka  
  
-   Poniższy przykład pobiera w kształcie dzwonka kardynalna przechodzący przez pięć punktów wyznaczonym. Na poniższej ilustracji przedstawiono krzywej i pięć punktów.  
  
     ![Cardinal Spline](./media/cardinalspline1.png "CardinalSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a>Rysowanie zamkniętej krzywej kardynalnej  
  
-   Użyj <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metody <xref:System.Drawing.Graphics> klasy, aby narysować zamkniętej krzywej kardynalnej. W zamkniętej krzywej kardynalnej krzywej kontynuuje do ostatniego punktu w macierzy i nawiązuje połączenie z pierwszym punktem w tablicy. Poniższy przykład pobiera zamknięte kardynalna przechodzący przez sześć wyznaczonym punktów. Poniższa ilustracja przedstawia zamkniętej krzywej składanej wraz z sześciu punktów.  
  
 ![Cardinal Spline](./media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a>Zmiana odcinek łącznika krzywej składanej kardynalnych  
  
-   Zmiana sposobu kardynalna załamania przez przekazanie argumentu napięcie <xref:System.Drawing.Graphics.DrawCurve%2A> metody. Poniższy przykład pobiera trzy kardynalne, które przechodzą przez ten sam zestaw punktów. Poniższa ilustracja przedstawia trzy krzywe wraz z wartościami napięcie. Należy pamiętać, że gdy naciągnięcie wynosi 0, punkty są połączone liniami proste.  
  
 ![Cardinal Spline](./media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższych przykładach są skonstruowane do użycia za pomocą interfejsu Windows Forms i wymagają one <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- [Linie, krzywe i kształty](lines-curves-and-shapes.md)
- [Konstruowanie i rysowanie krzywych](constructing-and-drawing-curves.md)
