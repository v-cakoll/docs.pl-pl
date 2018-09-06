---
title: Jak malować obszar gradientem liniowym
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: aee9931fc366131ae492891cc4d0fff70b4a4441
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43780000"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="0e0ef-102">Jak malować obszar gradientem liniowym</span><span class="sxs-lookup"><span data-stu-id="0e0ef-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="0e0ef-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.LinearGradientBrush> klasy Maluj obszar gradientem liniowym.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="0e0ef-104">W poniższym przykładzie <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> jest malowany przechodzi z żółtym kolor czerwony, niebieski do Limonowozielony Ukośny gradient liniowy.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e0ef-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e0ef-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="0e0ef-106">Poniższa ilustracja przedstawia gradientu utworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="0e0ef-107">![Po przekątnej gradientu liniowego](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="0e0ef-107">![Diagonal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="0e0ef-108">Aby utworzyć poziomego gradientu liniowego, zmienić <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> do (0,0.5) i (1,0.5).</span><span class="sxs-lookup"><span data-stu-id="0e0ef-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="0e0ef-109">W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowany poziomego gradientu liniowego.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="0e0ef-110">Poniższa ilustracja przedstawia gradientu utworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="0e0ef-111">![Poziomy gradient liniowy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="0e0ef-111">![A horizontal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="0e0ef-112">Aby utworzyć pionowe gradientu liniowego, zmienić <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> do (0.5,0) i (0.5,1).</span><span class="sxs-lookup"><span data-stu-id="0e0ef-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="0e0ef-113">W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowane pionowy gradientem liniowym.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="0e0ef-114">Poniższa ilustracja przedstawia gradientu utworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="0e0ef-115">![Gradient liniowy pionowy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="0e0ef-115">![Vertical linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e0ef-116">Przykłady w tym temacie na użytek w układzie współrzędnych domyślne ustawienie punktach i punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="0e0ef-117">System współrzędnych domyślne są określane względem obwiedni: 0 oznacza wartość 0 procent obwiedni, a wartość 1 oznacza 100 procent obwiedni.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="0e0ef-118">Ten układ współrzędnych można zmienić, określając <xref:System.Windows.Media.GradientBrush.MappingMode%2A> właściwości na wartość <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0e0ef-119">Bezwzględnych współrzędnych jest względem obwiedni.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="0e0ef-120">Wartości są interpretowane bezpośrednio w przestrzeni lokalnej.</span><span class="sxs-lookup"><span data-stu-id="0e0ef-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="0e0ef-121">Aby uzyskać więcej przykładów, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="0e0ef-121">For additional examples, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="0e0ef-122">Aby uzyskać więcej informacji na temat gradientów oraz inne rodzaje pędzle, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0e0ef-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
