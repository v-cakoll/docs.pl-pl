---
title: 'Instrukcje: Wyrównywanie w poziomie lub w pionie zawartości w kontrolce StackPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: 03348aa0eb5b6c1791c27683c1c6c6a5d4a8a9d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771036"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>Instrukcje: Wyrównywanie w poziomie lub w pionie zawartości w kontrolce StackPanel
W tym przykładzie pokazano, jak dostosować <xref:System.Windows.Controls.StackPanel.Orientation%2A> zawartości w ramach <xref:System.Windows.Controls.StackPanel> elementu, a także, jak dostosować <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> z zawartość elementu podrzędnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy trzy <xref:System.Windows.Controls.ListBox> elementów w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Każdy <xref:System.Windows.Controls.ListBox> reprezentuje możliwe wartości <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości <xref:System.Windows.Controls.StackPanel>. Gdy użytkownik wybierze wartości w jednym z <xref:System.Windows.Controls.ListBox> elementy, właściwości skojarzonej z <xref:System.Windows.Controls.StackPanel> i jej podrzędne <xref:System.Windows.Controls.Button> zmiany elementów.  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 Następujący plik CodeBehind definiuje zmiany na zdarzenia, które są skojarzone z <xref:System.Windows.Controls.ListBox> zmian zaznaczenia. <xref:System.Windows.Controls.StackPanel> jest identyfikowany przez <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [Panele — omówienie](panels-overview.md)
