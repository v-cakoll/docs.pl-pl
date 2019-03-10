---
title: 'Instrukcje: Rysowanie sekwencji B&#233;zier krzywe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 1de2f44be189cb2ff874a748ae6093c945120178
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711800"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>Instrukcje: Rysowanie sekwencji B&#233;zier krzywe
Możesz użyć <xref:System.Drawing.Graphics.DrawBeziers%2A> metody <xref:System.Drawing.Graphics> klasy Rysowanie sekwencji połączone krzywych Beziera.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera składający się z dwóch połączonych krzywych Beziera krzywej. Punkt końcowy pierwszy Beziera to punkt początkowy elementu Beziera drugiego.  
  
 Poniższa ilustracja przedstawia połączonych krzywe wraz z siedmiu punktów.  
  
 ![Bezier Spline](./media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Krzywe Beziera w GDI+](bezier-splines-in-gdi.md)
- [Konstruowanie i rysowanie krzywych](constructing-and-drawing-curves.md)
