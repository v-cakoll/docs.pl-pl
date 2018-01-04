---
title: "Jak animować Matrix z wykorzystaniem klatek kluczowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 862e1afdcd823181dff0948fab43b1656b85f721
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="523ff-102">Jak animować Matrix z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="523ff-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="523ff-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform> przy użyciu klucza ramki.</span><span class="sxs-lookup"><span data-stu-id="523ff-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="523ff-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="523ff-104">Example</span></span>  
 <span data-ttu-id="523ff-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="523ff-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="523ff-106">W przykładzie użyto <xref:System.Windows.Media.MatrixTransform> obiekt, aby przekształcić wyglądu i położenia <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="523ff-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="523ff-107">Używa tego animacji <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> klas do utworzenia dwóch ramek kluczowych i wykonuje następujące z nich:</span><span class="sxs-lookup"><span data-stu-id="523ff-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1.  <span data-ttu-id="523ff-108">Animuje pierwszy <xref:System.Windows.Media.Matrix> podczas pierwszego 0,2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="523ff-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="523ff-109">Przykład zmiany <xref:System.Windows.Media.Matrix.M11%2A> i <xref:System.Windows.Media.Matrix.M12%2A> właściwości <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="523ff-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="523ff-110">Ta zmiana powoduje, że przycisk, aby rozciągać i stać się niesymetryczna.</span><span class="sxs-lookup"><span data-stu-id="523ff-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="523ff-111">W przykładzie również zmieniono <xref:System.Windows.Media.Matrix.OffsetX%2A> i <xref:System.Windows.Media.Matrix.OffsetY%2A> właściwości tak, aby przycisk zmienia pozycję.</span><span class="sxs-lookup"><span data-stu-id="523ff-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2.  <span data-ttu-id="523ff-112">Animuje drugi <xref:System.Windows.Media.Matrix> w sekundach 1.0.</span><span class="sxs-lookup"><span data-stu-id="523ff-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="523ff-113">Przycisk przemieszczeniu na inne stanowisko, gdy przycisk jest już niesymetryczna lub rozciągnięty.</span><span class="sxs-lookup"><span data-stu-id="523ff-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3.  <span data-ttu-id="523ff-114">Powtarza animacji w nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="523ff-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="523ff-115">Klucz ramek, które pochodzą z <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> obiekt tworzenie nagłym przechodzi między wartościami, przenoszenie animacji jest jerky.</span><span class="sxs-lookup"><span data-stu-id="523ff-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="523ff-116">Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="523ff-116">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523ff-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="523ff-117">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [<span data-ttu-id="523ff-118">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="523ff-118">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="523ff-119">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="523ff-119">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
