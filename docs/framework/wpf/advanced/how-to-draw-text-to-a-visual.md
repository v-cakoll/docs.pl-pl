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
ms.openlocfilehash: 1ea31540ad59ab419e209e4133bcb88640cc01fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776171"
---
# <a name="how-to-draw-text-to-a-visual"></a>Instrukcje: Rysowanie tekstu w wizualizacji
Poniższy przykład pokazuje, jak rysować tekst do <xref:System.Windows.Media.DrawingVisual> przy użyciu <xref:System.Windows.Media.DrawingContext> obiektu. Rysowanie kontekstu jest zwracany przez wywołanie metody <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metody <xref:System.Windows.Media.DrawingVisual> obiektu. W kontekście rysunku, można narysować grafiki i tekstu.  
  
 Aby rysować tekst do rysowania kontekstu, użyj <xref:System.Windows.Media.DrawingContext.DrawText%2A> metody <xref:System.Windows.Media.DrawingContext> obiektu. Po zakończeniu rysowania zawartości do rysowania kontekstu wywołania <xref:System.Windows.Media.DrawingContext.Close%2A> metodę, aby zamknąć kontekst rysowania i zachować zawartość.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  Cały przykładowy kod z którego został wyodrębniony w poprzednim przykładzie kodu, można zobaczyć [trafień za pomocą DrawingVisuals próbkę](https://go.microsoft.com/fwlink/?LinkID=159994).
