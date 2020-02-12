---
title: Jak ustawić właściwości wysokości elementu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 6500af3c637092820e538d79894d600d617953bf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124289"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="be9cf-102">Jak ustawić właściwości wysokości elementu</span><span class="sxs-lookup"><span data-stu-id="be9cf-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="be9cf-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="be9cf-103">Example</span></span>  
 <span data-ttu-id="be9cf-104">Ten przykład wizualnie pokazuje różnice między zachowaniem renderowania a czterema właściwościami dotyczącymi wysokości w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="be9cf-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="be9cf-105">Klasa <xref:System.Windows.FrameworkElement> uwidacznia cztery właściwości, które opisują charakterystykę wysokości elementu.</span><span class="sxs-lookup"><span data-stu-id="be9cf-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="be9cf-106">Te cztery właściwości mogą powodować konflikt i gdy tak się stanie, wartość, która ma pierwszeństwo, jest określana w następujący sposób: wartość <xref:System.Windows.FrameworkElement.MinHeight%2A> ma pierwszeństwo przed wartością <xref:System.Windows.FrameworkElement.MaxHeight%2A>, która z kolei ma pierwszeństwo przed wartością <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="be9cf-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="be9cf-107">Czwarta właściwość, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, jest tylko do odczytu i raportuje rzeczywistą wysokość ustaloną przez interakcje z procesem układu.</span><span class="sxs-lookup"><span data-stu-id="be9cf-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="be9cf-108">Poniższe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady rysują element <xref:System.Windows.Shapes.Rectangle> (`rect1`) jako element podrzędny <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="be9cf-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="be9cf-109">Właściwości wysokości <xref:System.Windows.Shapes.Rectangle> można zmienić przy użyciu serii <xref:System.Windows.Controls.ListBox> elementów, które reprezentują wartości właściwości <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>i <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="be9cf-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="be9cf-110">Dzięki temu pierwszeństwo każdej właściwości jest wyświetlane wizualnie.</span><span class="sxs-lookup"><span data-stu-id="be9cf-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="be9cf-111">Poniższe przykłady kodu obsługują zdarzenia zgłoszone przez zdarzenie <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>.</span><span class="sxs-lookup"><span data-stu-id="be9cf-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="be9cf-112">Każdy program obsługi pobiera dane wejściowe z <xref:System.Windows.Controls.ListBox>, analizuje wartość jako <xref:System.Double>i stosuje wartość do określonej właściwości powiązanej z wysokością.</span><span class="sxs-lookup"><span data-stu-id="be9cf-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="be9cf-113">Wartości wysokości są również konwertowane na ciąg i zapisywane w różnych elementach <xref:System.Windows.Controls.TextBlock> (definicja tych elementów nie jest pokazana w wybranym kodzie XAML).</span><span class="sxs-lookup"><span data-stu-id="be9cf-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="be9cf-114">Aby uzyskać kompletny przykład, zobacz [przykład właściwości Height](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).</span><span class="sxs-lookup"><span data-stu-id="be9cf-114">For the complete sample, see [Height Properties Sample](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be9cf-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be9cf-115">See also</span></span>

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [<span data-ttu-id="be9cf-116">Ustawianie właściwości szerokości elementu</span><span class="sxs-lookup"><span data-stu-id="be9cf-116">Set the Width Properties of an Element</span></span>](how-to-set-the-width-properties-of-an-element.md)
- [<span data-ttu-id="be9cf-117">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="be9cf-117">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="be9cf-118">Przykład właściwości Height</span><span class="sxs-lookup"><span data-stu-id="be9cf-118">Height Properties Sample</span></span>](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
