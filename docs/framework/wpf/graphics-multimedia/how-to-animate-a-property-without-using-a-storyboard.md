---
title: 'Instrukcje: Animowanie właściwości bez użycia scenorysu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 93609cdeb4d879cbec0f90096e4fa2c131a2ec5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091710"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a><span data-ttu-id="2ddd3-102">Instrukcje: Animowanie właściwości bez użycia scenorysu</span><span class="sxs-lookup"><span data-stu-id="2ddd3-102">How to: Animate a Property Without Using a Storyboard</span></span>
<span data-ttu-id="2ddd3-103">Ten przykład przedstawia sposób zastosowania animacji właściwości bez użycia <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="2ddd3-103">This example shows one way to apply an animation to a property without using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ddd3-104">Ta funkcja nie jest dostępna w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2ddd3-104">This functionality is not available in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="2ddd3-105">Aby uzyskać informacje na temat Animowanie właściwości w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [animować właściwość przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="2ddd3-105">For information about animating a property in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="2ddd3-106">Aby zastosować lokalna Animacja na właściwość, należy użyć <xref:System.Windows.UIElement.BeginAnimation%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2ddd3-106">To apply a local animation to a property, use the <xref:System.Windows.UIElement.BeginAnimation%2A> method.</span></span> <span data-ttu-id="2ddd3-107">Ta metoda przyjmuje dwa parametry: <xref:System.Windows.DependencyProperty> , który określa właściwość, animować i animacji, aby zastosować do tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ddd3-107">This method takes two parameters: a <xref:System.Windows.DependencyProperty> that specifies the property to animate, and the animation to apply to that property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ddd3-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ddd3-108">Example</span></span>  
 <span data-ttu-id="2ddd3-109">Poniższy przykład pokazuje, jak animować kolor tła i szerokość <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="2ddd3-109">The following example shows how to animate the width and background color of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <span data-ttu-id="2ddd3-110">Różne klasy animacji w <xref:System.Windows.Media.Animation> przestrzeń nazw istnieje animowania różnego rodzaju właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ddd3-110">A variety of animation classes in the <xref:System.Windows.Media.Animation> namespace exist for animating different types of properties.</span></span> <span data-ttu-id="2ddd3-111">Aby uzyskać więcej informacji na temat Animowanie właściwości, zobacz [Przegląd animacja](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2ddd3-111">For more information about animating properties, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="2ddd3-112">Aby uzyskać więcej informacji na temat właściwości zależności (typ właściwości, które są wyświetlane w tych przykładach) i ich funkcji, zobacz [Przegląd właściwości zależności](../advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2ddd3-112">For more information about dependency properties (the type of properties that are shown in these examples) and their features, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="2ddd3-113">Istnieją inne sposoby, aby animować bez użycia <xref:System.Windows.Media.Animation.Storyboard> obiektów; Aby uzyskać więcej informacji, zobacz [Przegląd techniki animacji właściwości](property-animation-techniques-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2ddd3-113">There are other ways to animate without using <xref:System.Windows.Media.Animation.Storyboard> objects; for more information, see [Property Animation Techniques Overview](property-animation-techniques-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ddd3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ddd3-114">See also</span></span>

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="2ddd3-115">Przegląd Techniki animacji właściwości</span><span class="sxs-lookup"><span data-stu-id="2ddd3-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="2ddd3-116">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="2ddd3-116">Animation Overview</span></span>](animation-overview.md)
