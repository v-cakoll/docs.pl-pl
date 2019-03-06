---
title: 'Instrukcje: Przewijaj zawartość przy użyciu interfejsu IScrollInfo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 145c58064b8557f9cb4730ec9272c354c7aa9c1b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378981"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>Instrukcje: Przewijaj zawartość przy użyciu interfejsu IScrollInfo
W tym przykładzie pokazano, jak przewijać zawartość przy użyciu <xref:System.Windows.Controls.Primitives.IScrollInfo> interfejsu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano funkcje <xref:System.Windows.Controls.Primitives.IScrollInfo> interfejsu. W przykładzie jest tworzony <xref:System.Windows.Controls.StackPanel> element [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] zagnieżdżony w obiekcie nadrzędnym <xref:System.Windows.Controls.ScrollViewer>. Elementy podrzędne <xref:System.Windows.Controls.StackPanel> mogą być przewijane logicznie za pomocą metod zdefiniowanych przez <xref:System.Windows.Controls.Primitives.IScrollInfo> interfejsu i Rzutowanie na wystąpienie <xref:System.Windows.Controls.StackPanel> (`sp1`) w kodzie.  
  
 [!code-xaml[IScrollInfoMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 Każdy <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku wyzwala skojarzone niestandardową metodę, która kontroluje zachowanie przewijania w <xref:System.Windows.Controls.StackPanel>. Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> i <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> metod; również ogólną pokazuje sposób użycia metody pozycjonowania, <xref:System.Windows.Controls.Primitives.IScrollInfo> klasa definiuje.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [ScrollViewer — omówienie](scrollviewer-overview.md)
- [Tematy z instrukcjami](scrollviewer-how-to-topics.md)
- [Panele — omówienie](panels-overview.md)
