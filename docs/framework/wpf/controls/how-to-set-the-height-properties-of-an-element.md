---
title: 'Instrukcje: Ustaw właściwości wysokości elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 608f74afd95ce03b3ecf71819c2181a9728b25af
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356298"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="a5f80-102">Instrukcje: Ustaw właściwości wysokości elementu</span><span class="sxs-lookup"><span data-stu-id="a5f80-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="a5f80-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5f80-103">Example</span></span>  
 <span data-ttu-id="a5f80-104">W tym przykładzie przedstawiono wizualnie różnice między renderowania zachowanie między cztery właściwości związane z wysokość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5f80-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="a5f80-105"><xref:System.Windows.FrameworkElement> Klasa udostępnia cztery właściwości, które opisują właściwości wysokości elementu.</span><span class="sxs-lookup"><span data-stu-id="a5f80-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="a5f80-106">Te cztery właściwości mogą powodować konflikt, a gdy tak robią, wartość, która ma pierwszeństwo przed jest określany w następujący sposób: <xref:System.Windows.FrameworkElement.MinHeight%2A> wartość ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.MaxHeight%2A> wartość, która z kolei ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.Height%2A> wartość.</span><span class="sxs-lookup"><span data-stu-id="a5f80-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="a5f80-107">Czwarty właściwość <xref:System.Windows.FrameworkElement.ActualHeight%2A>, jest tylko do odczytu i raporty rzeczywiste wysokość zgodnie z ustaleniami interakcji z procesem układu.</span><span class="sxs-lookup"><span data-stu-id="a5f80-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="a5f80-108">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Rysowanie przykłady <xref:System.Windows.Shapes.Rectangle> — element (`rect1`) jako element podrzędny elementu <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="a5f80-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="a5f80-109">Można zmienić właściwości wysokości <xref:System.Windows.Shapes.Rectangle> przy użyciu szeregu <xref:System.Windows.Controls.ListBox> elementy, które reprezentują wartości właściwości <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, i <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5f80-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="a5f80-110">W ten sposób priorytet każdej właściwości jest wyświetlana wizualnie.</span><span class="sxs-lookup"><span data-stu-id="a5f80-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="a5f80-111">Poniższe przykłady związane z kodem obsługi zdarzeń, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a5f80-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="a5f80-112">Każdy program obsługi przyjmuje dane wejściowe z <xref:System.Windows.Controls.ListBox>, analizuje wartość jako <xref:System.Double>i dotyczy wartość określonej właściwości związane z wysokość.</span><span class="sxs-lookup"><span data-stu-id="a5f80-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="a5f80-113">Wartość wysokości są również konwertowana na ciąg i zapisywane w różnych <xref:System.Windows.Controls.TextBlock> elementów (definicja tych elementów nie znajduje się w wybranej XAML).</span><span class="sxs-lookup"><span data-stu-id="a5f80-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="a5f80-114">Aby uzyskać pełny przykład, zobacz [przykład właściwości wysokości](https://go.microsoft.com/fwlink/?LinkID=159993).</span><span class="sxs-lookup"><span data-stu-id="a5f80-114">For the complete sample, see [Height Properties Sample](https://go.microsoft.com/fwlink/?LinkID=159993).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f80-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5f80-115">See also</span></span>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [<span data-ttu-id="a5f80-116">Ustawianie właściwości szerokości elementu</span><span class="sxs-lookup"><span data-stu-id="a5f80-116">Set the Width Properties of an Element</span></span>](how-to-set-the-width-properties-of-an-element.md)
- [<span data-ttu-id="a5f80-117">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="a5f80-117">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="a5f80-118">Przykład właściwości wysokości</span><span class="sxs-lookup"><span data-stu-id="a5f80-118">Height Properties Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159993)
