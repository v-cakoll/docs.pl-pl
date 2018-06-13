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
ms.openlocfilehash: 4fbb0931ee7d17d4b3264de512353dc75caf070d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543566"
---
# <a name="how-to-draw-text-to-a-visual"></a>Jak rysować tekst do Visual
Poniższy przykład przedstawia sposób Rysowanie tekstu do <xref:System.Windows.Media.DrawingVisual> przy użyciu <xref:System.Windows.Media.DrawingContext> obiektu. Rysowanie kontekstu jest zwracany przez wywołanie metody <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metody <xref:System.Windows.Media.DrawingVisual> obiektu. Może wykonywać rysowanie grafiki i tekst w kontekście rysowania.  
  
 Rysowanie tekstu w kontekście rysunku, użyj <xref:System.Windows.Media.DrawingContext.DrawText%2A> metody <xref:System.Windows.Media.DrawingContext> obiektu. Po zakończeniu rysowania zawartości do rysowania kontekstu, wywołaj <xref:System.Windows.Media.DrawingContext.Close%2A> metodę, aby zamknąć kontekst rysowania i utrwala zawartości.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  Dla przykładu kompletny kod, z którego został wyodrębniony w poprzednim przykładzie kodu, zobacz [trafień przy użyciu DrawingVisuals próbki](http://go.microsoft.com/fwlink/?LinkID=159994).
