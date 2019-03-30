---
title: 'Instrukcje: Rysowanie zawiniętego tekstu w prostokącie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: 35eca2fc0fe40db1b590f4c599baee01c9a9faf3
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654535"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>Instrukcje: Rysowanie zawiniętego tekstu w prostokącie
Zawijanie tekstu w prostokącie można rysować za pomocą <xref:System.Drawing.Graphics.DrawString%2A> przeciążone metody <xref:System.Drawing.Graphics> klasy, która przyjmuje <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.RectangleF> parametru. Ponadto <xref:System.Drawing.Brush> i <xref:System.Drawing.Font>.  
  
 Można też rysować zawiniętego tekstu w prostokącie, za pomocą <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążone metody <xref:System.Windows.Forms.TextRenderer> przyjmującej <xref:System.Drawing.Rectangle> i <xref:System.Windows.Forms.TextFormatFlags> parametru. Ponadto <xref:System.Drawing.Color> i <xref:System.Drawing.Font>.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe tekstu rysowane w prostokącie, gdy używasz <xref:System.Drawing.Graphics.DrawString%2A> metody:
  
 ![Zrzut ekranu pokazujący dane wyjściowe w przypadku korzystania z metody sznurkiem.](./media/how-to-draw-wrapped-text-in-a-rectangle/drawstring-method-font-text.png)  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Rysowanie zawiniętego tekstu w prostokącie za pomocą GDI +  
  
1.  Użyj <xref:System.Drawing.Graphics.DrawString%2A> przeciążonej metody, przekazując tekst, który ma, <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> i <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Rysowanie zawiniętego tekstu w prostokącie za pomocą GDI  
  
1.  Użyj <xref:System.Windows.Forms.TextFormatFlags> powinna być otoczona wartość wyliczenia, aby określić tekst z <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążonej metody, przekazując tekst, który ma, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> i <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wymagaj poprzednich przykładach:  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Rysowanie tekstu za pomocą GDI](how-to-draw-text-with-gdi.md)
- [Używanie czcionek i tekstu](using-fonts-and-text.md)
- [Instrukcje: Tworzenie rodzin czcionek i czcionek](how-to-construct-font-families-and-fonts.md)
- [Instrukcje: Rysowanie tekstu w określonej lokalizacji](how-to-draw-text-at-a-specified-location.md)
