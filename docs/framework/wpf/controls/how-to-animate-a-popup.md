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
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="10621-102">Instrukcje: Animuj okno podręczne</span><span class="sxs-lookup"><span data-stu-id="10621-102">How to: Animate a Popup</span></span>
<span data-ttu-id="10621-103">Ten przykład przedstawia dwa sposoby, aby animować <xref:System.Windows.Controls.Primitives.Popup> kontroli.</span><span class="sxs-lookup"><span data-stu-id="10621-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10621-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="10621-104">Example</span></span>  
 <span data-ttu-id="10621-105">Poniższy przykład ustawia <xref:System.Windows.Controls.Primitives.PopupAnimation> właściwości na wartość <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, co powoduje, że <xref:System.Windows.Controls.Primitives.Popup> do "slajdów w" gdy się pojawi.</span><span class="sxs-lookup"><span data-stu-id="10621-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="10621-106">Aby obrócić <xref:System.Windows.Controls.Primitives.Popup>, w tym przykładzie przypisuje <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość <xref:System.Windows.Controls.Canvas>, który jest elementem podrzędnym <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="10621-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="10621-107">Przekształcenia działała prawidłowo, należy ustawić przykład <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="10621-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="10621-108">Ponadto <xref:System.Windows.FrameworkElement.Margin%2A> na <xref:System.Windows.Controls.Canvas> zawartości należy określić wystarczającej ilości miejsca dla <xref:System.Windows.Controls.Primitives.Popup> wymiany.</span><span class="sxs-lookup"><span data-stu-id="10621-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="10621-109">W poniższym przykładzie pokazano jak <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie, które występuje, gdy <xref:System.Windows.Controls.Button> zostanie kliknięty wyzwalaczy <xref:System.Windows.Media.Animation.Storyboard> , powoduje uruchomienie animacji.</span><span class="sxs-lookup"><span data-stu-id="10621-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="10621-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10621-110">See also</span></span>
- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="10621-111">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="10621-111">How-to Topics</span></span>](popup-how-to-topics.md)
- [<span data-ttu-id="10621-112">Okno podręczne — omówienie</span><span class="sxs-lookup"><span data-stu-id="10621-112">Popup Overview</span></span>](popup-overview.md)
