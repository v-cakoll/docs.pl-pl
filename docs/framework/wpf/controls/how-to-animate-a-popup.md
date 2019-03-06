---
title: 'Instrukcje: Animuj okno podręczne'
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: ed5edf298e59d6a9adddc03fc21de1900c7ee8e9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372844"
---
# <a name="how-to-animate-a-popup"></a>Instrukcje: Animuj okno podręczne
Ten przykład przedstawia dwa sposoby, aby animować <xref:System.Windows.Controls.Primitives.Popup> kontroli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ustawia <xref:System.Windows.Controls.Primitives.PopupAnimation> właściwości na wartość <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, co powoduje, że <xref:System.Windows.Controls.Primitives.Popup> do "slajdów w" gdy się pojawi.  
  
 Aby obrócić <xref:System.Windows.Controls.Primitives.Popup>, w tym przykładzie przypisuje <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość <xref:System.Windows.Controls.Canvas>, który jest elementem podrzędnym <xref:System.Windows.Controls.Primitives.Popup>.  
  
 Przekształcenia działała prawidłowo, należy ustawić przykład <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> właściwość `true`. Ponadto <xref:System.Windows.FrameworkElement.Margin%2A> na <xref:System.Windows.Controls.Canvas> zawartości należy określić wystarczającej ilości miejsca dla <xref:System.Windows.Controls.Primitives.Popup> wymiany.  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 W poniższym przykładzie pokazano jak <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie, które występuje, gdy <xref:System.Windows.Controls.Button> zostanie kliknięty wyzwalaczy <xref:System.Windows.Media.Animation.Storyboard> , powoduje uruchomienie animacji.  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [Tematy z instrukcjami](popup-how-to-topics.md)
- [Okno podręczne — omówienie](popup-overview.md)
