---
title: 'Instrukcje: Stosowanie antyaliasingu do tekstu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: b0dc3cf5cff9cf3e163478861ec55a05427ad6ce
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718574"
---
# <a name="how-to-use-antialiasing-with-text"></a>Instrukcje: Stosowanie antyaliasingu do tekstu
*Antyaliasing* odwołuje się do wygładzania nierówne krawędzie rysowane grafiki i tekstu w celu zwiększenia ich wyglądu i czytelności. Za pomocą zarządzanych [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klas, umożliwiający renderowanie tekstu antialiased wysokiej jakości, a także niższa jakość tekstu. Zazwyczaj wyższej jakości renderowania jest bardziej czasochłonne przetwarzania niż niższa jakość renderowania. Aby ustawić poziom jakości tekstu, ustaw <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwość <xref:System.Drawing.Graphics> do jednego z elementów <xref:System.Drawing.Text.TextRenderingHint> wyliczenia  
  
## <a name="example"></a>Przykład  
 Poniższy kod rysuje tekst za pomocą dwóch ustawień inną jakość.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 Na poniższej ilustracji przedstawiono dane wyjściowe przykładowego kodu:  
  
 ![Fonts Text](./media/fontstext10.png "FontsText10")  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie czcionek i tekstu](using-fonts-and-text.md)
