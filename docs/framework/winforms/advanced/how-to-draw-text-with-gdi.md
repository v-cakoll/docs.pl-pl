---
title: 'Instrukcje: Rysowanie tekstu za pomocą GDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956542"
---
# <a name="how-to-draw-text-with-gdi"></a>Instrukcje: Rysowanie tekstu za pomocą GDI
Za pomocą <xref:System.Windows.Forms.TextRenderer> metody w klasie można uzyskać dostęp do funkcji GDI do rysowania tekstu w formularzu lub formancie. <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Renderowanie tekstu GDI zwykle zapewnia lepszą wydajność i dokładniejsze mierzenie tekstu niż GDI+.  
  
> [!NOTE]
> <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody<xref:System.Windows.Forms.TextRenderer> klasy nie są obsługiwane na potrzeby drukowania. Podczas drukowania zawsze używaj <xref:System.Drawing.Graphics.DrawString%2A> metod <xref:System.Drawing.Graphics> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób rysowania tekstu w wielu wierszach w prostokącie przy użyciu <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 Aby renderować tekst <xref:System.Windows.Forms.TextRenderer> z klasą, potrzebna jest <xref:System.Drawing.IDeviceContext>, <xref:System.Drawing.Font>taka jak <xref:System.Drawing.Graphics> i, lokalizacja do rysowania tekstu oraz kolor, w którym ma zostać narysowany. Opcjonalnie można określić formatowanie tekstu przy użyciu <xref:System.Windows.Forms.TextFormatFlags> wyliczenia.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Drawing.Graphics>uzyskiwania, [zobacz How to: Utwórz obiekty graficzne do rysowania](how-to-create-graphics-objects-for-drawing.md). Aby uzyskać więcej informacji na temat konstruowania <xref:System.Drawing.Font>, zobacz [How to: Skonstruuj rodziny czcionek i czcionki](how-to-construct-font-families-and-fonts.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład kodu jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, <xref:System.Windows.Forms.PaintEventHandler>który jest parametrem.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [Używanie czcionek i tekstu](using-fonts-and-text.md)
