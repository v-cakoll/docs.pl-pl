---
title: Jak animować Matrix z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344918"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="864ab-102">Jak animować Matrix z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="864ab-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="864ab-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość a <xref:System.Windows.Media.MatrixTransform> za pomocą klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="864ab-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="864ab-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="864ab-104">Example</span></span>  
 <span data-ttu-id="864ab-105">W poniższym przykładzie <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> użyto <xref:System.Windows.Media.MatrixTransform.Matrix%2A> klasy do <xref:System.Windows.Media.MatrixTransform>animowania właściwości . .</span><span class="sxs-lookup"><span data-stu-id="864ab-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="864ab-106">W przykładzie <xref:System.Windows.Media.MatrixTransform> użyto obiektu do przekształcenia wyglądu i położenia pliku <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="864ab-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="864ab-107">Ta animacja <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> używa klasy do utworzenia dwóch klatek kluczowych i wykonuje następujące czynności z nimi:</span><span class="sxs-lookup"><span data-stu-id="864ab-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="864ab-108">Animowanie pierwszego <xref:System.Windows.Media.Matrix> w ciągu pierwszych 0,2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="864ab-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="864ab-109">W przykładzie <xref:System.Windows.Media.Matrix.M11%2A> <xref:System.Windows.Media.Matrix.M12%2A> zmienia się <xref:System.Windows.Media.Matrix>właściwości .</span><span class="sxs-lookup"><span data-stu-id="864ab-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="864ab-110">Ta zmiana powoduje, że przycisk się rozciąga i staje się pochylony.</span><span class="sxs-lookup"><span data-stu-id="864ab-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="864ab-111">W przykładzie <xref:System.Windows.Media.Matrix.OffsetX%2A> również <xref:System.Windows.Media.Matrix.OffsetY%2A> zmienia właściwości i tak, aby przycisk zmienia położenie.</span><span class="sxs-lookup"><span data-stu-id="864ab-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="864ab-112">Animowanie drugiego <xref:System.Windows.Media.Matrix> w 1,0 sekundy.</span><span class="sxs-lookup"><span data-stu-id="864ab-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="864ab-113">Przycisk przesuwa się w inne miejsce, gdy przycisk nie jest już skośny lub rozciągnięty.</span><span class="sxs-lookup"><span data-stu-id="864ab-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="864ab-114">Powtarza animację przez czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="864ab-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="864ab-115">Klatki kluczowe, które <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> wynikają z obiektu, tworzą nagłe skoki między wartościami, czyli ruch animacji jest szarpany.</span><span class="sxs-lookup"><span data-stu-id="864ab-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="864ab-116">Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="864ab-116">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="864ab-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="864ab-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="864ab-118">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="864ab-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="864ab-119">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="864ab-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
