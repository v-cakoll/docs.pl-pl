---
title: "Jak przerzucić element interfejsu użytkownika w poziomie lub w pionie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 84d1360246141cfa565d669fff108e3e4db3ce33
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a><span data-ttu-id="68f5b-102">Jak przerzucić element interfejsu użytkownika w poziomie lub w pionie</span><span class="sxs-lookup"><span data-stu-id="68f5b-102">How to: Flip a UIElement Horizontally or Vertically</span></span>
<span data-ttu-id="68f5b-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.ScaleTransform> do przerzucenia <xref:System.Windows.UIElement> poziomo czy pionowo.</span><span class="sxs-lookup"><span data-stu-id="68f5b-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to flip a <xref:System.Windows.UIElement> horizontally or vertically.</span></span> <span data-ttu-id="68f5b-104">W tym przykładzie <xref:System.Windows.Controls.Button> formantu (typu <xref:System.Windows.UIElement>) jest odwrócony, stosując <xref:System.Windows.Media.ScaleTransform> do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="68f5b-104">In this example, a <xref:System.Windows.Controls.Button> control (a type of <xref:System.Windows.UIElement>) is flipped by applying a <xref:System.Windows.Media.ScaleTransform> to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68f5b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="68f5b-105">Example</span></span>  
 <span data-ttu-id="68f5b-106">Na poniższej ilustracji przedstawiono przycisku do przerzucenia.</span><span class="sxs-lookup"><span data-stu-id="68f5b-106">The following illustration shows the button to flip.</span></span>  
  
 <span data-ttu-id="68f5b-107">![Przycisk bez przekształcenia](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span><span class="sxs-lookup"><span data-stu-id="68f5b-107">![A button with no transform](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span></span>  
<span data-ttu-id="68f5b-108">UIElement do przerzucenia</span><span class="sxs-lookup"><span data-stu-id="68f5b-108">The UIElement to flip</span></span>  
  
 <span data-ttu-id="68f5b-109">Poniżej przedstawiono kod, który tworzy przycisku.</span><span class="sxs-lookup"><span data-stu-id="68f5b-109">The following shows the code that creates the button.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a><span data-ttu-id="68f5b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="68f5b-110">Example</span></span>  
 <span data-ttu-id="68f5b-111">Przerzuć przycisku w poziomie, należy utworzyć <xref:System.Windows.Media.ScaleTransform> i ustawić jej <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości na wartość -1.</span><span class="sxs-lookup"><span data-stu-id="68f5b-111">To flip the button horizontally, create a <xref:System.Windows.Media.ScaleTransform> and set its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property to -1.</span></span> <span data-ttu-id="68f5b-112">Zastosuj <xref:System.Windows.Media.ScaleTransform> na przycisk <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="68f5b-112">Apply the <xref:System.Windows.Media.ScaleTransform> to the button's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 <span data-ttu-id="68f5b-113">![Przycisk poziomie przerzucane o &#40; 0,0 &#41; ] (../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span><span class="sxs-lookup"><span data-stu-id="68f5b-113">![A button flipped horizontally about &#40;0,0&#41;](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span></span>  
<span data-ttu-id="68f5b-114">Przycisk po zastosowaniu ScaleTransform</span><span class="sxs-lookup"><span data-stu-id="68f5b-114">The button after applying the ScaleTransform</span></span>  
  
## <a name="example"></a><span data-ttu-id="68f5b-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="68f5b-115">Example</span></span>  
 <span data-ttu-id="68f5b-116">Jak widać na poprzedniej ilustracji, przycisk został odwrócony, ale również została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="68f5b-116">As you can see from the previous illustration, the button was flipped, but it was also moved.</span></span> <span data-ttu-id="68f5b-117">Wynika to z przycisku został odwrócony z jego lewym górnym rogu.</span><span class="sxs-lookup"><span data-stu-id="68f5b-117">That's because the button was flipped from its top left corner.</span></span> <span data-ttu-id="68f5b-118">Aby odwrócić przycisku w miejscu, które chcesz zastosować <xref:System.Windows.Media.ScaleTransform> jego Centrum, a nie jej rogu.</span><span class="sxs-lookup"><span data-stu-id="68f5b-118">To flip the button in place, you want to apply the <xref:System.Windows.Media.ScaleTransform> to its center, not its corner.</span></span> <span data-ttu-id="68f5b-119">Łatwo zastosować <xref:System.Windows.Media.ScaleTransform> do przycisków Centrum jest skonfigurowanie przycisku <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości 0,5, 0,5.</span><span class="sxs-lookup"><span data-stu-id="68f5b-119">An easy way to apply the <xref:System.Windows.Media.ScaleTransform> to the buttons center is to set the button's <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to 0.5, 0.5.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 <span data-ttu-id="68f5b-120">![Przycisk poziomie przerzucane o jego center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="68f5b-120">![A button flipped horizontally about its center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span></span>  
<span data-ttu-id="68f5b-121">Przycisk RenderTransformOrigin 0,5, 0,5</span><span class="sxs-lookup"><span data-stu-id="68f5b-121">The button with a RenderTransformOrigin of 0.5, 0.5</span></span>  
  
## <a name="example"></a><span data-ttu-id="68f5b-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="68f5b-122">Example</span></span>  
 <span data-ttu-id="68f5b-123">Aby przerzucić przycisku w pionie, ustaw <xref:System.Windows.Media.ScaleTransform> obiektu <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości zamiast jego <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="68f5b-123">To flip the button vertically, set the <xref:System.Windows.Media.ScaleTransform> object's <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> property instead of its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 <span data-ttu-id="68f5b-124">![Przycisk pionowo przerzucane o jego center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="68f5b-124">![A button flipped vertically about its center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span></span>  
<span data-ttu-id="68f5b-125">Przycisk pionowo odwrócony</span><span class="sxs-lookup"><span data-stu-id="68f5b-125">The vertically flipped button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f5b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68f5b-126">See Also</span></span>  
 [<span data-ttu-id="68f5b-127">Przekształca — omówienie</span><span class="sxs-lookup"><span data-stu-id="68f5b-127">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
