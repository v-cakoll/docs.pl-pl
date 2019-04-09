---
title: 'Instrukcje: Pobieranie lub ustawianie wartości dokowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
ms.openlocfilehash: fb6c8a7d62aa09a6e1d82cb4079d1425a7f39f8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160743"
---
# <a name="how-to-get-or-set-a-dock-value"></a>Instrukcje: Pobieranie lub ustawianie wartości dokowania
Poniższy przykład pokazuje, jak przypisać <xref:System.Windows.Controls.Dock> wartość obiektu. W przykładzie użyto <xref:System.Windows.Controls.DockPanel.GetDock%2A> i <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody <xref:System.Windows.Controls.DockPanel>.  
  
## <a name="example"></a>Przykład  
 Przykład tworzy wystąpienie <xref:System.Windows.Controls.TextBlock> elementu, `txt1`, a następnie przypisuje <xref:System.Windows.Controls.Dock> wartość `Top` przy użyciu <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody <xref:System.Windows.Controls.DockPanel>. Następnie dołącza wartości <xref:System.Windows.Controls.Dock> właściwości <xref:System.Windows.Controls.TextBlock.Text%2A> z <xref:System.Windows.Controls.TextBlock> elementu za pomocą <xref:System.Windows.Controls.DockPanel.GetDock%2A> metody. Ponadto w przykładzie dodano <xref:System.Windows.Controls.TextBlock> elementu nadrzędnego <xref:System.Windows.Controls.DockPanel>, `dp1`.  
  
 [!code-csharp[DockPanelSetDock#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [Przegląd Panele](panels-overview.md)
