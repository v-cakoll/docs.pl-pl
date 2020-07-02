---
title: 'Porady: rysowanie wypełnionego prostokąta w formularzu systemu Windows'
description: Dowiedz się, jak programowo rysować wypełniony prostokąt w formularzu systemu Windows. Poznaj również informacje na temat kompilowania kodu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621642"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a>Porady: rysowanie wypełnionego prostokąta w formularzu systemu Windows
Ten przykład rysuje wypełniony prostokąt w formularzu.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Nie można wywołać tej metody w <xref:System.Windows.Forms.Form.Load> obsłudze zdarzeń. Narysowana zawartość nie zostanie ponownie narysowana, jeśli rozmiar formularza zostanie zmieniony lub zasłonięty przez inny formularz. Aby zawartość była odświeżana automatycznie, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metodę.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Należy zawsze wywoływać <xref:System.IDisposable.Dispose%2A> wszystkie obiekty, które zużywają zasoby systemowe, takie <xref:System.Drawing.Brush> jak <xref:System.Drawing.Graphics> obiekty i.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md)
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
- [Pędzle i wypełnione kształty w GDI+](brushes-and-filled-shapes-in-gdi.md)
