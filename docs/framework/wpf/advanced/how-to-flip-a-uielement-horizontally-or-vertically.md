---
title: 'Instrukcje: Przerzucanie element interfejsu użytkownika w poziomie lub w pionie'
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 6b3da322493d17e4f8e36a35b9a0e40fdc9dc685
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215524"
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a><span data-ttu-id="5ea7c-102">Instrukcje: Przerzucanie element interfejsu użytkownika w poziomie lub w pionie</span><span class="sxs-lookup"><span data-stu-id="5ea7c-102">How to: Flip a UIElement Horizontally or Vertically</span></span>
<span data-ttu-id="5ea7c-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.ScaleTransform> przerzucić <xref:System.Windows.UIElement> poziomo czy pionowo.</span><span class="sxs-lookup"><span data-stu-id="5ea7c-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to flip a <xref:System.Windows.UIElement> horizontally or vertically.</span></span> <span data-ttu-id="5ea7c-104">W tym przykładzie <xref:System.Windows.Controls.Button> kontroli (typ <xref:System.Windows.UIElement>) jest odwrócony, stosując <xref:System.Windows.Media.ScaleTransform> do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ea7c-104">In this example, a <xref:System.Windows.Controls.Button> control (a type of <xref:System.Windows.UIElement>) is flipped by applying a <xref:System.Windows.Media.ScaleTransform> to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ea7c-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ea7c-105">Example</span></span>  
 <span data-ttu-id="5ea7c-106">Poniższa ilustracja przedstawia przycisk do przerzucenia.</span><span class="sxs-lookup"><span data-stu-id="5ea7c-106">The following illustration shows the button to flip.</span></span>  
  
 <span data-ttu-id="5ea7c-107">![Przycisk bez przekształcenia](./media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span><span class="sxs-lookup"><span data-stu-id="5ea7c-107">![A button with no transform](./media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span></span>  
<span data-ttu-id="5ea7c-108">Element interfejsu użytkownika do przerzucenia</span><span class="sxs-lookup"><span data-stu-id="5ea7c-108">The UIElement to flip</span></span>  
  
 <span data-ttu-id="5ea7c-109">Poniżej przedstawiono kod, który tworzy przycisku.</span><span class="sxs-lookup"><span data-stu-id="5ea7c-109">The following shows the code that creates the button.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a><span data-ttu-id="5ea7c-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ea7c-110">Example</span></span>  
 <span data-ttu-id="5ea7c-111">Aby przerzucić przycisku w poziomie, należy utworzyć <xref:System.Windows.Media.ScaleTransform> i ustaw jego <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości na wartość -1.</span><span class="sxs-lookup"><span data-stu-id="5ea7c-111">To flip the button horizontally, create a <xref:System.Windows.Media.ScaleTransform> and set its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property to -1.</span></span> <span data-ttu-id="5ea7c-112">Zastosuj <xref:System.Windows.Media.ScaleTransform> na przycisk <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ea7c-112">Apply the <xref:System.Windows.Media.ScaleTransform> to the button's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 <span data-ttu-id="5ea7c-113">![Przycisk poziomo przerzucane o &#40;0,0&#41;](./media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span><span class="sxs-lookup"><span data-stu-id="5ea7c-113">![A button flipped horizontally about &#40;0,0&#41;](./media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span></span>  
<span data-ttu-id="5ea7c-114">Przycisk po zastosowaniu ScaleTransform —</span><span class="sxs-lookup"><span data-stu-id="5ea7c-114">The button after applying the ScaleTransform</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ea7c-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ea7c-115">Example</span></span>  
 <span data-ttu-id="5ea7c-116">Jak widać na poprzedniej ilustracji, przycisk został przerzucać, ale również została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="5ea7c-116">As you can see from the previous illustration, the button was flipped, but it was also moved.</span></span> <span data-ttu-id="5ea7c-117">Wynika to z przycisku został przerzucać z jego lewym górnym rogu.</span><span class="sxs-lookup"><span data-stu-id="5ea7c-117">That's because the button was flipped from its top left corner.</span></span> <span data-ttu-id="5ea7c-118">Aby przerzucić przycisku w miejscu, chcesz zastosować <xref:System.Windows.Media.ScaleTransform> do jego center, a nie jego rogu.</span><span class="sxs-lookup"><span data-stu-id="5ea7c-118">To flip the button in place, you want to apply the <xref:System.Windows.Media.ScaleTransform> to its center, not its corner.</span></span> <span data-ttu-id="5ea7c-119">Prosty sposób zastosowania <xref:System.Windows.Media.ScaleTransform> do przycisków Centrum jest ustawienie przycisku <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwość 0,5 0,5.</span><span class="sxs-lookup"><span data-stu-id="5ea7c-119">An easy way to apply the <xref:System.Windows.Media.ScaleTransform> to the buttons center is to set the button's <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to 0.5, 0.5.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 <span data-ttu-id="5ea7c-120">![Przycisk poziomo przerzucane o jej środka](./media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="5ea7c-120">![A button flipped horizontally about its center](./media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span></span>  
<span data-ttu-id="5ea7c-121">Przycisk z RenderTransformOrigin cosinus 0,5 0,5</span><span class="sxs-lookup"><span data-stu-id="5ea7c-121">The button with a RenderTransformOrigin of 0.5, 0.5</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ea7c-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ea7c-122">Example</span></span>  
 <span data-ttu-id="5ea7c-123">Aby przerzucić przycisku w pionie, należy ustawić <xref:System.Windows.Media.ScaleTransform> obiektu <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości zamiast jego <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ea7c-123">To flip the button vertically, set the <xref:System.Windows.Media.ScaleTransform> object's <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> property instead of its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 <span data-ttu-id="5ea7c-124">![Przycisk w pionie przerzucane o jej środka](./media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="5ea7c-124">![A button flipped vertically about its center](./media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span></span>  
<span data-ttu-id="5ea7c-125">W pionie odwrócony przycisku</span><span class="sxs-lookup"><span data-stu-id="5ea7c-125">The vertically flipped button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea7c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ea7c-126">See also</span></span>

- [<span data-ttu-id="5ea7c-127">Przegląd Przekształcenia</span><span class="sxs-lookup"><span data-stu-id="5ea7c-127">Transforms Overview</span></span>](../graphics-multimedia/transforms-overview.md)
