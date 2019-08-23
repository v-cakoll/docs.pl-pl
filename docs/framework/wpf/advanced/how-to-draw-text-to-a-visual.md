---
title: 'Instrukcje: Rysowanie tekstu w wizualizacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: bd760a06150098d0fff17dbdce95b55a0e5fe713
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963847"
---
# <a name="how-to-draw-text-to-a-visual"></a>Instrukcje: Rysowanie tekstu w wizualizacji
Poniższy przykład pokazuje, jak narysować tekst w <xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.Media.DrawingContext> obiekcie. Kontekst rysowania jest zwracany przez wywołanie <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metody <xref:System.Windows.Media.DrawingVisual> obiektu. Możesz narysować grafikę i tekst w kontekście rysowania.  
  
 Aby narysować tekst w kontekście rysowania, użyj <xref:System.Windows.Media.DrawingContext.DrawText%2A> metody <xref:System.Windows.Media.DrawingContext> obiektu. Po zakończeniu rysowania zawartości w kontekście rysowania Wywołaj <xref:System.Windows.Media.DrawingContext.Close%2A> metodę, aby zamknąć kontekst rysowania i zachować zawartość.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> Aby uzyskać kompletny przykład kodu, z którego został wyodrębniony poprzedni przykład kodu, zobacz [test trafień za pomocą przykładu DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).
