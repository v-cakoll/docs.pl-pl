---
title: 'Porady: rysowanie linii w formularzu systemu Windows'
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
ms.openlocfilehash: da83699b1f7a3c2e6c781040ca0be7ec2c9a6df0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523345"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a>Porady: rysowanie linii w formularzu systemu Windows
W tym przykładzie rysuje linię w formularzu. Zazwyczaj podczas rysowania na formularzu, należy obsługiwać formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń i wykonywać Rysowanie za pomocą <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwość <xref:System.Windows.Forms.PaintEventArgs>, jak pokazano w tym przykładzie  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Zawsze należy wywołać <xref:System.IDisposable.Dispose%2A> na wszystkie obiekty używające zasobów systemowych, takich jak <xref:System.Drawing.Pen> obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Graphics.DrawLine%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [Wprowadzenie do programowania grafiki](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
