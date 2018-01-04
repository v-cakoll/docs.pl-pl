---
title: "Jak animować okno podręczne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd79b29849510f40034dd0e2f1d9668c9b742929
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-popup"></a>Jak animować okno podręczne
Ten przykład przedstawia dwa sposoby animować <xref:System.Windows.Controls.Primitives.Popup> formantu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Controls.Primitives.PopupAnimation> właściwości na wartość <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, co powoduje, że <xref:System.Windows.Controls.Primitives.Popup> do "slajdów w" wyświetlanym.  
  
 W celu obracania <xref:System.Windows.Controls.Primitives.Popup>, w tym przykładzie przypisuje <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość <xref:System.Windows.Controls.Canvas>, który jest elementem podrzędnym <xref:System.Windows.Controls.Primitives.Popup>.  
  
 Przekształcenia działał prawidłowo, należy ustawić przykładzie <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> właściwości `true`. Ponadto <xref:System.Windows.FrameworkElement.Margin%2A> na <xref:System.Windows.Controls.Canvas> zawartość musi określać wystarczającej ilości miejsca dla <xref:System.Windows.Controls.Primitives.Popup> obrotu.  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 W poniższym przykładzie przedstawiono sposób <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie, które występuje podczas <xref:System.Windows.Controls.Button> zostanie kliknięty wyzwalaczy <xref:System.Windows.Media.Animation.Storyboard> zaczynającym się animacji.  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [Okno podręczne — omówienie](../../../../docs/framework/wpf/controls/popup-overview.md)
