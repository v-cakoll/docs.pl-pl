---
title: 'Porady: rysowanie pionowego tekstu w formularzu systemu Windows'
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
- cpp
f1_keywords:
- StringFormat.FormatFlags
- Graphics.DrawString
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- strings [Windows Forms], drawing vertical
- text [Windows Forms], drawing
- text [Windows Forms], vertical text
ms.assetid: 717a6131-00f6-4373-b574-9894e8317799
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76da7be50f9e12454e16e08ec4db494585fae613
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a>Porady: rysowanie pionowego tekstu w formularzu systemu Windows
Poniższy przykładowy kod przedstawia sposób Rysowanie pionowego tekstu w formularzu za pomocą <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Nie można wywołać tej metody <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń. Narysowanego zawartość nie zostanie narysowany ponownie Jeśli zmiany rozmiaru lub zostanie przesłonięty przez inny formularz formularza. Aby automatycznie odświeżenia zawartości, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Czcionka Arial nie jest zainstalowany.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Graphics.DrawString%2A>  
 <xref:System.Drawing.StringFormat.FormatFlags%2A>  
 <xref:System.Drawing.StringFormatFlags>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [Wprowadzenie do programowania grafiki](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
