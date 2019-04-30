---
title: 'Instrukcje: Rysowanie pionowego tekstu w formularzu systemu Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: eb00928205a318b068d49ea3f6f71c398f77bbcd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61722916"
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a>Instrukcje: Rysowanie pionowego tekstu w formularzu systemu Windows
Poniższy przykład kodu pokazuje, jak rysowanie pionowego tekstu w formularzu za pomocą <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Nie można wywołać tej metody w <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń. Rysowane zawartość nie zostanie narysowany ponownie, gdy formularz jest zmiany rozmiaru lub zostanie przesłonięty przez inny formularz. Aby automatycznie odświeżenia zawartości, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Czcionka Arial nie jest zainstalowany.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md)
- [Używanie czcionek i tekstu](using-fonts-and-text.md)
