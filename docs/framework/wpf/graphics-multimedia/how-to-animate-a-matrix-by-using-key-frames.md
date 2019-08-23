---
title: 'Instrukcje: Animowanie elementu Matrix przy użyciu klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 6aa3e27cdfda7597c9b6acbf2980a2774f2b667b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963022"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="b43f8-102">Instrukcje: Animowanie elementu Matrix przy użyciu klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="b43f8-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="b43f8-103">Ten przykład pokazuje, jak animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> Właściwość <xref:System.Windows.Media.MatrixTransform> z przy użyciu klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="b43f8-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b43f8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b43f8-104">Example</span></span>  
 <span data-ttu-id="b43f8-105">Poniższy przykład używa <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> klasy do <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animowania właściwości <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="b43f8-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="b43f8-106">W przykładzie zastosowano <xref:System.Windows.Media.MatrixTransform> obiekt do przekształcenia wyglądu i położenia. <xref:System.Windows.Controls.Button></span><span class="sxs-lookup"><span data-stu-id="b43f8-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="b43f8-107">Ta animacja używa <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> klasy do tworzenia dwóch kluczowych klatek i wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b43f8-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="b43f8-108">Animuj pierwszy <xref:System.Windows.Media.Matrix> w ciągu pierwszych 0,2 sekund.</span><span class="sxs-lookup"><span data-stu-id="b43f8-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="b43f8-109">Przykład zmienia <xref:System.Windows.Media.Matrix.M11%2A> właściwości <xref:System.Windows.Media.Matrix.M12%2A>i. <xref:System.Windows.Media.Matrix></span><span class="sxs-lookup"><span data-stu-id="b43f8-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="b43f8-110">Ta zmiana powoduje, że przycisk rozciąga się i stanie się skośny.</span><span class="sxs-lookup"><span data-stu-id="b43f8-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="b43f8-111">Przykład zmienia <xref:System.Windows.Media.Matrix.OffsetX%2A> również właściwości i <xref:System.Windows.Media.Matrix.OffsetY%2A> tak, aby przycisk zmienia pozycję.</span><span class="sxs-lookup"><span data-stu-id="b43f8-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="b43f8-112">Animuj sekundę <xref:System.Windows.Media.Matrix> o 1,0 sekund.</span><span class="sxs-lookup"><span data-stu-id="b43f8-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="b43f8-113">Przycisk jest przesuwany do innego położenia, gdy przycisk nie jest już skośny lub rozciągany.</span><span class="sxs-lookup"><span data-stu-id="b43f8-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="b43f8-114">Powtarza animację na czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="b43f8-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b43f8-115">Klatki kluczowe, które pochodzą od <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> obiektu, tworzą nagłe uskoki między wartościami, czyli przenoszenie animacji jest Jerky.</span><span class="sxs-lookup"><span data-stu-id="b43f8-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="b43f8-116">Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji klatki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="b43f8-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43f8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b43f8-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="b43f8-118">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="b43f8-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="b43f8-119">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="b43f8-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
