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
ms.workload: dotnet
ms.openlocfilehash: 7fc65c9342cc86d4ceebd65e91c05cc1bea464e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Jak utworzyć efekt najazdu przy użyciu zdarzenia
W tym przykładzie pokazano, jak zmiana koloru elementu jako wskaźnik myszy uzyskuje i opuszcza obszar zajęty przez element.  
  
 W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oraz plik CodeBehind.  
  
> [!NOTE]
>  W tym przykładzie pokazano, jak używać zdarzeń, ale zalecany sposób, aby osiągnąć ten sam efekt jest użycie <xref:System.Windows.Trigger> w stylu. Aby uzyskać więcej informacji, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] tworzy interfejs użytkownika, który składa się z <xref:System.Windows.Controls.Border> wokół <xref:System.Windows.Controls.TextBlock>i dołącza <xref:System.Windows.Input.Mouse.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave> procedury obsługi zdarzeń do <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Poniższy kod za tworzy <xref:System.Windows.UIElement.MouseEnter> i <xref:System.Windows.UIElement.MouseLeave> procedury obsługi zdarzeń.  Gdy wskaźnik myszy zostanie umieszczony <xref:System.Windows.Controls.Border>, tło <xref:System.Windows.Controls.Border> zostanie zmieniona na czerwony.  Gdy wskaźnik myszy opuści <xref:System.Windows.Controls.Border>, tło <xref:System.Windows.Controls.Border> zmieniony na biały.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
