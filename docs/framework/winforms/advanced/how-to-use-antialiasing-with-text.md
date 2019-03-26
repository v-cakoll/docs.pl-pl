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
ms.openlocfilehash: ffd8600c730baca54a9cbd098dd2f37ce5ecb728
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464726"
---
# <a name="how-to-use-antialiasing-with-text"></a>Instrukcje: Stosowanie antyaliasingu do tekstu
*Antyaliasing* odwołuje się do wygładzania nierówne krawędzie rysowane grafiki i tekstu w celu zwiększenia ich wyglądu i czytelności. Za pomocą zarządzanych [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klas, umożliwiający renderowanie tekstu antialiased wysokiej jakości, a także niższa jakość tekstu. Zazwyczaj wyższej jakości renderowania jest bardziej czasochłonne przetwarzania niż niższa jakość renderowania. Aby ustawić poziom jakości tekstu, ustaw <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwość <xref:System.Drawing.Graphics> do jednego z elementów <xref:System.Drawing.Text.TextRenderingHint> wyliczenia  
  
## <a name="example"></a>Przykład  
 Poniższy kod rysuje tekst za pomocą dwóch ustawień inną jakość.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 Na poniższej ilustracji przedstawiono dane wyjściowe przykładowego kodu:  
  
 ![Zrzut ekranu pokazujący tekstu za pomocą dwóch ustawień inną jakość.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie czcionek i tekstu](using-fonts-and-text.md)
