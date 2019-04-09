---
title: 'Instrukcje: Zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: ef05b72b33d3f28d1811389dfae65554a1567d43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096956"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>Instrukcje: Zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek
Podwójnego buforowania używa bufora pamięci, aby rozwiązywać problemy migotania skojarzonych wiele operacji malowania. Po włączeniu podwójnego buforowania wszystkich operacji malowania najpierw są renderowane w buforze pamięci zamiast powierzchni do rysowania na ekranie. Po ukończeniu wszystkich operacji malowania bufora pamięci jest kopiowana bezpośrednio na powierzchni do rysowania skojarzone z nią. Ponieważ grafiki tylko jedna operacja jest wykonywana na ekranie, obraz migotanie skojarzone z operacjami złożonego rysowania zostanie wyeliminowany. W przypadku większości aplikacji domyślnej podwójnego buforowania podał [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] udostępni najlepsze rezultaty. Standardowych kontrolek Windows Forms są double buforowana domyślnie. Można włączyć domyślny podwójnego buforowania w formularzach i autorstwa formantów na dwa sposoby. Możesz albo zestaw <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true`, można też wywołać <xref:System.Windows.Forms.Control.SetStyle%2A> metodę, aby ustawić <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flaga `true`. Obie metody zostanie włączony, domyślne podwójnego buforowania danych formularza lub formantu i podaj renderowania pozbawionej migotania grafiki. Wywoływanie <xref:System.Windows.Forms.Control.SetStyle%2A> metoda jest zalecana tylko w przypadku kontrolek niestandardowych, dla których ma napisany cały kod renderowania.  
  
 Dla bardziej zaawansowanych podwójnego buforowania scenariuszach, na przykład animacji lub zarządzanie zaawansowanej pamięci można zaimplementować własną podwójnego buforowania logikę. Aby uzyskać więcej informacji, zobacz [jak: Ręczne zarządzanie buforowaną grafiką](how-to-manually-manage-buffered-graphics.md).  
  
### <a name="to-reduce-flicker"></a>Aby Zmniejszanie migotania  
  
-   Ustaw <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwość `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- lub —  
  
-   Wywołaj <xref:System.Windows.Forms.Control.SetStyle%2A> metodę, aby ustawić <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flaga `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [Podwójnie buforowana grafika](double-buffered-graphics.md)
- [Grafika i rysowanie w formularzach systemu Windows](graphics-and-drawing-in-windows-forms.md)
