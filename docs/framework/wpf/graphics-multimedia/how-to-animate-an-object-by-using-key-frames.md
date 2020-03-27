---
title: Jak animować obiekt z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344705"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="5d100-102">Jak animować obiekt z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="5d100-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="5d100-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Controls.Page.Background%2A> obiekt, <xref:System.Windows.Controls.Page> który w tym przykładzie jest właściwością formantu, przy użyciu klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="5d100-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d100-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d100-104">Example</span></span>  
 <span data-ttu-id="5d100-105">W poniższym przykładzie <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> użyto klasy do <xref:System.Windows.Controls.Page.Background%2A> animowania <xref:System.Windows.Controls.Page> zmian kolorów właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="5d100-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="5d100-106">Przykładowa animacja zmienia się na inny pędzel tła w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="5d100-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="5d100-107">Ta animacja <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> używa klasy do utworzenia trzech różnych klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="5d100-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="5d100-108">Animacja używa klatek kluczowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5d100-108">The animation uses key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="5d100-109">Na końcu pierwszej sekundy animuje wystąpienie <xref:System.Windows.Media.LinearGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="5d100-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="5d100-110">W tej sekcji przykładu stosuje się gradient liniowy do koloru tła, dzięki czemu kolor przechodzi z żółtego na pomarańczowy na czerwony.</span><span class="sxs-lookup"><span data-stu-id="5d100-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2. <span data-ttu-id="5d100-111">Na końcu następnej sekundy animuje wystąpienie <xref:System.Windows.Media.RadialGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="5d100-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="5d100-112">W tej sekcji przykładu stosuje gradient promieniowy do koloru tła, dzięki czemu kolor przechodzi z białego na niebieski na czarny.</span><span class="sxs-lookup"><span data-stu-id="5d100-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3. <span data-ttu-id="5d100-113">Na końcu trzeciej sekundy animuje wystąpienie <xref:System.Windows.Media.DrawingBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="5d100-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="5d100-114">W tej sekcji przykładu stosuje się wzorzec szachownicy do tła.</span><span class="sxs-lookup"><span data-stu-id="5d100-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4. <span data-ttu-id="5d100-115">Animacja rozpoczyna się ponownie i powtarza się przez czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="5d100-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d100-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>jest jedynym typem klatki kluczowej, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> której można używać z klasą.</span><span class="sxs-lookup"><span data-stu-id="5d100-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="5d100-117">Klatki kluczowe, takie jak <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> tworzenie nagłych zmian wartości, to znaczy, zmiany kolorów w tym przykładzie występują nagle.</span><span class="sxs-lookup"><span data-stu-id="5d100-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="5d100-118">Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="5d100-118">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d100-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d100-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="5d100-120">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="5d100-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="5d100-121">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="5d100-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
