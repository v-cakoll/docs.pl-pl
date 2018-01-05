---
title: "Jak uzyskać przezroczystość lub półprzezroczystość elementu interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25245319c02ae376410d71afb7a1e56eda259e99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a><span data-ttu-id="3d209-102">Jak uzyskać przezroczystość lub półprzezroczystość elementu interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="3d209-102">How to: Make a UIElement Transparent or Semi-Transparent</span></span>
<span data-ttu-id="3d209-103">W tym przykładzie pokazano, jak utworzyć <xref:System.Windows.UIElement> przezroczysty lub półprzezroczysty.</span><span class="sxs-lookup"><span data-stu-id="3d209-103">This example shows how to make a <xref:System.Windows.UIElement> transparent or semi-transparent.</span></span> <span data-ttu-id="3d209-104">Do uczynienia elementu przezroczystym lub półprzezroczystym, ustaw jej <xref:System.Windows.UIElement.Opacity%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3d209-104">To make an element transparent or semi-transparent, you set its <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="3d209-105">Wartość `0.0` powoduje, że element jest całkowicie przezroczysty podczas wartość `1.0` powoduje, że element jest całkowicie przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="3d209-105">A value of `0.0` makes the element completely transparent, while a value of `1.0` makes the element completely opaque.</span></span> <span data-ttu-id="3d209-106">Wartość `0.5` powoduje, że element 50% nieprzezroczystych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3d209-106">A value of `0.5` makes the element 50% opaque, and so on.</span></span> <span data-ttu-id="3d209-107">Element <xref:System.Windows.UIElement.Opacity%2A> ustawiono `1.0` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="3d209-107">An element's <xref:System.Windows.UIElement.Opacity%2A> is set to `1.0` by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d209-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d209-108">Example</span></span>  
 <span data-ttu-id="3d209-109">W poniższym przykładzie <xref:System.Windows.UIElement.Opacity%2A> przycisku do `0.25`, ustawianie zawartością (w tym przypadku tekst przycisku) 25% nieprzezroczystego.</span><span class="sxs-lookup"><span data-stu-id="3d209-109">The following example sets the <xref:System.Windows.UIElement.Opacity%2A> of a button to `0.25`, making it and its contents (in this case, the button's text) 25% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 <span data-ttu-id="3d209-110">Jeśli element zawartości mają swoje własne <xref:System.Windows.UIElement.Opacity%2A> ustawienia, te wartości są mnożone przed zawierającego elementy <xref:System.Windows.UIElement.Opacity%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d209-110">If an element's contents have their own <xref:System.Windows.UIElement.Opacity%2A> settings, those values are multiplied against the containing elements <xref:System.Windows.UIElement.Opacity%2A>.</span></span>  
  
 <span data-ttu-id="3d209-111">Poniższy przykład przedstawia przycisk <xref:System.Windows.UIElement.Opacity%2A> do `0.25`i <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Image> kontroli objętych przycisk, aby `0.5`.</span><span class="sxs-lookup"><span data-stu-id="3d209-111">The following example sets a button's <xref:System.Windows.UIElement.Opacity%2A> to `0.25`, and the <xref:System.Windows.UIElement.Opacity%2A> of an <xref:System.Windows.Controls.Image> control contained with in the button to `0.5`.</span></span> <span data-ttu-id="3d209-112">W związku z tym obraz pojawia się 12,5% nieprzezroczyste: 0,25 * 0,5 = 0,125.</span><span class="sxs-lookup"><span data-stu-id="3d209-112">As a result, the image appears 12.5% opaque: 0.25 * 0.5 = 0.125.</span></span>  
  
 [!code-xaml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 <span data-ttu-id="3d209-113">Innym sposobem kontrolować nieprzezroczystość elementu jest skonfigurowanie nieprzezroczystość <xref:System.Windows.Media.Brush> który malowany element.</span><span class="sxs-lookup"><span data-stu-id="3d209-113">Another way to control the opacity of an element is to set the opacity of the <xref:System.Windows.Media.Brush> that paints the element.</span></span> <span data-ttu-id="3d209-114">Takie podejście umożliwia selektywne alter nieprzezroczystość części elementu i zapewnia korzyści wydajności w przypadku elementu <xref:System.Windows.UIElement.Opacity%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3d209-114">This approach enables you to selectively alter the opacity of portions of an element, and provides performance benefits over using the element's <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="3d209-115">W poniższym przykładzie <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush> używana do malowania przycisku <xref:System.Windows.Controls.Control.Background%2A> ma ustawioną wartość `0.25`.</span><span class="sxs-lookup"><span data-stu-id="3d209-115">The following example sets the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush> used to paint the button's <xref:System.Windows.Controls.Control.Background%2A> is set to `0.25`.</span></span> <span data-ttu-id="3d209-116">W związku z tym pędzel tła jest 25% nieprzezroczyste, przy zachowaniu jego zawartości (tekst przycisku) przezroczystości 100%.</span><span class="sxs-lookup"><span data-stu-id="3d209-116">As a result, the brush's background is 25% opaque, but its contents (the button's text) remain 100% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 <span data-ttu-id="3d209-117">Może też kontrolować nieprzezroczystość poszczególnych kolorów w pędzla.</span><span class="sxs-lookup"><span data-stu-id="3d209-117">You may also control the opacity of individual colors within a brush.</span></span> <span data-ttu-id="3d209-118">Aby uzyskać więcej informacji na temat kolorów i pędzle, zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3d209-118">For more information about colors and brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span> <span data-ttu-id="3d209-119">Na przykład przedstawiający sposób Animuj przezroczystość elementu zobacz [Animuj przezroczystość pędzla lub Element](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span><span class="sxs-lookup"><span data-stu-id="3d209-119">For an example showing how to animate an element's opacity, see [Animate the Opacity of an Element or Brush](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span></span>
