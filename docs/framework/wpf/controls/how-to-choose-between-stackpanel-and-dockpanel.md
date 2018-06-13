---
title: Jak wybrać pomiędzy StackPanel i DockPanel
ms.date: 03/30/2017
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
ms.openlocfilehash: c9bfb8d29051a9cfa61d3fcb93b8bb9a68d14e00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551937"
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
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
