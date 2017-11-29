---
title: "Jak utworzyć efekt najazdu przy użyciu zdarzenia"
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
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c82d993c31174419793319da74ffa38d122ef203
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="e511d-102">Jak utworzyć efekt najazdu przy użyciu zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e511d-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="e511d-103">W tym przykładzie pokazano, jak zmiana koloru elementu jako wskaźnik myszy uzyskuje i opuszcza obszar zajęty przez element.</span><span class="sxs-lookup"><span data-stu-id="e511d-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="e511d-104">W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oraz plik CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="e511d-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e511d-105">W tym przykładzie pokazano, jak używać zdarzeń, ale zalecany sposób, aby osiągnąć ten sam efekt jest użycie <xref:System.Windows.Trigger> w stylu.</span><span class="sxs-lookup"><span data-stu-id="e511d-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="e511d-106">Aby uzyskać więcej informacji, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="e511d-106">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e511d-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e511d-107">Example</span></span>  
 <span data-ttu-id="e511d-108">Następujące [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.Border> wokół <xref:System.Windows.Controls.TextBlock>i dołącza <xref:System.Windows.Input.Mouse.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave> procedury obsługi zdarzeń do <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="e511d-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="e511d-109">Poniższy kod za tworzy <xref:System.Windows.UIElement.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave> procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e511d-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="e511d-110">Gdy wskaźnik myszy zostanie umieszczony <xref:System.Windows.Controls.Border>, tło <xref:System.Windows.Controls.Border> zostanie zmieniona na czerwony.</span><span class="sxs-lookup"><span data-stu-id="e511d-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="e511d-111">Gdy wskaźnik myszy opuści <xref:System.Windows.Controls.Border>, tło <xref:System.Windows.Controls.Border> zmieniony na biały.</span><span class="sxs-lookup"><span data-stu-id="e511d-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
