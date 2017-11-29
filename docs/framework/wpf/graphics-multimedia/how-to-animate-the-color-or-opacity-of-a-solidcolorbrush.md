---
title: "Jak animować kolor lub nieprzezroczystość SolidColorBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 03052cdf68a5a8564d5a24c91521749c10afa6cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="01669-102">Jak animować kolor lub nieprzezroczystość SolidColorBrush</span><span class="sxs-lookup"><span data-stu-id="01669-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="01669-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> i <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="01669-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01669-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="01669-104">Example</span></span>  
 <span data-ttu-id="01669-105">W poniższym przykładzie użyto trzy animacje do animowania <xref:System.Windows.Media.SolidColorBrush.Color%2A> i <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="01669-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
-   <span data-ttu-id="01669-106">Pierwszy animacji <xref:System.Windows.Media.Animation.ColorAnimation>, zmienia kolor pędzla do <xref:System.Windows.Media.Colors.Gray%2A> gdy mysz przejdzie prostokąta.</span><span class="sxs-lookup"><span data-stu-id="01669-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
-   <span data-ttu-id="01669-107">Animacja dalej innego <xref:System.Windows.Media.Animation.ColorAnimation>, zmienia kolor pędzla do <xref:System.Windows.Media.Colors.Orange%2A> gdy mysz opuści prostokąta.</span><span class="sxs-lookup"><span data-stu-id="01669-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
-   <span data-ttu-id="01669-108">Końcowe animacji <xref:System.Windows.Media.Animation.DoubleAnimation>, zmiany przezroczystość pędzla 0,0 po naciśnięciu lewego przycisku myszy.</span><span class="sxs-lookup"><span data-stu-id="01669-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="01669-109">Aby uzyskać bardziej szczegółowy przykładzie pokazano, jak animować różnego rodzaju pędzle, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="01669-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="01669-110">Aby uzyskać więcej informacji na temat animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="01669-110">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="01669-111">Spójności z innymi przykładami animacji, użyj wersji kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> obiekt do zastosowania ich animacji.</span><span class="sxs-lookup"><span data-stu-id="01669-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="01669-112">Jednak podczas stosowania pojedynczego animacji w kodzie, łatwiej jest użyć <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zamiast <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="01669-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="01669-113">Na przykład zobacz [animowania właściwości bez Using scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="01669-113">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01669-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01669-114">See Also</span></span>  
 [<span data-ttu-id="01669-115">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="01669-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="01669-116">Scenorys — omówienie</span><span class="sxs-lookup"><span data-stu-id="01669-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="01669-117">Pędzle próbki</span><span class="sxs-lookup"><span data-stu-id="01669-117">Brushes Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159973)
