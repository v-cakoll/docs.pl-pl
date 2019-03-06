---
title: 'Instrukcje: Uzyskaj przezroczystość lub półprzezroczystość elementu interfejsu użytkownika'
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 1de9a7e11fee241ecb71242e9808e77b7e5e63b0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370530"
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a><span data-ttu-id="0bd98-102">Instrukcje: Uzyskaj przezroczystość lub półprzezroczystość elementu interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="0bd98-102">How to: Make a UIElement Transparent or Semi-Transparent</span></span>
<span data-ttu-id="0bd98-103">W tym przykładzie pokazano, jak wprowadzić <xref:System.Windows.UIElement> przezroczystym lub półprzezroczystym.</span><span class="sxs-lookup"><span data-stu-id="0bd98-103">This example shows how to make a <xref:System.Windows.UIElement> transparent or semi-transparent.</span></span> <span data-ttu-id="0bd98-104">Do uczynienia elementu przezroczystym lub półprzezroczystym, ustaw jego <xref:System.Windows.UIElement.Opacity%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0bd98-104">To make an element transparent or semi-transparent, you set its <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="0bd98-105">Wartość `0.0` sprawia, że element jest całkowicie przezroczysty podczas wartość `1.0` sprawia, że element jest całkowicie nieprzezroczysty.</span><span class="sxs-lookup"><span data-stu-id="0bd98-105">A value of `0.0` makes the element completely transparent, while a value of `1.0` makes the element completely opaque.</span></span> <span data-ttu-id="0bd98-106">Wartość `0.5` sprawia, że element 50% nieprzezroczystych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="0bd98-106">A value of `0.5` makes the element 50% opaque, and so on.</span></span> <span data-ttu-id="0bd98-107">Element <xref:System.Windows.UIElement.Opacity%2A> ustawiono `1.0` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0bd98-107">An element's <xref:System.Windows.UIElement.Opacity%2A> is set to `1.0` by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bd98-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0bd98-108">Example</span></span>  
 <span data-ttu-id="0bd98-109">Poniższy przykład ustawia <xref:System.Windows.UIElement.Opacity%2A> przycisku, aby `0.25`, co on i jego zawartości (w tym przypadku tekst przycisku) 25% nieprzezroczystości.</span><span class="sxs-lookup"><span data-stu-id="0bd98-109">The following example sets the <xref:System.Windows.UIElement.Opacity%2A> of a button to `0.25`, making it and its contents (in this case, the button's text) 25% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 <span data-ttu-id="0bd98-110">Jeśli element zawartości mają swoje własne <xref:System.Windows.UIElement.Opacity%2A> ustawienia, te wartości są mnożone przed zawierającego elementy <xref:System.Windows.UIElement.Opacity%2A>.</span><span class="sxs-lookup"><span data-stu-id="0bd98-110">If an element's contents have their own <xref:System.Windows.UIElement.Opacity%2A> settings, those values are multiplied against the containing elements <xref:System.Windows.UIElement.Opacity%2A>.</span></span>  
  
 <span data-ttu-id="0bd98-111">W poniższym przykładzie ustawiono przycisku <xref:System.Windows.UIElement.Opacity%2A> do `0.25`i <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Image> kontroli zawarte w przycisk, aby `0.5`.</span><span class="sxs-lookup"><span data-stu-id="0bd98-111">The following example sets a button's <xref:System.Windows.UIElement.Opacity%2A> to `0.25`, and the <xref:System.Windows.UIElement.Opacity%2A> of an <xref:System.Windows.Controls.Image> control contained with in the button to `0.5`.</span></span> <span data-ttu-id="0bd98-112">W rezultacie obraz jest wyświetlany 12,5% nieprzezroczysty: 0.25 \* 0.5 = 0.125.</span><span class="sxs-lookup"><span data-stu-id="0bd98-112">As a result, the image appears 12.5% opaque: 0.25 \* 0.5 = 0.125.</span></span>  
  
 [!code-xaml[brushsamples_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 <span data-ttu-id="0bd98-113">Innym sposobem na kontrolowanie nieprzezroczystość elementu jest aby ustawić nieprzezroczystość <xref:System.Windows.Media.Brush> , malowany element.</span><span class="sxs-lookup"><span data-stu-id="0bd98-113">Another way to control the opacity of an element is to set the opacity of the <xref:System.Windows.Media.Brush> that paints the element.</span></span> <span data-ttu-id="0bd98-114">Takie podejście umożliwia selektywne zmienić nieprzezroczystość części elementu oraz zapewnia korzyści w wydajności przy użyciu elementu <xref:System.Windows.UIElement.Opacity%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0bd98-114">This approach enables you to selectively alter the opacity of portions of an element, and provides performance benefits over using the element's <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="0bd98-115">Poniższy przykład ustawia <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush> używany do rysowania przycisku <xref:System.Windows.Controls.Control.Background%2A> ustawiono `0.25`.</span><span class="sxs-lookup"><span data-stu-id="0bd98-115">The following example sets the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush> used to paint the button's <xref:System.Windows.Controls.Control.Background%2A> is set to `0.25`.</span></span> <span data-ttu-id="0bd98-116">W rezultacie pędzel tła jest 25% nieprzezroczyste, ale jego zawartość (tekst przycisku) pozostają nieprzezroczyste w 100%.</span><span class="sxs-lookup"><span data-stu-id="0bd98-116">As a result, the brush's background is 25% opaque, but its contents (the button's text) remain 100% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 <span data-ttu-id="0bd98-117">Może także kontrolować nieprzezroczystość poszczególnych kolory pędzla.</span><span class="sxs-lookup"><span data-stu-id="0bd98-117">You may also control the opacity of individual colors within a brush.</span></span> <span data-ttu-id="0bd98-118">Aby uzyskać więcej informacji na temat kolorów i pędzle, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0bd98-118">For more information about colors and brushes, see [Painting with Solid Colors and Gradients Overview](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span> <span data-ttu-id="0bd98-119">Aby uzyskać przykład pokazujący sposób animować nieprzezroczystość elementu, zobacz [animować nieprzezroczystość elementu lub pędzla](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span><span class="sxs-lookup"><span data-stu-id="0bd98-119">For an example showing how to animate an element's opacity, see [Animate the Opacity of an Element or Brush](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span></span>
