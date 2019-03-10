---
title: 'Instrukcje: Rysowanie pojedynczej B&#233;zier z krzywymi składanymi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 6fc4e12bb7532019a0571095263b5447e4b0d1ed
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702519"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>Instrukcje: Rysowanie pojedynczej B&#233;zier z krzywymi składanymi
Krzywej Beziera jest definiowany przez cztery punkty: punkt początkowy, punktów kontrolnych dwóch i punkt końcowy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera krzywej Beziera punkt początkowy (10, 100) i punkt końcowy (200, 100). Kontrolka wskazuje, czy (100, 10) i (150, 150).  
  
 Poniższa ilustracja przedstawia wynikowy Beziera wraz z jego punkt początkowy, punktów kontrolnych i punktu końcowego. Na ilustracji pokazano również krzywej składanej wypukłe kadłuba, czyli wielokąta sformułowany, łącząc cztery punkty za pomocą prostych wierszy.  
  
 ![Bezier Spline](./media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [Krzywe Beziera w GDI+](bezier-splines-in-gdi.md)
- [Instrukcje: Rysowanie sekwencji krzywych Beziera](how-to-draw-a-sequence-of-bezier-splines.md)
