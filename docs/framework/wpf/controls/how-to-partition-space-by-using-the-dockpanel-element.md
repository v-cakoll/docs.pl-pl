---
title: Jak rozdzielić przestrzeń przy użyciu elementu DockPanel
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
ms.openlocfilehash: 6b10fbcd14236f9259dc5772e7f8763c1602d0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553887"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Jak rozdzielić przestrzeń przy użyciu elementu DockPanel
Poniższy przykład tworzy prosty [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework za pomocą <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Controls.DockPanel> Partycje dostępne miejsce do jego elementów podrzędnych.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Windows.Controls.DockPanel.Dock%2A> właściwość, która jest dołączona właściwość, aby dock dwie identyczne <xref:System.Windows.Controls.Border> elementy w <xref:System.Windows.Controls.Dock.Top> miejsca podzielonym na partycje. W trzecim <xref:System.Windows.Controls.Border> element jest zadokowany do <xref:System.Windows.Controls.Dock.Left>, przy czym jego szerokość ustawioną 200 pikseli. Czwarty <xref:System.Windows.Controls.Border> jest zadokowana <xref:System.Windows.Controls.Dock.Bottom> ekranu. Ostatni <xref:System.Windows.Controls.Border> elementu automatycznie wypełnia pozostałe miejsce.  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  Domyślnie ostatni element podrzędny elementu <xref:System.Windows.Controls.DockPanel> element wypełnia pozostałe nieprzydzielone miejsce. Jeśli nie chcesz, aby ten problem, ustaw `LastChildFill="False"`.  
  
 Skompilowana aplikacja zwraca nowy interfejs użytkownika, który wygląda następująco.  
  
 ![Typowy scenariusz DockPanel. ] (../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.DockPanel>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
