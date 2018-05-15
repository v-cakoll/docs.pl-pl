---
title: Jak malować obszar gradientem liniowym
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: ec07a0c33468681f67d086ec3d1d58b378412ff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="e9868-102">Jak malować obszar gradientem liniowym</span><span class="sxs-lookup"><span data-stu-id="e9868-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="e9868-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.LinearGradientBrush> klasy namalować obszar o gradientu liniowego.</span><span class="sxs-lookup"><span data-stu-id="e9868-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="e9868-104">W poniższym przykładzie <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> jest malowany przekątnej gradientu liniowego, który przejścia z żółtym na kolor czerwony, niebieski do Limonowy zielony.</span><span class="sxs-lookup"><span data-stu-id="e9868-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9868-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9868-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="e9868-106">Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie gradientu.</span><span class="sxs-lookup"><span data-stu-id="e9868-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="e9868-107">![Przekątnej gradientu liniowego](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="e9868-107">![Diagonal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="e9868-108">Aby utworzyć poziomego gradientu liniowego, zmienić <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> do (0,0.5) i (1,0.5).</span><span class="sxs-lookup"><span data-stu-id="e9868-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="e9868-109">W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowany poziomego gradientu liniowego.</span><span class="sxs-lookup"><span data-stu-id="e9868-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="e9868-110">Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie gradientu.</span><span class="sxs-lookup"><span data-stu-id="e9868-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="e9868-111">![Poziomy gradient liniowy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="e9868-111">![A horizontal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="e9868-112">Aby utworzyć pionowy gradient liniowy, zmienić <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> do (0.5,0) i (0.5,1).</span><span class="sxs-lookup"><span data-stu-id="e9868-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="e9868-113">W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowany pionowy gradientu liniowego.</span><span class="sxs-lookup"><span data-stu-id="e9868-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="e9868-114">Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie gradientu.</span><span class="sxs-lookup"><span data-stu-id="e9868-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="e9868-115">![Gradient liniowy pionowy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="e9868-115">![Vertical linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9868-116">Przykłady w tym temacie Korzystanie z systemu współrzędnych domyślne ustawienie punkty początkowy i końcowy.</span><span class="sxs-lookup"><span data-stu-id="e9868-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="e9868-117">System współrzędnych domyślna jest określana względem obwiedni: 0 wskazuje 0 procent obwiedni, a wartość 1 oznacza 100 procent obwiedni.</span><span class="sxs-lookup"><span data-stu-id="e9868-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="e9868-118">Ten układ współrzędnych można zmienić, określając <xref:System.Windows.Media.GradientBrush.MappingMode%2A> na wartość <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e9868-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e9868-119">Bezwzględny układ współrzędnych nie jest określana względem obwiedni.</span><span class="sxs-lookup"><span data-stu-id="e9868-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="e9868-120">Wartości są interpretowane bezpośrednio w lokalnej przestrzeni.</span><span class="sxs-lookup"><span data-stu-id="e9868-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="e9868-121">Aby uzyskać dodatkowe przykłady, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="e9868-121">For additional examples, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="e9868-122">Aby uzyskać więcej informacji na temat gradientach i innych typów pędzle zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e9868-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
