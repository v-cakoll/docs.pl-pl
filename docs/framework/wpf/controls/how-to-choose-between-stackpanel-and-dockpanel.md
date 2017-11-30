---
title: "Jak wybrać pomiędzy StackPanel i DockPanel"
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
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 40d99e090a0599c98560e4102d18d35ee7174259
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>Jak wybrać pomiędzy StackPanel i DockPanel
W tym przykładzie pokazano, jak przy użyciu <xref:System.Windows.Controls.StackPanel> lub <xref:System.Windows.Controls.DockPanel> po stosu zawartość <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Przykład  
 Chociaż można używać <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.Controls.StackPanel> stos elementy podrzędne, dwóch formantów nie zawsze utworzyć takie same wyniki. Na przykład kolejności umieszczenie elementów podrzędnych może mieć wpływ na rozmiar elementów podrzędnych w <xref:System.Windows.Controls.DockPanel> , ale nie <xref:System.Windows.Controls.StackPanel>. Takie zachowanie różnych <xref:System.Windows.Controls.StackPanel> środki w kierunku układania w <xref:System.Double>.<xref:System.Double.PositiveInfinity>; jednak <xref:System.Windows.Controls.DockPanel> mierzy tylko dostępny rozmiar.  
  
 W poniższym przykładzie pokazano to Najważniejsza różnica między <xref:System.Windows.Controls.DockPanel> i <xref:System.Windows.Controls.StackPanel>.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.DockPanel>  
 [Omówienie paneli](../../../../docs/framework/wpf/controls/panels-overview.md)
