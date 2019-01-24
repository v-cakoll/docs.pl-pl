---
title: 'Instrukcje: Pobierz lub ustaw wartość dokowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
ms.openlocfilehash: 847f8732e1807ab2541d42fe720aacbecb034154
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738511"
---
# <a name="how-to-get-or-set-a-dock-value"></a><span data-ttu-id="668da-102">Instrukcje: Pobierz lub ustaw wartość dokowania</span><span class="sxs-lookup"><span data-stu-id="668da-102">How to: Get or Set a Dock Value</span></span>
<span data-ttu-id="668da-103">Poniższy przykład pokazuje, jak przypisać <xref:System.Windows.Controls.Dock> wartość obiektu.</span><span class="sxs-lookup"><span data-stu-id="668da-103">The following example shows how to assign a <xref:System.Windows.Controls.Dock> value for an object.</span></span> <span data-ttu-id="668da-104">W przykładzie użyto <xref:System.Windows.Controls.DockPanel.GetDock%2A> i <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="668da-104">The example uses the <xref:System.Windows.Controls.DockPanel.GetDock%2A> and <xref:System.Windows.Controls.DockPanel.SetDock%2A> methods of <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="668da-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="668da-105">Example</span></span>  
 <span data-ttu-id="668da-106">Przykład tworzy wystąpienie <xref:System.Windows.Controls.TextBlock> elementu, `txt1`, a następnie przypisuje <xref:System.Windows.Controls.Dock> wartość `Top` przy użyciu <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="668da-106">The example creates an instance of the <xref:System.Windows.Controls.TextBlock> element, `txt1`, and assigns a <xref:System.Windows.Controls.Dock> value of `Top` by using the <xref:System.Windows.Controls.DockPanel.SetDock%2A> method of <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="668da-107">Następnie dołącza wartości <xref:System.Windows.Controls.Dock> właściwości <xref:System.Windows.Controls.TextBlock.Text%2A> z <xref:System.Windows.Controls.TextBlock> elementu za pomocą <xref:System.Windows.Controls.DockPanel.GetDock%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="668da-107">It then appends the value of the <xref:System.Windows.Controls.Dock> property to the <xref:System.Windows.Controls.TextBlock.Text%2A> of the <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.DockPanel.GetDock%2A> method.</span></span> <span data-ttu-id="668da-108">Ponadto w przykładzie dodano <xref:System.Windows.Controls.TextBlock> elementu nadrzędnego <xref:System.Windows.Controls.DockPanel>, `dp1`.</span><span class="sxs-lookup"><span data-stu-id="668da-108">Finally, the example adds the <xref:System.Windows.Controls.TextBlock> element to the parent <xref:System.Windows.Controls.DockPanel>, `dp1`.</span></span>  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="668da-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="668da-109">See also</span></span>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [<span data-ttu-id="668da-110">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="668da-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
