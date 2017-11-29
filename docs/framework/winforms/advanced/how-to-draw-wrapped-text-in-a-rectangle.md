---
title: "Porady: rysowanie zawiniętego tekstu w prostokącie"
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
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 773216c30adf1c684ec705a909038354aab0fec9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>Porady: rysowanie zawiniętego tekstu w prostokącie
Można Rysowanie zawiniętego tekstu w prostokącie przy użyciu <xref:System.Drawing.Graphics.DrawString%2A> przeciążona metoda <xref:System.Drawing.Graphics> klasy, która przyjmuje <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.RectangleF> parametru. Ponadto <xref:System.Drawing.Brush> i <xref:System.Drawing.Font>.  
  
 Zawijanie tekstu może Rysowanie w prostokącie, za pomocą <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążona metoda <xref:System.Windows.Forms.TextRenderer> pobierającej <xref:System.Drawing.Rectangle> i <xref:System.Windows.Forms.TextFormatFlags> parametru. Ponadto <xref:System.Drawing.Color> i <xref:System.Drawing.Font>.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe tekstu w prostokącie, korzystając z <xref:System.Drawing.Graphics.DrawString%2A> metody.  
  
 ![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Rysowanie zawiniętego tekstu w prostokącie z GDI +  
  
1.  Użyj <xref:System.Drawing.Graphics.DrawString%2A> przeciążona metoda przekazywanie tekst, który ma, <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> i <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Rysowanie zawiniętego tekstu w prostokącie za pomocą GDI  
  
1.  Użyj <xref:System.Windows.Forms.TextFormatFlags> wartość wyliczenia do Podaj tekst, który musi być ujęte z <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążona metoda przekazywanie tekst, który ma, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> i <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wymagaj poprzednich przykładach:  
  
-   <xref:System.Windows.Forms.PaintEventArgs>`e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Rysowanie tekstu z GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Porady: tworzenie rodzin czcionek i czcionek](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [Porady: Rysowanie tekstu w określonej lokalizacji](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)
