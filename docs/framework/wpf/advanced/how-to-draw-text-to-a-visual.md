---
title: Jak rysować tekst do Visual
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
ms.openlocfilehash: 654bfadb42f053b6dcf353d4423bddf281d69478
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094556"
---
# <a name="how-to-draw-text-to-a-visual"></a>Jak rysować tekst do Visual
Poniższy przykład przedstawia sposób rysowania tekstu do <xref:System.Windows.Media.DrawingVisual> przy użyciu obiektu <xref:System.Windows.Media.DrawingContext>. Kontekst rysowania jest zwracany przez wywołanie metody <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> obiektu <xref:System.Windows.Media.DrawingVisual>. Możesz narysować grafikę i tekst w kontekście rysowania.  
  
 Aby narysować tekst w kontekście rysowania, użyj metody <xref:System.Windows.Media.DrawingContext.DrawText%2A> obiektu <xref:System.Windows.Media.DrawingContext>. Po zakończeniu rysowania zawartości w kontekście rysowania Wywołaj metodę <xref:System.Windows.Media.DrawingContext.Close%2A>, aby zamknąć kontekst rysowania i zachować zawartość.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> Aby uzyskać kompletny przykład kodu, z którego został wyodrębniony poprzedni przykład kodu, zobacz [test trafień za pomocą przykładu DrawingVisuals](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).
