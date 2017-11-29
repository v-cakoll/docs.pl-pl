---
title: "Porady: rysowanie tekstu w określonej lokalizacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text a a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aab9570b98caec5b3975a5b3ff6f1e62d4ad303b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-at-a-specified-location"></a>Porady: rysowanie tekstu w określonej lokalizacji
Podczas wykonywania Rysowanie niestandardowe może wykonywać Rysowanie tekstu w jednej linii poziomej rozpoczynającą się w określonym punkcie. W ten sposób można narysować tekstu przy użyciu <xref:System.Drawing.Graphics.DrawString%2A> przeciążona metoda <xref:System.Drawing.Graphics> klasy, która przyjmuje <xref:System.Drawing.Point> lub <xref:System.Drawing.PointF> parametru. <xref:System.Drawing.Graphics.DrawString%2A> Wymaga również metody <xref:System.Drawing.Brush> i<xref:System.Drawing.Font>  
  
 Można również użyć <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążona metoda <xref:System.Windows.Forms.TextRenderer> pobierającej <xref:System.Drawing.Point>. <xref:System.Windows.Forms.TextRenderer.DrawText%2A>wymaga również <xref:System.Drawing.Color> i <xref:System.Drawing.Font>.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe tekstu w określonym momencie, gdy używasz <xref:System.Drawing.Graphics.DrawString%2A> przeciążonej metody.  
  
 ![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Rysowanie linii tekstu z GDI +  
  
1.  Użyj <xref:System.Drawing.Graphics.DrawString%2A> jest metoda tekst, który ma, <xref:System.Drawing.Point> lub <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, i <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Rysowanie linii tekstu z GDI  
  
1.  Użyj <xref:System.Windows.Forms.TextRenderer.DrawText%2A> jest metoda tekst, który ma, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, i <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wymagaj poprzednich przykładach:  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`, która jest parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Rysowanie tekstu z GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Porady: tworzenie rodzin czcionek i czcionek](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [Porady: Rysowanie zawiniętego tekstu w prostokącie](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)
