---
title: 'Porady: stosowanie antyaliasingu do tekstu'
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
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182486"
---
# <a name="how-to-use-antialiasing-with-text"></a>Porady: stosowanie antyaliasingu do tekstu
*Antialiasing* odnosi się do wygładzania postrzępionych krawędzi rysowanej grafiki i tekstu, aby poprawić ich wygląd lub czytelność. Dzięki zarządzanym klasom GDI+ można renderować wysokiej jakości tekst antyaliasowany, a także tekst niższej jakości. Zazwyczaj renderowanie wyższej jakości zajmuje więcej czasu przetwarzania niż renderowanie niższej jakości. Aby ustawić poziom jakości tekstu, <xref:System.Drawing.Graphics.TextRenderingHint%2A> ustaw <xref:System.Drawing.Graphics> właściwość a na <xref:System.Drawing.Text.TextRenderingHint> jeden z elementów wyliczenia  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu rysuje tekst z dwoma różnymi ustawieniami jakości.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 Na poniższej ilustracji przedstawiono dane wyjściowe przykładowego kodu:  
  
 ![Zrzut ekranu przedstawiający tekst z dwoma różnymi ustawieniami jakości.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład kodu jest przeznaczony do użytku z <xref:System.Windows.Forms.PaintEventArgs> `e`formularzami systemu Windows <xref:System.Windows.Forms.PaintEventHandler>i wymaga , który jest parametrem .  
  
## <a name="see-also"></a>Zobacz też

- [Używanie czcionek i tekstu](using-fonts-and-text.md)
