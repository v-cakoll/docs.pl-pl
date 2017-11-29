---
title: "Jak utworzyć i używać kanwę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8925b9b6cd6cea1a29592f591f9c1c89d32d49e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="028cd-102">Jak utworzyć i używać kanwę</span><span class="sxs-lookup"><span data-stu-id="028cd-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="028cd-103">W tym przykładzie przedstawiono sposób tworzenia i używania wystąpienia <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="028cd-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="028cd-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="028cd-104">Example</span></span>  
 <span data-ttu-id="028cd-105">Poniższy przykład jawnie umieszcza dwa <xref:System.Windows.Controls.TextBlock> elementów za pomocą <xref:System.Windows.Controls.Canvas.SetTop%2A> i <xref:System.Windows.Controls.Canvas.SetLeft%2A> metody <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="028cd-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="028cd-106">Przykład przypisuje także <xref:System.Windows.Controls.Control.Background%2A> kolor `LightSteelBlue` do <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="028cd-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="028cd-107">Jeśli używasz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pozycji <xref:System.Windows.Controls.TextBlock> elementy, użyj <xref:System.Windows.Controls.Canvas.Top%2A> i <xref:System.Windows.Controls.Canvas.Left%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="028cd-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="028cd-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="028cd-108">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.TextBlock>  
 <xref:System.Windows.Controls.Canvas.SetTop%2A>  
 <xref:System.Windows.Controls.Canvas.SetLeft%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 [<span data-ttu-id="028cd-109">Omówienie paneli</span><span class="sxs-lookup"><span data-stu-id="028cd-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="028cd-110">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="028cd-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)
