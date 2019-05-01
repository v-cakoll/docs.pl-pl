---
title: B&#233;zier krzywe w GDI +
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: ff4e9eb18610b70c88e057d3d44020321bbb9f4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779275"
---
# <a name="b233zier-splines-in-gdi"></a>B&#233;zier krzywe w GDI +
Krzywej Beziera jest określony przez cztery punkty krzywej: dwa punkty końcowe (p1 i p2) i punkty kontrolne dwóch (c1 i c2). Krzywa rozpoczyna się od p1 i kończy się na p2. Krzywa nie przechodzi przez punkty kontrolne, ale punktów kontrolnych pełnić rolę pól, ściągając krzywej w niektórych kierunkach i wywieranie wpływu na sposób, w jaki załamania krzywej. Poniższa ilustracja przedstawia krzywej Beziera, wraz z jej punktów końcowych i punkty kontrolne.  
  
 ![Bezier Splines](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 Krzywa rozpoczyna się od p1 i jest przesuwany c1 punktu kontroli. Tangens linii krzywej w p1 jest linią od p1 do c1. Stycznej wiersza na p2 punkt końcowy jest linią z c2 do p2.  
  
## <a name="drawing-bzier-splines"></a>Rysowanie krzywych Beziera  
 Rysowanie krzywej Beziera, potrzebne jest wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Pen>. Wystąpienie <xref:System.Drawing.Graphics> klasa udostępnia <xref:System.Drawing.Graphics.DrawBezier%2A> metody i <xref:System.Drawing.Pen> przechowuje atrybuty, takie jak szerokość i kolor linii służącej do renderowania krzywej. <xref:System.Drawing.Pen> Jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawBezier%2A> metody. Pozostałe argumenty przekazywane do <xref:System.Drawing.Graphics.DrawBezier%2A> metody są punkty końcowe i punkty kontrolne. Poniższy przykład pobiera krzywej Beziera z początkowy (0, 0), kontrolować punkty (40, 20) i (80, 150), a końcowe (100, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#71](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 Na poniższej ilustracji przedstawiono krzywej, punktów kontrolnych i dwa wiersze stycznej.  
  
 ![Bezier Splines](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 Krzywe Beziera pierwotnie opracowano w za Beziera Pierre w dziedzinie projektowania w przemysł samochodowy. One od okazały się przydatne w wielu rodzajach CAD i są również używane do definiowania konturów czcionki. Krzywe Beziera może przynieść szereg kształtów, niektóre z nich są wyświetlane na poniższej ilustracji.  
  
 ![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Linie, krzywe i kształty](lines-curves-and-shapes.md)
- [Konstruowanie i rysowanie krzywych](constructing-and-drawing-curves.md)
- [Instrukcje: Tworzenie obiektów graficznych do rysowania](how-to-create-graphics-objects-for-drawing.md)
- [Instrukcje: Tworzenie pióra](how-to-create-a-pen.md)
