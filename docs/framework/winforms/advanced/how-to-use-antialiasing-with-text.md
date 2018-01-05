---
title: 'Porady: stosowanie antyaliasingu do tekstu'
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
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edd31ec5b9d94ac1791fb0f2a73522fdf4178627
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-antialiasing-with-text"></a>Porady: stosowanie antyaliasingu do tekstu
*Antyaliasing* odwołuje się do wygładzanie nieregularne krawędzi narysowanego grafiki i tekstu, aby zwiększyć ich wyglądu i czytelności. Z zarządzanego [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klas, umożliwiający renderowanie tekstu antyaliasowany wysokiej jakości, jak również niższe jakość tekstu. Zazwyczaj wyższej jakości renderowania potrzebuje więcej czasu przetwarzania niż niższa jakość renderowania. Aby ustawić poziom jakość tekstu, ustaw <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwość <xref:System.Drawing.Graphics> do jednego z elementów <xref:System.Drawing.Text.TextRenderingHint> — wyliczenie  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod rysuje tekst z dwóch różnych jakości ustawień.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe cod przykładowy kod.  
  
 ![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
