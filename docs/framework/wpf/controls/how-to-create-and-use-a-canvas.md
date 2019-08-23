---
title: 'Instrukcje: Tworzenie i używanie kanwy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: edef660b2da2f09e0a6edbc0a87f0d1f26eb03da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964219"
---
# <a name="how-to-create-and-use-a-canvas"></a>Instrukcje: Tworzenie i używanie kanwy
Ten przykład pokazuje, jak utworzyć i użyć wystąpienia <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład <xref:System.Windows.Controls.TextBlock> jawnie umieszcza dwa elementy przy <xref:System.Windows.Controls.Canvas.SetTop%2A> użyciu metod <xref:System.Windows.Controls.Canvas>i <xref:System.Windows.Controls.Canvas.SetLeft%2A> . Przykład przypisuje <xref:System.Windows.Controls.Control.Background%2A> także `LightSteelBlue` kolor do <xref:System.Windows.Controls.Canvas>.  
  
> [!NOTE]
> Gdy używasz <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.Canvas.Top%2A> do pozycjonowania elementów, użyj właściwości i <xref:System.Windows.Controls.Canvas.Left%2A>. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [Panele — omówienie](panels-overview.md)
- [Tematy z instrukcjami](canvas-how-to-topics.md)
