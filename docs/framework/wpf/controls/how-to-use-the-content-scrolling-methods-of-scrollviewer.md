---
title: "Jak używać metod przesuwania zawartości ScrollViewer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc9b79ae9b8078bbdc4c41fb0c952237f86fcac8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a>Jak używać metod przesuwania zawartości ScrollViewer
Ten przykład przedstawia sposób użycia metody przewijania <xref:System.Windows.Controls.ScrollViewer> elementu. Te metody udostępniają przyrostowe przewijanie zawartości, za pomocą wiersza lub przez strony, w <xref:System.Windows.Controls.ScrollViewer>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ScrollViewer> o nazwie `sv1`, który zawiera element podrzędny <xref:System.Windows.Controls.TextBlock> elementu. Ponieważ <xref:System.Windows.Controls.TextBlock> jest większy niż element nadrzędny <xref:System.Windows.Controls.ScrollViewer>, aby włączyć przewijanie zostaną wyświetlone paski przewijania. <xref:System.Windows.Controls.Button>elementy, które reprezentują różne metody przewijania są zadokowane po lewej stronie w oddzielnej <xref:System.Windows.Controls.StackPanel>. Każdy <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik wywołuje powiązanej metody niestandardowe kontrolujące zachowanie przewijania w <xref:System.Windows.Controls.ScrollViewer>.  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> i <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> metody.  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.StackPanel>
