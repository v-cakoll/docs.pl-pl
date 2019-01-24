---
title: 'Instrukcje: Rozdziel przestrzeń przy użyciu elementu DockPanel'
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
ms.openlocfilehash: 8b79b89e512ec9da27774188aeaeed8ebd5b1153
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577662"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Instrukcje: Rozdziel przestrzeń przy użyciu elementu DockPanel
Poniższy przykład tworzy prostą [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] przy użyciu framework <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Controls.DockPanel> Partycje dostępnego miejsca na jego elementy podrzędne.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Windows.Controls.DockPanel.Dock%2A> właściwość, która jest dołączona właściwość, aby zadokować dwa identyczne <xref:System.Windows.Controls.Border> elementy w <xref:System.Windows.Controls.Dock.Top> miejsca podzielonym na partycje. Trzeci <xref:System.Windows.Controls.Border> element jest zadokowany do <xref:System.Windows.Controls.Dock.Left>, za pomocą jego szerokość równa 200 pikseli. Czwarty <xref:System.Windows.Controls.Border> jest zadokowany do <xref:System.Windows.Controls.Dock.Bottom> ekranu. Ostatni <xref:System.Windows.Controls.Border> elementu automatycznie wypełnia pozostałe miejsce.  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  Domyślnie ostatni element podrzędny elementu <xref:System.Windows.Controls.DockPanel> element wypełnia pozostałe nieprzydzielone miejsce. Jeśli nie chcesz tego zachowania, ustaw `LastChildFill="False"`.  
  
 Skompilowaną aplikację daje nowy interfejs użytkownika, który wygląda w następujący sposób.  
  
 ![Typowy scenariusz DockPanel. ](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.DockPanel>
- [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
