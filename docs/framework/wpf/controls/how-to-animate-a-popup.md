---
title: 'Instrukcje: Animowanie okna podręcznego'
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: b70d9c4cb1bca26a6c77d3a7c50add517ca8ef92
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150114"
---
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="3f490-102">Instrukcje: Animowanie okna podręcznego</span><span class="sxs-lookup"><span data-stu-id="3f490-102">How to: Animate a Popup</span></span>
<span data-ttu-id="3f490-103">Ten przykład przedstawia dwa sposoby, aby animować <xref:System.Windows.Controls.Primitives.Popup> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3f490-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f490-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f490-104">Example</span></span>  
 <span data-ttu-id="3f490-105">Poniższy przykład ustawia <xref:System.Windows.Controls.Primitives.PopupAnimation> właściwości na wartość <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, co powoduje, że <xref:System.Windows.Controls.Primitives.Popup> do "slajdów w" gdy się pojawi.</span><span class="sxs-lookup"><span data-stu-id="3f490-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="3f490-106">Aby obrócić <xref:System.Windows.Controls.Primitives.Popup>, w tym przykładzie przypisuje <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość <xref:System.Windows.Controls.Canvas>, który jest elementem podrzędnym <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="3f490-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="3f490-107">Przekształcenia działała prawidłowo, należy ustawić przykład <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="3f490-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="3f490-108">Ponadto <xref:System.Windows.FrameworkElement.Margin%2A> na <xref:System.Windows.Controls.Canvas> zawartości należy określić wystarczającej ilości miejsca dla <xref:System.Windows.Controls.Primitives.Popup> wymiany.</span><span class="sxs-lookup"><span data-stu-id="3f490-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="3f490-109">W poniższym przykładzie pokazano jak <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie, które występuje, gdy <xref:System.Windows.Controls.Button> zostanie kliknięty wyzwalaczy <xref:System.Windows.Media.Animation.Storyboard> , powoduje uruchomienie animacji.</span><span class="sxs-lookup"><span data-stu-id="3f490-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="3f490-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f490-110">See also</span></span>

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="3f490-111">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="3f490-111">How-to Topics</span></span>](popup-how-to-topics.md)
- [<span data-ttu-id="3f490-112">Przegląd Okna podręczne</span><span class="sxs-lookup"><span data-stu-id="3f490-112">Popup Overview</span></span>](popup-overview.md)
