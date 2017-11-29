---
title: "Jak rozdzielić przestrzeń przy użyciu elementu DockPanel"
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
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 056aeaf1dfb7db420ce5359849a9a409dcd3fe13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="1644d-102">Jak rozdzielić przestrzeń przy użyciu elementu DockPanel</span><span class="sxs-lookup"><span data-stu-id="1644d-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="1644d-103">Poniższy przykład tworzy prosty [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework za pomocą <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="1644d-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="1644d-104"><xref:System.Windows.Controls.DockPanel> Partycje dostępne miejsce do jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1644d-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1644d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="1644d-105">Example</span></span>  
 <span data-ttu-id="1644d-106">W tym przykładzie użyto <xref:System.Windows.Controls.DockPanel.Dock%2A> właściwość, która jest dołączona właściwość, aby dock dwie identyczne <xref:System.Windows.Controls.Border> elementy w <xref:System.Windows.Controls.Dock.Top> miejsca podzielonym na partycje.</span><span class="sxs-lookup"><span data-stu-id="1644d-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="1644d-107">W trzecim <xref:System.Windows.Controls.Border> element jest zadokowany do <xref:System.Windows.Controls.Dock.Left>, przy czym jego szerokość ustawioną 200 pikseli.</span><span class="sxs-lookup"><span data-stu-id="1644d-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="1644d-108">Czwarty <xref:System.Windows.Controls.Border> jest zadokowana <xref:System.Windows.Controls.Dock.Bottom> ekranu.</span><span class="sxs-lookup"><span data-stu-id="1644d-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="1644d-109">Ostatni <xref:System.Windows.Controls.Border> elementu automatycznie wypełnia pozostałe miejsce.</span><span class="sxs-lookup"><span data-stu-id="1644d-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  <span data-ttu-id="1644d-110">Domyślnie ostatni element podrzędny elementu <xref:System.Windows.Controls.DockPanel> element wypełnia pozostałe nieprzydzielone miejsce.</span><span class="sxs-lookup"><span data-stu-id="1644d-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="1644d-111">Jeśli nie chcesz, aby ten problem, ustaw `LastChildFill="False"`.</span><span class="sxs-lookup"><span data-stu-id="1644d-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="1644d-112">Skompilowana aplikacja zwraca nowy interfejs użytkownika, który wygląda następująco.</span><span class="sxs-lookup"><span data-stu-id="1644d-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="1644d-113">![Typowy scenariusz DockPanel. ] (../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="1644d-113">![A typical DockPanel scenario.](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1644d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1644d-114">See Also</span></span>  
 <xref:System.Windows.Controls.DockPanel>  
 [<span data-ttu-id="1644d-115">Omówienie paneli</span><span class="sxs-lookup"><span data-stu-id="1644d-115">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
