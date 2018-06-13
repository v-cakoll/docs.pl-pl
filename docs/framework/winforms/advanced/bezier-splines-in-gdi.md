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
ms.openlocfilehash: 2e247ec2bcd57c2fb2f5c32f61d38a2e7a267ff1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517576"
---
# <a name="b233zier-splines-in-gdi"></a>B&#233;zier krzywe w GDI +
Krzywej Beziera jest określony przez cztery punkty krzywej: dwa punkty końcowe (p1 i p2) i punkty kontrolne dwóch (c1 i c2). Krzywej zaczyna się od p1 i kończy się na p2. Krzywej nie przechodzi przez punkty kontrolne, ale punktów kontrolnych pełnienie pól, ściąganie krzywej w niektórych kierunkach i mające wpływ na sposób załamania krzywej. Na poniższej ilustracji przedstawiono krzywej Beziera, wraz z jego punktów końcowych i punkty kontrolne.  
  
 ![Krzywe Beziera](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 Krzywej rozpoczyna się od p1 i przenosi kierunku c1 punktu kontroli. Stycznej wiersz na krzywą na p1 jest rysowane z p1 c1 wiersza. Stycznej wiersza na p2 punktu końcowego jest rysowane z c2 p2 wiersza.  
  
## <a name="drawing-bzier-splines"></a>Rysowanie krzywych Beziera  
 Rysowanie krzywej Beziera, potrzebujesz wystąpienia <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Pen>. Wystąpienie <xref:System.Drawing.Graphics> klasa udostępnia <xref:System.Drawing.Graphics.DrawBezier%2A> metody i <xref:System.Drawing.Pen> przechowuje atrybuty, takie jak szerokości i koloru linii służącej do renderowania krzywej. <xref:System.Drawing.Pen> Jest przekazywany jako jeden z argumentów <xref:System.Drawing.Graphics.DrawBezier%2A> metody. Pozostałe argumenty przekazane do <xref:System.Drawing.Graphics.DrawBezier%2A> metody są punkty końcowe i punkty kontrolne. Poniższy przykład rysuje krzywej Beziera, z punkt (0, 0), początkowy kontroli punktów (40, 20) i (80, 150) i końcowe (100, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 Na poniższej ilustracji przedstawiono krzywej, punkty kontrolne i dwa wiersze stycznej.  
  
 ![Krzywe Beziera](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 Krzywe Beziera pierwotnie zostały opracowane przez Beziera Pierre dla projektu w branży motoryzacyjnych. Ponieważ okazały się użyteczne w wielu rodzajów CAD, a także są używane do definiowania konturów czcionki. Krzywe Beziera umożliwia uzyskanie szerokiej gamy kształtów, niektóre z nich są wyświetlane na poniższej ilustracji.  
  
 ![Ścieżki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Konstruowanie i rysowanie krzywych](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)  
 [Instrukcje: tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Instrukcje: tworzenie pióra](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
