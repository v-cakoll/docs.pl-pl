---
title: 'Porady: rysowanie linii z zakończeniem linii'
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
ms.openlocfilehash: be492f2317d4677776cc9f89f546c935d271019b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-line-with-line-caps"></a>Porady: rysowanie linii z zakończeniem linii
Może wykonywać Rysowanie początek lub koniec wiersza w jednym z kilku kształtów o nazwie wielkości graniczne linii. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] obsługuje kilka wielkości graniczne linii, takich jak round, kwadratowe romb i strzałki.  
  
## <a name="example"></a>Przykład  
 Można określić wielkości graniczne linii do początku wiersza (start cap), na koniec wiersza (zakończenie) lub łączniki linii kreskowanej (dash cap).  
  
 Poniższy przykład rysuje linię za pomocą strzałki w jeden element end i okrągłe zakończenie na drugim końcu. Na ilustracji przedstawiono wynikowego wiersza:  
  
 ![Pióra](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Tworzenie formularza systemu Windows i obsługiwać formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń. Wklej przykładowy kod do <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń przekazywanie `e` jako <xref:System.Windows.Forms.PaintEventArgs>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
