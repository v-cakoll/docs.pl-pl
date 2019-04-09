---
title: 'Instrukcje: Rozdzielanie miejsca przy użyciu elementu DockPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
ms.openlocfilehash: ab51270644bf370944ebc933c765b40c528681c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158889"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="5e33b-102">Instrukcje: Rozdzielanie miejsca przy użyciu elementu DockPanel</span><span class="sxs-lookup"><span data-stu-id="5e33b-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="5e33b-103">Poniższy przykład tworzy prostą [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] przy użyciu framework <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="5e33b-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="5e33b-104"><xref:System.Windows.Controls.DockPanel> Partycje dostępnego miejsca na jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="5e33b-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e33b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e33b-105">Example</span></span>  
 <span data-ttu-id="5e33b-106">W tym przykładzie użyto <xref:System.Windows.Controls.DockPanel.Dock%2A> właściwość, która jest dołączona właściwość, aby zadokować dwa identyczne <xref:System.Windows.Controls.Border> elementy w <xref:System.Windows.Controls.Dock.Top> miejsca podzielonym na partycje.</span><span class="sxs-lookup"><span data-stu-id="5e33b-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="5e33b-107">Trzeci <xref:System.Windows.Controls.Border> element jest zadokowany do <xref:System.Windows.Controls.Dock.Left>, za pomocą jego szerokość równa 200 pikseli.</span><span class="sxs-lookup"><span data-stu-id="5e33b-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="5e33b-108">Czwarty <xref:System.Windows.Controls.Border> jest zadokowany do <xref:System.Windows.Controls.Dock.Bottom> ekranu.</span><span class="sxs-lookup"><span data-stu-id="5e33b-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="5e33b-109">Ostatni <xref:System.Windows.Controls.Border> elementu automatycznie wypełnia pozostałe miejsce.</span><span class="sxs-lookup"><span data-stu-id="5e33b-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  <span data-ttu-id="5e33b-110">Domyślnie ostatni element podrzędny elementu <xref:System.Windows.Controls.DockPanel> element wypełnia pozostałe nieprzydzielone miejsce.</span><span class="sxs-lookup"><span data-stu-id="5e33b-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="5e33b-111">Jeśli nie chcesz tego zachowania, ustaw `LastChildFill="False"`.</span><span class="sxs-lookup"><span data-stu-id="5e33b-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="5e33b-112">Skompilowaną aplikację daje nowy interfejs użytkownika, który wygląda w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5e33b-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="5e33b-113">![Typowy scenariusz DockPanel. ](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="5e33b-113">![A typical DockPanel scenario.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e33b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e33b-114">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="5e33b-115">Przegląd Panele</span><span class="sxs-lookup"><span data-stu-id="5e33b-115">Panels Overview</span></span>](panels-overview.md)
