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
ms.openlocfilehash: ebb53e7df979a553ed4a44deba34345c9ecac772
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171681"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>Instrukcje: Rysowanie pojedynczej B&#233;zier z krzywymi składanymi
Krzywej Beziera jest definiowany przez cztery punkty: punkt początkowy, punktów kontrolnych dwóch i punkt końcowy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera krzywej Beziera punkt początkowy (10, 100) i punkt końcowy (200, 100). Kontrolka wskazuje, czy (100, 10) i (150, 150).  
  
 Poniższa ilustracja przedstawia wynikowy Beziera wraz z jego punkt początkowy, punktów kontrolnych i punktu końcowego. Na ilustracji pokazano również krzywej składanej wypukłe kadłuba, czyli wielokąta sformułowany, łącząc cztery punkty za pomocą prostych wierszy.  
  
 ![Ilustracja Krzywa Beziera.](./media/how-to-draw-a-single-bezier-spline/bezier-spline-illustration.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [Krzywe Beziera w GDI+](bezier-splines-in-gdi.md)
- [Instrukcje: Rysowanie sekwencji krzywych Beziera](how-to-draw-a-sequence-of-bezier-splines.md)
