---
title: 'Instrukcje: Wybierz pomiędzy StackPanel i DockPanel'
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
ms.openlocfilehash: 458ba2fe23ecde28b3eb15400e7a9fa49c4cca68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622536"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a><span data-ttu-id="9ad11-102">Instrukcje: Wybierz pomiędzy StackPanel i DockPanel</span><span class="sxs-lookup"><span data-stu-id="9ad11-102">How to: Choose Between StackPanel and DockPanel</span></span>
<span data-ttu-id="9ad11-103">Ten przykład pokazuje, jak wybrać między za pomocą <xref:System.Windows.Controls.StackPanel> lub <xref:System.Windows.Controls.DockPanel> kiedy stos zawartość <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="9ad11-103">This example shows how to choose between using a <xref:System.Windows.Controls.StackPanel> or a <xref:System.Windows.Controls.DockPanel> when you stack content in a <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ad11-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ad11-104">Example</span></span>  
 <span data-ttu-id="9ad11-105">Chociaż można używać <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.Controls.StackPanel> na stosie elementów podrzędnych, dwie kontrolki nie zawsze działają tak samo.</span><span class="sxs-lookup"><span data-stu-id="9ad11-105">Although you can use either <xref:System.Windows.Controls.DockPanel> or <xref:System.Windows.Controls.StackPanel> to stack child elements, the two controls do not always produce the same results.</span></span> <span data-ttu-id="9ad11-106">Na przykład kolejność umieszczenie elementów podrzędnych może mieć wpływ na rozmiar elementów podrzędnych na <xref:System.Windows.Controls.DockPanel> , ale nie <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="9ad11-106">For example, the order that you place child elements can affect the size of child elements in a <xref:System.Windows.Controls.DockPanel> but not in a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="9ad11-107">Takie zachowanie różnych <xref:System.Windows.Controls.StackPanel> miary w kierunku układania na <xref:System.Double>.<xref:System.Double.PositiveInfinity>; jednak <xref:System.Windows.Controls.DockPanel> mierzy tylko dostępny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="9ad11-107">This different behavior occurs because <xref:System.Windows.Controls.StackPanel> measures in the direction of stacking at <xref:System.Double>.<xref:System.Double.PositiveInfinity>; however, <xref:System.Windows.Controls.DockPanel> measures only the available size.</span></span>  
  
 <span data-ttu-id="9ad11-108">W poniższym przykładzie pokazano to główną różnicą między <xref:System.Windows.Controls.DockPanel> i <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="9ad11-108">The following example demonstrates this key difference between <xref:System.Windows.Controls.DockPanel> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9ad11-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ad11-109">See also</span></span>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="9ad11-110">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="9ad11-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
