---
title: Jak animować geometrię prostokąta z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344678"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="1d49b-102">Jak animować geometrię prostokąta z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="1d49b-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="1d49b-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.RectangleGeometry.Rect%2A> właściwość a <xref:System.Windows.Media.RectangleGeometry> za pomocą klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="1d49b-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d49b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d49b-104">Example</span></span>  
 <span data-ttu-id="1d49b-105">W poniższym przykładzie <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> użyto <xref:System.Windows.Media.RectangleGeometry.Rect%2A> klasy do <xref:System.Windows.Media.RectangleGeometry>animowania właściwości . .</span><span class="sxs-lookup"><span data-stu-id="1d49b-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="1d49b-106">Ta animacja wykorzystuje trzy klatki kluczowe w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1d49b-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="1d49b-107">W ciągu pierwszych dwóch sekund używa <xref:System.Windows.Media.Animation.LinearRectKeyFrame> wystąpienia klasy do animowania stopniowej zmiany pozycji, szerokości i wysokości prostokąta.</span><span class="sxs-lookup"><span data-stu-id="1d49b-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="1d49b-108">Liniowe klatki <xref:System.Windows.Media.Animation.LinearRectKeyFrame> kluczowe, takie jak tworzenie płynnego liniowego przejścia między wartościami.</span><span class="sxs-lookup"><span data-stu-id="1d49b-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="1d49b-109">Pod koniec następnej połowy sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> klasy, aby nagle zmniejszyć wysokość prostokąta.</span><span class="sxs-lookup"><span data-stu-id="1d49b-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="1d49b-110">Dyskretne klatki <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> kluczowe, takie jak tworzenie nagłych zmian między wartościami, to znaczy, spadek wysokości występuje szybko i nie jest subtelny.</span><span class="sxs-lookup"><span data-stu-id="1d49b-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="1d49b-111">W ciągu ostatnich dwóch sekund używa <xref:System.Windows.Media.Animation.SplineRectKeyFrame> wystąpienia klasy, aby zmienić prostokąt z powrotem do jego pierwotnego rozmiaru i położenia.</span><span class="sxs-lookup"><span data-stu-id="1d49b-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="1d49b-112">Klatki kluczowe splajnu, takie jak <xref:System.Windows.Media.Animation.SplineRectKeyFrame> tworzenie <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> zmiennego przejścia między wartościami zgodnie z wartościami właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d49b-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="1d49b-113">W tym przykładzie zmiana rozpoczyna się powoli i przyspiesza wykładniczo pod koniec segmentu czasu.</span><span class="sxs-lookup"><span data-stu-id="1d49b-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="1d49b-114">Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="1d49b-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d49b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d49b-115">See also</span></span>

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [<span data-ttu-id="1d49b-116">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="1d49b-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="1d49b-117">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="1d49b-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
