---
title: "Jak animować obiekt z wykorzystaniem klatek kluczowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71feb0ecef7a6356c95b843fbc2657ad2e4a7996
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="f2508-102">Jak animować obiekt z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="f2508-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="f2508-103">W tym przykładzie pokazano, jak animować obiekt, który w tym przykładzie jest <xref:System.Windows.Controls.Page.Background%2A> właściwość <xref:System.Windows.Controls.Page> formantu przy użyciu klucza ramki.</span><span class="sxs-lookup"><span data-stu-id="f2508-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2508-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2508-104">Example</span></span>  
 <span data-ttu-id="f2508-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasy animacji kolorów zmiany dla <xref:System.Windows.Controls.Page.Background%2A> właściwość <xref:System.Windows.Controls.Page> formantu.</span><span class="sxs-lookup"><span data-stu-id="f2508-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="f2508-106">Przykład zmiany animacji pędzel tła różnych w regularnych odstępach czasu.</span><span class="sxs-lookup"><span data-stu-id="f2508-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="f2508-107">Używa tego animacji <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> klasy w celu utworzenia trzech różnych klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="f2508-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="f2508-108">Animacja używa klatek kluczowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f2508-108">The animation uses key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="f2508-109">Na końcu pierwszego sekundę animuje wystąpienia <xref:System.Windows.Media.LinearGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="f2508-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="f2508-110">Ta sekcja przykładu dotyczy gradientu liniowego kolor tła, tak aby kolor przejścia z żółtym na pomarańczowy na czerwony.</span><span class="sxs-lookup"><span data-stu-id="f2508-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2.  <span data-ttu-id="f2508-111">Po zakończeniu następnej sekundy animuje wystąpienia <xref:System.Windows.Media.RadialGradientBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="f2508-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="f2508-112">Ta sekcja przykładu dotyczy gradient promieniowy kolor tła, tak aby kolor przejścia od białego na niebieski na kolor czarny.</span><span class="sxs-lookup"><span data-stu-id="f2508-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3.  <span data-ttu-id="f2508-113">Na końcu drugiej danej wejściowej trzecie animuje wystąpienia <xref:System.Windows.Media.DrawingBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="f2508-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="f2508-114">Ta sekcja przykładu dotyczy wzorzec szachownicy tła.</span><span class="sxs-lookup"><span data-stu-id="f2508-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4.  <span data-ttu-id="f2508-115">Animacja rozpoczyna się od nowa i nieskończoność powtarza się.</span><span class="sxs-lookup"><span data-stu-id="f2508-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2508-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>jest to jedyny typ klucza ramki, w której można używać z <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasy.</span><span class="sxs-lookup"><span data-stu-id="f2508-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="f2508-117">Klucz ramek, takich jak <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> utworzyć nagłym zmian w wartości, oznacza to, zmiany kolorów w tym przykładzie występują nagle.</span><span class="sxs-lookup"><span data-stu-id="f2508-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="f2508-118">Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="f2508-118">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2508-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2508-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [<span data-ttu-id="f2508-120">Omówienie klucza poklatkowych</span><span class="sxs-lookup"><span data-stu-id="f2508-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="f2508-121">Klucz ramki — tematy porad</span><span class="sxs-lookup"><span data-stu-id="f2508-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
