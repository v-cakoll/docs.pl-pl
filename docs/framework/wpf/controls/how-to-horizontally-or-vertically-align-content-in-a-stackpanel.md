---
title: Jak wyrównać w poziomie lub w pionie zawartość w StackPanel
description: Dowiedz się, jak dostosować orientację zawartości w Windows Presentation Foundation StackPanel i HorizontalAlignment i VerticalAlignment zawartości podrzędnej.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: d3c7215d8193d1d8a72597c44cf265f5bd400ea1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167629"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>Jak wyrównać w poziomie lub w pionie zawartość w StackPanel
Ten przykład pokazuje, jak dostosować <xref:System.Windows.Controls.StackPanel.Orientation%2A> zawartość w obrębie <xref:System.Windows.Controls.StackPanel> elementu, a także dostosować <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> zawartość elementu <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> podrzędnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy trzy <xref:System.Windows.Controls.ListBox> elementy w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Każdy <xref:System.Windows.Controls.ListBox> reprezentuje możliwe wartości <xref:System.Windows.Controls.StackPanel.Orientation%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości,, i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.Controls.StackPanel> . Gdy użytkownik wybierze wartość w którymkolwiek z <xref:System.Windows.Controls.ListBox> elementów, skojarzona właściwość <xref:System.Windows.Controls.StackPanel> i jego <xref:System.Windows.Controls.Button> elementy podrzędne zmienią się.  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 Następujący plik związany z kodem definiuje zmiany w zdarzeniach, które są skojarzone z <xref:System.Windows.Controls.ListBox> zmianą zaznaczenia. <xref:System.Windows.Controls.StackPanel>jest identyfikowany przez <xref:System.Windows.FrameworkElement.Name%2A> `sp1` .  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [Przegląd Panele](panels-overview.md)
