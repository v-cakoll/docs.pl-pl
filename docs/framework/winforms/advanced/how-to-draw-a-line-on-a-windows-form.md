---
title: 'Instrukcje: Rysuj linię w formularzu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
ms.openlocfilehash: 4274072b55c79cfe88e906d1401d275b414ebe97
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586751"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a>Instrukcje: Rysuj linię w formularzu Windows
W tym przykładzie rysuje linię w formularzu. Zwykle, kiedy rysujesz w formularzu można obsłużyć formularza <xref:System.Windows.Forms.Control.Paint> zdarzenia i wykonywać Rysowanie za pomocą <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwość <xref:System.Windows.Forms.PaintEventArgs>, jak pokazano w poniższym przykładzie  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Zawsze powinna wywołać <xref:System.IDisposable.Dispose%2A> na wszystkie obiekty, których wartość użycia zasobów systemowych, takich jak <xref:System.Drawing.Pen> obiektów.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Wprowadzenie do programowania grafiki](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
