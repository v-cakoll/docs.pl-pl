---
title: 'Instrukcje: Wyrównywanie narysowanego tekstu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
ms.openlocfilehash: 1cd6566e5eb5b60128206458c6e82b8eecf5492e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632377"
---
# <a name="how-to-align-drawn-text"></a>Instrukcje: Wyrównywanie narysowanego tekstu
Podczas wykonywania niestandardowego rysowania często warto Centrum narysowanego tekstu na formularz lub formant. Możesz łatwo wyrównać narysowany tekst <xref:System.Drawing.Graphics.DrawString%2A> lub <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metod, tworząc odpowiedni obiekt formatowania i ustawienie flagi w odpowiednim formacie.  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a>Aby narysować wyśrodkowany tekst z użyciem interfejsu GDI + (sznurkiem)  
  
1.  Użyj <xref:System.Drawing.StringFormat> z odpowiednią <xref:System.Drawing.Graphics.DrawString%2A> metodę, aby określić tekst wyśrodkowany.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a>Aby narysować wyśrodkowany tekst z użyciem interfejsu GDI (DrawText)  
  
1.  Użyj <xref:System.Windows.Forms.TextFormatFlags> wyliczenie dla zawijania, a także w pionie i poziomie wyśrodkowanie tekstu z odpowiednią <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W powyższych przykładach kodu są skonstruowane do użycia za pomocą interfejsu Windows Forms i wymagają one <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Rysowanie tekstu za pomocą GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
- [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
- [Instrukcje: Tworzenie rodzin czcionek i czcionek](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)
