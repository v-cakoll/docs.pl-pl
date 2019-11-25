---
title: Jak wybrać pomiędzy StackPanel i DockPanel
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
ms.openlocfilehash: bdf4b38e67a7856136224368e86609c135e5ad6f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976439"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>Jak wybrać pomiędzy StackPanel i DockPanel
W tym przykładzie pokazano, jak wybrać opcję użycia <xref:System.Windows.Controls.StackPanel> lub <xref:System.Windows.Controls.DockPanel> podczas stosu zawartości w <xref:System.Windows.Controls.Panel>.

## <a name="example"></a>Przykład
 Mimo że można użyć <xref:System.Windows.Controls.DockPanel> lub <xref:System.Windows.Controls.StackPanel> do stosu elementów podrzędnych, dwie kontrolki nie zawsze generują te same wyniki. Na przykład kolejność umieszczania elementów podrzędnych może wpływać na rozmiar elementów podrzędnych w <xref:System.Windows.Controls.DockPanel> ale nie w <xref:System.Windows.Controls.StackPanel>. Takie zachowanie występuje, ponieważ <xref:System.Windows.Controls.StackPanel> miary w kierunku układania przy użyciu wartości [Double. PositiveInfinity](xref:System.Double.PositiveInfinity); jednak <xref:System.Windows.Controls.DockPanel> mierzy tylko dostępny rozmiar.

 Poniższy przykład ilustruje tę różnicę między <xref:System.Windows.Controls.DockPanel> i <xref:System.Windows.Controls.StackPanel>.

 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [Panele — omówienie](panels-overview.md)
