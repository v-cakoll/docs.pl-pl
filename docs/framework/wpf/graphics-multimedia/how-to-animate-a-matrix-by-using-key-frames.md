---
title: Jak animować Matrix z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 8f58b43a870f2c85ae4349965f586a33e2f75a2a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485853"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="3008b-102">Jak animować Matrix z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="3008b-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="3008b-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform> przy użyciu klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="3008b-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3008b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3008b-104">Example</span></span>  
 <span data-ttu-id="3008b-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="3008b-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="3008b-106">W przykładzie użyto <xref:System.Windows.Media.MatrixTransform> obiekt, aby przekształcić wyglądu i położenia <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="3008b-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="3008b-107">Korzysta z tą animację <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> klasy do utworzenia dwóch ramek kluczowych i wykonuje następujące czynności, które z nich:</span><span class="sxs-lookup"><span data-stu-id="3008b-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1.  <span data-ttu-id="3008b-108">Animuje pierwszy <xref:System.Windows.Media.Matrix> podczas pierwszego 0,2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="3008b-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="3008b-109">Przykład zmienia <xref:System.Windows.Media.Matrix.M11%2A> i <xref:System.Windows.Media.Matrix.M12%2A> właściwości <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="3008b-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="3008b-110">Ta zmiana powoduje, że przycisk, aby zwiększyć i stają się nierówne.</span><span class="sxs-lookup"><span data-stu-id="3008b-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="3008b-111">Przykład zmienia także <xref:System.Windows.Media.Matrix.OffsetX%2A> i <xref:System.Windows.Media.Matrix.OffsetY%2A> właściwości, aby przycisk zmienia pozycję.</span><span class="sxs-lookup"><span data-stu-id="3008b-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2.  <span data-ttu-id="3008b-112">Animuje drugi <xref:System.Windows.Media.Matrix> w wersji 1.0 w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="3008b-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="3008b-113">Przycisk przemieszczeniu na inne stanowisko, gdy nie jest już nierówne czy rozciągnięte przycisku.</span><span class="sxs-lookup"><span data-stu-id="3008b-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3.  <span data-ttu-id="3008b-114">Powtarza animacji w nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="3008b-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3008b-115">Klucz klatek, które wynikają z <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> obiektu tworzenie nagłe skoki między wartościami, oznacza to, że ruch animacji jest jerky.</span><span class="sxs-lookup"><span data-stu-id="3008b-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="3008b-116">Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="3008b-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3008b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3008b-117">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [<span data-ttu-id="3008b-118">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="3008b-118">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="3008b-119">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="3008b-119">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
