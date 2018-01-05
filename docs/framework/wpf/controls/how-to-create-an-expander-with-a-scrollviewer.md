---
title: "Jak utworzyć ekspander za pomocą ScrollViewer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2066ccce28138cfecf4e0b4574d45783a9ba4ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a>Jak utworzyć ekspander za pomocą ScrollViewer
W tym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Controls.Expander> formant, który zawiera złożone zawartości, takich jak obraz i tekst. Przykład obejmuje również zawartość <xref:System.Windows.Controls.Expander> w <xref:System.Windows.Controls.ScrollViewer> formantu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.Expander>. W przykładzie użyto <xref:System.Windows.Controls.Primitives.BulletDecorator> formant, który zawiera obraz i tekst, aby zdefiniować <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>. A <xref:System.Windows.Controls.ScrollViewer> kontroli zapewnia metodę przewijanie zawartości rozwinięte.  
  
 Należy pamiętać, że w przykładzie <xref:System.Windows.FrameworkElement.Height%2A> właściwość <xref:System.Windows.Controls.ScrollViewer> zamiast na zawartość. Jeśli <xref:System.Windows.FrameworkElement.Height%2A> jest ustawiony dla zawartości, <xref:System.Windows.Controls.ScrollViewer> nie zezwala użytkownikowi na przewijanie zawartości. <xref:System.Windows.FrameworkElement.Width%2A> Właściwość jest ustawiona na <xref:System.Windows.Controls.Expander> kontroli i to ustawienie dotyczy <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i rozszerzonej zawartości.  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Expander>  
 [Ekspander — omówienie](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
