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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052186"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Instrukcje: Rozdzielanie miejsca przy użyciu elementu DockPanel
Poniższy przykład tworzy prostą [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] przy użyciu framework <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Controls.DockPanel> Partycje dostępnego miejsca na jego elementy podrzędne.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Windows.Controls.DockPanel.Dock%2A> właściwość, która jest dołączona właściwość, aby zadokować dwa identyczne <xref:System.Windows.Controls.Border> elementy w <xref:System.Windows.Controls.Dock.Top> miejsca podzielonym na partycje. Trzeci <xref:System.Windows.Controls.Border> element jest zadokowany do <xref:System.Windows.Controls.Dock.Left>, za pomocą jego szerokość równa 200 pikseli. Czwarty <xref:System.Windows.Controls.Border> jest zadokowany do <xref:System.Windows.Controls.Dock.Bottom> ekranu. Ostatni <xref:System.Windows.Controls.Border> elementu automatycznie wypełnia pozostałe miejsce.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  Domyślnie ostatni element podrzędny elementu <xref:System.Windows.Controls.DockPanel> element wypełnia pozostałe nieprzydzielone miejsce. Jeśli nie chcesz tego zachowania, ustaw `LastChildFill="False"`.  
  
 Skompilowaną aplikację daje nowy interfejs użytkownika, który wygląda w następujący sposób.  
  
 ![Typowy scenariusz DockPanel. ](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DockPanel>
- [Panele — omówienie](panels-overview.md)
