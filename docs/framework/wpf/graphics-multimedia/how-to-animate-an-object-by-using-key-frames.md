---
title: 'Instrukcje: Animowanie obiektu przy użyciu klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933907"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="0d1aa-102">Instrukcje: Animowanie obiektu przy użyciu klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="0d1aa-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="0d1aa-103">Ten przykład pokazuje, jak animować obiekt, który w tym przykładzie jest <xref:System.Windows.Controls.Page.Background%2A> właściwością <xref:System.Windows.Controls.Page> kontrolki, przy użyciu klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d1aa-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d1aa-104">Example</span></span>  
 <span data-ttu-id="0d1aa-105">Poniższy przykład używa <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasy do animowania zmian <xref:System.Windows.Controls.Page.Background%2A> koloru właściwości <xref:System.Windows.Controls.Page> formantu.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="0d1aa-106">Przykład animacji zmienia się w inny Pędzel tła w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="0d1aa-107">Ta animacja używa klasy <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> , aby utworzyć trzy różne kluczowe klatki.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="0d1aa-108">Animacja używa kluczowych klatek w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0d1aa-108">The animation uses key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="0d1aa-109">Na końcu pierwszej sekundy program Animuj wystąpienie <xref:System.Windows.Media.LinearGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="0d1aa-110">W tej sekcji przykładu stosuje się gradient liniowy do koloru tła, dzięki czemu kolory z żółtej do pomarańczy są zmieniane na czerwony.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2. <span data-ttu-id="0d1aa-111">Na końcu kolejnej sekundy program Animuj wystąpienie <xref:System.Windows.Media.RadialGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="0d1aa-112">W tej sekcji przykładu stosuje się gradient promieniowy do koloru tła, dzięki czemu kolory z czerni do czerni mają być czarne.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3. <span data-ttu-id="0d1aa-113">Na końcu trzeciej sekundy program Animuj wystąpienie <xref:System.Windows.Media.DrawingBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="0d1aa-114">W tej sekcji przykładu stosuje się wzór szachownicy do tła.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4. <span data-ttu-id="0d1aa-115">Animacja rozpocznie się ponownie i powtarza się w nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d1aa-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>jest jedynym typem ramki klucza, której można użyć z <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasą.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="0d1aa-117">Kluczowe klatki, <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> takie jak tworzenie nagłych zmian w wartości, oznacza to, że kolor zmiany w tym przykładzie wystąpił nagle.</span><span class="sxs-lookup"><span data-stu-id="0d1aa-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="0d1aa-118">Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji klatki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="0d1aa-118">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d1aa-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d1aa-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="0d1aa-120">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="0d1aa-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="0d1aa-121">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="0d1aa-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
