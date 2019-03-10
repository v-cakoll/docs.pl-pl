---
title: 'Instrukcje: Rysowanie tekstu w określonej lokalizacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
ms.openlocfilehash: 3bca6cd364ed4e0d0179c13fb378449b7cf05739
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705353"
---
# <a name="how-to-draw-text-at-a-specified-location"></a>Instrukcje: Rysowanie tekstu w określonej lokalizacji
Podczas wykonywania niestandardowego rysowania można rysować tekst w pojedynczej linii poziomej, zaczynając od określonego punktu. W ten sposób można rysować tekst przy użyciu <xref:System.Drawing.Graphics.DrawString%2A> przeciążone metody <xref:System.Drawing.Graphics> klasy, która przyjmuje <xref:System.Drawing.Point> lub <xref:System.Drawing.PointF> parametru. <xref:System.Drawing.Graphics.DrawString%2A> Wymaga również metoda <xref:System.Drawing.Brush> i <xref:System.Drawing.Font>  
  
 Można również użyć <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążone metody <xref:System.Windows.Forms.TextRenderer> przyjmującej <xref:System.Drawing.Point>. <xref:System.Windows.Forms.TextRenderer.DrawText%2A> wymaga również <xref:System.Drawing.Color> i <xref:System.Drawing.Font>.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe tekstu rysowane w określonym momencie, gdy używasz <xref:System.Drawing.Graphics.DrawString%2A> przeciążonej metody.  
  
 ![Fonts Text](./media/csfontstext1.png "csfontstext1")  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Aby narysować linię tekstu za pomocą GDI +  
  
1.  Użyj <xref:System.Drawing.Graphics.DrawString%2A> jest metoda tekst, który ma, <xref:System.Drawing.Point> lub <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, i <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Aby narysować linię tekstu za pomocą GDI  
  
1.  Użyj <xref:System.Windows.Forms.TextRenderer.DrawText%2A> jest metoda tekst, który ma, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, i <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wymagaj poprzednich przykładach:  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Rysowanie tekstu za pomocą GDI](how-to-draw-text-with-gdi.md)
- [Używanie czcionek i tekstu](using-fonts-and-text.md)
- [Instrukcje: Tworzenie rodzin czcionek i czcionek](how-to-construct-font-families-and-fonts.md)
- [Instrukcje: Rysowanie zawiniętego tekstu w prostokącie](how-to-draw-wrapped-text-in-a-rectangle.md)
