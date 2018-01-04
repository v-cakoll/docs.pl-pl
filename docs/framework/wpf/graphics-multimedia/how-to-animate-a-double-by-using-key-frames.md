---
title: "Jak animować double z wykorzystaniem klatek kluczowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e87717f6e2691142efa54a7e363f1038f8b74c1b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a><span data-ttu-id="6e95f-102">Jak animować double z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="6e95f-102">How to: Animate a Double by Using Key Frames</span></span>
<span data-ttu-id="6e95f-103">W tym przykładzie pokazano, jak można animować właściwości, która przyjmuje wartość <xref:System.Double> przy użyciu klucza ramki.</span><span class="sxs-lookup"><span data-stu-id="6e95f-103">This example shows how to animate the value of a property that takes a <xref:System.Double> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e95f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e95f-104">Example</span></span>  
 <span data-ttu-id="6e95f-105">Poniższy przykład porusza się prostokąt na ekranie.</span><span class="sxs-lookup"><span data-stu-id="6e95f-105">The following example moves a rectangle across a screen.</span></span> <span data-ttu-id="6e95f-106">W przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> stosowane do <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="6e95f-106">The example uses the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.TranslateTransform.X%2A> property of a <xref:System.Windows.Media.TranslateTransform> applied to a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="6e95f-107">Animacja powtarza nieskończoność, używa trzech klatek kluczowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6e95f-107">This animation, which repeats indefinitely, uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="6e95f-108">Podczas pierwszego trzy sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> klasę, aby przenieść prostokąt na ścieżce stałą szybkością z punktu początkowego do 500 pozycji.</span><span class="sxs-lookup"><span data-stu-id="6e95f-108">During the first three seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> class to move the rectangle along a path at a steady rate from its starting position to the 500 position.</span></span> <span data-ttu-id="6e95f-109">Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> utworzyć liniowej przejścia między wartościami.</span><span class="sxs-lookup"><span data-stu-id="6e95f-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="6e95f-110">Na końcu czwarty drugi używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> klasy nagle przesuwać pozycji dalej.</span><span class="sxs-lookup"><span data-stu-id="6e95f-110">At the end of the fourth second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> class to suddenly move the rectangle to the next position.</span></span> <span data-ttu-id="6e95f-111">Odrębny klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> tworzenie nagłym przeskoków między wartościami.</span><span class="sxs-lookup"><span data-stu-id="6e95f-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> create sudden jumps between values.</span></span> <span data-ttu-id="6e95f-112">W tym przykładzie prostokąta znajduje się na pozycji początkowej i nagle pojawia się na 500 pozycji.</span><span class="sxs-lookup"><span data-stu-id="6e95f-112">In this example, the rectangle is at the starting position and then suddenly appears at the 500 position.</span></span>  
  
3.  <span data-ttu-id="6e95f-113">W ostatnim dwóch sekund, używa wystąpienia <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> klasę, aby przenieść prostokąt z powrotem do punktu początkowego.</span><span class="sxs-lookup"><span data-stu-id="6e95f-113">In the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> class to move the rectangle back to its starting position.</span></span> <span data-ttu-id="6e95f-114">Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> utworzyć zmiennej przejścia między wartościami zgodnie z wartością <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e95f-114">Spline key frames like <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> create a variable transition between values according to the value of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="6e95f-115">W tym przykładzie prostokąt rozpoczyna się powoli przenosząc, a następnie przyspiesza wykładniczo do końca segmentu czasu.</span><span class="sxs-lookup"><span data-stu-id="6e95f-115">In this example, the rectangle begins by moving slowly and then speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="6e95f-116">Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="6e95f-116">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="6e95f-117">Spójności z innymi przykładami animacji, użyj wersji kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> obiekt do zastosowania <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="6e95f-117">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="6e95f-118">Alternatywnie podczas stosowania pojedynczego animacji w kodzie, łatwiej jest użyć <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zamiast <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="6e95f-118">Alternatively, when applying a single animation in code, it is simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="6e95f-119">Na przykład zobacz [animowania właściwości bez Using scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="6e95f-119">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e95f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e95f-120">See Also</span></span>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [<span data-ttu-id="6e95f-121">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="6e95f-121">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="6e95f-122">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="6e95f-122">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
