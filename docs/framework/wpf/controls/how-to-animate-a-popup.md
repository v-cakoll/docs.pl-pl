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
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="7dd3e-102">Jak animować okno podręczne</span><span class="sxs-lookup"><span data-stu-id="7dd3e-102">How to: Animate a Popup</span></span>
<span data-ttu-id="7dd3e-103">Ten przykład przedstawia dwa sposoby animować <xref:System.Windows.Controls.Primitives.Popup> formantu.</span><span class="sxs-lookup"><span data-stu-id="7dd3e-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dd3e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7dd3e-104">Example</span></span>  
 <span data-ttu-id="7dd3e-105">W poniższym przykładzie <xref:System.Windows.Controls.Primitives.PopupAnimation> właściwości na wartość <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, co powoduje, że <xref:System.Windows.Controls.Primitives.Popup> do "slajdów w" wyświetlanym.</span><span class="sxs-lookup"><span data-stu-id="7dd3e-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="7dd3e-106">W celu obracania <xref:System.Windows.Controls.Primitives.Popup>, w tym przykładzie przypisuje <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość <xref:System.Windows.Controls.Canvas>, który jest elementem podrzędnym <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="7dd3e-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="7dd3e-107">Przekształcenia działał prawidłowo, należy ustawić przykładzie <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="7dd3e-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="7dd3e-108">Ponadto <xref:System.Windows.FrameworkElement.Margin%2A> na <xref:System.Windows.Controls.Canvas> zawartość musi określać wystarczającej ilości miejsca dla <xref:System.Windows.Controls.Primitives.Popup> obrotu.</span><span class="sxs-lookup"><span data-stu-id="7dd3e-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="7dd3e-109">W poniższym przykładzie przedstawiono sposób <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie, które występuje podczas <xref:System.Windows.Controls.Button> zostanie kliknięty wyzwalaczy <xref:System.Windows.Media.Animation.Storyboard> zaczynającym się animacji.</span><span class="sxs-lookup"><span data-stu-id="7dd3e-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="7dd3e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7dd3e-110">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="7dd3e-111">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="7dd3e-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [<span data-ttu-id="7dd3e-112">Okno podręczne — omówienie</span><span class="sxs-lookup"><span data-stu-id="7dd3e-112">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)
