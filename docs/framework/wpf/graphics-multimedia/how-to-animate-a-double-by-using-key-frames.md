---
title: 'Instrukcje: Animowanie elementu double przy użyciu klatek kluczowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 73cbeab8aee566313bad8e8a18a5500374287de0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010205"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a><span data-ttu-id="32a4d-102">Instrukcje: Animowanie elementu double przy użyciu klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="32a4d-102">How to: Animate a Double by Using Key Frames</span></span>
<span data-ttu-id="32a4d-103">W tym przykładzie pokazano, jak animować wartość właściwości, która przyjmuje <xref:System.Double> przy użyciu klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="32a4d-103">This example shows how to animate the value of a property that takes a <xref:System.Double> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32a4d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="32a4d-104">Example</span></span>  
 <span data-ttu-id="32a4d-105">Poniższy przykład powoduje przeniesienie prostokąt na ekranie.</span><span class="sxs-lookup"><span data-stu-id="32a4d-105">The following example moves a rectangle across a screen.</span></span> <span data-ttu-id="32a4d-106">W przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> dotyczą <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="32a4d-106">The example uses the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.TranslateTransform.X%2A> property of a <xref:System.Windows.Media.TranslateTransform> applied to a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="32a4d-107">Animacja jest powtarzany na czas nieokreślony, używa trzech ramek kluczowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="32a4d-107">This animation, which repeats indefinitely, uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="32a4d-108">Podczas pierwszego trzy sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> klasy, aby przenieść prostokąt na ścieżce według stałej stawki z punktu początkowego do 500 pozycji.</span><span class="sxs-lookup"><span data-stu-id="32a4d-108">During the first three seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> class to move the rectangle along a path at a steady rate from its starting position to the 500 position.</span></span> <span data-ttu-id="32a4d-109">Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> utworzyć płynne przejście liniowy między wartościami.</span><span class="sxs-lookup"><span data-stu-id="32a4d-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="32a4d-110">Na koniec czwarte sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> klasy nagle przenieść prostokąt na pozycji dalej.</span><span class="sxs-lookup"><span data-stu-id="32a4d-110">At the end of the fourth second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> class to suddenly move the rectangle to the next position.</span></span> <span data-ttu-id="32a4d-111">Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> tworzenie nagłe skoki między wartościami.</span><span class="sxs-lookup"><span data-stu-id="32a4d-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> create sudden jumps between values.</span></span> <span data-ttu-id="32a4d-112">W tym przykładzie prostokąta znajduje się na pozycji początkowej i następnie nagle pojawia się na 500 pozycji.</span><span class="sxs-lookup"><span data-stu-id="32a4d-112">In this example, the rectangle is at the starting position and then suddenly appears at the 500 position.</span></span>  
  
3. <span data-ttu-id="32a4d-113">W ostatnim dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> klasy, aby przenieść prostokąt z powrotem do jego pozycja początkowa.</span><span class="sxs-lookup"><span data-stu-id="32a4d-113">In the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> class to move the rectangle back to its starting position.</span></span> <span data-ttu-id="32a4d-114">Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartością <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="32a4d-114">Spline key frames like <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> create a variable transition between values according to the value of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="32a4d-115">W tym przykładzie rozpoczyna się powoli przenosząc i następnie przyspiesza wykładniczo w kierunku końca odcinka czasu.</span><span class="sxs-lookup"><span data-stu-id="32a4d-115">In this example, the rectangle begins by moving slowly and then speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="32a4d-116">Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="32a4d-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="32a4d-117">Aby zachować spójność z innymi przykładami animacji, użyj wersji kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> obiekt, aby zastosować <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="32a4d-117">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="32a4d-118">Alternatywnie, stosując jednej animacji w kodzie, jest łatwiejszy w obsłudze <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zamiast <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="32a4d-118">Alternatively, when applying a single animation in code, it is simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="32a4d-119">Aby uzyskać przykład, zobacz [animować właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="32a4d-119">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a4d-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32a4d-120">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [<span data-ttu-id="32a4d-121">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="32a4d-121">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="32a4d-122">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="32a4d-122">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
