---
title: 'Instrukcje: Używaj metod przesuwania zawartości ScrollViewer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: 0f2ed1c0ac0d29a47ab98e0329ff161fd54daba6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547043"
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a>Instrukcje: Używaj metod przesuwania zawartości ScrollViewer
W tym przykładzie pokazano, jak używać metody przewijania <xref:System.Windows.Controls.ScrollViewer> elementu. Metody te zapewniają przyrostowe przewijanie zawartości przy użyciu wiersza lub przez stronę, <xref:System.Windows.Controls.ScrollViewer>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ScrollViewer> o nazwie `sv1`, która hostuje element podrzędny <xref:System.Windows.Controls.TextBlock> elementu. Ponieważ <xref:System.Windows.Controls.TextBlock> jest większy niż element nadrzędny <xref:System.Windows.Controls.ScrollViewer>, paski przewijania są wyświetlane w celu umożliwienia przewijania. <xref:System.Windows.Controls.Button> elementy, które reprezentują różne metody przewijania są zadokowane po lewej stronie w osobnym <xref:System.Windows.Controls.StackPanel>. Każdy <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku wywołuje powiązanej metody niestandardowego, który kontroluje zachowanie przewijania w <xref:System.Windows.Controls.ScrollViewer>.  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> i <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> metody.  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.StackPanel>
