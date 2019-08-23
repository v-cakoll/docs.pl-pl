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
ms.openlocfilehash: d22a808ce3ab95e3b351408bf4cc372a335da553
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960199"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="65f39-102">Instrukcje: Rozdzielanie miejsca przy użyciu elementu DockPanel</span><span class="sxs-lookup"><span data-stu-id="65f39-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="65f39-103">Poniższy przykład tworzy prostą [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] strukturę <xref:System.Windows.Controls.DockPanel> przy użyciu elementu.</span><span class="sxs-lookup"><span data-stu-id="65f39-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="65f39-104">Dostępne <xref:System.Windows.Controls.DockPanel> są partycje do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="65f39-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65f39-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="65f39-105">Example</span></span>  
 <span data-ttu-id="65f39-106">W tym przykładzie zastosowano <xref:System.Windows.Controls.DockPanel.Dock%2A> właściwość, która jest dołączoną właściwością, aby zadokować dwa identyczne <xref:System.Windows.Controls.Dock.Top> <xref:System.Windows.Controls.Border> elementy w obszarze partycjonowanym.</span><span class="sxs-lookup"><span data-stu-id="65f39-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="65f39-107">Trzeci <xref:System.Windows.Controls.Border> element jest zadokowany <xref:System.Windows.Controls.Dock.Left>do, z szerokością ustawioną na 200 pikseli.</span><span class="sxs-lookup"><span data-stu-id="65f39-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="65f39-108">Czwarty <xref:System.Windows.Controls.Border> jest zadokowany <xref:System.Windows.Controls.Dock.Bottom> do ekranu.</span><span class="sxs-lookup"><span data-stu-id="65f39-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="65f39-109">Ostatni <xref:System.Windows.Controls.Border> element automatycznie wypełnia pozostałe miejsce.</span><span class="sxs-lookup"><span data-stu-id="65f39-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
> <span data-ttu-id="65f39-110">Domyślnie ostatni element podrzędny <xref:System.Windows.Controls.DockPanel> elementu wypełnia pozostałe nieprzypisane miejsce.</span><span class="sxs-lookup"><span data-stu-id="65f39-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="65f39-111">Jeśli nie chcesz tego zachowania, ustaw wartość `LastChildFill="False"`.</span><span class="sxs-lookup"><span data-stu-id="65f39-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="65f39-112">Skompilowana aplikacja daje nowy interfejs użytkownika, który będzie wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="65f39-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="65f39-113">![Typowy scenariusz DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="65f39-113">![A typical DockPanel scenario.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f39-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65f39-114">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="65f39-115">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="65f39-115">Panels Overview</span></span>](panels-overview.md)
