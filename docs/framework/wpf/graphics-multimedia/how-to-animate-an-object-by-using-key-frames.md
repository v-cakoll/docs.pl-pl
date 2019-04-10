---
title: 'Instrukcje: Animowanie obiektu przy użyciu klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: b0a0f7c00125a43228a2658415b72f4d541f37be
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315845"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="9688f-102">Instrukcje: Animowanie obiektu przy użyciu klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="9688f-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="9688f-103">W tym przykładzie pokazano, jak animować obiekt, który w tym przykładzie jest <xref:System.Windows.Controls.Page.Background%2A> właściwość <xref:System.Windows.Controls.Page> kontroli przy użyciu klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="9688f-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9688f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9688f-104">Example</span></span>  
 <span data-ttu-id="9688f-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasy, aby animować kolor zmienia się dla <xref:System.Windows.Controls.Page.Background%2A> właściwość <xref:System.Windows.Controls.Page> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9688f-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="9688f-106">Przykład animacji zmienia się na pędzel tła różnych w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="9688f-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="9688f-107">Korzysta z tą animację <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> klasy w celu utworzenia trzech różnych klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="9688f-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="9688f-108">Animacja korzysta z klatkami kluczowymi w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9688f-108">The animation uses key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="9688f-109">Na końcu pierwszego sekundę animuje wystąpienie <xref:System.Windows.Media.LinearGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="9688f-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="9688f-110">Ta sekcja przykładu dotyczy gradientu liniowego kolor tła, tak aby kolor przechodzi z żółtym na pomarańczowy na czerwony.</span><span class="sxs-lookup"><span data-stu-id="9688f-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2. <span data-ttu-id="9688f-111">Na koniec następnej sekundy animuje wystąpienie <xref:System.Windows.Media.RadialGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="9688f-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="9688f-112">Ta sekcja przykładu dotyczy gradient promieniowy kolor tła, tak aby kolor zmienia się od białego na niebieski na czarny.</span><span class="sxs-lookup"><span data-stu-id="9688f-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3. <span data-ttu-id="9688f-113">Na koniec trzeciego sekundę animuje wystąpienie <xref:System.Windows.Media.DrawingBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="9688f-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="9688f-114">Ta sekcja przykład dotyczy wzorzec szachownicy tła.</span><span class="sxs-lookup"><span data-stu-id="9688f-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4. <span data-ttu-id="9688f-115">Animacja rozpoczyna się od nowa i jest powtarzany na czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="9688f-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> <span data-ttu-id="9688f-116">jest to jedyny typ używanego przy użyciu klatek kluczowych <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasy.</span><span class="sxs-lookup"><span data-stu-id="9688f-116">is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="9688f-117">Klucz ramek, takich jak <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> tworzenie nagłe zmiany w wartościach, to znaczy, zmiany kolorów w tym przykładzie występuje nieoczekiwanie.</span><span class="sxs-lookup"><span data-stu-id="9688f-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="9688f-118">Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="9688f-118">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9688f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9688f-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="9688f-120">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="9688f-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="9688f-121">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="9688f-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
