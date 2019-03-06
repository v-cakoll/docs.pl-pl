---
title: 'Instrukcje: Utwórz i używaj kanwę'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: 13ed32195621350284530da78544e026ed341658
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360384"
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="a8541-102">Instrukcje: Utwórz i używaj kanwę</span><span class="sxs-lookup"><span data-stu-id="a8541-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="a8541-103">W tym przykładzie przedstawiono sposób tworzenia i używania wystąpienia <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="a8541-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8541-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8541-104">Example</span></span>  
 <span data-ttu-id="a8541-105">Poniższy przykład jawnie umieszcza dwa <xref:System.Windows.Controls.TextBlock> elementy przy użyciu <xref:System.Windows.Controls.Canvas.SetTop%2A> i <xref:System.Windows.Controls.Canvas.SetLeft%2A> metody <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="a8541-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="a8541-106">Przykład przypisuje także <xref:System.Windows.Controls.Control.Background%2A> kolor `LightSteelBlue` do <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="a8541-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8541-107">Kiedy używasz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pozycji <xref:System.Windows.Controls.TextBlock> elementów, użyj <xref:System.Windows.Controls.Canvas.Top%2A> i <xref:System.Windows.Controls.Canvas.Left%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8541-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a8541-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8541-108">See also</span></span>
- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [<span data-ttu-id="a8541-109">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="a8541-109">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="a8541-110">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="a8541-110">How-to Topics</span></span>](canvas-how-to-topics.md)
