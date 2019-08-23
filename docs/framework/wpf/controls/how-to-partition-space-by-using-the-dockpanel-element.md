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
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Instrukcje: Rozdzielanie miejsca przy użyciu elementu DockPanel
Poniższy przykład tworzy prostą [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] strukturę <xref:System.Windows.Controls.DockPanel> przy użyciu elementu. Dostępne <xref:System.Windows.Controls.DockPanel> są partycje do elementów podrzędnych.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano <xref:System.Windows.Controls.DockPanel.Dock%2A> właściwość, która jest dołączoną właściwością, aby zadokować dwa identyczne <xref:System.Windows.Controls.Dock.Top> <xref:System.Windows.Controls.Border> elementy w obszarze partycjonowanym. Trzeci <xref:System.Windows.Controls.Border> element jest zadokowany <xref:System.Windows.Controls.Dock.Left>do, z szerokością ustawioną na 200 pikseli. Czwarty <xref:System.Windows.Controls.Border> jest zadokowany <xref:System.Windows.Controls.Dock.Bottom> do ekranu. Ostatni <xref:System.Windows.Controls.Border> element automatycznie wypełnia pozostałe miejsce.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
> Domyślnie ostatni element podrzędny <xref:System.Windows.Controls.DockPanel> elementu wypełnia pozostałe nieprzypisane miejsce. Jeśli nie chcesz tego zachowania, ustaw wartość `LastChildFill="False"`.  
  
 Skompilowana aplikacja daje nowy interfejs użytkownika, który będzie wyglądać następująco.  
  
 ![Typowy scenariusz DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DockPanel>
- [Panele — omówienie](panels-overview.md)
