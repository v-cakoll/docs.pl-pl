---
title: 'Porady: zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: 6e11e364af5dc361a24cdd88d72432d6ba4d4058
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>Porady: zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek
Podwójne buforowanie używa bufora pamięci rozwiązywania problemów migotania skojarzone z wielu operacji malowania. Po włączeniu podwójnego buforowania wszystkie operacje paint najpierw są renderowane w buforze pamięci zamiast powierzchni rysowania na ekranie. Po ukończeniu wszystkich działań programu paint, bufora pamięci jest kopiowana bezpośrednio na powierzchni rysowania skojarzonych z nim. Grafika tylko jedna operacja jest wykonywana na ekranie, migotanie obrazu skojarzonego z operacjami malowania złożonego wyeliminowania. W przypadku większości aplikacji domyślne podwójnego buforowania dostarczonych przez [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zapewni najlepsze wyniki. Standardowe formanty formularzy systemu Windows są dwa razy buforowana domyślnie. Można włączyć domyślny podwójnego buforowania w formularzach i utworzone formantów na dwa sposoby. Można albo zestaw <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true`, lub możesz wywołać <xref:System.Windows.Forms.Control.SetStyle%2A> metodę, aby ustawić <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flaga `true`. Obie metody włączy domyślne podwójnego buforowania formularza lub kontrolki i podaj renderowania pozbawione migotania grafiki. Wywoływanie <xref:System.Windows.Forms.Control.SetStyle%2A> metody jest zalecane tylko w przypadku kontrolek niestandardowych, dla których napisano kod renderowania.  
  
 W bardziej zaawansowanych podwójnego buforowania, takich scenariuszach animacji lub pamięci Zaawansowane zarządzanie można zaimplementować własne podwójnego buforowania logiki. Aby uzyskać więcej informacji, zobacz [porady: ręczne zarządzanie buforowana grafika](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
### <a name="to-reduce-flicker"></a>Aby zmniejszyć migotania  
  
-   Ustaw <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- lub -  
  
-   Wywołanie <xref:System.Windows.Forms.Control.SetStyle%2A> metodę, aby ustawić <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flaga `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>  
 <xref:System.Windows.Forms.Control.SetStyle%2A>  
 [Podwójnie buforowana grafika](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
