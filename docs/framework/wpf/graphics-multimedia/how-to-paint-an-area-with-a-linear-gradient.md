---
title: 'Instrukcje: Malowanie obszaru gradientem liniowym'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 92c9ccd846dbbce043d13e6ba82b9fa8e72fa8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916164"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="f73e9-102">Instrukcje: Malowanie obszaru gradientem liniowym</span><span class="sxs-lookup"><span data-stu-id="f73e9-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="f73e9-103">Ten przykład pokazuje, <xref:System.Windows.Media.LinearGradientBrush> jak używać klasy do malowania obszaru gradientem liniowym.</span><span class="sxs-lookup"><span data-stu-id="f73e9-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="f73e9-104">W poniższym przykładzie <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> kolor jest malowany ukośnym gradientem liniowym, który przechodzi z żółtego do czerwonego do zielonego na zielony.</span><span class="sxs-lookup"><span data-stu-id="f73e9-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f73e9-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f73e9-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="f73e9-106">Na poniższej ilustracji przedstawiono gradient utworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f73e9-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="f73e9-107">![Gradient liniowy ukośny](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="f73e9-107">![Diagonal linear gradient](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="f73e9-108">Aby utworzyć poziomy gradient liniowy, Zmień wartości <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> <xref:System.Windows.Media.LinearGradientBrush> z do (0, 0,5) i (1, 0,5).</span><span class="sxs-lookup"><span data-stu-id="f73e9-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="f73e9-109">W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowany poziom gradientu liniowego.</span><span class="sxs-lookup"><span data-stu-id="f73e9-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="f73e9-110">Na poniższej ilustracji przedstawiono gradient utworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f73e9-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="f73e9-111">![Poziomy gradient liniowy](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="f73e9-111">![A horizontal linear gradient](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="f73e9-112">Aby utworzyć pionowy gradient liniowy, Zmień <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> wartości <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush> do (0,5, 0) i (0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="f73e9-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="f73e9-113">W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowany pionowym gradientem liniowym.</span><span class="sxs-lookup"><span data-stu-id="f73e9-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="f73e9-114">Na poniższej ilustracji przedstawiono gradient utworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f73e9-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="f73e9-115">![Gradient liniowy pionowy](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="f73e9-115">![Vertical linear gradient](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f73e9-116">Przykłady w tym temacie używają domyślnego układu współrzędnych do ustawiania punktów początkowych i punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="f73e9-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="f73e9-117">Domyślny system współrzędnych jest względny w stosunku do pola ograniczenia: wartość 0 oznacza 0 procent obwiedni, a 1 wskazuje 100 procent obwiedni.</span><span class="sxs-lookup"><span data-stu-id="f73e9-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="f73e9-118">Można zmienić ten system współrzędnych przez ustawienie <xref:System.Windows.Media.GradientBrush.MappingMode%2A> właściwości na wartość. <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f73e9-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f73e9-119">Bezwzględny układ współrzędnych nie należy do obwiedni.</span><span class="sxs-lookup"><span data-stu-id="f73e9-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="f73e9-120">Wartości są interpretowane bezpośrednio w miejscu lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f73e9-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="f73e9-121">Aby uzyskać więcej przykładów, zobacz [przykłady pędzli](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="f73e9-121">For additional examples, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="f73e9-122">Aby uzyskać więcej informacji o gradientach i innych typach pędzli, zobacz [malowanie przy użyciu pełnych kolorów i gradientów przegląd](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f73e9-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
