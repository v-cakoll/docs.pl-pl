---
title: "Jak animować rozmiar FrameworkElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf31fa1a10748c3c2f6d239d041c72c57a148e1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a><span data-ttu-id="fa544-102">Jak animować rozmiar FrameworkElement</span><span class="sxs-lookup"><span data-stu-id="fa544-102">How to: Animate the Size of a FrameworkElement</span></span>
<span data-ttu-id="fa544-103">Aby animować rozmiar <xref:System.Windows.FrameworkElement>, albo można animować jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości lub użyj animowany <xref:System.Windows.Media.ScaleTransform>.</span><span class="sxs-lookup"><span data-stu-id="fa544-103">To animate the size of a <xref:System.Windows.FrameworkElement>, you can either animate its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties or use an animated <xref:System.Windows.Media.ScaleTransform>.</span></span>  
  
 <span data-ttu-id="fa544-104">W poniższym przykładzie animuje rozmiar dwa przyciski, za pomocą tych dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="fa544-104">In the following example animates the size of two buttons using these two approaches.</span></span> <span data-ttu-id="fa544-105">Jeden z przycisków zmieni się rozmiar przez animację jego <xref:System.Windows.FrameworkElement.Width%2A> właściwości i jedno zmieni się rozmiar przez animację <xref:System.Windows.Media.ScaleTransform> stosowane do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fa544-105">One button is resized by animating its <xref:System.Windows.FrameworkElement.Width%2A> property and another is resized by animating a <xref:System.Windows.Media.ScaleTransform> applied to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span> <span data-ttu-id="fa544-106">Każdy przycisk zawiera tekst.</span><span class="sxs-lookup"><span data-stu-id="fa544-106">Each button contains some text.</span></span> <span data-ttu-id="fa544-107">Początkowo tekstu pojawi się taka sama w obu przycisków, ale jak przyciski zmieniany jest rozmiar, zostaje zniekształcony tekst drugiego przycisku.</span><span class="sxs-lookup"><span data-stu-id="fa544-107">Initially, the text appears the same in both buttons, but as the buttons are resized, the text in the second button becomes distorted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa544-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa544-108">Example</span></span>  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 <span data-ttu-id="fa544-109">Przekształcenie elementu transformacji całego elementu i jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="fa544-109">When you transform an element, the entire element and its contents are transformed.</span></span> <span data-ttu-id="fa544-110">Podczas bezpośrednio zmienić rozmiar elementu, tak jak w przypadku pierwszego przycisku zawartości elementu nie są zmieniany, chyba że ich rozmiar i położenie zależą od rozmiaru jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fa544-110">When you directly alter the size of an element, as in the case of the first button, the element's contents are not resized unless their size and position depend on the size of their parent element.</span></span>  
  
 <span data-ttu-id="fa544-111">Animowanie rozmiar elementu, stosując animowany transformacji do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości zapewnia lepszą wydajność niż animowany jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> bezpośrednio, ponieważ <xref:System.Windows.UIElement.RenderTransform%2A> właściwości wyzwala przebieg układu.</span><span class="sxs-lookup"><span data-stu-id="fa544-111">Animating the size of an element by applying an animated transform to its <xref:System.Windows.UIElement.RenderTransform%2A> property provides better performance than animated its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> directly, because the <xref:System.Windows.UIElement.RenderTransform%2A> property does not trigger a layout pass.</span></span>  
  
 <span data-ttu-id="fa544-112">Aby uzyskać więcej informacji na temat właściwości animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fa544-112">For more information about animating properties, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="fa544-113">Aby uzyskać więcej informacji na temat transformacje, zobacz [przekształca omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fa544-113">For more information about transforms, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>
