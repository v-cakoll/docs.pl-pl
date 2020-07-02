---
title: 'Porady: rysowanie linii w formularzu systemu Windows'
description: Dowiedz się, jak narysować linię w formularzu przez obsługę zdarzenia Paint, a następnie wykonać rysowanie przy użyciu właściwości Graphics PaintEventArgs.
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
ms.openlocfilehash: c8e92dc265c63413275561d0e2e3aa820eaec724
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621629"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a>Porady: rysowanie linii w formularzu systemu Windows
Ten przykład rysuje linię w formularzu. Zwykle podczas rysowania na formularzu jest obsługiwane <xref:System.Windows.Forms.Control.Paint> zdarzenie formularza i wykonywanie rysunku przy użyciu <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwości <xref:System.Windows.Forms.PaintEventArgs> , jak pokazano w tym przykładzie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e` , który jest parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Należy zawsze wywoływać <xref:System.IDisposable.Dispose%2A> wszystkie obiekty, które zużywają zasoby systemowe, takie jak <xref:System.Drawing.Pen> obiekty.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md)
- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
