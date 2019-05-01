---
title: 'Instrukcje: Rysowanie tekstu w formularzu systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: ae7749deedba03f0a63bb74099d071d5da4fe27e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004084"
---
# <a name="how-to-draw-text-on-a-windows-form"></a>Instrukcje: Rysowanie tekstu w formularzu systemu Windows
Poniższy przykład kodu pokazuje sposób użycia <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> Rysowanie tekstu w formularzu. Alternatywnie, można użyć <xref:System.Windows.Forms.TextRenderer> dla Rysowanie tekstu w formularzu. Aby uzyskać więcej informacji, zobacz [jak: Rysowanie tekstu za pomocą GDI](how-to-draw-text-with-gdi.md).  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Nie można wywołać <xref:System.Drawing.Graphics.DrawString%2A> method in Class metoda <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń. Rysowane zawartość nie zostanie narysowany ponownie, gdy formularz jest zmiany rozmiaru lub zostanie przesłonięty przez inny formularz. Aby automatycznie odświeżenia zawartości, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Czcionka Arial nie jest zainstalowany.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Windows.Forms.TextRenderer.DrawText%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.TextFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md)
- [Instrukcje: Rysowanie tekstu za pomocą GDI](how-to-draw-text-with-gdi.md)
