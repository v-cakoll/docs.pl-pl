---
title: 'Porady: zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek'
description: Dowiedz się, jak zmniejszyć migotanie grafiki przy użyciu podwójnego buforowania dla Windows Forms i użyć kontrolek do rozwiązywania problemów z migotaniem związanych z operacjami malowania.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: f7c0425729f8a1a780124621788a1c49e06e0c4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618132"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>Porady: zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek
Podwójne buforowanie używa bufora pamięci do rozwiązywania problemów z migotaniem skojarzonych z wieloma operacjami malowania. Po włączeniu podwójnego buforowania wszystkie operacje programu Paint są najpierw renderowane do bufora pamięci, a nie na powierzchni rysowania na ekranie. Po zakończeniu wszystkich operacji programu Paint bufor pamięci jest kopiowany bezpośrednio do powierzchni rysunku, z którą jest skojarzona. Ponieważ na ekranie jest wykonywana tylko jedna operacja grafiki, migotanie obrazu skojarzone z złożonymi operacjami rysowania jest eliminowane. W przypadku większości aplikacji domyślne buforowanie podwójne zapewniane przez .NET Framework zapewni najlepsze wyniki. Standardowe formanty Windows Forms są domyślnie buforowane. Domyślne buforowanie podwójne można włączyć w formularzach i w kontrolkach utworzonych na dwa sposoby. Można ustawić <xref:System.Windows.Forms.Control.DoubleBuffered%2A> Właściwość na `true` lub wywołać <xref:System.Windows.Forms.Control.SetStyle%2A> metodę w celu ustawienia <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flagi `true` . Obie metody spowodują włączenie domyślnego podwójnego buforowania dla formularza lub kontrolki i udostępnienie renderowania grafiki bez migotania. Wywołanie <xref:System.Windows.Forms.Control.SetStyle%2A> metody jest zalecane tylko w przypadku kontrolek niestandardowych, dla których zapisano cały kod renderowania.  
  
 W przypadku bardziej zaawansowanych scenariuszy podwójnego buforowania, takich jak animacja lub zaawansowane zarządzanie pamięcią, można zaimplementować własną logikę podwójnego buforowania. Aby uzyskać więcej informacji, zobacz [jak: ręczne zarządzanie buforowaną grafiką](how-to-manually-manage-buffered-graphics.md).  
  
### <a name="to-reduce-flicker"></a>Aby zmniejszyć migotanie  
  
- Ustaw <xref:System.Windows.Forms.Control.DoubleBuffered%2A> Właściwość na wartość `true` .  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \-oraz  
  
- Wywołaj <xref:System.Windows.Forms.Control.SetStyle%2A> metodę, aby ustawić <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flagę `true` .  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [Podwójnie buforowana grafika](double-buffered-graphics.md)
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
