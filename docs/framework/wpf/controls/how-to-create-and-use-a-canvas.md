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
ms.openlocfilehash: 33b98024699a88f56d27b7e5ab8d5216c906e7ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001003"
---
# <a name="how-to-create-and-use-a-canvas"></a>Instrukcje: Tworzenie i używanie kanwy
W tym przykładzie przedstawiono sposób tworzenia i używania wystąpienia <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jawnie umieszcza dwa <xref:System.Windows.Controls.TextBlock> elementy przy użyciu <xref:System.Windows.Controls.Canvas.SetTop%2A> i <xref:System.Windows.Controls.Canvas.SetLeft%2A> metody <xref:System.Windows.Controls.Canvas>. Przykład przypisuje także <xref:System.Windows.Controls.Control.Background%2A> kolor `LightSteelBlue` do <xref:System.Windows.Controls.Canvas>.  
  
> [!NOTE]
>  Kiedy używasz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pozycji <xref:System.Windows.Controls.TextBlock> elementów, użyj <xref:System.Windows.Controls.Canvas.Top%2A> i <xref:System.Windows.Controls.Canvas.Left%2A> właściwości.  
  
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
