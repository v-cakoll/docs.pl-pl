---
title: Jak przewijać zawartość przy użyciu interfejsu IScrollInfo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 8154a626c6bf48a59be0540f857c0c51d59a26c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>Jak przewijać zawartość przy użyciu interfejsu IScrollInfo
W tym przykładzie pokazano, jak przewijanie zawartości przy użyciu <xref:System.Windows.Controls.Primitives.IScrollInfo> interfejsu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano funkcje <xref:System.Windows.Controls.Primitives.IScrollInfo> interfejsu. W przykładzie jest tworzony <xref:System.Windows.Controls.StackPanel> element [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] zagnieżdżony w katalogu nadrzędnym <xref:System.Windows.Controls.ScrollViewer>. Elementy podrzędne <xref:System.Windows.Controls.StackPanel> mogą być przewijane logicznie przy użyciu metody zdefiniowane przez <xref:System.Windows.Controls.Primitives.IScrollInfo> interfejsu i Rzutowanie na wystąpienie <xref:System.Windows.Controls.StackPanel> (`sp1`) w kodzie.  
  
 [!code-xaml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 Każdy <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku wyzwala skojarzone metody niestandardowej kontrolujące zachowanie przewijania w <xref:System.Windows.Controls.StackPanel>. Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> i <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> metod; również objęty przedstawia sposób użycia metody pozycjonowania który <xref:System.Windows.Controls.Primitives.IScrollInfo> definiuje klasę.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 <xref:System.Windows.Controls.StackPanel>  
 [ScrollViewer — omówienie](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
