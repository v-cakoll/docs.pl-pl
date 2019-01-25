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
ms.openlocfilehash: a0d4d92d7201c4ac09eadd11d8f2e38a3c80c287
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713142"
---
# <a name="how-to-draw-a-line-with-line-caps"></a>Instrukcje: Rysowanie linii z zakończeniem linii
Możesz narysować początek lub koniec wiersza w jednym z kilku kształtów wywoływana z zakończeniem linii. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] obsługuje kilka zakończeniem linii, takich jak round, kwadratowy, romb i grotu strzałki.  
  
## <a name="example"></a>Przykład  
 Możesz określić limity wiersz na początku wiersza (start cap), na koniec wiersza (zakończenie) lub łączniki linii kreskowanej (kreska cap).  
  
 Poniższy przykład rysuje za pomocą strzałki na jednym końcu i okrągłe zakończenie na końcu. Na ilustracji przedstawiono wynikowego wiersza:  
  
 ![Pióra](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Tworzenie formularza Windows i obsłużyć formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń. Wklej przykładowy kod do <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń, przekazując `e` jako <xref:System.Windows.Forms.PaintEventArgs>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
