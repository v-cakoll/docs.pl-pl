---
title: 'Instrukcje: Rysowanie linii z zakończeniem linii'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: 34abfc86e980a24ebb835cfd88d2522f8372c68d
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506023"
---
# <a name="how-to-draw-a-line-with-line-caps"></a>Instrukcje: Rysowanie linii z zakończeniem linii
Możesz narysować początek lub koniec wiersza w jednym z kilku kształtów wywoływana z zakończeniem linii. GDI + obsługuje kilka zakończeniem linii, takich jak round, kwadratowy, romb i grotu strzałki.  
  
## <a name="example"></a>Przykład  
 Możesz określić limity wiersz na początku wiersza (start cap), na koniec wiersza (zakończenie) lub łączniki linii kreskowanej (kreska cap).  
  
 Poniższy przykład rysuje za pomocą strzałki na jednym końcu i okrągłe zakończenie na końcu. Na ilustracji przedstawiono wynikowego wiersza:  
  
 ![Ilustracją, na której wyświetlany jest wiersz round limit.](./media/how-to-draw-a-line-with-line-caps/line-cap-arrowhead-example.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Tworzenie formularza Windows i obsłużyć formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń. Wklej przykładowy kod do <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń, przekazując `e` jako <xref:System.Windows.Forms.PaintEventArgs>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
