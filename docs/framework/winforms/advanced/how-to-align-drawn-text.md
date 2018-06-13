---
title: 'Porady: wyrównywanie narysowanego tekstu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
ms.openlocfilehash: 96e14ef510a08ed0c387733e37b6acae6cbd31cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522760"
---
# <a name="how-to-align-drawn-text"></a>Porady: wyrównywanie narysowanego tekstu
Podczas wykonywania Rysowanie niestandardowe można często Centrum narysowanego tekstu na formularz lub formant. Można łatwo Dopasuj narysowany tekst <xref:System.Drawing.Graphics.DrawString%2A> lub <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metod tworzenia prawidłowy obiekt formatowania i ustawiając flagi w odpowiednim formacie.  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a>Rysowanie wyśrodkowany tekst mający GDI + (sznurkiem)  
  
1.  Użyj <xref:System.Drawing.StringFormat> z odpowiednią <xref:System.Drawing.Graphics.DrawString%2A> metodę, aby określić wyśrodkowany tekst.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a>Rysowanie wyśrodkowany tekst mający GDI (DrawText)  
  
1.  Użyj <xref:System.Windows.Forms.TextFormatFlags> wyliczenie dla zawijania, jak również w poziomie i w pionie wyśrodkowanie tekstu z odpowiednią <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W powyższych przykładach kodu są przeznaczone do użytku z formularzy systemu Windows, a potrzebują <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: rysowanie tekstu za pomocą GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Instrukcje: tworzenie rodzin czcionek i czcionek](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)
